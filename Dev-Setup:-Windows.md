###Index
* [Simple Windows Installation](#simplewindows)
* [Detailed Windows Installation](#detailedwindows)
* [Step by Step](#stepbystep)


### <a name="simplewindows"><a name="windows_details"></a></a> Simple Windows

Download the latest version [here (v3.7)](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/coco-dev-win-setup-3.7.zip) and/or follow the instructions from [this step-by-step guide](#Setup-on-Windows:-a-step-by-step-guide).  The complete process is fully automated for all supported Windows versions.

We support the following, and only the following versions:
* Windows Vista
* Windows 7
* Windows 8.0 - Problems found
* Windows 8.1


**Note**: if your brunch isn't compiling sass properly, try removing the bless-brunch entry from package.json and deleting the bless-brunch folder from node_modules, then getting sass-brunch 1.7.0 with `npm install --save-dev sass-brunch@1.7.0`

Other versions, newer then _Windows XP_, and not listed above, might work, but we don't guarantee that they will.

### <a name="detailedwindows"></a> Detailed Windows Install

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

### <a name="stepbystep"></a> Step by Step Guide

#### TLDR
1. [download](#download);
2. unarchive;
3. open ``setup.exe`` and follow the instructions;
4. open ``configuration.exe`` and follow the instructions;
5. start ``.\SCOCODE.bat`` and enjoy your fresh Code Combat environment;
6. in case of an error in one of the opened windows of step 5, redo the step.

#### Index
0. **[Download](#download)**
1. **[Archmage instructions](#archmage-instructions)**
2. **[Introduction](#introduction)**
3. **[How to use this installation](#how-to-use-this-installation)**
4. **[The first steps](#the-first-steps)**
5. **[Software guide](#software-guide)**
6. **[Git Initialization](#git-initialization)**
7. **[NPM, Brunch and MongoDB](#npm-brunch-and-mongodb)**
8. **[Known Nodemon Issue](#known-nodemon-issue)**
9. **[Final Note](#final-note)**

#### Download
Download the latest version: [v3.7 (beta)](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/coco-dev-win-setup-3.7.zip)

#### Archmage instructions
This paragraph is only for people who want to help on the development of the installation system, if you're a user of this system, you can and should skip this paragraph and go to [the next one](#introduction).

[The scripts for the installer](https://github.com/codecombat/codecombat/tree/master/scripts/windows/coco-dev-setup/batch/scripts) are all scripts used for the installer. They are packed [with this script](https://github.com/codecombat/codecombat/blob/master/scripts/windows/coco-dev-setup/dev-setup-packer.bat) into an installation package by us, when releasing a new version. You should know that the installation package also contains a ``utilities`` directory. This contains curl and 7zip command-line executables. The install system depends on this. So in case you want to open the setup from your develop environment, for testing, you should [download](https://s3.amazonaws.com/CodeCombatLargeFiles/utilities.zip) and unarchive the utilities directory in [./scripts/windows/coco-dev-setup/batch/](https://github.com/codecombat/codecombat/tree/master/scripts/windows/coco-dev-setup/batch).

**[Go back to the top.](#index)**

#### Introduction
The manual installation of the CodeCombat development environment on Windows was tricky, and a lot of users had troubles with this. Therefore we decided to develop a fully automatic setup for Windows, to avoid users getting frustrated and giving up before they ever started on real development. That's in a nutshell the short background of why this setup exists in the first place.

Please note that this setup is in development and maintained by only one person. This means that there is a high risk of potential bugs. These can and should be reported like any other issue on [the official CodeCombat issue list](https://github.com/codecombat/codecombat/issues?labels=enhancement&state=open). Because of this solo development process there is probably quite some room for optimizations and improvements possible, to make it work faster, safer and better. Feel free to discuss proposals to improve it, with **Glen DC** on the [CodeCombat chatroom](http://www.hipchat.com/g3plnOKqa).

**[Go back to the top.](#index)**

#### How to use this installation
First, you'll have to extract the downloaded archived setup. You can find the download [here](#download). Once you've done this, you can just go inside the directory and open the setup.bat file. Don't be scared by this old-school approach. Trust me, it's really easy to use!

The only requirements for this setup are a keyboard and a working brain.

The entire installation is command-line based to keep the installation as lightweight and clean as possible. It also allows us to have a minimum amount of dependencies. The installation is **question-based**. This means that there will be several questions asked. Some are simple Yes or No questions where you respectively answer with _Y_ or _N_. Other questions are more complex. These type of questions usually ask you to enter a full path. Here follow **some important rules when entering a path as the answer to a question**:
* A path should be entered as a full path, that means starting with the Drive Letter and going up from there on. (e.g. c:\directory)
* Use the backslash ( \\ ) character to separate directory levels.
* Please avoid whitespace characters in any part of your full path. If you really really insist on having a space character in your path, be sure to surround the entire path with the quote ( " ) character.
* Make sure to double check your entry before pressing enter. Entering an invalid path can lead to a failed setup and even to the modification and/or deletion of wrong directories.

The entire setup is designed to be as user friendly and automatic as possible. In fact this guide shouldn't be needed at all. It is only here to fill in, where the setup failed in usability and to make the installation of the environment on Windows even easier than it already is.

**[Go back to the top.](#index)**

#### The first steps
1. You have downloaded, unarchived and opened the installer. Congratulations! ![Install Text](https://dl.dropboxusercontent.com/u/80071057/codecombat/1_title.png)
2. Enter 'Y' to accept [our license](http://codecombat.com/cla). You can't install if you don't accept. ![Accept the license.](https://dl.dropboxusercontent.com/u/80071057/codecombat/1_license.png)
3. Enter the ID (number) of your language of choice and press enter. (e.g. _1_ for English) ![Choose your language.](https://dl.dropboxusercontent.com/u/80071057/codecombat/1_language.png)

**[Go back to the top.](#index)**

#### Software guide
1. Installing the software needed for the CodeCombat is an easy process that can be skipped by entering _Y_ ![Software Installation Title](https://dl.dropboxusercontent.com/u/80071057/codecombat/2_title.png)
2. There are several software you'll need, in order to use CodeCombat. But the process is the same for all of them.
  1. Enter _N_ if you want to install the software. You can skip it with _Y_ (in case you already have it).
  2. After it is downloaded, it will open the installation window. Follow the instructions to complete the installation of the application.
  3. Go back to the CodeCombat installation windows after the installation finishes.

#### Remarks
1. When installing Git Bash, make sure to select the option that adds this tool to your Windows PATH.
![Git Bash Remark](https://dl.dropboxusercontent.com/u/80071057/codecombat/gitbash_path.png)
   1. Don't change the default path of your bash installation. This will save you work later on in the installation.
   2. Do select the option to add git to your path. Otherwise, there will be errors related to not finding git later on in this installation.
2. When installing NodeJS, make sure to select the option to add this tool to your Windows PATH. ![NodeJS Windows Path](https://dl.dropboxusercontent.com/u/80071057/codecombat/nodejs_path.png)
   1. When you fail this step, you'll get errors related to npm in a later phase of this installation.
3. When installing Ruby, make sure to select the option to add this tool to your Windows PATH. ![Ruby Windows Path](https://dl.dropboxusercontent.com/u/80071057/codecombat/ruby_path.png)

**[Go back to the top.](#index)**

#### Git Initialization
1. We are open source, and so you'll checkout a forked version of our repository to start working online. ![](https://dl.dropboxusercontent.com/u/80071057/codecombat/3_title.png)
  1. If you are an experienced user you might want to do this step manually. (e.g. to be able to checkout via ssh)
  2. For the easy solution, go for the automated version provided by us by entering _N_ on the first question.
     1. First you'll have to give the path to your root directory of where you installed Git Bash in a previous step.
     2. After that is done you can enter the full path of where we can put the CodeCombat repository for you.

##### Note

The automatic option for this phase will ask at the end for your git username and password. It will use this to modify the _origin_ remote of your local repository so that you can push easily to your forked repository of CodeCombat without any extra auth steps necessary. Note that this is not recommended in case you are developing on a public computer, as your git login information will be saved as plain text inside the .git directory of your local repository.

In case you are working on a public computer or if you want a more secure solution, you can switch to an ssh connection for your origin remote. You can edit your remote after the automated setup is done, or you can choose the manual git setup option when this question is prompted. Before you can use an ssh connection, you'll have to generate an SSH key and add it to your GitHub account. You can read and learn how to do this via [this official ssh key guide](https://help.github.com/articles/generating-ssh-keys) by GitHub. After that you'll need the SSH URL of your forked repository, which will look like this: ``git@github.com:YOUR_USER_NAME/codecombat.git``

**[Go back to the top.](#index)**

#### NPM, Brunch and MongoDB
This part is fully automatic and requires no user interaction. This step can take several minutes to complete, so please have patience. Note that this step is to be **manually started** by opening the ``configuration.exe`` file AFTER the ``setup.exe`` file has successfully finished.

During this phase, bower will also ask you if they can sent reports with information to improve their software. You can either accept or decline this by answering ``y`` or ``n``.

##### Note

Although this separate ``configuration.exe`` setup file isn't designed to be used as a stand-alone installer, with a little effort on your side, you could use it as a stand-alone installer to configure a fresh local CodeCombat repository on a computer that already has all the software CodeCombat depends on. This configuration.exe file also requires that all your environment variables have been set correctly. In order to use this step as a stand-alone installer, you'll have to create an xml-structured file named ``cache.coco`` inside ``.\config\``, where the root is the installer root (the directory you downloaded).

Here is a template cache file you can base yourself on:

    <?xml version="1.0" encoding="ISO-8859-1" ?>
    <variables>
        <language_id>LANGUAGE_CODE</language_id>
        <repository_path>THE_FULL_PATH_TO_YOUR_LOCAL_COCO_REPOSITORY</repository_path>
    </variables>

* An example for the ``LANGUAGE_CODE`` is ``en`` (which is the code for _English_). You can find all the language codes inside ``.\localisation\languages.coco``. Every language code is also represented by a file named ``.\localisation\LANGUAGE_CODE.coco``.
* An example for ``THE_FULL_PATH_TO_YOUR_LOCAL_COCO_REPOSITORY`` is ``C:\coco``.

**[Go back to the top.](#index)**

#### Known Nodemon Issues

Starting up SOCODE.bat for the first time and seeing the following error?
![NodeMon Issue](http://scdn-discourse.r.worldssl.net/uploads/codecombat/_optimized/8e3/53d/9bd7a0f086_674x500.png)

Don't worry, we know about this issue, and are working on a solution. Here is how are you can solve it, untill we fix the problem for good:

1.  Let MongoDB make a succesfull local connection and let Brunch finnish a full compilation
2.  Close all windows
3.  Start SOCODE.bat again and enjoy your local CodeCombat Development Environment!

#### SCOCODE.bat is not connecting to MongoDB

SCOCODE.bat should pop up three command prompts. The first one is MongoDB. If this prompt does not open or Nodemon is showing an exception when connecting to MongoDB (localhost:27017) check if MongoDB has been added to the PATH-variable. If not, add the full path where you installed MongoDB to the PATH-variable.

**[Go back to the top.](#index)**

#### Final Note
That's it. If there are any question, just ask them on the [CodeCombat chatroom](http://www.hipchat.com/g3plnOKqa). 

**[Go back to the top.](#index)**