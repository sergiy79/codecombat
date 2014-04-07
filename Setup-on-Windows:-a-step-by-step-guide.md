#### WARNING
_The automatic setup for Windows is still in development. This first version doesn't install the npm depandancies yet. it also doesn't setup your mongodb yet. For more information on release of newer versions, ask **Glen DC** on the [CodeCombat chatroom](http://www.hipchat.com/g3plnOKqa)._

_For now it's best to use [the manual installation guide](https://github.com/codecombat/codecombat/wiki/Windows-Development-Environment-Setup-Guide) if you want to develop on CodeCombat on the Windows platform._ 

#### TLDR
[Download](#download), unarchive, open and follow the instructions within the installer. That's how simple this installation is. Still facing a problem? No worries, your answer is probably to be found in this guide.

#### Index
0. **[Download](#download)**
1. **[Introduction](#introduction)**
2. **[How to use this installation](#how-to-use-this-installation)**
3. **[The first steps](#the-first-steps)**
4. **[Software guide](#software-guide)**
5. **[Git Initialisation](#git-initialisation)**
6. **[NPM, Brunch and MongoDB](#npm-brunch-and-mongodb)**
7. **[Final Note](#final-note)**

#### Download
Download the latest version: [v2.0 (beta)](https://s3.amazonaws.com/CodeCombatLargeFiles/coco-dev-win-setup-2.0.zip)

Here is a list of older versions, available to download:
* [v1.2 (beta)](https://s3.amazonaws.com/CodeCombatLargeFiles/coco-dev-win-setup-1.2.zip)
* [v1.1 (beta)](https://s3.amazonaws.com/CodeCombatLargeFiles/coco-dev-win-setup-1.1.zip)
* [v1.0 (beta)](https://s3.amazonaws.com/CodeCombatLargeFiles/coco-dev-win-setup-1.1.zip)

#### Introduction
The manual installation of the CodeCombat development environment on Windows was tricky, and a lot of users had troubles of this. Therefore we decided to develop a fully automatic setup for Windows, to avoid users getting frustrated, and possibly give up, before they ever started on the real development. That's in a nullshet the short background of why this setup exists in the first place.

Please note that this setup is development and maintained by only one person. This means that there is a high risk of potential bugs. These can and should be reported like any other issue on [the official CodeCombat issue list](https://github.com/codecombat/codecombat/issues?labels=enhancement&state=open). Because of this solo development process there is probably quite some room for optimisations and improvements possible, to make it work faster, safer and better. Feel free to discuss proposels to improve it, with **Glen DC** on the [CodeCombat chatroom](http://www.hipchat.com/g3plnOKqa).

**[Go back to the top.](#index)**

####How to use this installation
First of all you'll have to extract the downloaded archived setup. You can find the download [here](#download). Once you've done this, you can just go inside the directory and open the setup.bat file. Don't be scared by this old-school approach, trust me, it's really easy to use!

The only requirements for this setup are a keyboard and a working brain.

The entire installation is command-line based to keep the installation as lightweight and clean as possible. It also allows us to have a minimum amount of depandancies. The installation is **question-based**. This means that there will be several questions asked. Some are simple Yes or No questions where you respectively answer with _Y_ or _N_. Other questions are more complex. These type of questions usually ask you to enter a full path. Here follow **some important rules when entering a path as the answer of a question**:
* A path should be entered as a full path, that means starting with the Drive Letter and going up from there on. (e.g. c:\directory)
* Use the backslash ( \\ ) character to seperate directory levels.
* Please avoid whitespace characters in any part of your full path. If you really really insist on having a space character in your path, be sure to surround the entire path with the quote ( " ) character.
* Make sure to double check your entered before pressing enter, entering a wrong path can lead to a failed setup and even to the modification and/or delations of wrong directories.

The entire setup is designed to be as user friendly and automatic as possible. In fact this guide shouldn't be needed at all. It is only here to fill in, where the setup failed in usability and to make the installation of the environment on Windows even easier, than it already is.

**[Go back to the top.](#index)**

####The first steps
1. You have downloaded, unarchived and opened the installar, Congratulations! ![Install Text](https://dl.dropboxusercontent.com/u/80071057/codecombat/1_title.png)
2. Enter 'Y' to accept our license. You can't install if you don't accept. ![Accept the license.](https://dl.dropboxusercontent.com/u/80071057/codecombat/1_license.png)
3. Enter the ID (number) of your language of choice and press enter. (e.g. _1_ for English) ![Choose your language.](https://dl.dropboxusercontent.com/u/80071057/codecombat/1_language.png)

**[Go back to the top.](#index)**

####Software guide
1. Installing the software needed for the CodeCombat is an easy process that can be skipped by entering _Y_ ![Software Installation Title](https://dl.dropboxusercontent.com/u/80071057/codecombat/2_title.png)
2. There is several software you'll need, in order to use CodeCombat. But the process is the same for all of them.
  1. Enter _N_ if you want to install the software. You can skip it with _Y_, in case you already have it.
  2. After it is downloaded it will open the installation window, follow the instructions, to complete the installation of the application.
  3. Go back to the CodeCombat installation windows, after the installation of the application is complete.

####Remarks
1. When installing GitBash, make sure to select the option that adds this tool to your Windows PATH.
![Git Bash Remark](https://dl.dropboxusercontent.com/u/80071057/codecombat/gitbash_path.png)
   1. Not changing the default path of your bash installation, will safe you work later on, in the installation!
   2. Not selecting the option to add git to your path, will give you errors related to not finding git later on in this installation.
2. When installing NodeJS, make sure to select the option to add this tool to your Windows PATH. ![NodeJS Windows Path](https://dl.dropboxusercontent.com/u/80071057/codecombat/nodejs_path.png)
   1. When you fail this step, you'll get errors related to npm in a later phase of this installation.
3. When installing Ruby, make sure to select the option to addd this tool to your Windows PATH. ![Ruby Windows Path](https://dl.dropboxusercontent.com/u/80071057/codecombat/ruby_path.png)

**[Go back to the top.](#index)**

####Git Initialisation
1. We are opensource, and so you'll checkout a forked version of our repository to start working online. ![](https://dl.dropboxusercontent.com/u/80071057/codecombat/3_title.png)
  1. If you are an experienced user you might want to do this step manually. (e.g. to be able to checkout via ssh)
  2. For the easy solution, go for the automated version provided by us, by entering _N_ on the first question.
     1. First you'll have to give the path to your root directory of where you installed Git Bash in a previous step.
     2. After that is done you can enter the full path of where we can put the CodeCombat repository for you.

**[Go back to the top.](#index)**

####NPM, Brunch and MongoDB
This part is fully automatic and reacts no user interaction. This step can take several minutes to complete, so please have patient.

**[Go back to the top.](#index)**

####Final Note
That's it. If there are any question, just ask them on the [CodeCombat chatroom](http://www.hipchat.com/g3plnOKqa). 

**[Go back to the top.](#index)**