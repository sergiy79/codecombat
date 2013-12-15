## Setup

1. Set up a Github account if you don't already have one.
1. Fork the CodeCombat project.
1. Git clone it to your machine.
1. Install software (gem, npm, npm_modules).
1. Add bin to path.
1. Run whatever is required to download the dev environment mongo stuff.
1. Run coco-brunch and coco-dev-server.

## Working in the environment

You don't need any particular IDE to work with CodeCombat. Scott uses WebStorm, Nick uses Emacs and George uses Sublime Text, so already the most important parts are IDE agnostic.

### Live coding

If Brunch is running and you have a page open to the development server and you make changes to the programming logic one way or another, Brunch will reload the page automatically. So open the page you are working on in your browser, make changes in your editor, save, and the page will refresh so you can see the pages. Try to make whatever you're working on be the first thing you see when you open the page, so you don't have to lose focus on your editor while iterating. If you edit just the styling, Brunch will apply the new styling without refreshing.

Brunch is good, but it is finicky (or possibly improperly configured). Its finicks include but are not limited to:

* Stops reloading the page properly
* Takes strangely long to compile
* Doesn't compile every file into app.js

Usually, restarting it by hitting Ctrl-C once in the Brunch terminal window will fix it. Because of the frequency of it needing restarting, it will automatically restart when terminated once, and will only really stop if it's terminated twice in a row manually.

### Database

When building in the dev environment, you have a filtered copy of the live database with just the publicly available data. It may look like what you'll find on the site, but changes you make won't show up on the site. Currently, there's no automatic way to transfer data you make on your dev environment back to production, so be sure to build levels you want to share on the site.

### Third Party Services

API services we use such as MailChimp and FireBase will not be accessible unless you have an API key. Generally you shouldn't need them to work on the site, but if you do then let us know and we'll see if we can get something worked out. Some systems may break without the keys, and so will need to be modified to soldier on without them.