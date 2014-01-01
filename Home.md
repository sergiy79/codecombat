Hello [Archmages](codecombat.com/contribute#archmage)! Welcome to the developer wiki for CodeCombat. These documents are designed to give you everything you need to know, technical and non-technical, to dive into the project. If you see an opportunity to improve the docs, go ahead!

## Stuff Everyone Should Know

* [[Mission Statement]]
* [[Technical Overview]]
* [[Developer Environment]]
* [[Developer Organization]]
* [[Third Party Software and Services]]
* [[JSON-Schema]]
* [[Coco Models]]
* [[Coding Guidelines]]
* [[Testing]]

## Frontend Development

* [[Client Models]]
* [[Views]]
* [[Events, Subscriptions, Shortcuts]]
* [[i18n]]

## Backend Development

* [[Coco Backend Overview]]
* [[Versioning]]
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