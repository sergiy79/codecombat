Here are some ideas that would make good summer projects for student developers. They run from beginner-level up to crazy compiler stuff and everything in between. This is a very friendly project to work on–since CodeCombat's mission is to teach everyone to code, we like to help people learn how to contribute effectively to open source, too. CodeCombat has over 250 contributors from around the world, from novices to pros. CodeCombat is written in CoffeeScript (it's basically just JavaScript), so pretty much any project will use that as a base language.

Students wanting to submit a proposal should start with the following:

1. [Get your development environment set up](https://github.com/codecombat/codecombat/wiki/Developer-environment).
1. To get a great feel for the project, make a [small pull request or two](https://github.com/codecombat/codecombat/issues?labels=good-for-newbies&page=1&state=open).
1. You should also [sign up as an Archmage](http://codecombat.com/contribute/archmage), [follow our forum](http://discourse.codecombat.com/), and watch this GitHub repository.
1. Play through [some of our existing levels](http://codecombat.com/play) to get a feel for the game.
1. Read through some of the [articles on our Archmage wiki](https://github.com/codecombat/codecombat/wiki/Archmage-Home) to better understand the code.
1. If you need help getting oriented or experience difficulties with the dev setup you can join our [HipChat room](https://www.hipchat.com/g3plnOKqa) and start talking to us about what they're passionate about doing and finding the perfect project idea. But make sure to read [the HipChat FAQ](https://github.com/codecombat/codecombat/wiki/HipChat-Room) first.

**Because GSoC applications are *very very* competitive, we'll heavily favor students who have started contributing to CodeCombat already** before submitting a proposal, because then we know you're really into the project, and we'll already be familiar from working with you. If you want to participate in GSoC, it's definitely a good idea to apply for more than one organization, since most organizations don't have enough slots to accept all their applicants. (Last year CodeCombat had 70 applicants and 4 slots.)

GSoC 2015 hasn't officially kicked off, so nothing is guaranteed, but to learn more about the Google Summer of Code application process early, see [last year's CodeCombat GSoC page](http://www.google-melange.com/gsoc/org2/google/gsoc2014/codecombat). It has last year's application template you can preview. Later, you can share applications you're working on for review with us as Google Docs shared with nick@codecombat.com and also submit something to the GSoC website [before the application deadline sometime in March](http://www.google-melange.com/gsoc/events/google/gsoc2014) so you can be in their system, too.

We are going to be ranking proposals in early April, and since mostly we care about your CodeCombat contributions, you still have time to build some cool things until then–just make sure you have submitted something to the GSoC site by the earlier deadline.

# Project Ideas

1. [Make Aether Transpiler More Friendly](#wiki-aether)
1. [Build More Levels](#wiki-levels)
1. [Create More Items, Heroes, and Special Abilities](#wiki-more-thangs)
1. [Improve Treema (JSON editor)](#wiki-treema)
1. [Build Automated Level Testing Harness](#wiki-level-testing)
1. [Add More Programming Languages](#wiki-languages)
1. [Improve iPad App Performance](#wiki-ipad)
1. [Upgrade the Level Editor](#wiki-editor)
1. [Add Classroom Organization Features](#wiki-classroom)
1. [Add Visual Effects](#wiki-effects)
1. [Organize Multilingual Audio Recordings](#wiki-multilingual-audio)
1. [Improve Game Physics](#wiki-physics)
1. [Add WebRTC Voice/Video Chat to Multiplayer](#wiki-webrtc)
1. [Add Responsive Sound / Music](#wiki-audio)
1. [Create Developer Tools Window](#wiki-devtools)
1. [Build Massively Multiplayer Sandbox Play](#wiki-sandbox)
1. [Your Own Idea](#wiki-your-idea)

### <a name="aether"/> Make Aether Transpiler More Friendly

Throughout the process of parsing, transforming, compiling, and running user-submitted code in the game world, there are hundreds of different types of info, warning, and error messages that can result. Most of these were designed for experienced programmers, like `Expected an identifier and instead saw '}'`. That doesn't help anyone learn to code if they don't know what an identifier is! Our [Aether transpiler](http://aetherjs.com/) can rewrite, anticipate, and friendly-ify all possible error messages, but each type of problem needs to be thought out and made more understandable to beginners. In addition to coming up with friendly error messages, you'll need to write a lot of abstract syntax tree traversals to find the problems before they become runtime errors.

*Expected results:* Aether's info/warning/error messages are beginner-friendly so that CodeCombat players can understand what's going wrong with their code instead of concluding that this programming stuff doesn't make sense.

*Knowledge prerequisite:* Good programming fundamentals, good writing skills, and some knowledge of CoffeeScript or JavaScript.

*Difficulty:* Medium. Most of the error messages will be simple string replacements with perhaps some interpolation, but some will require some really smart parser alterations.


### <a name="levels"/> Build More Levels

Want to make CodeCombat levels to teach regular expressions? Math? Physics? Recursion? Advanced RTS AI micro skills? Want to make super-hard dungeon crawl series? Want to do a level progression with your own game mechanics ideas? CodeCombat's level editor is yours to command! It's an extraordinarily powerful, drag-and-drop, live-programmable editor inspired by the StarCraft II Galaxy Editor, and you can use it to build just about anything. All [Artisans](http://codecombat.com/contribute/artisan) share Systems and Components, so the building blocks you create to enable custom logic in your levels will be available in everyone else's levels and vice versa.

*Expected results:* Dozens of fun, playable, polished levels that fit into CodeCombat's existing campaigns.

*Knowledge prerequisite:* An interest in game design, and basic programming knowledge. You don't need to know any programming to use the level editor, but presumably you're trying to teach some programming, so you need to know at least what you're teaching. It will also help to know JavaScript / CoffeeScript if you want to write custom Components and Systems, which will be needed if your levels are significantly different than existing CodeCombat levels.

*Difficulty:* Medium. Although the coding is easy, it takes a lot of thought to make good levels, so expect to iterate a lot on each level.


### <a name="more-thangs"/> Create More Items, Heroes, Enemies, and Special Abilities

We have hundreds of items (swords and watches and rings, oh my!) and a dozen heroes done or on the way, but as we build more and more advanced levels, we can introduce many more items, heroes, enemies, and special abilities tied to those items, enemies, and heroes. Want to make a plan for what cool items and heroes to add, figure out the game balance for them, tell our illustrator what to draw, and code up the new skills? Then you can make lightsabers, portal guns, mirror shields, flying giants, or whatever you want! The game is your playground as you create powerful new Thangs that our elite players will die for.

*Expected results:* Hundreds fun, novel, and balanced items, enemies, heroes, or abilities that fit into CodeCombat's existing campaign progression.

*Knowledge prerequisite:* An interest in game design, and basic programming knowledge. You don't need to know any programming to use the Thang editor, but if you want to add special abilities, you'll need to know enough to at least copy other abilities we've already done. It will help to know CoffeeScript for this.

*Difficulty:* Medium. Although the coding is easy, good game design takes a lot of thought and some basic mathematical modeling to ensure balance.



### <a name="treema"/> Improve [Treema (JSON editor)](http://codecombat.github.io/treema/)

Treema is a jQuery plugin that builds interfaces for editing large, complex, well-defined JSON data. It runs on tv4, which implements JSON-Schema validation. We use it for our Level, Article, and Thang editors, and it's generally useful in any project which wants to generate UIs for JSON data. It works pretty well, but there are a bunch of refactorings and improvements and upgrades that'll make it really shine, not just in CodeCombat, but in many other projects which need to deal with JSON.

*Expected results:* Treema will be polished to a gleaming shine and take over all online JSON editors.

*Knowledge prerequisite:* Basic web development knowledge and CoffeeScript or JavaScript.

*Difficulty:* Medium. Treema's code is small, but very meta, so you'll need to be able to understand some complicated schema-schemas.


### <a name="level-testing"/> Build Automated Level Testing Harness

As we get more and more levels, it becomes harder to make changes to the game engine while still making sure that we don't break the balance on any of the levels. A good solution for this will be to make an automated level testing harness where we can test game engine changes against all past levels to make sure that failing solutions still fail, successful solutions still succeed, etc. Then we'll be able to improve the game engine with much more confidence, as well as have a quick way to see which levels are having problems with their intended solutions. This would have a web front-end but probably mostly run on the server using our headless level simulator.

*Expected results:* CodeCombat has automated testing for its levels the way it has automated unit testing for its code.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Medium. The front-end will be easy, but the server code will be pretty involved, so it's a good opportunity to learn more about Node.js.


### <a name="languages"/> Add [More Programming Languages](https://github.com/codecombat/codecombat/issues/72)

The [Aether transpiler](http://aetherjs.com/) currently parses and [transpiles](http://en.wikipedia.org/wiki/Source-to-source_compiler) JavaScript, Python, CoffeeScript, Lua, Clojure, and Io code into safe, yielding, instrumented JavaScript that can be integrated into the CodeCombat game engine and other projects. If you want to see CodeCombat players play in Ruby, C, Swift, or whatever language you think you can pull off, then you'd need to write or adapt an in-browser parser for that language to the [Mozilla Parser abstract syntax tree format](https://developer.mozilla.org/en-US/docs/SpiderMonkey/Parser_API).

*Expected results:* Players can play all CodeCombat levels in the new language.

*Knowledge prerequisite:* Basic understanding of parsers. Familiarity with the language you're trying to add. CoffeeScript or JavaScript will help, but they're easy to pick up.

*Difficulty:* Harder the further away from JavaScript the language is. Something like TypeScript or Roy would be easy, whereas languages like Haskell or Ruby would be hard, and some static languages like C++ would be very hard.


### <a name="ipad"/> Improve iPad App Performance

CodeCombat is a web app written with cross-platform HTML5 in mind from the start, and we developed a complete iPad app which wraps it in Apple's new, fast WKWebView. Unfortunately, it's still too slow and uses too much memory, so we can't release it. If you like optimizing performance, here's a challenge for you!

*Expected results:* Players can have fun playing CodeCombat on iPad.

*Knowledge prerequisite:* Advanced web development optimization. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS. It may also help to know Swift and iOS development. And you'll need a Mac and an iPad 3+ to test with.

*Difficulty:* Hard. Our current efforts get it running slowly with occasional memory crashes on iPad 3 and almost smooth enough with rare memory crashes on iPad Air. We need it to be solid and smooth on iPad 3 and up, so we'll have to pull out all the stops to optimize our JS, reduce memory usage, and bundle native resources.


### <a name="editor"/> Upgrade the Level Editor

The level editor is really cool: drag-and-drop, completely configurable, and even live-programmable from within the editor itself. It's a powerful tool, but the user interface is always a challenge; the learning curve is too steep right now. You could do usability testing, improve the design, polish the rough edges, add missing features, write documentation, and generally make it easier to use such that anyone can figure it out and make their own levels.

*Expected results:* CodeCombat's level editor should be easier to use than it is now.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Easy. You can watch people try to make levels, see where they get stuck, and tweak the design until they stop getting stuck there.


### <a name="classroom"/> Add Classroom Organization Features

Teachers of students of all ages often ask us for features to manage student accounts so that they can see their students' progress, give them levels to do, and better run a classroom of CodeCombatants. It would be great to bring CodeCombat into more schools by adding the classroom organization features that teachers need and [learning tools interoperability](https://github.com/codecombat/codecombat/issues/1238).

*Expected results:* A system where teachers can create and manage groups of student accounts and get reports on their progress.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS. This will get into the server, so familiarity with Node.js or Express will also help, but aren't required.

*Difficulty:* Medium. Teachers don't need a lot of features, but the features must be well-designed and intuitive to use.


### <a name="effects"/> Add Visual Effects

CodeCombat uses [EaselJS](http://www.createjs.com/#!/EaselJS), a 2D graphics library for Canvas with a Flash-like API, for rendering the game graphics. It also has [a new WebGL-backed renderer](http://blog.createjs.com/webgl-easeljs-a-technical-intro/) that we use for awesome performance. But we could do so much more with the visuals, like adding particle emitters, faux 3D effects, drawing heroes' equipped weapons and armor, and visualizing the effects of player's code. Plus, we could dynamically adaptive performance to push up to 60 FPS when performance allows it.

*Expected results:* CodeCombat can introduce particle emitters and other visual effects.

*Knowledge prerequisite:* Basic programming skills and an interest in graphics. Knowledge of CoffeeScript or JavaScript helpful.

*Difficulty:* Easy. Getting the basic particle emitters in should be a cinch, and then after that, it's up to you how much cool stuff to add using it.


### <a name="multilingual-audio"/> Organize Multilingual Audio Recordings

We've built internationalization and localization tools allowing translation of almost all of CodeCombat's text (pretty much except for the names of the player's API methods themselves), but we still have some voiceover from the heroes that is only in English. We could organize our Diplomats to record this dialogue for us in their own languages so that even younger international players can understand it (since often they want to hear, not read, the instructions, plus having flavor sound bytes in your own language is always cool). This wouldn't take much coding, although if you can code, there is some to do to be able to use the sound files in game and visualize the recording completion coverage progress. But mostly it'll take patience and communication with all of our Diplomats to get the recordings done. Alternatively, if your coding is strong, you could build an HTML5-based speech recorder node for [Treema](https://github.com/codecombat/treema) that would allow anyone to record their language's audio from their browser, normalize the audio and remove noise using the web audio APIs, and upload it to our server in mp3 and ogg.

*Expected results:* CodeCombat's voiceover and hero flavor audio can be localized.

*Knowledge prerequisite:* Either good communication skills or good coding skills with a focus on JavaScript and web audio APIs.

*Difficulty:* Medium. Don't underestimate the difficulty of recording good audio and coordinating with dozens of contributors.


### <a name="physics"/> Improve Game Physics

CodeCombat uses a 2D physics engine with Box2D for collision detection, and we've written some basic position / velocity / acceleration stuff and locomotion dynamics, but there's so much more physics that could be done, enabling more physics-based gameplay and levels. Imagine coding the laser targeting system to solve reflection-based puzzle levels in CodeCombat, or levels where you adjust your thrust to guide your rocket. You could make that happen. Plus, we can always make it more performant, like by [implementing quadtrees](https://github.com/codecombat/codecombat/issues/358).

*Expected results:* CodeCombat should have a general physics system that enables lots of emergent physics-based gameplay while still being performant.

*Knowledge prerequisite:* Physics (mechanics) and proficiency with algorithms. Knowledge of CoffeeScript or JavaScript helpful.

*Difficulty:* Medium. The basics of the physics system are all there, so it's more about handling more mechanics and improving performance.


### <a name="webrtc"/> Add WebRTC Voice/Video Chat to Multiplayer

In CodeCombat's real-time cooperative and eventually competitive multiplayer, it's nice to be able to chat textually with other players, but it'd be even cooler to hook up voice and even video chat using the new WebRTC protocols. No more learning to code alone! You'd research and pick a high-level WebRTC library, integrate it into CodeCombat's multiplayer mode, and possibly figure out how to deal with trolls.

*Expected results:* Players can talk to each other and even see each other if desired.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Easy–WebRTC libraries do most of the work for you.


### <a name="audio"/> Add Responsive Sound / Music

We have some great music and sound effects, but they don't do enough to add to the immersion, since the sound and music that plays is often not adapting to what's going on in the game. Doing some smart music switches and possibly audio processing in the browser could go a long way toward adding to the fun. There's some really good audio APIs that would be great to put through their paces.

*Expected results:* CodeCombat's music and sound would adapt to the game environment for an immersive game experience.

*Knowledge prerequisite:* Basic programming knowledge and an interest in game design. Knowledge of CoffeeScript or JavaScript helpful.

*Difficulty:* Medium. In addition to figuring out the audio processing stuff, it's going to require a good design sense to figure out what music and sounds should play when and how they should be processed.


### <a name="devtools"/> Create [Developer Tools Window](https://github.com/codecombat/codecombat/issues/35)

One thing that would make it much easier for Archmages to contribute to the CodeCombat code would be a way for them to see what's going on with the site as they're on it. Anywhere on the site, the developer could click a button or press a shortcut and open a Developer Tools like interface in a separate window which includes:

1) Current view and subviews. They could be clicked to highlight what element that view represents. Show the module path for each one.
2) Current instances of other classes and models and collections in existence.
3) Events, subscriptions and keyboard shortcuts currently active, and what they call.
4) Active log of events, subscriptions and keyboard shortcuts as they happen.
5) Regular updating of all these as they change.

This could be used to:

1) Edify an Archmage on what is going on with a given view. See what files are involved and how they're involved and how they communicate with one another.
2) Debug issues involving tearing down objects and views and investigating memory leaks.

This could be created as its own open source project for all other Backbone-powered sites to use as well. We may want to build off of Backbone debugger extensions for [Chrome](https://github.com/Maluen/Backbone-Debugger) and [Firefox](https://github.com/dhruvaray/spa-eye).

*Expected results:* It'll be easy for developers to find the code that's active in the app.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS. Familiarity with Backbone helpful.

*Difficulty:* Easy. All of the info should be present in the Backbone view hierarchy at any time, so designing and implementing the UI will be most of the work.


### <a name="sandbox"/> Build Massively Multiplayer Sandbox Play

CodeCombat currently simulates a level from beginning to end every time the code changes and replaces the past, present, and future with the new results for a live-coding experience. This limits the size of the game levels that we can run, though. It would be fascinating to experiment with a persistent game world in which players' code changes didn't change the past. We could support huge levels with many players in open sandbox play, like Minecraft but actually programming the algorithms instead of executing them with zillions of pickaxe strikes. You would create a new game mode where the synchronous multiplayer (which already works) doesn't result in history replacement, then see how big you could make it and experiment with game design to find a sandbox environment that's really fun.

*Expected results:* CodeCombat should support a massive, persistent game world mode for sandbox play.

*Knowledge prerequisite:* Good programming fundamentals, some knowledge of CoffeeScript or JavaScript, and an interest in game design.

*Difficulty:* Very hard.


### <a name="sandbox"/> Your Own Idea

Want to do something else, or some combination or remix of ideas from this list? Just talk to us and let's figure out how to do it! These ideas are just starting points; really, we want you to work on what you're passionate about doing and confident that you can pull off. Whatever it is, just keep in mind that the more players it can help, the better.

*Expected results:* Your brilliant idea is implemented in CodeCombat. A choir of angels rejoices.

*Knowledge prerequisite:* Whatever the idea is, just make sure you know enough to get started, and we can help you learn the rest along the way.

*Difficulty:* Up to you!