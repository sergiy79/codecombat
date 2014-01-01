CodeCombat uses [EaselJS](http://www.createjs.com/#!/EaselJS) for graphics, which is part of the CreateJS suite for rich HTML5 web apps. It mimics the Adobe Flash APIs and can do many of the things Flash can do. The **Surface** is what we call the thing that manages the EaselJS Stage on top of an HTML5 canvas. It handles updating all of our 2.5D sprite graphics.

![Sprites!](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/surface_00.png)

Each LevelView has a Surface, and each LevelEditView's ThangsTabView has one, but you don't need one to display a CocoSprite--you can just put those on top of an EaselJS stage, as is done in the ThangAvatarView, Thang Editor, and the home page. It's only when you want to take a [[World]] and display its [[Thang]]s that you need a Surface.

To make dealing with all the CocoSprites easier, each Surface has a SpriteBoss. The SpriteBoss makes a CocoSprite for each Thang that exists in the World at the current frame, adding and removing sprites when Thangs appear or disappear as time changes or spells are recast. It also tracks CocoSprites that are not actually part of the World simulation, like WizardSprites and sprites that are controlled just by Scripts--we call these IndieSprites.

The Surface has many Layers, and some of these Layers have child Layers. One of the important things to do to get good performance out of EaselJS is to cache DisplayObjects and only redraw them when needed, so we've split things into layers whenever it's needed either for z-indexing purposes or for caching purposes. For example, all obstacles (like Dungeon Walls) go into an `"Obstacle"` Layer, which is then cached, so that we don't have to redraw every sprite in it every frame but can instead blit the whole cached thing as an image to the canvas. This goes on top of the `"Ground"` layer, which does the same thing for all Lands. Here are the Layers so far:

* Surface Layer - moves and scales with the camera
    * CameraBorder - an outer shadow to indicate the viewport boundary
    * Grid - blue lines with labeled ticks (needs a lot of work)
    * Choosers - point/region overlays for choosing script targets in the level editor
    * Sprite Layers - the SpriteBoss will assign CocoSprites and their Marks to these
        * Land - below everything (grass, dungeon floor); cached
        * Ground - anything that should sit on the ground, like selection and target Marks
        * Obstacle - walls and obstacles that won't ever move and can't have sprites behind them; cached
        * Path - past/future path indicators are drawn here
        * Default - most CocoSprites go here, with stacking determined by their Thangs' y- and z-coordinates
        * Floating - Wizards, health bars, and above-head Marks go on top
* Surface Text Layer - moves but does not scale with the camera
    * CoordinateDisplay - shows (x, y) coordinates on mouse hover
    * CocoSprite Labels - like Wizard names and `say()` speech bubbles
* Screen - independent of camera
    * Letterbox
    * DebugDisplay

Layers also respond differently to changes in Camera zoom and target. Things inside a Layer don't have to worry about those sorts of transforms, since the parent Layer knows what to do.

## Camera

CodeCombat's graphics are in 2.5D--you might say isometric but it's probably not exactly accurate. Sprites do not appear smaller when they are further from the camera, and parallel lines are actually parallel instead of converging to a vanishing point. All the details are in the [app/lib/surface/Camera class](https://github.com/codecombat/codecombat/blob/master/app/lib/surface/Camera.coffee): we have a default viewing angle of 48.59˚ and horizontal field of view of 30˚, which corresponds to a sphere's y-dimension appearing 0.750 times as long as its x-dimension and its z-dimension being 0.661 times as long as its x-dimension. In theory the camera could change some of these parameters, but much of the sprite art assumes them, so not everything would look right. We do have the ability to pan and zoom and to know how far away in meters the camera is from anything on the map.

The main reason we have the Camera is to easily convert between three sets of coordinates:

* [[World]] coordinates, which are in meters;
* Surface coordinates, which are in pixels; and
* Canvas coordinates, which are in pixels and account for the current camera zoom and target.

It's also possible to convert to screen coordinates, but we never ended up needing that, so it's unfinished.

## Vector art

CodeCombat's sprite art is all stored in the database in vector format, which lets us go resolution independent and save a lot of download time compared to our old raster art system. The sprite sheets are built on the fly from the vector data when you go to play a level. See [app/lib/LevelLoader.coffee](https://github.com/codecombat/codecombat/blob/master/app/lib/LevelLoader.coffee) for how that's done. The vector art files are exported from Adobe Flash Creative Cloud targeted at CreateJS, and we wrote a custom parser to pull the animation data from the exported JavaScript files. That stuff is in the [app/lib/sprites](https://github.com/codecombat/codecombat/blob/master/app/lib/sprites). Then there's the [[Thang Editor]], which provides a GUI for turning those vector sprites into a usable ThangType that can be used in the [[Level Editor]]. Since the sprite export and Thang Editor import are a bit tricky, you probably don't need to know about them; unless someone really wants to work on them, they'll be an undocumented internal use tool.

## CocoSprite

EaselJS has a Sprite class, which is a subclass of DisplayObject and allows for animations. So we called our sprite class, which "has-a" Sprite, a CocoSprite instead. Actually, CocoSprite has an `imageObject` and a `displayObject`; its `displayObject` is an EaselJS Container, and *that* has the `imageObject` as a child (as well as perhaps a health bar, and maybe eventually other children). Probably the health bar should just become a Mark, at which point we might not need to have a separate container.

When the Surface updates, it tells its SpriteBoss to update, and the SpriteBoss tells each CocoSprite to update, which makes the CocoSprite do things like move to new positions and change its action animation and such. It also tells its Marks and Labels to update. Some of these updates are avoided when we know nothing has changed.

CocoSprites have to have associated `thangType` properties which tell them both what sprite sheet data to use to draw themselves and also how to do various offsets, so that we can do things like place shadows below them and health bars above them and speech bubbles off to the sides of their heads. They also usually have a `thang` property, which gets updated to the proper [[World]] state each frame, and from which they update their display accordingly.

They also know how to play sounds depending on what action they're taking (if it's the first frame that they're acting, so `actionActivated` is true), whether any World events happened to them that frame (like if they took damage or collected an item), and if they said anything.

### IndieSprites and WizardSprites

IndieSprites are not actually part of the World simulation. In the first level, Captain Anya doesn't take part in the World simulation--she just shows up to say some dialogue and be moved around by scripts. IndieSprites get added to the Level by configuring the UI [[System]]. Since their `thang`s aren't part of the World, they aren't affected by things like updating positions and actions when playback time changes.

WizardSprites are a subclass of IndieSprites. They represent the players in a Level. Mostly they just move around to follow a player's Thang selection or camera focus, bobbing up and down, indicating presence. They also respond to players typing code by starting their cast spell animation, so you can see who is editing which Thangs' spells.

We are soon going to be adding more than one ThangType of WizardSprite, as well as allowing players to customize the colors of their Wizards by dynamically tinting their sprite sheets as they are being created.

### Marks

Related to CocoSprites are things like targeting and selection indicators, highlight arrows, shadows, broken code "repair" animations, and soon, range indicator radii. These Marks stay with the sprite, but may have to go on another layer to do the z-indexing properly. The selection and target Marks, each being singular, are controlled by the SpriteBoss instead of by a particular CocoSprite. Check the [Mark class](https://github.com/codecombat/codecombat/blob/master/app/lib/surface/Mark.coffee) for details.

### Labels

Labels are like Marks, but for text, since we don't want the text to actually scale really huge when you zoom in--they're on the Surface Text Layer. They're associated with CocoSprites just like Marks. They're used for things like Wizard names, `say()` blurbs, and script dialogue bubbles. Check the [Label class](https://github.com/codecombat/codecombat/blob/master/app/lib/surface/Label.coffee) for details. There's some gnarly code in there for styling text within EaselJS that should be improved, since two of the styles should be merged and don't look very good right now.

### Paths

![Paths example](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/surface_01.png)

CodeCombat uses these path indicators to give hints to the past and future positions, actions, and targets of Thangs, since otherwise you'd have to manually scrub through time to figure out what's going to happen or has happened each time you change the code. The visual styling can get overwhelming sometimes, and the performance is often horrendous, so we want to try another approach that scales better. If we could find a way to do animated, fading-out footprint trails, that would be awesome.

In a Level's UI System, one can configure whether paths show up never, when the level is paused, just for the selected unit, or always. This is done on a per-level basis based on whether and when it's overwhelming or useful to see paths in that level. Probably what we should do is to add an option or shortcut for players to toggle through the path settings, too.

### Other Stuff

* The **Dimmer** lets us darken parts of the Surface, when it's disabled, to focus visual attention on the parts we leave undimmed. Its performance is bad and it doesn't look that great, but it's often necessary from a UX perspective. Something better that fulfills the same role of focusing the player's attention would be useful.
* The **Letterbox** comes into play once we go into a script cutscene moment, just to make things look more cinematic. It's just two black bars at the top and bottom. It also disables playback control when it's on.
* The **CoordinateDisplay** shows (x, y) coordinates when the player hovers over the map, and can be turned on/off per-level in the UI System config. It's sometimes necessary, but not very discoverable and not liked. Better solutions are welcome.
* The **PointChooser** and **RegionChooser** are used in the Level Editor to help make targeting scripts easier.
* The **CameraBorder** is a sort of inner shadow around the edges of the Camera bounds to indicate that the player can't scroll past there.
* The **DebugDisplay** shows which frame is selected and what the current framerate is (for monitoring performance). The shortcut that turns it on also turns on collision shape overlays for all Thangs which collide.