Here are some ideas that would make good summer projects for student developers. They run from beginner-level up to crazy compiler stuff and everything in between. This is a very friendly project to work on–although CodeCombat's GitHub has only been open a month at the time of writing, it already has 49 contributors from around the world, both novices and pros. CodeCombat is written in CoffeeScript (it's basically just JavaScript), so pretty much any project will use that as a base language.

# Projects

### Add [More Programming Languages](https://github.com/codecombat/codecombat/issues/72)

The [Aether transpiler](http://aetherjs.com/) currently parses and transpiles JavaScript (and soon CoffeeScript) code to safe, yielding, instrumented JavaScript that can be integrated into the CodeCombat game engine and other projects. If you want to see CodeCombat players play in Python, Haskell, or whatever language you think you can pull off, then you'd just need to write or adapt an in-browser parser for that language to the [Mozilla Parser abstract syntax tree format](https://developer.mozilla.org/en-US/docs/SpiderMonkey/Parser_API).

*Expected results:* Players can play all CodeCombat levels in the new language.

*Knowledge prerequisite:* Basic understanding of compilers. Familiarity with the language you're trying to add. CoffeeScript or JavaScript will help, but they're easy to pick up.

*Difficulty:* Harder the further away from JavaScript the language is. Something like TypeScript or Roy would be easy, whereas languages like Python or Ruby would be hard, and some static languages like C++ would be very hard.

### Devise Mobile-Friendly Programming Interface

CodeCombat, a web app written with cross-platform HTML5 in mind from the start, should be able to run anywhere, but it currently doesn't work on iPads and most mobile devices because the [ACE code editor](http://ace.c9.io/) doesn't support them. Even if it did work, typing code on mobile is no fun. You'd design and implement an alternative interface to typing in code for mobile devices.

*Expected results:* Players can have fun playing CodeCombat on mobile.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Medium. The implementation shouldn't be too hard, but the design itself will be critical. Simply adding [a code-focused keyboard](https://itunes.apple.com/app/id599976903?mt=8&&referrer=click%3Dd351443d-765b-4f58-a4e7-83d4e9e87fbf) or [Blockly](https://code.google.com/p/blockly/) isn't going to be enough.

### Integrate WebGL Renderer

CodeCombat uses [EaselJS](http://www.createjs.com/#!/EaselJS), a 2D graphics library for Canvas with a Flash-like API, for rendering the game graphics. EaselJS has introduced [a new WebGL-backed renderer](http://blog.createjs.com/webgl-easeljs-a-technical-intro/) that could be used for crazy performance and visual effects galore, but only on a subset of CodeCombat's graphics. You'd add a second SpriteStage on top of the existing Stage to draw the parts that can be accelerated, then have fun pushing the performance, particle emitters, and 3D effects to the max. You'd also do a before-and-after optimization comparison to see just how large a game level CodeCombat can support–will you be the one to unlock epic battles at 60 frames per second?

*Expected results:* CodeCombat can use WebGL where supported for better graphics effects and performance.

*Knowledge prerequisite:* Basic programming skills and an interest in graphics. Knowledge of CoffeeScript or JavaScript helpful.

*Difficulty:* Easy. Getting the basic SpriteStage integration in should be a cinch, and then after that, it's up to you how much cool stuff to add using it.

### Add WebRTC Voice/Video Chat to Multiplayer

In CodeCombat's real-time cooperative (and eventually competitive) multiplayer, it's nice to be able to chat textually with other players, but it'd be even cooler to hook up voice and even video chat using the new WebRTC protocols. No more learning to code alone! You'd research and pick a high-level WebRTC library, integrate it into CodeCombat's multiplayer mode, and possibly figure out how to deal with trolls.

*Expected results:* Players can talk to each other and even see each other if desired.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Easy–WebRTC libraries do most of the work for you.

### Build More Campaigns

Want to make a CodeCombat campaign for elementary school students? For girls? For boys? For math? For elite hackers? For Game of Thrones? For Minecraft players? CodeCombat's level editor is yours to command! It's an extraordinarily powerful, drag-and-drop, live-programmable editor inspired by the StarCraft II Galaxy Editor, and you can use it to build just about anything. All [Artisans](http://codecombat.com/contribute/artisan) share Systems and Components, so the building blocks you create to enable custom logic in your levels will be available in everyone else's levels and vice versa.

*Expected results:* A fun, playable, polished campaign.

*Knowledge prerequisite:* An interest in game design, and basic programming knowledge. You don't need to know any programming to use the level editor, but presumably you're trying to teach some programming, so you need to know at least what you're teaching. It will also help to know JavaScript / CoffeeScript if you want to write custom Components and Systems, which will be needed more the more different your levels are than the existing CodeCombat levels.

*Difficulty:* Medium. Although the coding is easy, it takes a lot of thought to make good levels, so expect to iterate a lot on each level.

### Optimize for Offline / Low-Bandwidth Play

Wouldn't it be great if you could play CodeCombat and learn to code in low-internet environments like remote schools? CodeCombat currently requires ~10MB of download data to start playing, and then once you're downloaded, it should mostly be able to play offline–but we haven't set it up to function as an offline, cached HTML 5 app. If you did that, and perhaps optimized the download size some more, then this could get into many more of the countries that we currently have translations for but which often don't have enough internet to reliably play. This would also be a big step towards making it great on mobile.

*Expected results:* CodeCombat should be playable offline after the initial download.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Medium. It may take quite a bit of tinkering to cache things smartly in various environments such that the necessary offline cache info is all present.

### Improve Game Physics

CodeCombat uses a 2D physics engine with Box2D for collision detection, and we've written some basic position / velocity / acceleration stuff and locomotion dynamics, but there's so much more physics that could be done, enabling more physics-based gameplay and levels. Imagine coding the laser targeting system to solve reflection-based puzzle levels in CodeCombat, or levels where you adjust your thrust to guide your rocket. You could make that happen.

*Expected results:* CodeCombat should be have a general physics system that enables lots of emergent physics-based gameplay while still being performant.

*Knowledge prerequisite:* Physics (mechanics) and proficiency with algorithms. Knowledge of CoffeeScript or JavaScript helpful.

*Difficulty:* Medium. The basics of the physics system are all there, so it's more about handling more mechanics and improving performance.

### Upgrade the Level Editor

The level editor is really cool: drag-and-drop, completely configurable, and even live-programmable from within the editor itself. It's a powerful tool, but the user interface is always a challenge; the learning curve is far too steep right now. You could do usability testing, improve the design, polish the rough edges, add missing features, and generally make it easier to use such that anyone can figure it out and make their own levels and campaigns.

*Expected results:* CodeCombat's level editor should be much easier to use than it is now.

*Knowledge prerequisite:* Basic web development knowledge. We use CoffeeScript, Jade, and Sass, but those are easy to pick up if you know JavaScript, HTML, and CSS.

*Difficulty:* Easy. You just watch people try to make levels, see where they get stuck, and tweak the design until they stop getting stuck there.

### Add Responsive Sound / Music

We have some great music and sound effects, but they don't do enough to add to the immersion, since the sound and music that plays is often not adapting to what's going on in the game. Doing some smart music switches and possibly audio processing in the browser could go a long way toward adding to the fun. There's some really audio APIs that would be great to put through their paces.

*Expected results:* CodeCombat's music and sound would adapt to the game environment for an immersive game experience.

*Knowledge prerequisite:* Basic programming knowledge and an interest in game design. Knowledge of CoffeeScript or JavaScript helpful.

*Difficulty:* Medium. In addition to figuring out the audio processing stuff, it's going to require a good design sense to figure out what music and sounds should play when and how they should be processed.

### Optimize World Simulation Performance

When a player's code changes, CodeCombat resimulates the entire level from beginning to end in a web worker within a split second and sends the results back to the main thread for a live-coding experience. The simulation performance of our game engine limits how fast that is and how big and long our levels can be. We need a lot of smart algorithms and optimization work on the engine to unlock the truly large-scale epic levels that we want to simulate. You could dig deep into the profiler, learn all about making JavaScript run quickly, and enable massive scale in CodeCombat levels.

*Expected results:* CodeCombat's world simulation performance could be at least four times as fast as it is now.

*Knowledge prerequisite:* Good programming and algorithms fundamentals and a solid knowledge of CoffeeScript or JavaScript.

*Difficulty:* Hard. We've already done a lot of the low-hanging optimizations in Chrome, so some of the remaining optimizations will require smarter algorithms or recoding things to stream the simulation results instead of waiting until they're done.

### Improve [Treema (JSON editor)](http://codecombat.github.io/treema/)

Treema is a jQuery plugin that builds interfaces for editing large, complex, well-defined JSON data. It runs on tv4, which implements JSON-Schema validation. We use it for our Level, Article, and Thang editors, and it's generally useful in any project which wants to generate UIs for JSON data. It works pretty well, but there are a bunch of refactorings and improvements and upgrades that'll make it really shine, not just in CodeCombat, but in many other projects which need to deal with JSON.

*Expected results:* Treema will be polished to a gleaming shine and take over all online JSON editors.

*Knowledge prerequisite:* Basic web development knowledge and CoffeeScript or JavaScript.

*Difficulty:* Medium. Treema's code is small, but very meta, so you'll need to be able to understand some complicated schema-schemas.

### Upgrade Testing Infrastructure


### Build Great Classic Algorithm Demos


### Add Classroom Organization Features


### Make Aether Transpiler More Friendly


### Build Massively Multiplayer Sandbox Play


