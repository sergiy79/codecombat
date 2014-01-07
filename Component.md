In our [[Thang Component System]] architecture, the Components are the building blocks that attach real data and behavior to Thangs. (Normally, Components in this type of system don't contain code, but in our system they do--in fact, they're mostly code.)

Note that because we don't yet safely sandbox Component code and haven't quite finished those permissions, you can't actually edit Components yet as a non-admin. So to edit them and add new ones, [install the local server](Developer Environment) and create a local account there, which will automatically be an admin account. Then [send us](Developer Organization) the Component edits for review and addition to the live site.

Let's do a series of examples. We'll start with a Thang named William with [[ThangType]] of [Soldier](http://codecombat.com/editor/thang/soldier]). William has these Components by default:

* `action.Acts`
* `ai.ChasesAndAttacks`
* `ai.AutoTargetsNearest`
* `alliance.Allied`
* `collision.Collides`
* `combat.Attacks`
* `event.HasEvents`
* `existence.Exists`
* `hearing.Hears`
* `hearing.Says`
* `movement.Moves`
* `physics.Physical`
* `targeting.Targets`
* `ui.Selectable`
* `vision.Sees`

I don't want William to be able to hear, say, or see anything, so I might just delete those Components. I do, however, want him to jump. A lot. So I'll go and add the `ai.JumpsTooMuch` Component. When I do that, the editor also adds the `movement.JumpsStraightUp` Component, since that's listed as a dependency of the `ai.JumpsTooMuch` Component.

![movement.JumpsStraightUp Component configuration](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/jumps_straight_up_component.png)

Let's make him be able to jump twenty meters in the air. Cool. But what if I didn't like the way he was jumping? After all, wouldn't it be cooler if he jumped *really fast*, hovered at the top, and then fell faster than gravity? Let's go and edit the `movement.JumpsStraightUp` Component code itself in the Components tab of the level editor.

![Code for the movement.JumpsStraightUp Component](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/jumps_straight_up_component_code.png)

I can see the default code has this `update` method:

```coffee
  update: ->
    if @action is 'jump' and @isGrounded() and @act()
      @velocity.z = @world.gravity * @jumpTime / 2
```

Basically, the Thang just sets its initial velocity once at the time of the jump, and that's it. Let's update all the time we're in the air, too, though, and mess with our trajectory some more:

```coffee
  update: ->
    if @action is 'jump' and @isGrounded() and @act()
      @velocity.z = @world.gravity * @jumpTime / 2
    else unless @isGrounded()
      # Add some code here that accelerates the up-and-down phases
      # and extends the floating phase
```

I can then just press Play in the upper right to test out my new code in a child window, without saving or reloading anything, until I get the behavior just right. When I'm satisfied, I can then save [a new version](Versioning) of `movement.JumpsStraightUp` and enjoy the more-dramatic jumping across all my levels.

*By the way, I didn't actually write the code to make the jumps more dramatic--if you think that'd be cool, it may be a fun exercise. We'd just want to make sure we didn't change the total jump time.*

But maybe I don't want all units to jump dramatically--it should be an option in the Component configuration for each Thang. Let's add it:

![Adding a jumpsDramatically property to the Component config](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/jumps_straight_up_component_config.png)

See our [[JSON Schema]] info for more on how to structure these. Then I can update my code just like this:

```coffee
  update: ->
    if @action is 'jump' and @isGrounded() and @act()
      @velocity.z = @world.gravity * @jumpTime / 2
    else if @jumpsDramatically and not @isGrounded()
      # Add some code here that accelerates the up-and-down phases
      # and extends the floating phase
```

Components automatically copy all the properties from their `config` constructor argument to their target Thangs, and we're fine with the default being falsy if we haven't specified it, so we don't need to do anything else to have access to the `jumpsDramatically` property here.

Components can be as simple as adding a single property, like the `movement.Land` Component just adding  `isLand`, or as complex as managing the entire programming environment, like the `programming.Programmable` Component.

To see all the entity data for, say, the `movement.JumpsStraightUp` Component, I can just go to [http://localhost:3000/db/level_component/jumpsstraightup](http://localhost:3000/db/level_component/jumpsstraightup).