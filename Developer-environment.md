## Getting started

### The new, easy, buggy way

1. [Set up a GitHub account](https://help.github.com/articles/set-up-git) if you don't already have one.
1. Open a terminal and paste this in:
```bash
curl https://raw.github.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | sudo bash
```
1. Follow the prompts. This should download and install all the necessary dependencies.
1. Run the scripts at `coco/bin/startDatabase.py`, `coco/bin/startBrunch.py`, and `coco/bin/startApp.py`.
1. Go to [http://localhost:3000](http://localhost:3000) to see your local CodeCombat in action.

This should work on Mac and Linux, but it's brand new, so please let us know of any problems you run into. On Mac, you'll need [Xcode Developer Tools](http://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12). On Linux, you'll need ruby, curl, and git installed. We'll be making it work on Windows soon.

To get a sandbox copy of the CodeCombat database for your local Mongo, see [Restoring a backup](https://github.com/codecombat/codecombat/wiki/Developer-environment#restoring-a-backup).

### The do-it-yourself way

**TODO: document this better**

1. [Set up a GitHub account](https://help.github.com/articles/set-up-git) if you don't already have one.
1. Fork the CodeCombat project.
1. `git clone` it to your computer.
1. Install software (gem, npm, npm_modules).
1. Run whatever is required to download the dev environment mongo stuff.
1. Run bin/coco-brunch and bin/coco-dev-server.
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

When building in the dev environment, you have a filtered copy of the live database with just the publicly available data. It may look like what you'll find on the site, but changes you make won't show up on the site. Currently, there's no automatic way to transfer data you make on your dev environment back to production, so be sure to build levels you want to share on the site.

#### Restoring a backup
Download [the public CodeCombat MongoDB sandbox copy backup](https://s3.amazonaws.com/uploads.hipchat.com/60497/416620/ZMjjuurAEY3SUb9/coco_backup_public.tar.gz) and import it into your locally running database with the following steps.

1. Make sure the database is running on your computer.
2. If the backup file is compressed, uncompress it (for instance, if it is a .tar.gz file, run `tar xzvf [filename]`) 
3. Step 2 should generate a `dump` folder. To import this run `mongorestore [path to dump]` if mongorestore is in your path, or if it's not and you used the script, run `[path to CodeCombat folder]/bin/mongo/mongorestore [path to dump]`

### Third Party Services

API services we use such as MailChimp will not be accessible unless you have an API key. Generally you shouldn't need them to work on the site, but if you do then let us know and we'll see if we can get something worked out. Some systems may break without the keys, and so will need to be modified to soldier on without them.