## Campaign

A collection of Levels. Its exact structure has not yet been formed, but we’ll work on this. Think about how Levels can be related to one another (linear? a mario-style world map with offshoots and bonus stages?) and help us figure out how to shape these things.

### Level

A collection of all the stuff below, and more.

### Thang

Something in the level, like units, regions (script triggers), doodads and lands. They are composed of a ThangType and a bunch of Components.

### ThangType

What determines the graphic and audio side of the Thang. If a Thang’s Type is "Soldier", it will look and sound like a soldier. How it acts though is completely based on the Components. You can have a wall that attacks and is attacked, if you want.

### Component

Components are bits of logic attached to Thangs. These determine how the Thangs act and interact with one another. If it’s got a Physical component, it’s going to have things like a position and dimensions. If it’s got an Attackable component, that means it will have health that can go down. And if it has a Programmable component, the player can take control of the unit.

### System

Like Components, Systems are bits of logic. Whereas Components are attached to Thangs, Systems are attached to the Level itself, and manage things like Combat, Physics, and Vision. Components and Systems often interact with one another, and Components are grouped by the System they depend on.

### Script

CodeCombat has a Mediator pattern system of messaging between components in the game. For example, if the player presses the play button, a message gets sent out there that it happened, and the Surface (which draws the canvas) hears that message and starts playing through the level. Scripts can hook into this message system and trigger based on these messages and what sort of data they pass, and emit messages itself. So if the level has started, the scripts can add goals for the player to achieve. And once the goals are achieved, show the victory screen. And so on.

### Article

We’re teaching how to program here, and there’s no way around conveying difficult concepts in raw text. To that end, we’re building a wiki of sorts that levels can link to for reference on these concepts. Say you’re building a level that teaches for loops, then you have Anya tell the player a bit about them, show examples in the editor, and add the JavaScript For Loops article to the level. This will save you guys some explaining to do, and give players some ‘further reading’ if they want or need more explanation. This will also be useful for identifying what topics any given level is teaching.