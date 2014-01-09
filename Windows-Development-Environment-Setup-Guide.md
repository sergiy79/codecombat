Mongo Download Links

| Windows Version | 32 bit      | 64 bit  |
| --------------- |:-------------:| :-----:|
| 7/8/Server 2008R2 | [Not recommended](http://fastdl.mongodb.org/win32/mongodb-win32-i386-2.5.4.zip) | [MongoDB](http://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-2.5.4.zip) |
| Vista |  [Not recommended](http://fastdl.mongodb.org/win32/mongodb-win32-i386-2.5.4.zip)  | [MongoDB](http://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2.5.4.zip) |
| XP              | Not supported |  Not Supported |

Ruby Download Links

| Windows Version | 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p353.exe?direct) | [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p353-x64.exe?direct) | 

Note for later: make sure Ruby sets path when it installs

Node Download Links

| Windows Version| 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [node.js](http://nodejs.org/dist/v0.10.24/node-v0.10.24-x86.msi) | [node.js](http://nodejs.org/dist/v0.10.24/x64/node-v0.10.24-x64.msi) | 

Git for Windows

[Download link for all versions](https://msysgit.googlecode.com/files/Git-1.8.5.2-preview20131230.exe)

Node-gyp prerequisites

  * On Windows:
    * [Python][windows-python] ([`v2.7.3`][windows-python-v2.7.3] recommended, `v3.x.x` is __*not*__ supported)
    * Windows XP/Vista/7:
      * Microsoft Visual Studio C++ 2010 ([Express][msvc2010] version works well)
      * For 64-bit builds of node and native modules you will _**also**_ need the [Windows 7 64-bit SDK][win7sdk]
        * If the install fails, try uninstalling any C++ 2010 x64&x86 Redistributable that you have installed first.
      * If you get errors that the 64-bit compilers are not installed you may also need the [compiler update for the Windows SDK 7.1]
    * Windows 7/8:
      * Microsoft Visual Studio C++ 2012 for Windows Desktop ([Express][msvc2012] version works well)

Steps from @deepak1556

Steps : 

- git clone https://github.com/codecombat/codecombat
- `npm install -g bower brunch nodemon`
- cd `codecombat/`
- `npm install`
- `bower install`
- sass-brunch currently doesnt have the windows socket close error [fix](https://github.com/brunch/sass-brunch/issues/33) on npm , so delete sass-brunch from node_modules dir and do the following inside codecombat/node_modules :
     - git clone https://github.com/vanto/sass-brunch
     - git checkout windows-spawn-fix
     - `npm install`
- rename brunch.coffee to config.coffee 
- `brunch w` //if any compilation error throws up on sass files just update your sass gem and that should do

Setting up mongodb:

- extract mongodb into a folder and add the path to bin folder inside mongodb folder to your system path
- create a `db` folder anywhere ex: `C:/db`
- `mongod --setParameter textSearchEnabled=true --dbpath path/to/db` folder we created in earlier step
- download database dump from https://s3.amazonaws.com/uploads.hipchat.com/60497/416620/DyI9sxIrTmiR6ms/coco_backup_public.tar.gz and extract it to `db/` folder inside `codecombat/` folder
- cd `codecombat/db`
- `mongorestore dump`

Finally :

- `nodemon -w server -w server_config.js`
- visit `http://localhost:3000`