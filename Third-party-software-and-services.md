This is not an exhaustive list, but these are the most important for you to know about. We rely heavily on open source code and high quality services to speed development and focus on building CodeCombat, and these tools are what inspire us to open source our own work as well, to give back to the community that has given us all this. 

You don't need to learn how to use all of these tools, but please take some time to familiarize yourself with at least the ones you'll be using for the area(s) you'd like to work on.

If you add a project or tool to CodeCombat, please list it here and on the open-source shoutout section of the [legal page](https://github.com/codecombat/codecombat/blob/master/app/templates/legal.jade).

## Core Languages

* [CoffeeScript](http://coffeescript.org/): Used throughout the site instead of JavaScript. If you're familiar with Python or Ruby then you'll feel right at home. If you're familiar with JavaScript, you'll find CoffeeScript seeks to fix many of JavaScript's faults and, we think, does a pretty good job.
* [Jade](http://jade-lang.com/): HTML needs to be rendered on the client. Jade files get compiled into JavaScript functions that, given a context object, returns an HTML string. All our pages are written in Jade; use it rather than other HTML generation methods like jQuery.
* [Sass](http://sass-lang.com/guide): These are compiled in to CSS files and provide many nice features CSS does not have.
* [Markdown](http://daringfireball.net/projects/markdown/basics): Used for static HTML strings, such as in database text documents or incorporated in some text-heavy Jade templates (see the legal page for an example).

## Server-side

* [Node.js](http://nodejs.org/api/): The web server.
* [Express](http://expressjs.com/guide.html): The web framework.
* [MongoDB](http://docs.mongodb.org/manual/): The database. Beyond standard collections, we also use the MongoDB search indexing and GridFS.

### Libraries available on the server
* [Passport](http://passportjs.org/guide/): Authentication. Right now we just use it for authentication through passwords, but one project is to expand the site's login options through it.
* [Mongoose](http://mongoosejs.com/docs/guide.html): An interface for MongoDB that turns documents into active records. We mainly use their plugin system to share certain logic between multiple collections, for versioning, naming, searching and permissions.
* [TV4](https://github.com/geraintluff/tv4): JSON-Schema validation. Whole other article on this subject.
* [Request](https://github.com/mikeal/request): Simpler request handling, used in testing to test query the test server, and on the production server to interact with HTTP APIs for services like Facebook and Google.
* [Lodash](http://lodash.com/docs) and [Underscore.String](https://github.com/epeli/underscore.string#readme): Great utility libraries.
* [Async](https://github.com/caolan/async): Various utility methods for doing all sorts of fun asynchronous tricks. We mainly have used its waterfall method to do a serial string of checks on User documents when they are changed.

## Browser-side

### Site-wide Libraries

* [Backbone.js](http://backbonejs.org/): Provides a lot of the basic structure we use. The classes they provide are subclassed and extended. Each collection in the database has a parallel Backbone Model and each page on the site has one View which can contain many more Views. The Event system is also used, though perhaps underutilized for objects other than Views.
* [Backbone-Mediator](https://github.com/chalbert/Backbone-Mediator): A mediator so wide-spread classes and views can communicate with one another more easily.
* [jQuery](http://api.jquery.com/): Used largely for manipulating DOM elements. When it comes to utilities, Lodash tends to be used instead.
* [jQueryUI](http://api.jqueryui.com/): autocomplete and others.
* [Keymaster](https://github.com/madrobby/keymaster): Keyboard bound events.
* [Twitter Bootstrap](http://getbootstrap.com/2.3.2/): Used mainly for styling and its JavaScript components. Scaffolding isn't really used. We're on 2.3.2, but will eventually migrate to 3.
* [Moment](http://momentjs.com/): Formats times and dates.
* [Treema](https://github.com/codecombat/treema): Custom built library for editing schema-defined JSON data. Used for all editors. Scott is mainly in charge of working on this.
* Lodash, Underscore.String, and TV4 are also available in the browser.

### Gameplay Libraries and Services

* [CreateJS](http://www.createjs.com/#!/CreateJS): A suite of four libraries, all of which are used extensively for animation, tweening, sound and loading resources. It has its own internal event system, so that's used in lieu of Backbone events when required.
* [ACE](http://ace.c9.io/#nav=about): The code editor in game, and also used when editing code everywhere else on the site.
* [Box2D](http://box2d.org/): Physics engine.
* [Aether](https://github.com/codecombat/aether): Custom built library for running and deeply analyzing code. Used in gameplay to show things like what code is running at any given frame or where the code breaks and why. Nick is mainly in charge of working on this.
* [Firebase](https://www.firebase.com/): Service that synchronizes data between multiple clients. Used for synchronizing gameplay data when multiple people are playing on the same level. We also plan to use it for other inter-player communications, like chatting with friends or inviting other players to join in a campaign.
* [Firepad](http://www.firepad.io/): Collaborative text-editor built on top of Firebase, used as the backbone of CodeCombat's spell editor.

## Other tools
* [Jasmine](http://jasmine.github.io/2.0/introduction.html): Used for testing.
* [Karma](https://github.com/karma-runner/karma): Test runner.
* [Brunch](https://github.com/brunch/brunch): Assembles the project, and is pretty much central to everything development.