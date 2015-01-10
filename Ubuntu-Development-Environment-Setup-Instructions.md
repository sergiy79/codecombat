Thank you to Steve Malmskog for writing this great guide on getting the development environment running on Ubuntu 12.04 LTS!

###Installation
The installation assumes a couple destinations. Season to taste:

* $ export COCO_TREE=~/src/coco/codecombat
* $ export COCO_DB=~/src/coco/db
* $ export MONGO_DL=~/mongodl

Sometimes these will not work, if that is the case just replace the variable names with the location whenever you see them.

Fork and download the codecombat git repo:
- Create git account or sign in
- Go to http://github.com/codecombat/codecombat
- Click 'Fork' to fork the repo.
- Clone the repo:
    - mkdir -p $COCO_TREE && cd $COCO_TREE
    - git clone https://github.com/codecombat/codecombat.git .
        (make it git clone https://github.com/[github_yourname_OR_ID]/codecombat/codecombat.git .)
       (what you're doing in this step is cloning your repo that you forked 
           and you'll link it with remote step next : path depends on how you setted)
         (Try to follow https://help.github.com/articles/fork-a-repo/)
    - git remote add upstream https://github.com/codecombat/codecombat.git

Download and install nodejs for Ubuntu 12.04:
- sudo add-apt-repository ppa:chris-lea/node.js
- sudo apt-get update
- sudo apt-get install nodejs

Install node packages:
- cd $COCO_TREE (based on codecombat directory with packages)
- npm install 

Install brunch and bower:
- sudo npm install -g brunch
- sudo npm install -g bower

Install ruby and sass:
- sudo apt-get install ruby1.9.1 ruby1.9.1-dev
- sudo gem install sass

Setup bower:
- cd $COCO_TREE && bower install

Download and (manually) install mongodb 2.6 for Linux:
- mkdir -p $MONGO_DL && cd $MONGO_DL
- wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-2.6.4.tgz (wget https://fastdl.mongodb.org/linux/mongodb-linux-i686-2.6.4.tgz for 32-bit)
- tar xfz mongodb-linux-x86_64-2.6.4.tgz
- sudo cp mongodb-linux-x86_64-2.6.4/bin/* /usr/local/bin
- sudo mkdir -p /data/db
- sudo chown -R \<username\>:\<username\> /data/db
   where \<username\> = your username (e.g., whoami)

Download and unpack database snapshot:
- mkdir -p $COCO_DB && cd $COCO_DB
- wget http://54.91.159.37/dump.tar.gz
- tar xfz dump.tar.gz

Install database snapshot:
- In first terminal:
   - cd $COCO_TREE && bin/coco-mongodb
- In another terminal:
   - cd $COCO_DB && mongorestore --drop dump

###Running

Start up mongo:
- Mongo should already be running from your database snapshot install. If not:
   - cd $COCO_TREE && bin/coco-mongodb

Start up brunch:
- cd $COCO_TREE && bin/coco-brunch
   Note: you may get a ulimit warning; you can safely ignore.
   This should say something like:

   info: compiled 696 files into 6 files, copied 286 in 34766ms

   It will continue to run in the foreground.

Start up the dev server:
- cd $COCO_TREE && bin/coco-dev-server

Accessing the local instance of codecombat:
- Start up a local browser and go to: http://localhost:3000.

###Code Syncing

Pick up upstream changes:
- git fetch upstream
