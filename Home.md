Hello [Archmages](codecombat.com/contribute#archmage), welcome to the developer wiki for CodeCombat! These documents are designed to give you everything you need to know, technical and non-technical, to dive into the project.

## Stuff Everyone Should Know

* [[Mission Statement]]
* [[Technical Overview]]
* [[Developer Environment]]
* [[Developer Organization]]
* [[Third Party Software and Services]]
* [[JSON-Schema]]
* [[Coco Models]]
* [[Coding Guidelines]]

## Main Systems

* [[Versioning]]
* [[Testing]]
* [[i18n]]

## Frontend Development

* [[Client Models]]
* [[Views]]
* [[Events, Subscriptions, Shortcuts]]

## Backend Development

* [[Coco Backend Overview]]
* [[Permissions]]
* [[File System]]

## Game Engine

* CodeCombat uses a [[Thang Component System]] architecture.
    * A [[Thang]] can be an ogre, a land, an arrow--anything.
    * Thangs are just clusters of [[Component]]s.
    * [[System]]s organize the Components.
* [[World]]s simulate deterministically.
* The [[Surface]] is what we call our graphics layer.
* The [[Tome]] is our spell editor.
* [[Multiplayer]]

## Level Editor
* **TODO**: organize an outline here

## Thang Editor
* **TODO**: document this if anyone cares to gaze upon it

## Side Projects

* [[Treema]], our general interface for editing JSON data with schemas
* [[Aether]], our transpiler