Once a user is authenticated, authorization to access and modify a document is specified based on two values: the user's `permissions` array and the document's `permissions` array. The handler for a given document type determines what can be edited based on those values.

## User Permissions

Here's part of Nick's `User` object:

```json
{
  "_id": "512ef4805a67a8c507000001",
  "...otherProperties...": {},
  "permissions": [
    "admin"
  ],
  "name": "Nick!",
}
```

For example, the `Article` handler indirectly checks the user's `permissions` array for an `'admin'` value when determining what methods are allowed, and specifies which properties any user, admin or not, may edit through the handler (so as to prevent editing values such as creation date or version numbers).

Only the web server can really protect the database from unauthorized access or tampering, so if you need to make sure documents only get changed in certain ways, do it through the handler for that sort of document.

## Document Permissions

Here's part of the `JumpsForeverAndEver` Component including its `permissions`:

```json
{
  "name": "JumpsForeverAndEver",
  "...otherProperties...": {},
  "permissions": [
    {
      "access": "owner",
      "target": "512ef4805a67a8c507000001"
    },
    {
      "access": "read",
      "target": "public"
    }
  ]
}
```

Document permissions are an array of objects with two properties: target and access. Target is either an `ObjectId` or the string `'public'`. Access is either `'read'`, `'write'`, or `'owner'`. There must always be at least one entry whose access value is `'owner'`. `'read'` can access the document, `'write'` can access and modify the document, and 'owner' can change the permissions of the document. That's the general rule of thumb, anyway; there are case specific exceptions. For example, users with property `'admin'` are assumed to have `'write'` permission at all times. The handler for a document must specify any additional special cases.