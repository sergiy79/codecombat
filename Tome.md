The TomeView contains all the spell editors within a challenge:

![An example SpellView inside the TomeView for Zone of Danger](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/tome_00.png)

You can see it in [app/views/play/level/tome](https://github.com/codecombat/codecombat/tree/master/app/views/play/level/tome). It contains subviews like:

* **CastButtonView** - displays spell changed status, click to cast, edit autocast settings
* **SpellListTabEntryView** - shows which Thang and Spell are selected, includes spell reload button
    * **ThangAvatarView** - for the currently selected Thang 
* **SpellListView** - owned by TomeView, but triggered from button in current SpellListTabEntryView
    * **SpellListEntryView** - one list entry per selectable spell
        * **ThangAvatarView**s - showing which types of Thangs share this spell
        * **SpellListEntryThangsView** - select which Thang to edit for this Spell
            * **ThangAvatarView**s - one for each Thang of a given type which shares this spell
* **SpellView**s - zero or one displayed at a time depending on which Thang and Spell are selected
    * An **[ACE editor](http://ace.c9.io/)** instance, possibly hooked up to [Firepad](http://www.firepad.io/#1) for real-time collaborative editing
    * **ProblemAlertView**s - display user code problems overlaid on bottom of the spell editor
* **SpellPaletteView** - shows which methods/properties are available in this level
    * **SpellPaletteEntryView**s - hover for docs and current value for an available property
* **ThangListView** - quick way to select a Thang and see which Thangs can be cast
    * **ThangListEntryView**s - see available spells for a Thang
    * **ThangAvatarView** - shows the Thang's face

Each Spell has a SpellView and a SpellListTabEntryView associated with it, and it might have multiple Thangs. This is because sometimes Thangs can share a spell, like if you want Max, Jax, and Dax to all run Max's code. They might have different runtime information, though--Jax might throw an error when Max doesn't with the same code, because maybe Max dies before he gets to the point where the code errors out, say. Or Dax might execute different if-else statements because he's too far away. The SpellView displays control flow and problems, so even though Thangs may share Spells and SpellViews, you still always have to know which Thang is selected so you know which runtime information to show.

![Example of multiple Thangs sharing a spell: TomeView -> SpellListView -> SpellListEntryView -> ThangAvatarView + SpellListEntryThangsView -> More ThangAvatarViews](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/tome_01.png)

Phew! If you think that's fun, you can watch Nick spend a couple days coding it during his [epic coding time-lapse video](http://www.youtube.com/watch?v=E0qlr22cF14).

Some of the background images, like for the SpellListTabEntryView and ThangListView, are totally temporary and should be replaced with something awesome. There are other things to do with all these related views, but most improvements are probably lying within the SpellView itself.

## SpellView

This is CodeCombat's code editor itself. We used to call it the editor, but there are enough editors (Level Editor, Thang Editor, Article Editor, etc.). So instead of "code" it's often "spell", and instead of "editor" we have the overarching "tome". Kind of a wizards-scribing-spells-on-scrolls metaphor.

If you want to do anything with ACE itself, the [ACE docs](http://ace.c9.io/#nav=api) are nice. We wrote [the Firepad ACE adapter](https://github.com/firebase/firepad/blob/master/lib/ace-adapter.coffee), so if there's something going wrong in Firepad, it's probably our fault, but at least we know how to dig in there.

Many of the improvements one might want to make should actually be made in our [Aether transpiler](Aether), since that's what powers everything that happens to a player's code after she types it, from linting to transpiling to showing error messages to displaying runtime execution information.

### Configuring ACE

The ACE editor is immensely powerful and has many options available, like text themes, code snippets, smart editor behaviors, Emacs / vim modes, and more. Unfortunately, those aren't exposed in any sort of [configuration menu](http://ace.c9.io/build/kitchen-sink.html) yet--a wonderful addition to make for any enterprising Archmage--so they're just configured in the `createACE` method of SpellView right now. Note that we removed all the themes except the one we are using from `app/assets/lib/ace` (the funny path is for making sure the ACE requires go through all right when copied to the public folder), so if you want to try another, grab it from [the ACE builds repo](https://github.com/ajaxorg/ace-builds/tree/master/src-min-noconflict).

### Keyboard Shortcuts

All the keyboard shortcuts in the LevelView must go through the SpellView, because we force-focus ACE whenever possible so that players don't have that horrible problem of trying to type code and not realizing that the code isn't actually going into the editor (especially a problem for young players and hunt-and-peck typists). You can see them in the `createACEShortcuts` method. Things like being able to skip to the next script, start/stop playback, cast the current spell, etc.

We are hard-pressed to find shortcuts that don't affect typing in ACE and don't conflict with popular shortcuts for the browser and OS, though. There has to be a better way to find good shortcuts without just trying some and waiting for [someone with an Icelandic keyboard](http://discourse.codecombat.com/t/cant-enter-square-brackets-in-code-window/112/5) or a [different keyboard usage pattern](http://discourse.codecombat.com/t/capture-ctrl-s-might-make-the-experience-better-for-new-players/126/2) to tell us it won't fly. Thoughts welcome.

### Multiplayer and Firepad

Currently, when you play a level, ACE is instantiated and starts saving the code to the CodeCombat MongoDB using the LevelBus. It's single player to take unnecessary load off of Firebase. When you enable multiplayer, though, it goes into multiplayer mode, hooking up [Firepad](http://www.firepad.io/) and starting to sync edits there in realtime. So think about that when changing things and when you are seeing bugs: is it in single player mode, multiplayer mode, or both?

### Code Change Callbacks

The `createOnCodeChangeHandlers` section is interesting. There are various low- and high-cost things that we might want to do whenever the player's code changes, ranging from showing other players that your wizard is casting to updating error messages to casting the spell. To get good performance while still being performant, we try to [debounce](http://lodash.com/docs#debounce) and [throttle](http://lodash.com/docs#throttle) these, and we separate them into handlers that run when there's any change vs. handlers that only run when there's a significant change.

When has the code significantly changed? This can be hard to determine; the code actually lies within [[Aether]]. Generally, it's when the abstract syntax tree that you get when you parse with Esprima changes--so we ignore things like whitespace and comments as best we can. There are some complications in that Aether's linting output might change even though the AST doesn't change, so we actually do `updateAether` on any change, but try to return early before transpiling the whole thing again if we realize that we don't need to. `updateAether` gets you to the full-blown error message display, and if the code is significantly the same as the last time it was actually cast, it'll also include runtime information, like highlighting the lines which have run and the current line.

![Example of the runtime information and error display](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/tome_02.png)

But often the code isn't the same as when it was cast, so in those cases, we hide most of the runtime information, since it might not be accurate. We do display lint problems, but only with the gutter annotations, not the error alert, since we don't want to be in the player's face with potential problems when they haven't cast the spell yet.

You may think it silly that the error messages don't include line numbers. They should, but at some point we broke it. Help fixing that up in [[Aether]] would be awesome!

### Smart Autocast

When you're talking about beginning programmers, researchers have identified three types: stoppers, movers, and tinkerers. Stoppers give up too easily and don't play around to find solutions enough. Tinkerers are on the other end: they just try things too often without really thinking about what they're doing enough. In the middle, where we want players to be, are movers: they think a bit, try something, and see what happens. JP Posma over at [jsdares](http://jsdares.com) suggests in [his thesis](https://github.com/janpaul123/jsdares/blob/master/misc/thesis/thesis-jan-paul-posma.pdf) that the perfect interface would speed stoppers up and slow tinkerers down. This is why CodeCombat spells autocast by default.

If we trigger an autocast when the player isn't ready, it's frustrating, because it's going to throw errors or do the thing they don't want just before they got it to the point where they think it'll do the thing they do want. So we don't want to autocast except when we think they player has the code in a meaningful state. Our heuristics include checking for any lint or parse errors and seeing if the player's cursor is at the beginning or end of a line. If those are true, we cast immediately. If not, we want until the set autocast delay (default of 5000ms) and then cast, since we can't actually show errors until we cast, so leaving it on manual isn't friendly except for experienced programmers. More heuristics could make this even better.

(We A/B tested this on fifty thousand students and found that an autocast delay of 3000ms was equivalent to 5000ms, but that the manual cast had significantly worse level completion rates, even after the first level where they must have learned how to use it to continue, lending support to JP's speed-up-the-stoppers idea.)

Autocasting inappropriately has still been a major complaint of experienced programmers, though, so further improvements are needed.