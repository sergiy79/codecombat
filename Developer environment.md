#Page is being deleted on 16/01/2015

New pages:
* [General Information](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-General-Information)
* [Linux Setup](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Linux)
* [Windows Setup](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Windows)
* [Mac and Vagrant Setup](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Mac-and-Vagrant)


## <a name="getting_started"></a> Getting started 

* [Mac OS X Screencast](https://www.youtube.com/watch?v=fom1ksXSbKM)
* [Ubuntu Screencast](http://youtu.be/usN85KSiWUM)
* [Simple Linux and Mac Tutorial](#simplelinux)
* [Simple Windows Tutorial](#simplewindows)
* [The Vagrant VM Method](#vagrantvm)


### <a name="simplelinux"></a> Simple Linux and Mac Tutorial

This method should work on Mac and Linux, if you run into any problems, let us know!  On Mac, you'll need the [XCode Developer Tools](http://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12).  On Linux, you'll need make, build-essential, ruby, curl and git installed (`sudo apt-get install make build-essential ruby curl git`).

1. [Create a GitHub account](https://github.com/join) if you don't already have one.
2. [Set up Git on your computer](https://help.github.com/articles/set-up-git/) to allow your computer to speak to GitHub
3. (Optional) [Fork](https://github.com/codecombat/codecombat/fork) our CodeCombat repository if you wish to make changes.
4. Make sure
5. Open a terminal and navigate to the folder you wish to install CodeCombat under.
6. * If you've forked the repository, paste in the following command.  *Replace "your_repository_url" with your repository*.

    ```bash
    curl https://raw.githubusercontent.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash -s your_repository_url
    ```
   * If you haven't forked the repository, paste in the following command.
    ```bash
    curl https://raw.githubusercontent.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash
    ```
    NOTE: The repository will be in the coco subdirectory.  You should not run a separate git clone, as that is taken care of.
7. Ensure you have Python 2 installed with `sudo apt-get install python2`, or your distributional equivalent.  Python 3.1 is also supported, but 3.2+ are not tested.
8. Follow the on-screen prompts.  The program will download and install all necessary dependencies.  If nothing seems to be happening, try running `sudo python ./coco/scripts/devSetup/setup.py` or join the [HipChat](www.hipchat.com/g3plnOKqa) to fix things.
9.  Run the following commands in separate windows:
    * `./coco/bin/coco-mongodb` - Starts MongoDB
    * `sudo ./coco/bin/coco-brunch` - Starts brunch, which watches for file changes 
    * `./coco/bin/coco-dev-server` - Starts your local web server
10. Setup [MongoDB](#MongoDB) *Soon to be Optional*
### To be Edited
11. Visit [http://localhost:3000](http://localhost:3000) to see your CodeCombat development environment!

If you get errors with bower not being able to clone git repositories, try [cloning over https](http://stackoverflow.com/questions/1722807/git-convert-git-urls-to-http-urls/11383587#11383587).  If SASS brings up an error about file encodings being wrong, add this to your .bash_profile:
```bash
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```
If you see a white screen only, check to see if the first line of app.css is `ERROR: Cannot load compass.`. If so, try either uninstalling compass (`gem uninstall compass`) or re-installing it if you actually need it (`gem install compass --pre`).

### <a name="simplewindows"><a name="windows_details"></a></a> Simple Windows

Download the latest version [here (v3.7)](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/coco-dev-win-setup-3.7.zip) and/or follow the instructions from [this step-by-step guide](#Setup-on-Windows:-a-step-by-step-guide).  The complete process is fully automated for all supported Windows versions.

We support the following, and only the following versions:
* Windows Vista
* Windows 7
* Windows 8.0 - Problems found
* Windows 8.1


**Note**: if your brunch isn't compiling sass properly, try removing the bless-brunch entry from package.json and deleting the bless-brunch folder from node_modules, then getting sass-brunch 1.7.0 with `npm install --save-dev sass-brunch@1.7.0`

Other versions, newer then _Windows XP_, and not listed above, might work, but we don't guarantee that they will.
### <a name="vagrantvm"></a> The Do-It-Yourself Vagrant VM Method
If you have [vagrant](http://www.vagrantup.com/) and virtualbox installed, [https://github.com/dpen2000/Codecombat-Vagrant](https://github.com/dpen2000/Codecombat-Vagrant) provides a method of starting a vagrant-managed VM with folder mappings, the website available at http://localhost:3000/ on your host machine and the latest mongo data auto restored into your Mongo instance (included in VM). Setup instructions are in the [Readme](https://github.com/dpen2000/Codecombat-Vagrant/blob/master/README.md).  
##### The-do-it-via-a-vm-way (THIS METHOD IS UNAVAILABLE FOR NOW, DOWNLOAD LINKS DO NOT WORK)
If you want to run the VM, you'll have to [download VirtualBox](http://download.virtualbox.org/virtualbox/4.3.6/VirtualBox-4.3.6-91406-Win.exe), install it, then [download](https://s3.amazonaws.com/CodeCombatLargeFiles/CoCoLinux.ova) ([torrent](https://s3.amazonaws.com/CodeCombatLargeFiles/CoCoLinux.ova?torrent)) and import the CodeCombat Linux appliance by going to File:Import Appliance (note that occasionally the large download may be corrupted, so it's often easier to use the torrent.) The "CodeCombat" user account password is "coco". Once you have the Linux virtual machine running, the follow the directions above. To ease development, you can set up a shared folder so that you can edit files in Windows and have them accessible to the Ubuntu VM. See directions for setting up shared folders [here.](http://mikesmithers.wordpress.com/2011/03/23/installing-ubuntu-in-virtualbox-on-a-windows-7-host/#attachment_898) You can also [set up bridged networking](http://askubuntu.com/questions/196118/how-to-access-localhost-on-virtualbox-host-machine) so that your server is accessible from Windows.


### The do-it-yourself way

**TODO: document this better**

If you're on Ubuntu, check out [Steve Malmskog's instructions.](https://github.com/codecombat/codecombat/wiki/Ubuntu-Development-Environment-Setup-Instructions)

1. [Set up a GitHub account](https://help.github.com/articles/set-up-git) if you don't already have one.
1. Fork the CodeCombat project.
1. `git clone` it to your computer.
1. Install software
  1. sudo npm install
  1. sudo npm install -g bower
  1. bower install ( bower install each dependency from bower.json )
  1. sudo npm install -g brunch
  1. Download [MongoDB 2.6.0](http://www.mongodb.org/downloads)
  1. Start up Mongodb and define the bin folder of coco as your --dbpath variable
1. Run bin/coco-mongodb, bin/coco-brunch and bin/coco-dev-server.
1. Go to [http://localhost:3000](http://localhost:3000) to see your local CodeCombat in action.

## Working in the environment

You don't need any particular IDE to work with CodeCombat. Scott uses WebStorm, Nick uses Emacs, and George uses Sublime Text, so already the most important parts are IDE-agnostic. We need help making it friendly for Linux and Windows, though, since we all develop on Mac.

### Live-coding

If Brunch is running and you have a page open to the development server and you make changes to the programming logic one way or another, Brunch will reload the page automatically. So open the page you are working on in your browser, make changes in your editor, save, and the page will refresh so you can see the changes. Try to make whatever you're working on be the first thing you see when you open the page, so you don't have to lose focus on your editor while iterating. If you edit just the styling, Brunch will apply the new styling without refreshing.

Brunch is good, but it is finicky (or possibly improperly configured). Its finicks include but are not limited to:

* Stops reloading the page properly
* Takes strangely long to compile
* Doesn't compile every file into app.js

Usually, restarting it by hitting Ctrl-C once in the Brunch terminal window will fix it. Because of the frequency of it needing restarting, it will automatically restart when terminated once, and will only really stop if it's terminated twice in a row manually.

### Database

When building in the dev environment, you have a filtered copy of the live database with just the publicly available data. It may look like what you'll find on the site, but changes you make won't show up on the site. Currently, there's no easy way to transfer data you make on your dev environment back to production, so be sure to build levels you want to share on the site, not on the dev server.

#### Setup
Download [the public CodeCombat MongoDB sandbox copy backup](http://54.91.159.37/dump.tar.gz) (updated every 10 minutes) and import it into your locally running database with the following steps. 

1. Make sure the database is running on your computer (./bin/coco-mongodb).
2. If the backup file is compressed, uncompress it (for instance, if it is a .tar.gz file, run `tar xzvf [filename]`) 
3. Step 2 should generate a `dump` folder. To import this run `mongorestore --drop [path to dump]` if mongorestore is in your path. If it's not and you used the script, run `[path to CodeCombat folder]/bin/mongo/mongorestore --drop [path to dump]`

When downloading a new dump to keep the database up-to-date, use `mongorestore --drop [path to dump]` to clear out all old data (including any local data you have created) and replace with just the new data.

### Third Party Services

API services we use such as MailChimp will not be accessible unless you have an API key. Generally you shouldn't need them to work on the site, but if you do then let us know and we'll see if we can get something worked out. Some systems may break without the keys, and so will need to be modified to soldier on without them.