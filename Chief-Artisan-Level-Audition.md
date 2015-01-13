# Chief Artisan Level Audition

![](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/recruiting_banner.png)

You've read the blog post, you've asked us any questions about the job, and you're ready to try building a level, both to see if you like it and to prove that you've got what it takes even in the face of undocumented, horrifyingly complex tools like the CodeCombat level editor. Perfect! Here's the level design that you should implement. We normally design big batches of levels at a time with about this level of detail, so apart from working with us during the design sessions, this is how you'll do it if we hire you.

## The Level Design

This level is a theoretical level that would come right after Coinucopia, midway through the forest campaign. If you haven't gotten there yet, go play the campaign and come back, because otherwise you're not going to be able to understand what the player knows and doesn't know by this point. 

This one is a battle between humans and ogres, with both sides being spawned randomly by a Referee Thang. You'll probably want to use human soldiers and archers of both genders for the human troops. For ogres, try munchkins, medium male ogres, throwers, and shamans. Don't spawn all the guys at once, but spread it out a bit for maximum combat. All of this can be configured in the Referee Component for good randomization and waves. **Make sure you name the `buildType` exactly like you see in the Referee Component code, like `"soldier-m"` or `"ogre-munchkin-f"`, or it'll spit out a JS console warning and your waves will just spawn 15 Thangs.** (We'll make this less tricky soon.)

Make the balance such that the ogres are slightly winning, but that the hero can turn the tides of battle by contributing a little bit to the fight. The level should end in failure if the hero dies. Probably what the player should do is run to pick up the flag if there is a flag, otherwise fight. This way, they can fight until they're almost dead, then run away (or they can target ranged units behind the enemy lines). The player should die if they just do the naive loop-attack-nearest-enemy strategy unless they have bought some really sick gear. Don't worry if it can be balanced for ranger/wizard, since you probably don't have those heroes to test with (only subscribers will): it mainly needs to work for warriors.

Write the sample code to guide the player to use flags like this. Remember, they just saw flags in Coinucopia for the first time, so they need a lot of guidance on how to use them. You may even want to write a script in the Scripts tab that reminds them to press Submit at the right time so that they can use their flags, although maybe sample code comments is good enough for this. (You don't want to write too many sample code comments; keep it concise.)

I imagine the most common solution code would go like this:

```python
loop:
    enemy = self.findNearestEnemy()
    flag = self.findFlag()
    if flag:
        self.pickUpFlag(flag)
    elif enemy:
        if self.isReady("cleave"):
            self.cleave(enemy)
        else:
            self.attack(enemy)
```

Turn that into a skeleton in the player's sample code (in the programming.Programmable programmableMethods plan() source and languages config) so that they will be able to figure out what to add to finish the level.

When you're done spawning guys, balancing the waves, setting up the goals, and writing the sample code, decorate the level. You may find [these keyboard shortcuts](https://github.com/codecombat/codecombat/blob/master/app/views/editor/level/thangs/ThangsTabView.coffee#L57-L76) useful. Don't let the decorations interfere with line of sight and gameplay.

In the Settings tab, if you add a Tasks entry, it'll make a default checklist for you of things that need to be done to finish the level. You don't have to do all of these, but see how many you can figure out.

## Implementation Tips

You will probably want to either watch the [Mirage Maker level creation screencast](https://vimeo.com/codecombat/mirage-maker) or dig around in the level editor for levels like [Dust](http://codecombat.com/editor/level/dust) to see how things are set up. (Hint: check the Referee Component on the well.) Note that the rest of the docs on this Artisan wiki may be out of date.

When you make your level, you can call it whatever you want, but keep it private (don't publish it) so that other would-be Chief Artisans can't copy it. So basically don't check the "Publish" checkbox when you save your level.

When (not if, but when) you get stuck with something, pop by our [HipChat room](http://www.hipchat.com/g3plnOKqa) and ask. Hopefully we'll be awake and can help get you unstuck.

## Audition Tips

We don't want you to have to spend a zillion hours polishing this level, so just spend a few hours on it or until you think you've made a pretty good draft. When you're done, let us know and we'll check it out.

Don't start building the level until you've introduced yourself to us and asked any questions you have about the job.

Save often.

Look at other levels for inspiration on how to do things. The very latest levels at the end of the desert have the best examples, because we constantly improve our tooling to make common level scenarios easier.

Common gotcha/bug: if you see a problem with the level ending early and you have a "Kill the ogres (34/35)" thing going on, or if it doesn't end, try just naming the kill ogres goal with ID "ogres-die" and removing the "Kill Thangs" criterion from it. The Referee will mark it successful once all waves have spawned and then those ogres die. We just need to fix this bug so it actually works, but this is the workaround.

When you're ready to start, go to [the level editor](http://codecombat.com/editor/level), hit 'Create New Level', and have fun!

![](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/artisan_banner.png)