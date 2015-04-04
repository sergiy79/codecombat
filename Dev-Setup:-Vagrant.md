## About This Method

[Vagrant](https://www.vagrantup.com) is a tool for rapidly creating and configuring [virtual machines](http://en.wikipedia.org/wiki/Virtual_machine).

By using Vagrant, we can quickly create an environment for CodeCombat with all the necessary dependencies, without requiring these dependencies to be installed directly on your computer. Vagrant also simplifies rebuilding the environment and upgrading to newer versions of dependencies.

Vagrant supports a number of virtual machine environments. For this setup we will be using [VirtualBox](https://www.virtualbox.org/).

## Installation

Start by installing [Vagrant](https://www.vagrantup.com), [VirtualBox](https://www.virtualbox.org/), and [Git](http://git-scm.com/). If running on Windows, either Git for Windows or [GitHub for Windows](https://windows.github.com/) may be used.

Choose a folder on your computer for CodeCombat and clone the repository from GitHub. If you are intending to contribute, it is a good idea to fork the repository on GitHub first, then clone your fork.

If cloning on Windows, the Git section of the [Windows setup guide](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Windows#repository-setup) may be helpful. You only need to do the steps related to `git clone`.

## Setup

If you installed Git Bash, you can use it for these steps. Otherwise a regular Windows command prompt works too. On Linux and Mac, of course there is already a Terminal application available.

First open two copies of a command prompt. In each of them, change directory to where you cloned CodeCombat.

Enter the command `vagrant up`.

This will start the virtual machine. The first time you run it, it will download a copy of the vagrant "box", which is a copy of Ubuntu Linux that we will use to run CodeCombat. This box file is stored in your home directory in a subdirectory called `.vagrant.d` so it does not have to be downloaded every time.

If running on Windows and this is the first time you have used a VirtualBox virtual machine, you may get a firewall prompt. Be sure to allow VirtualBox access as requested, or we will not be able to connect to CodeCombat running inside the virtual machine.

The first time you do `vagrant up`, it will take much longer, because it will install the various dependencies, like Node, Bower, and MongoDB.

If there are errors during the setup, you can try `vagrant destroy` followed by `vagrant up` again. If you aren't able to figure it out, try asking in the [CodeCombat chat room](http://www.hipchat.com/g3plnOKqa).

## Running CodeCombat

Once the `vagrant up` command has completed successfully, change directory in each of your two command windows to where you cloned CodeCombat, and run these two commands:

* Linux / Mac / Windows with Git Bash:
  * scripts/vagrant/brunch.sh
  * scripts/vagrant/dev-server.sh
* Windows command prompt:
  * scripts\vagrant\brunch.bat
  * scripts\vagrant\dev-server.bat

Once the Brunch window shows that it has compiled the files, you can visit [http://localhost:3000](http://localhost:3000) in your browser and see CodeCombat running.

## Shutting down

First, hit `Ctrl-C` in each of the two command windows to stop Brunch and the dev server. Then, run `vagrant halt` in either window. This will stop the virtual machine but keep it available for future use. To start the VM again, just run `vagrant up`.

## Updating the MongoDB database

The first time `vagrant up` is run, it runs a provisioning script that installs dependencies. This script then runs `fillMongo.sh`, which downloads the latest [database dump](http://analytics.codecombat.com:8080/dump.tar.gz) and installs it into MongoDB.

To update the database to the latest version, there is an update script in `scripts/vagrant`. However, note that this update script drops the existing contents of the MongoDB database. If you wish to save user and achievement data, first run the backup script, which will make a copy of these MongoDB collections. The update script will look for this backup and load it into MongoDB after loading the latest dump of the production database.

* Linux / Mac / Windows with Git Bash:
  * scripts/vagrant/backup.sh
  * scripts/vagrant/update.sh
* Windows command prompt:
  * scripts\vagrant\backup.bat
  * scripts\vagrant\update.bat

## Rebuilding the virtual machine

The virtual machine has a copy of the various node dependencies, as well as some other tools used in running CodeCombat, such as MongoDB. It may be necessary to update the virtual machine as dependencies or dependency versions are changed.

To handle dependency changes, open a command window and change to the directory where you cloned CodeCombat. Run `vagrant provision`. Note that this will update the MongoDB database, so be sure to read the section above if you want to save users and achievements.

To rebuild the virtual machine from scratch, run `vagrant destroy` followed by `vagrant up`. This will destroy and re-create the MongoDB database from scratch, so be sure to read the section above if you want to save users and achievements.

## Extra notes

* On Windows, if you hit `Ctrl-C` to interrupt Vagrant while it is in the middle of an operation, it may return to the command prompt but still be running. This prevents any other Vagrant command from working. Just hit `Ctrl-C` again to fully terminate the previous command.
* The CodeCombat directory is visible inside the virtual machine as `/vagrant`. 
  * This uses VirtualBox shared folders, using the VirtualBox Guest Additions. 
  * If the Guest Additions are a different version from the installed VirtualBox (a common occurrence), then symbolic links will not work on Windows. 
  * This is problematic because `npm` likes to make symlinks to executables in `node_modules/.bin`. 
  * To work around this, a directory `/node_modules` is made inside the virtual machine and is mounted over top of `/vagrant/node_modules`.
  * This means that the `node_modules` directory will appear empty from outside the virtual machine. It should not be deleted.
* [Brunch](http://brunch.io/) is used by CodeCombat to watch for changes to Coffeescript files and recompile them automatically. In order to allow Brunch running in the virtual machine to detect changes made on the "host" machine, "polling" mode is used. This results in higher CPU usage.
  * In order to avoid this and run Brunch in regular mode, you can start Brunch manually inside the VM by `vagrant ssh`, `cd /vagrant`, and `brunch w`. You will need to have an SSH client installed (e.g. the one installed by Git for Windows).
  * When running Brunch in regular mode, changes must be made from inside the virtual machine (i.e. via `vagrant ssh`). The virtual machine is running Ubuntu Linux, so any of the normal text mode editors may be installed and used.

