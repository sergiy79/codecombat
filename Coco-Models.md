Each Model has several files associated with it. For a Model to be fully functional, it needs the following:

* A **handler** in `/server/handlers`. Implements the REST endpoints associated with this Model, security logic, which properties are editable, and pretty much anything else special or logically unique to that Model. These subclass Handler.coffee, where all common logic among handlers is found.
* A **schema** in `/server/schemas`. Defines the data structure of the model, and uses common.coffee for utility functions that construct the schemas (because they can be rather verbose, and there tend to be certain things we like to have set by default, like `additionalProperties` to `false` for objects).
* A **server model** class in `/server/models`. Uses Mongoose to create an Active Record class for that Model, and ties in Mongoose plugins and any custom middleware.
* An **app model** class in `/app/models`. This is class the browser uses, and is subclassed from CocoModel which subclasses from Backbone.Model. It defines the server endpoint and any custom logic for that model in the browser.

## Plugins

Plugins are a way to share common logic across different Models. To 'install' a plugin, have its server model add the plugin from plugins.coffee and the schema extended with the plugin properties from common.coffee.

## The Models Themselves

Some of these are more mature than others, but all of them are changing regularly as CodeCombat develops. Check the code for the latest data on any given Model.

### Level
A single Level on CodeCombat. Includes:

* Thangs (game units) and their Component configuration
* Systems and their configuration (these coordinate Components)
* Scripts (event triggers and actions)
* Articles to show in the Guide of the Level

### Level.Component
A bundle of logic to give properties and behavior to a Thang. These rely on certain Systems being present. Examples: `ai.AttacksNearestEnemy`, `programming.Programmable`, `ui.Selectable`

### Level.System
A bundle of logic for a given Level. This defines things like how health or physics work. Different Systems can fundamentally alter how Levels work. The Systems that have been built are for RTS/RPG style gameplay, but more could be written to allow even more types of games. Examples: `Inventory`, `Collision`, `Combat`

### Thang.Type
A common bundle of data for a Thang (actor, unit, doodad). Includes:

* Graphical data, in the form of raw vector data
* Audio data, like what it says when you click it
* Logical data, i.e. the Components that it has by default and their default configurations

### Level.Session
State for a single play of a given Level, usually for a given player. Includes:

* Script state
* Code state
* Playback state

### Article
Documentation for general programming knowledge. CodeCombat needs in addition to gameplay a reference corpus for players to check if they want a good general explanation of any given programming concept. These are what Scribes work on.

## Other kinds of data:

### Thangs
Individual elements in a Level are [[Thang]]s. Because these are denormalized as an array of them within the Level model, there's no explicit Thang model. Any given Thang within a level is pretty much just a single ThangType (which describes audio and visuals) and an array of [[Component]]s (which describe behavior).

### Scripts
Like Thangs, these are denormalized to just an array of them within a Level. Each Script consists mainly of how it is triggered and what happens when it's triggered.