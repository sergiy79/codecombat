We're building a lot of interconnected data here at CodeCombat. Levels, Components, Systems, Articles and ThangTypes point to one another one way or another and combine to form the game, and it's all in the database rather than the source code. This is handy, but also tricky. All this data can easily be changed, and that can cause some real stability problems in such a complex web of interdependencies. Stability and flexibility are at odds here, so we use a simple versioning system to allow us to have both. And by versioning models, we get the added benefit of VCS's, in that we can revert models to a previous version if things go wrong.

Non-versioned documents, when modified, simply overwrite the database entry with the new data. Not so with versioned documents. You can only post new versions of a given document--you can't edit old ones.

Bear in mind, the versioning system is not meant to be super reliable or feature rich like Git or SVN. It's purpose is to make it possible to allow old content to continue to work without preventing new content from changing the rules. Also, since code is housed in documents like Components and Systems, it provides some of the freedom from fear of changing and breaking things by allowing you to have earlier versions to revert to.

## Example

Here's part of a ThangType document. It uses the versioning system.

```json
{
  "name": "Tharin",
  "_id": "52bb7731d542dc0000000037",
  "...lotsOfOtherProperties...": {},
  "version": {
    "isLatestMinor": true,
    "isLatestMajor": true,
    "minor": 17,
    "major": 0
  }
}
```

## Numbering
Versions are two numbers: major and minor. Both start at 0, and are incremented by one when a new version is created. When making a new version, you have a choice: a new minor version of an existing major version, or a new major version? Here's an example history:

1. First version created is always 0.0
1. New minor version created is 0.1
1. New major version created is 1.0
1. New minor version of major version 0 is 0.2, since its last minor version was 1
1. New minor version of major version 1 is 1.1, since its last minor version was 0

## References
References from a document to a version document tend to point to the latest minor version of a given major version. That is, the reference effectively says "Whatever document is the latest minor version of x document for y major version". This allows propagation of changes to be targeted. If a new version of a document would break other documents referencing it, a new major version is created and the references continue to point to the old version. If the change would not break things, or would fix broken things, then a new minor version should be created for that document.

For example, say a Level uses the AI System, version 0.47. You want to change the AI System to add a new feature. If the new feature doesn't conflict with existing functionality, it should be a new minor version, which automatically chooses 0.48. But, if the change would fundamentally alter how AI works, then a new major version is called for, and it would probably be 1.0. If this new major version is created and later on you realize 0.47 has a bug, you can still go back and fix it to create version 0.48 while version 1.0 remains the same.

Note that the incrementing is smart. If you have versions 0.0 through 0.50, and you modify 0.25 and create a new minor version from it, the new version is 0.51. Same with major versions; it doesn't matter what the source is, the next number is still only chosen based on what are the version numbers in the database for that document. The database also has a unique index set up which doubly makes sure there can never, ever be two copies of the same version of the same document.

It might be good someday to replace this homegrown versioning system with something more powerful, such as git and GitHub, but for now this does the job and fits inside our Mongo database.