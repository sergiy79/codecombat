In our [[Thang Component System]] architecture, the Thangs are the units, the things, the actors, the entities. A Thang can be an ogre, a rock, an arrow, a land, an invisible obstacle, a goal trigger--whatever. Thangs are specific to Levels and have just three properties:

1. `id`: the Thang's unique name within the Level
2. `thangType`: a pointer to a [[ThangType]] in the database, which holds all the art and sound information needed to display the Thang, but which has no impact on the Level's [[World]] simulation itself.
3. `components`: a list of [[Component]]s and their configuration, which together determine everything about how the Thang behaves in the game engine.

A very simple Thang might be a land. Let's look at a default Dungeon Floor Thang. Its `id` might be `"DungeonFloor3"` if there were a few other floors placed before it. Or you could rename it to `"Top Left Floor"`--doesn't matter, as long as it's unique. Its `thangType` will point to [the latest Dungeon Floor ThangType](http://codecombat.com/editor/thang/dungeon-floor). And it'll just have three Components:

![Dungeon Floor Thang example](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/dungeon_floor_thang.png)

Represented as JSON, these Components are simply:

```javascript
[
  {"original":"524b4150ff92f1f4f8000024","majorVersion":0,
    "config":{"stateless":true}},
  {"original":"524b7aff7fc0f6d519000006","majorVersion":0},
  {"original":"524b75ad7fc0f6d519000001","majorVersion":0,
    "config":{"pos":{"x":10,"y":30,"z":1},"width":20,"height":20,"depth":2,"shape":"sheet"}}]
```

A more complex Thang might have 20+ Components, and its ThangType might have many animations and sounds associated.