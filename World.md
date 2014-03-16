Looming inside `/app/lib/world` is the base code for our [[Thang Component System]] game engine, and the heart of it is world.coffee. A Level and a World are similar--you might say that a Level "runs-a" World. The World only concerns itself with what happens in the simulation given an initial set of Thangs and Systems. Worlds always simulate deterministically, with the only varying input being the player's code as input to the `Programmable` Component configuration for one or more Thangs.

Because Worlds simulate deterministically based on the player's code, we can simulate the entire history of a World all at once in a Web Worker whenever the code changes and the player casts their spell. When the simulation is done, we swap out the old World with the new one. We try to make this really fast to get as close to live-coding as possible. Our game engine might simulate 1800 frames for 60 seconds at 30 frames per second, but we want it to happen in around a second, not a minute. This can be a challenge on large, long levels.

![An example performance breakdown of various world serialization stages for Break the Prison](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/world_simulation.png)

During the simulation, the World just advances time and updates each System in order to get the next frame until one of the Systems ends the world or its maximum lifespan is met. Each System also returns a simple hash based on what happened that frame--we can combine the hashes and determine whether this frame is the same as it was the last simulation and figure out which frame is the first that actually changed as a result of the user's code change, allowing us to automatically fast-forward past the boring parts.

When a World is done simulating, the interesting things about it are 1) its array of Thangs and 2) its array of WorldFrames. Each WorldFrame contains a mapping from Thang IDs to ThangState objects, which are almost unrecognizably optimized by now. They allow you to figure out what the important state of any Thang was at any frame in the simulation. So when you're on your [[Surface]] playing the level and you scrub to frame 33, you can restore frame 33's state for all Thangs and render that. Presto, wizards control time.

## Optimizations

It would be unbelievably slow to track and serialize every property for every Thang for every frame, so there are many optimizations.

**We only store `trackedProperties`.** Each Component that adds a property that might be interesting to display, like `pos` or `health`, will also call the Thang's `addTrackedProperty` method.

**We throw away properties that haven't changed.** In order to keep a tracked property, a Component must also, at some point, call the Thang's `keepTrackedProperty` method. For example, in the `combat.Attackable` Component, when a Thang gets hit and takes damage, it'll `keepTrackedProperty("health")`. If it never gets hit, we don't actually need to serialize the `health` property.

**We don't serialize `stateless` Thangs that don't have any changed tracked properties.** In the `existence.Exists` Component, there's an optional `stateless` property. If that's set, and none of the Thang's tracked properties are kept, then we don't need to serialize it.

