Documents from the database are loaded into the system through [Backbone](http://backbonejs.org/) [Models](http://backbonejs.org/#Model) and [Collections](http://backbonejs.org/#Collection). These are extended in the CocoModel class. There's also the Supermodel class which coordinates the loading and populating of these models.

## Supermodel

This class uses [JSON-Schema](https://github.com/codecombat/codecombat/wiki/JSON-Schema) to figure out, for a given model, what other models ought to be loaded. The logic for this is spread between Supermodel.coffee and CocoModel.coffee. This is used, for example, to load all documents required for a given Level model.

## Saving

Models that are not versioned save just as they normally do with Backbone Models.

To save a new version of a versioned model, use the CocoModel's cloneNewMinorVersion and cloneNewMajorVersion. Typically, the process is to modify the model as normal with 'set', then clone with the changes and save the clone.

Backbone does not natively support nested documents, which CodeCombat relies heavily on. Currently, the only way to set a subdocument is to set the root level property. See how LevelBus.coffee does this with LevelSession.

Patching is supported by the server. LevelBus.coffee also shows how this is handled.