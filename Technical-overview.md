CodeCombat is a single-page web application, stitching together many different open-source projects and high quality services.

# Application Layers

* Database: MongoDB. Pretty standard database responsibilities.
* Web Server: Node.JS, follows REST principles and a CRUD interface. Provides most of the security and maintains data integrity.
* Client: The single-page web application which follows the MVC pattern, using Backbone.

# Data Format

All layers use the same data format: JSON. Integrity and model meta-data is maintained using [[JSON-Schema]].

# Project files overview

* /app: Client application source. Code written here runs in the **browser**.
* /bin: Development bash utility scripts. 
* /public: Client application output. This is what the browser fetches from, and is built from /app, /vendor and /test.
* /server: Server application. Code written here runs on the **server**. Unlike the client application, no pre-compilation is needed; Node compiles the CoffeeScript files dynamically.
* /test: Testing files.
* /vendor: Third-party resources for the client(like jQuery, Bootstrap, and so on..) (server resources are governed by npm).
* config.coffee: Brunch config, mainly for compiling /app and /vendor into /public.
* package.json: NPM config: mainly for defining what packages the server requires.
* server_config.js: environmental variables for the server.
* server.coffee: main server file.