**We consolidate contiguous structural obstacles into fewer Thangs.** Sometimes a level just has 230 walls. Their only function in the simulation is to collide with things, so there's code to consolidate identical, contiguous walls into the smallest number of rectangles and just use those as the Thangs instead, since many algorithms are at best O(n^2) in the number of relevant Thangs. This rectangle consolidation code is also used in the `AI` System's pathfinding and in the [Gridmancer challenge](http://codecombat.com/play/level/gridmancer).

**Sometimes we track the properties only at the end.** If we don't need to know what a property's value was at each frame, we can serialize it separately. For example, we want to know all the `target`s that a Thang has had so we can show its targeting indicators, but it doesn't matter when it had them, so the `Targeting` System calls `addTrackedFinalProperty("allTargets")` on each Thang with a `targeting.Targets` Component at the end of the World.

**We convert all state into a giant typed ArrayBuffer for serialization.** Gaze upon the World's `serialize` method and despair. This used to be a nice method before we spent several days optimizing it to be able to use [Web Worker's transferable objects](http://updates.html5rocks.com/2011/12/Transferable-Objects-Lightning-Fast). We mangled it so that we can just transfer ownership to the main thread from the web worker instead of having to serialize and deserialize all that state--an instant transfer instead of a potentially multi-second interface freeze for a large World.

**We deserialize the World across several calls.** If we can afford a second or two to simulate and serialize a World, we can only afford around twenty milliseconds to deserialize it, since deserialization happens on the main thread and blocks the UI. But deserialization isn't that fast, so we break it up into batches--when we have been deserializing for more than 20ms, we wait until the next frame and deserialize some more until we're done.

## Gods and their Angels

We don't just use one Web Worker for all our World simulations. If the player changes her code before our simulation is done, we'll want to start a new simulation. If a worker gets into an infinite loop, we'll want to abort it. If we get an error message, we might want to display it in the spell editor before the simulation is even finished. So we created a God class to muster Angels to coordinate Workers.

(You can only have so many things named Worker and Agent and WorkerBoss and WorkerBossManager before you snap.)

Each LevelView has a God which listens for spells cast and summons new Angels on the main thread to oversee simulation of the World on worker threads. The Gods and Angels even have names. It's kind of fun.

It's also possible to simulate Worlds on the main thread without using workers--we put that in for easily performance profiling and to make it run in IE 9. It completely blocks the UI, though. I heard that's bad.

## Aether and Instrumenting the Player Code

Our transpiler, [[Aether]], does things like handle, prettify, and standardize error messages. It also logs statement execution metrics and logs control flow. Soon it will also provide the necessary data to support our amazing time-travel debugger (which has yet to be written). All of this stuff needs to be serialized, though, and that's often a performance penalty--so much so that we often just turn it off for levels with lots of user code execution like Gridmancer. It needs work on the performance so we're not trying to send too much runtime information, but rather just the information the player needs to see.

Whereas most of the Thang state is consumed by the Surface, the Aether runtime information is consumed by the spell editor within the [[Tome]].

The way that player code interacts with the world is through the `programming.Programmable` [[Component]]. It gets very crazy when we are running the `programming.Plans`-provided `plan()` method in a level, so also see that Component to check out how we do piecemeal execution and yielding of control flow. Here's a brief summary.

The `programming.Plans` Component replaces `chooseAction()` with one that calls the player's `plan()` code once at the beginning. `plan()` returns a generator, and the generator partially executes the player's code, going until some action is set, and then it returns the method that set the action and its arguments.

Meanwhile, `chooseAction()` keeps running once per frame, and it repeatedly calls the method for that action until the action's goal is achieved, which is indicated by the action method returning the string `'done'` instead of some other action string (like `'move'`). When that happens, `chooseAction()` calls the plan generator again to get the next plan. If there aren't any more plans, it stops doing anything and potentially ends the level.

Now, the complicated parts are two:

1. There are no generators in JavaScript (the ES5 version), so our transpiler fakes them by making the user code into a giant switch statement that works as if you could yield inside a generator function.

2. Every action method that can be used with `plan()` (which are listed in the `plannableMethods` array in the `programming.Plans` Component) has to be set up to either return an action string or `'done'` when being called with `plan()`, to indicate whether that action is still being performed. So that's why if you look at `movement.Moves`, it has this complicated stuff around `setMove()` that returns these strings, and all the other Components which provide action methods that have been coded to work with `plan()` have similar logic for determining whether the action is the same action and should be continued, or whether it has been achieved

This is the only way to have user code actually take any real world simulation time in the middle of execution, because otherwise the user code runs all the way to the end and then the simulation resumes. Most of the levels should use `chooseAction()` directly, which is already essentially wrapped in a loop deciding what the Thang should do each frame. It's way faster and doesn't suffer from any of the complexities of `plan()`. The downside is that if the player does something like `this.move({x: 5, y: 5}); this.attack(enemy);`, then the move action and target are overwritten immediately by the attack action and target, because none of these actions take time and yield control back to the rest of the world simulation. So we try to reserve `plan()` for beginner levels.

## Goals

Each Level injects its Goals into the World via its Scripts. As events happen in the World simulation, the GoalManager tracks which goals were completed and dispatches events. Some of these Goals can be configured to end the world when they are achieved or failed. The Goal states are also serialized alongside the World and consumed by both the GoalsView and the ScriptManager (which often does things like play cutscenes and cue dialogue when goals change state).