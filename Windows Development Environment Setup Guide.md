**NOTE**: Following the guide can be complicated. If you have any questions, just ask in the [CodeCombat chatroom](http://www.hipchat.com/g3plnOKqa).

Also, if you prefer, the [automated installer](https://s3.amazonaws.com/CodeCombatLargeFiles/coco-dev-win-setup-3.5.zip) is probably easier to use.

To get started, first you'll need to know a little bit about your computer: whether your computer is 32 or 64 bit, and what version of Windows you're running. 

* If you don't know if your computer is 32 or 64 bit, use [this link](http://windows.microsoft.com/en-us/windows7/find-out-32-or-64-bit) to find out. 

* If you're not sure what version of Windows you have, [this link](http://windows.microsoft.com/en-us/windows/which-operating-system) will tell you.

Once you have gotten those pieces of information, go through the sections below to download and install each dependency, which are
* Node.js
* MongoDB
* Ruby
* Python
* Git

## Required Packages
### Node.js


To install Node, first download the correct version of the installer from the table below. Then, run the installer. Make sure that the Node installer adds Node to your path(don't change the option in the installer circled below from its default value.)

####Node Download Links
| Windows Version| 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [node.js](http://nodejs.org/dist/v0.10.35/node-v0.10.35-x86.msi) | [node.js](http://nodejs.org/dist/v0.10.35/x64/node-v0.10.35-x64.msi) | 

<img src="http://i.imgur.com/tEKA0UAl.jpg" alt="Make sure Node is added to your PATH" style="width: 200px;" />

###MongoDB

MongoDB is the database used for CodeCombat. To install, execute the following steps:
* 1. Unzip the mongodb directory to any location that you want (e.g. C:\mongodb-2.6.4)
* 2. Save the location of the directory in your PATH variable:
  * a. Press the start button;
  * b. Type "advanced system settings" and press enter;
  * c. Press the "Environment Variables..." button;
  * d. Under "User variables for..." you'll find the PATH variable, select it and press the "Edit..." button;
  * e. Enter ';%PATH_TO_MONGODB' (e.g.: ;C:\mongodb-2.6.4\bin) at the end of the "Variable value" and press "OK".


####Mongo Download Links

| Windows Version | 32 bit      | 64 bit  |
| --------------- |:-------------:| :-----:|
| 7/8 | [MongoDB](https://fastdl.mongodb.org/win32/mongodb-win32-i386-2.8.0-rc4.zip) | [MongoDB](https://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-2.8.0-rc4.zip) |
| Vista |  [MongoDB](https://fastdl.mongodb.org/win32/mongodb-win32-i386-2.8.0-rc4.zip)  | [MongoDB](https://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-2.8.0-rc4.zip) |
| Server 2008 | [MongoDB](https://fastdl.mongodb.org/win32/mongodb-win32-i386-2.8.0-rc4.zip) | [MongoDB](https://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2.6.6.zip) |
| XP              | Not supported |  Not Supported |

###Ruby 

####Ruby Download Links

When Ruby asks if you want to **add Ruby to your path**, you must **say yes**.

| Windows Version | 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p353.exe?direct) | [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.0.0-p353-x64.exe?direct) | 



###Git

[Download link for all versions](https://msysgit.googlecode.com/files/Git-1.8.5.2-preview20131230.exe)

###Python

####Python download links

| Windows Version | 32 bit | 64 bit |
| :-------------: | :----: | :-----: |
| All versions | [Python](http://www.python.org/ftp/python/2.7.6/python-2.7.6.msi) | [Python](http://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64.msi) | 

Make sure you add Python to your path.

##Other prerequisites 

###Windows XP/Vista/7

####Both 32 and 64 bit systems
* [Microsoft Visual Studio C++ 2010](http://go.microsoft.com/?linkid=9709949) (Express). You don't need to run Visual Studio–the download is just to get the underlying SDKs.
* If the install fails, try uninstalling any C++ 2010 x64&x86 Redistributable that you have installed first.
* If you get errors that the 64-bit compilers are not installed you may also need the [compiler update for the Windows SDK 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=4422)

####64 bit systems
[Windows 7 64-bit SDK](http://www.microsoft.com/en-us/download/details.aspx?id=8279)

###Windows 7/8
* [Microsoft Visual Studio C++ 2012 for Windows Desktop](http://go.microsoft.com/?linkid=9816758)

##Repository Setup

A big thanks to @deepak1556 for these steps. (see [the original instructions](https://gist.github.com/deepak1556/8319345))

###Opening up Git Bash

You can use whatever shell you'd like to do the install, however Git Bash is recommended. To open up Git Bash, use the Start Menu to either search for Git Bash or open it in the programs menu.

###Cloning the repository
In your git bash, navigate to where you want to clone your repository (you can use the `cd` command to change directories, and `ls` to list the contents of the current directory). When you are in the folder that you'd like to clone the repository, run the command
```git clone https://github.com/codecombat/codecombat```

When you forked the repository do
```git clone https://github.com/[your GitHub username]/codecombat```

###Installing repository dependencies
For the following steps keep using git bash since some installation steps will require access to git.

First, change directory into the cloned CodeCombat repository with the command

`cd codecombat`

Then, run the commands
* `npm install -g bower brunch nodemon sendwithus`  
that mean install bower, brunch, nodemon and sendwithus. -g mean global
* `bower install`  
that command will install packages by using the dependencies listed in the current directory's bower.json   
you can read more about bower on Official Web site: http://bower.io/  
* `gem install sass`
* `npm install`

Finally run the command
* `brunch w` 

Note that once brunch has said that it has compiled and copied the files you can end the program.  Brunch will continue to run until you terminate it, as it looks for modifications to the CodeCombat code.

If there are any problems, you may need to update your version of the sass gem. Running `npm install` again may help too. Deleting the folder `codecombat/node_modules` before `npm install` rerun may help as well.

###Setting up MongoDB

- Create a `db` folder anywhere, for example `/c/db`. This is where MongoDB is going to keep the db data.
- Run the command `mongod --setParameter textSearchEnabled=true --dbpath [PATH TO DB FOLDER]` where `[PATH TO DB FOLDER]` would be `/c/db/` in the example and leave it running.
- Download the up-to-date database dump from [here](http://54.91.159.37/dump.tar.gz) somewhere else, and extract it.
- Navigate to the folder in which you extracted the dump (there should be a folder called `dump` in there)
- In a new shell (with the mongod still running), run the command `mongorestore --drop dump`.

###Running the server

Copy the start script (courtesy to @GlenDC) from `codecombat/scripts/windows/SCOCODE.bat` to the root folder of the repository `codecombat`. Before using it, edit the line that says `set "mongo_db_location=MONGO_DB_PATH_HERE"` with the path to your Mongo DB Path, e.g. `C:\db` (Git will ignore it). Then, all you have to do is click it (or otherwise start it) and the CodeCombat development environment will start.

Visit `http://localhost:3000` :).