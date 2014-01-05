Thank you to Steve Malmskog for writing this great guide on getting the development environment running on Ubuntu 12.04 LTS!

###Installation
The installation assumes a couple destinations. Season to taste:

* $ export COCO_TREE=~/src/coco/codecombat
* $ export COCO_DB=~/src/coco/db
* $ export MONGO_DL=~/mongodl

Fork and download the codecombat git repo:
- Create git account or sign in
- Go to http://github.com/codecombat/codecombat
- Click 'Fork' to fork the repo.
- Clone the repo:
    - mkdir -p $COCO_TREE && cd $COCO_TREE
    - git clone https://github.com/codecombat/codecombat.git
    - git remote add upstream https://github.com/codecombat/codecombat.git

Download and install nodejs for Ubuntu 12.04:
- sudo add-apt-repository ppa:chris-lea/node.js
- sudo apt-get update
- sudo apt-get install nodejs

Install node packages:
- cd $COCO_TREE && npm install

Install brunch and bower:
- sudo npm install -g brunch
- sudo npm install -g bower

Install ruby and sass:
- sudo apt-get install ruby1.9.1
- sudo install sass

Setup bower:
- cd $COCO_TREE && bower install

Download and (manually) install mongodb 2.5.4 for Linux:
- cd $MONGO_DL
- wget http://fastdl.mongodb.org/linux/mongodb-linux-x86_64-2.5.4.tgz
- tar xfz mongodb-linux-x86_64-2.5.4.tgz)
- sudo cp bin/* /usr/local/bin
- sudo mkdir -p /data/db
- sudo chown -R <username>:<username> /data/db
   where <username> = your username (e.g., whoami)

Download and unpack database snapshot:
- mkdir -p $COCO_DB && cd $COCO_DB
- wget https://s3.amazonaws.com/uploads.hipchat.com/60497/416620/DyI9sxIrTmiR6ms/coco_backup_public.tar.gz
- tar xfz coco_backup_public.tar.gz

Install database snapshot:
- In first terminal:
   - cd $COCO_TREE && bin/coco-mongodb
- In another terminal:
   - cd $COCO_DB && mongorestore dump

###Running

Start up mongo:
- Mongo should already be running from your database snapshot install. If not:
   - cd $COCO_TREE && bin/coco-mongodb

Start up brunch:
- cd $COCO_TREE && bin/coco-brunch
   Note: you may get a ulimit warning; you can safely ignore.
   This should say something like:

   info: compiled 411 files into 7 files, copied 102 in 47797ms

   It will continue to run in the foreground.

Start up the dev server:
- cd $COCO_TREE && bin/coco-dev-server

Accessing the local instance of codecombat:
- Start up a local browser and go to: http://localhost:3000.

###Code Syncing

Pick up upstream changes:
- git fetch upstream