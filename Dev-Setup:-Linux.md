###Index:

* [Automatic Linux Installation](#automatic-linux-installation)
* [Complex Linux Installation](#complex-linux-installation)
* [Ubuntu Installation](#ubuntu-installation)
* [Installing the Database](#installing-the-database)
* [Ubuntu Screencast](http://youtu.be/usN85KSiWUM) (video)

####Automatic Linux Installation

On Linux, you'll need _make_, _build-essential_, _ruby_, _curl_ and _git_ installed (`sudo apt-get install make build-essential ruby curl git`).

1. [Create a GitHub account](https://github.com/join) if you don't already have one.
2. [Set up Git on your computer](https://help.github.com/articles/set-up-git/) to allow your computer to speak to GitHub.
3. (Optional) [Fork](https://github.com/codecombat/codecombat/fork) our CodeCombat repository if you wish to make changes.
4. Open a terminal and navigate to the folder you wish to install CodeCombat under.
5. * If you've forked the repository, paste in the following command (*Replace "your_repository_url" with your repository*):

    ```bash
    curl https://raw.githubusercontent.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash -s your_repository_url
    ```
   * If you haven't forked the repository, paste in the following command:
    ```bash
    curl https://raw.githubusercontent.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash
    ```
    NOTE: The repository will be in the coco subdirectory.  You should not run a separate git clone, as that is taken care of.
6. Ensure you have Python 2 installed with `sudo apt-get install python2`, or your distributional equivalent.  Python 3.1 is also supported, but 3.2+ are not tested.  If that is not working, it is also possible to install it directly from the Ubuntu software center.
7. Follow the on-screen prompts.  The program will download and install all necessary dependencies.  If nothing seems to be happening, try running `sudo python ./coco/scripts/devSetup/setup.py` or join the [HipChat room](https://www.hipchat.com/g3plnOKqa) to fix things.
7.  Run the following commands in separate windows (these are python scripts, so make sure you have a python IDE installed):
    * `./coco/bin/coco-mongodb` - Starts MongoDB
    * `sudo ./coco/bin/coco-brunch` - Starts brunch, which watches for file changes 
    * `./coco/bin/coco-dev-server` - Starts your local web server
9. Setup [MongoDB](#installing-the-database).
9. Visit [http://localhost:3000](http://localhost:3000) to see your CodeCombat development environment!

If you get errors with bower not being able to clone git repositories, try [cloning over https](http://stackoverflow.com/questions/1722807/git-convert-git-urls-to-http-urls/11383587#11383587).  If SASS brings up an error about file encodings being wrong, add this to your .bash_profile:
```bash
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```
If you only see a white screen, check to see if the first line of app.css is `ERROR: Cannot load compass`. If so, try either uninstalling compass (`gem uninstall compass`) or re-installing it if you actually need it (`gem install compass --pre`).

####Complex Linux Installation

1. [Set up a GitHub account](https://help.github.com/articles/set-up-git) if you don't already have one.
2. [Fork](https://github.com/codecombat/codecombat/fork) the CodeCombat project.
3. `git clone` it to your computer.
4. Install software
  1. `sudo npm install`
  2. `sudo npm install -g bower` - _It might be necessary to do `cd coco`_
  3. `bower install` ( bower install each dependency from bower.json, make sure you're inside the coco directory )
  4. `sudo npm install -g brunch`
  5. Download [MongoDB 2.6.0](http://www.mongodb.org/downloads)
  6. Start up Mongodb and define the bin folder of coco as your --dbpath variable
5. Run `bin/coco-mongodb`, `bin/coco-brunch` and `bin/coco-dev-server`.
6. Go to [http://localhost:3000](http://localhost:3000) to see your local CodeCombat in action.

####Ubuntu Installation

Thank you to Steve Malmskog for writing this great guide on getting the development environment running on Ubuntu 12.04 LTS (and later)!

#####Installation
The installation assumes a couple destinations. Season to taste:

* `export COCO_TREE=~/src/coco/codecombat`
* `export COCO_DB=~/src/coco/db`
* `export MONGO_DL=~/mongodl`

Fork and download the codecombat git repo:
- Create a git account or sign in
- [Fork](https://github.com/codecombat/codecombat/fork) the CodeCombat repository
- Clone the repository:
    - `mkdir -p $COCO_TREE && cd $COCO_TREE`
    - `git clone https://github.com/[YOUR_USERNAME_OR_ID]/codecombat.git`
    - `git remote add upstream https://github.com/codecombat/codecombat.git`

Download and install Node.JS for Ubuntu 12.04 (and later):
- `sudo add-apt-repository ppa:chris-lea/node.js`
- `sudo apt-get update`
- `sudo apt-get install nodejs`

Install node packages:
- `cd $COCO_TREE` (based on CodeCombat directory with packages)
- `npm install `

Install brunch and bower:
- `sudo npm install -g brunch`
- `sudo npm install -g bower`

Install ruby and sass:
- `sudo apt-get install ruby1.9.1 ruby1.9.1-dev`
- `sudo gem install sass`

Setup bower:
- `cd $COCO_TREE && bower install`

Download and (manually) install mongodb 2.6 for Linux:
- `mkdir -p $MONGO_DL && cd $MONGO_DL`
- `wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-2.6.4.tgz` (`wget https://fastdl.mongodb.org/linux/mongodb-linux-i686-2.6.4.tgz` for 32-bit)
- `tar xfz mongodb-linux-x86_64-2.6.4.tgz` (`tar xfz mongodb-linux-i686-2.6.4.tgz` for 32-bit)
- `sudo cp mongodb-linux-x86_64-2.6.4/bin/* /usr/local/bin` (`sudo cp mongodb-linux-i686-2.6.4/bin/* /usr/local/bin` for 32-bit)
- `sudo mkdir -p /data/db`
- `sudo chown -R <username>:<username> /data/db` where \<username\> = your username (e.g., `whoami`)

Download and unpack database snapshot:
- `mkdir -p $COCO_DB && cd $COCO_DB`
- `wget http://analytics.codecombat.com:8080/dump.tar.gz`
- `tar xfz dump.tar.gz`

Install database snapshot:
- In first terminal:
   - `cd $COCO_TREE && bin/coco-mongodb`
- In another terminal:
   - `cd $COCO_DB && mongorestore --drop dump`

#####Running

Start up mongo:
- Mongo should already be running from your database snapshot install. If not:
   - `cd $COCO_TREE && bin/coco-mongodb`

Start up brunch:
- `sudo cd $COCO_TREE && bin/coco-brunch`
   This should say something like:

   info: compiled 806 files into 597 files, copied 371 in 34766ms

   It will continue to run in the foreground.

Start up the dev server:
- `cd $COCO_TREE && bin/coco-dev-server`

Accessing the local instance of codecombat:
- Start up a local browser and go to: http://localhost:3000.

#####Code Syncing

Pick up upstream changes:
- `git fetch upstream`

####Installing the Database
Download the [CodeCombat database](http://analytics.codecombat.com:8080/dump.tar.gz) (updated every 10 minutes) and import it to your locally running database with the following commands:

1. Make sure the database is running on your computer `./bin/coco-mongodb`.

1. Uncompress the file with `tar xzvf [filename]`.

1. Run `mongorestore --drop [path to dump]` if mongorestore is in your path. If mongorestore is not in your path, run `[path to CodeCombat folder]/bin/mongo/mongorestore --drop [path to dump]`.

When downloading a new dump to keep the database up-to-date, use `mongorestore --drop [path to dump]` to clear out all old data (including any local data you have created) and replace with just the new data.