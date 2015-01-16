###Index

* [Mac OS X Screencast](https://www.youtube.com/watch?v=fom1ksXSbKM)
* [Mac Tutorial](#simplemac)
* [Vagrant Tutorial](#the-do-it-yourself-vagrant-vm-method)

### <a name="simplemac"></a> Simple Linux and Mac Tutorial

This method should work on Mac and Linux, if you run into any problems, let us know!  On Mac, you'll need the [XCode Developer Tools](http://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12).

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

###The Do-It-Yourself Vagrant VM Method
If you have [vagrant](http://www.vagrantup.com/) and virtualbox installed, [https://github.com/dpen2000/Codecombat-Vagrant](https://github.com/dpen2000/Codecombat-Vagrant) provides a method of starting a vagrant-managed VM with folder mappings, the website available at http://localhost:3000/ on your host machine and the latest mongo data auto restored into your Mongo instance (included in VM). Setup instructions are in the [Readme](https://github.com/dpen2000/Codecombat-Vagrant/blob/master/README.md).  
##### The-do-it-via-a-vm-way (THIS METHOD IS UNAVAILABLE FOR NOW, DOWNLOAD LINKS DO NOT WORK)
If you want to run the VM, you'll have to [download VirtualBox](http://download.virtualbox.org/virtualbox/4.3.6/VirtualBox-4.3.6-91406-Win.exe), install it, then [download](https://s3.amazonaws.com/CodeCombatLargeFiles/CoCoLinux.ova) ([torrent](https://s3.amazonaws.com/CodeCombatLargeFiles/CoCoLinux.ova?torrent)) and import the CodeCombat Linux appliance by going to File:Import Appliance (note that occasionally the large download may be corrupted, so it's often easier to use the torrent.) The "CodeCombat" user account password is "coco". Once you have the Linux virtual machine running, the follow the directions above. To ease development, you can set up a shared folder so that you can edit files in Windows and have them accessible to the Ubuntu VM. See directions for setting up shared folders [here.](http://mikesmithers.wordpress.com/2011/03/23/installing-ubuntu-in-virtualbox-on-a-windows-7-host/#attachment_898) You can also [set up bridged networking](http://askubuntu.com/questions/196118/how-to-access-localhost-on-virtualbox-host-machine) so that your server is accessible from Windows.
