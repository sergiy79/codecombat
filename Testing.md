Testing is a very valuable process. Like version control, it absolves programmers from fear of making changes that might break things.

Unfortunately, our testing system is subpar. The server side has pretty good testing, but it can sometimes be hard to figure out why things break when they do and it relies on a separate server and database in order to work. It's a hassle to set up. The browser tests are worse in all these regards.

Treema has some pretty good testing. It has no auto-runner, but it does a good job of poking and prodding at an interface and identifying issues when they happen.

The testing system needs some serious work and definition. This would be an ambitious project for an ambitious Archmage to tackle, especially if they are familiar with testing JavaScript on clients and servers.

## Running server tests

* Run coco-mongodb
* Run coco-test-server
* Run coco-server-test-runner

Now when you make changes to server code or tests, the server-test-runner will run the tests in /test/server and show results in the terminal.

## Running client tests

* Run coco-mongodb
* Run coco-brunch
* Run coco-client-test-runner

A Chrome browser should appear. You can minimize it; it's karma running the tests. Whenever client side code changes or tests change, karma should run the tests from /test/app in that extra browser window and show results in the terminal.