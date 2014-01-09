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