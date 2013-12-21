At the top of any subclass of Coco* can be any combination of three objects: subscriptions, events, and shortcuts. These are the main place for callbacks to be specified.

## Subscriptions

Subscriptions are built on [Backbone-Mediator](https://github.com/chalbert/Backbone-Mediator). These are for inter-object communication that needs to be very generalized. This happens for example when:

* Relationships between objects are distant, varied or subject to change
* Scripts in levels need to be able to use them, either to trigger the script or to cause an effect of the script.

All Coco* subclasses support subscriptions. Objects subscribe on construction by default and tear them down when destroy is called.

See the [Backbone-Mediator repository](https://github.com/chalbert/Backbone-Mediator) for more details.

## Events

Events are [Backbone Events](http://backbonejs.org/#Events) for [Backbone Views](http://backbonejs.org/#View). These are for things like mouse clicks or other DOM events.

CocoView is a subclass of Backbone's View class so they all support events, and are handled by Backbone as usual.

See the [Backbone docs](http://backbonejs.org/) for more details.

## Shortcuts

Shortcuts are keyboard shortcuts. These are handled by [keymaster](https://github.com/madrobby/keymaster).

All Coco* subclasses support keyboard shortcuts. They are enabled when the object is created and removed when destroy is called.

## Inheritance

All these are defined as objects in the class prototype. Normally subclassing would overwrite superclass properties, but for events, subscriptions and shortcuts the classes will merge these objects together. So for example, subscriptions in CocoView would apply to all its subclasses, unless the subclasses have their own handlers for the same subscription.