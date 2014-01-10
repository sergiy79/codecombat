**NOTE**: This guide is a work in progress. If you have any questions in the meantime, just ask in the CodeCombat chatroom.

To get started, first you'll need to know a little bit about your computer: whether your computer is 32 or 64 bit, and what version of Windows you're running. 

* If you don't know if your computer is 32 or 64 bit, use [this link](http://windows.microsoft.com/en-us/windows7/find-out-32-or-64-bit) to find out. 

* If you're not sure what version of Windows you have, [this link](http://windows.microsoft.com/en-us/windows/which-operating-system) will tell you.

Once you have gotten those pieces of information, go through the sections below to download and install each dependency. 

##Node.js


To install Node, first download the correct version of the installer from the table below. Then, run the installer. Make sure that the Node installer adds Node to your path(illustrate with screenshot.)


####Node Download Links
| Windows Version| 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [node.js](http://nodejs.org/dist/v0.10.24/node-v0.10.24-x86.msi) | [node.js](http://nodejs.org/dist/v0.10.24/x64/node-v0.10.24-x64.msi) | 

##MongoDB

MongoDB is the database used for CodeCombat. To install, execute the following steps:
* 1. Unzip the mongodb directory to any location that you want (e.g. C:/mongodb-2.5.4)
* 2. Save the location of the directory in your PATH variable:
  * a. Press the start button;
  * b. Type "advanced system settings" and press enter;
  * c. Press the "Environment Variables..." button;
  * d. Under "User variables for..." you'll find the PATH variable, select it and press the "Edit..." button;
  * e. Enter ';%PATH_TO_MONGODB' (e.g.: ;C:\mongodb-2.5.4) at the end of the "Variable value" and press "OK".


####Mongo Download Links

| Windows Version | 32 bit      | 64 bit  |
| --------------- |:-------------:| :-----:|
| 7/8/Server 2008R2 | [Not recommended](http://fastdl.mongodb.org/win32/mongodb-win32-i386-2.5.4.zip) | [MongoDB](http://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-2.5.4.zip) |
| Vista |  [Not recommended](http://fastdl.mongodb.org/win32/mongodb-win32-i386-2.5.4.zip)  | [MongoDB](http://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2.5.4.zip) |
| XP              | Not supported |  Not Supported |

##Ruby 

####Ruby Download Links
| Windows Version | 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p353.exe?direct) | [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p353-x64.exe?direct) | 

Note for later: make sure Ruby sets path when it installs

##Git

[Download link for all versions](https://msysgit.googlecode.com/files/Git-1.8.5.2-preview20131230.exe)

##Python

####Python download links

| Windows Version | 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [Ruby](http://www.python.org/ftp/python/2.7.6/python-2.7.6.msi) | [Ruby](http://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64.msi) | 

Make sure you add Python to your path.

##Other prerequisites 

###Windows XP/Vista/7

####Both 32 and 64 bit systems
* [Microsoft Visual Studio C++ 2010](http://go.microsoft.com/?linkid=9709949) (Express)
* If the install fails, try uninstalling any C++ 2010 x64&x86 Redistributable that you have installed first.
* If you get errors that the 64-bit compilers are not installed you may also need the [compiler update for the Windows SDK 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=4422)

####64 bit systems
[Windows 7 64-bit SDK](http://www.microsoft.com/en-us/download/details.aspx?id=8279)

###Windows 7/8
* [Microsoft Visual Studio C++ 2012 for Windows Desktop](http://go.microsoft.com/?linkid=9816758http://go.microsoft.com/?linkid=9816758)

##Repository Setup

A big thanks to @deepak1556 for these steps.

###Opening up Git Bash

Detail here how to open up Git Bash. 

###Cloning the repository
In your git bash, navigate to where you want to clone your repository (explain how to do this).
```git clone https://github.com/codecombat/codecombat```

###Installing repository dependencies
First, change directory into the cloned CodeCombat repository with the command

`cd codecombat`

Then, run the commands
* `npm install`
* `bower install`
* `gem install sass`

###Fixing brunch

- sass-brunch currently doesnt have the windows socket close error [fix](https://github.com/brunch/sass-brunch/issues/33) on npm , so delete sass-brunch from node_modules dir and do the following inside codecombat/node_modules :
     - `git clone https://github.com/vanto/sass-brunch`
     - `git checkout windows-spawn-fix`
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