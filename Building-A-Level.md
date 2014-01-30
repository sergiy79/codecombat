## Steps

### PreProduction

1. **Come up with a level idea**. If this is your first time building a level, we recommend something fairly simple, or a variation on an existing level.

### Production

1. **Create your level**. Got to the [level search page](http://codecombat.com/editor/level) and either make a brand new, blank level, or pick a level from the list and fork it, copying all the existing logic to have something to start from.
1. **Place down Thangs in the Thangs tab**. The Thangs tab is the tab open by default. [Read more...](Thangs Tab)
1. **Configure your Thangs**. Double click on A Thang in Thangs tab to edit its Components. [Read more...](Editing Thang Components)
1. **Setup Scripts**. These add dialogue, goals, music and more to your level. [Read more...](Scripts Tab)
1. **Add Details**. In the Settings tab, give your Level a description, documentation, and a victory screen. [Read more...](Settings Tab)
1. **Configure Systems**. These control some higher level things associated with systems that don't often need to be changed, like teams, UI and gravity. [Read more...](Systems Tab)
1. **Roll your own Components and Systems**. This is rather advanced, and due to security concerns, not enabled by default (we'll be building a community review system in the future so that it can be enabled). If you would like to do some custom logic, you can edit and add systems and components in the level editor but you won't be able to save them. Get in touch with us through our [public HipChat room](http://www.hipchat.com/g3plnOKqa) and we'll help you out.
1. **Test test test**. Click 'play' in the upper right corner to play your level.
1. **Save and publish**. Check 'publish' when saving your Level to make it accessible to anyone.

### Iteration

No matter what you're building, regular and frequent iteration is key to making something incredible. Make a level and as soon as it's even a little bit usable, share it with us, with others, with anyone to get feedback. If you're not embarrassed by what you've built when you first demonstrate it, you're waiting too long.

To get feedback:

* Show us and others hanging out in our [public HipChat room](http://www.hipchat.com/g3plnOKqa).
* Post on the Artisan section of our [Discourse forum](discourse.codecombat.com/category/artisan).
* Link friends and family to it and have them play it.
* If you want the best possible result, consider UX testing it. It's a tough skill to learn, but extremely valuable.

## How Autosave Works

Whatever edits you make are saved in [localStorage](https://developer.mozilla.org/en-US/docs/Web/Guide/API/DOM/Storage#localStorage) until you save them in the database. This way if you reload the page, any changes you make to the Level, Components and Systems are not lost. These are only stored locally on your browser, though, so if you clear your browser data any backups are lost. And you can only access those changes on the browser of the computer you used to make those changes. It's a fairly simple system to take the edge off the all-too-common case of losing work by closing the tab or reloading accidentally or the tab crashing.

If you want to throw out changes to anything, click 'revert' in the upper right area, and you can select what to revert.