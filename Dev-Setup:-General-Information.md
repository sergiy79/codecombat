### Installation Guides

Our installation guides are now split into per-OS guides.
* **[Linux Setup](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Linux)**
 * [Automatic](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Linux#automatic-linux-installation)
 * [Hands-On](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Linux#complex-linux-installation)
 * [Ubuntu Hands-On](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Linux#ubuntu-installation)
* **[Windows Setup](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Windows)**
* **[Mac and Vagrant Setup](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-Mac-and-Vagrant)**
* **[Vagrant Setup](https://github.com/codecombat/wiki/Dev-Setup:-Vagrant)** (fast setup in a virtual machine for Linux, Windows, or Mac OS)

### Working in the environment

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

### Third Party Services

API services we use such as MailChimp will not be accessible unless you have an API key. Generally you shouldn't need them to work on the site, but if you do then let us know and we'll see if we can get something worked out. Some systems may break without the keys, and so will need to be modified to soldier on without them.