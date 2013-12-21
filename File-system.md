Most files are stored in and accessed from MongoDB's file-storage system, GridFS. This keeps the application from exploding with these resources as new levels and units and articles need somewhere to put images and sounds.

Files are manipulated through urls beginning with /file/. A file such as /file/<objectid> will fetch a file with a given Mongo ObjectId, but most systems will instead fetch through a file's name with something like /file/folder1/folder2/file_name.mp3.


GridFS has no conception of folders built in, but we have a 'path' metadata property which can serve as a folder designation for a given file. So a file accessed at "/file/folder1/folder2/sound.mp3' would have metadata something like:

{
     filename: 'sound.mp3',
     metadata: {
          path: 'folder1/folder2'
     }
}

Only one file can exist for any given full path. If you upload a file of the same name to the same path, the original will be overwritten if the property 'force' is truthy, otherwise the operation will fail.

Database documents that need links to GridFS files should use paths instead of ids. That way if the file is updated, those links are not broken.

Paths for files that are associated with a particular document should generally follow the pattern:

/db/<document.type>/<document.id>/filename.ext

That way, all files associated with a given level or thang.type can be found with a query for that path. This also encourages organizing files according to the document that uses it. If two documents would use the same resource, have copies of the file rather than trying to link to the same resource from two different documents. This simplifies tracking where a given resource is used.

Documents that are versioned should use the document's original value so that resources for all versions of a document are in the same path.

Files not related to any particular document should go in their own separate folders, depending on purpose. For example, game music (which is used for many levels) should go in a music folder instead.