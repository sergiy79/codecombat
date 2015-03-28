## About This Method

[Vagrant](https://www.vagrantup.com) is a tool for rapidly creating and configuring [virtual machines](http://en.wikipedia.org/wiki/Virtual_machine).

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

* Linux / Mac:
  * scripts/vagrant/brunch.sh
  * scripts/vagrant/dev-server.sh
* Windows:
  * scripts/vagrant/brunch.bat
  * scripts/vagrant/dev-server.bat

Once the Brunch window shows that it has compiled the files, you can visit (http://localhost:3000) in your browser and see CodeCombat running.
