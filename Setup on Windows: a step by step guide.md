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
Download the latest version: [v3.6 (beta)](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/coco-dev-win-setup-3.6.zip)

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