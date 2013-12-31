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

CodeCombat's graphics are in 2.5D--you might say isometric but it's probably not exactly accurate. Sprites do not appear smaller when they are further from the camera, and parallel lines are actually parallel instead of converging to a vanishing point. All the details are in the [app/lib/surface/Camera class](https://github.com/nwinter/codecombat/blob/master/app/lib/surface/Camera.coffee): we have a default viewing angle of 48.59˚ and horizontal field of view of 30˚, which corresponds to a sphere's y-dimension appearing 0.750 times as long as its x-dimension and its z-dimension being 0.661 times as long as its x-dimension. In theory the camera could change some of these parameters, but much of the sprite art assumes them, so not everything would look right. We do have the ability to pan and zoom and to know how far away in meters the camera is from anything on the map.

The main reason we have the Camera is to easily convert between three sets of coordinates:

* [[World]] coordinates, which are in meters;
* Surface coordinates, which are in pixels; and
* Canvas coordinates, which are in pixels and account for the current camera zoom and target.

It's also possible to convert to screen coordinates, but we never ended up needing that, so it's unfinished.

## Vector art

## CocoSprite

### Marks

### Labels

### IndieSprites and WizardSprites