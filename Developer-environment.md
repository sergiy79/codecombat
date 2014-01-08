## Getting started

### The easy, hands-off way

If you're running Mac OS X, you can see a screencast of the process [here.](https://www.youtube.com/watch?v=fom1ksXSbKM) If you're running Ubuntu, you can see a screencast [here.](http://youtu.be/usN85KSiWUM)

These directions apply to Linux and Mac OS X. For Windows, [see the paragraph near the bottom of this section.](#windows_details)

1. [Set up a GitHub account](https://help.github.com/articles/set-up-git) if you don't already have one.
1. (Optional) If you'd like your changes able to be integrated into the official CodeCombat repository, click the *Fork* button in the upper right hand corner of the page.
1. Open a terminal. 
    * If you've forked the repository, paste in the following command *with your forked repository URL*
```bash
curl https://raw.github.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash -s your_repository_url
```
    * If you haven't forked the repository, copy and paste in the following command
```bash
curl https://raw.github.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash
```
1. Follow the prompts. This should download and install all the necessary dependencies. If you've used the script above, it will prompt you to run the command below. If you cloned the repository yourself, you can also run the script below (you may need to edit it based on your current working directory.)
```
sudo python ./coco/scripts/devSetup/setup.py
```
1. Run each of these scripts in their own separate terminal window:
    * `coco/bin/coco-mongodb` (starts MongoDB, which stays running and awaits connections)
    * `coco/bin/coco-brunch` (starts brunch, which stays running and watches for file changes, may need to be run as sudo to increase the ulimit if brunch fails)
    * `coco/bin/coco-dev-server` (starts your local webserver, which stays running and watches for file changes)
1. Do the [MongoDB database import](https://github.com/codecombat/codecombat/wiki/Developer-environment#setup) *(we're working to making this optional)*
1. Go to [http://localhost:3000](http://localhost:3000) to see your local CodeCombat in action.

NOTE: The repository will be in the coco subdirectory.  You should not run a separate git clone, as that is taken care of.

This should work on Mac and Linux, but it's brand new, so please let us know of any problems you run into. On Mac, you'll need [Xcode Developer Tools](http://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12). On Linux, you'll need ruby, curl, and git installed. 

To get a sandbox copy of the CodeCombat database for your local Mongo, see [Restoring a backup](https://github.com/codecombat/codecombat/wiki/Developer-environment#restoring-a-backup).

<a name="windows_details"></a>
####Windows 
There isn't support for Windows yet（but coming very soon!), so you'll have to [download VirtualBox](http://download.virtualbox.org/virtualbox/4.3.6/VirtualBox-4.3.6-91406-Win.exe), install it, then [download](https://s3.amazonaws.com/CodeCombatLargeFiles/CoCoLinux.ova) ([torrent](https://s3.amazonaws.com/CodeCombatLargeFiles/CoCoLinux.ova?torrent)) and import the CodeCombat Linux appliance by going to File:Import Appliance (note that occasionally the large download may be corrupted, so it's often easier to use the torrent.) Once you have the Linux virtual machine running, the follow the directions above. To ease development, you can set up a shared folder so that you can edit files in Windows and have them accessible to the Ubuntu VM. See directions for setting up shared folders [here.](http://mikesmithers.wordpress.com/2011/03/23/installing-ubuntu-in-virtualbox-on-a-windows-7-host/#attachment_898) You can also [set up bridged networking](http://askubuntu.com/questions/196118/how-to-access-localhost-on-virtualbox-host-machine) so that your server is accessible from Windows.


### The do-it-yourself way

**TODO: document this better**

If you're on Ubuntu, check out [Steve Malmskog's instructions.](https://github.com/codecombat/codecombat/wiki/Ubuntu-Development-Environment-Setup-Instructions)

1. [Set up a GitHub account](https://help.github.com/articles/set-up-git) if you don't already have one.
1. Fork the CodeCombat project.
1. `git clone` it to your computer.
1. Install software
  1. sudo npm install
  1. bower install
  1. sudo npm install -g brunch
  1. Download [MongoDB 2.5.4](http://www.mongodb.org/downloads) and put the mongo folder in bin
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
Download [the public CodeCombat MongoDB sandbox copy backup](https://s3.amazonaws.com/uploads.hipchat.com/60497/416620/DyI9sxIrTmiR6ms/coco_backup_public.tar.gz) and import it into your locally running database with the following steps.

1. Make sure the database is running on your computer (./bin/coco-mongodb).
2. If the backup file is compressed, uncompress it (for instance, if it is a .tar.gz file, run `tar xzvf [filename]`) 
3. Step 2 should generate a `dump` folder. To import this run `mongorestore [path to dump]` if mongorestore is in your path. If it's not and you used the script, run `[path to CodeCombat folder]/bin/mongo/mongorestore [path to dump]`

### Third Party Services

API services we use such as MailChimp will not be accessible unless you have an API key. Generally you shouldn't need them to work on the site, but if you do then let us know and we'll see if we can get something worked out. Some systems may break without the keys, and so will need to be modified to soldier on without them.