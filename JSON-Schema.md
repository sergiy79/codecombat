[http://json-schema.org/](http://json-schema.org/)

Probably one of the least known tools in our kit, but also one of the most central. By defining our database documents with schemas, we get a great many benefits:

* __Integrity__. Data can be checked against the schema and is guaranteed to be of a certain structure. The server ensures that everything going into the database abides by the schema.
* __Validation__. Many of the rules that fields in forms, such as required fields or length constraints, can be specified in the schema, and can be discovered and reported to the user client-side without ever going to the server to check.
* __Interface Generation__. Treema takes the data and the schema and creates a baseline universal interface for editing the data, no matter what the schema is. This means when a new property to the schema of a type of document, frequently no further work is required for the editor to modify that data.
* __Automated Population__. Schemas can specify how to resolve references from one document to another. So when loading everything required for a Level, all related Components, ThangTypes, and Articles are loaded as a matter of course by the SuperModel which utilizes the schemas to figure out how to get the data.
* __Definition__. There is a universal place for data to be defined, which can be used by you, the Archmages, to see how a given document ought to be structured, and in the future for potential API clients to tap into our existing data structures.

It's important if you are working with data in any way on CodeCombat to understand how JSON-Schema relates to your work. Change to a schema affect every layer of the software stack. Look for further opportunities to use it to automate complex but repeated processes.