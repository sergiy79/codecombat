<div style="text-align:center"><img src ="http://www.owstartup.com/wp-content/uploads/2014/05/code-combat.png" /></div>

Hello [Archmages](http://codecombat.com/contribute/archmage)! Welcome to the developer wiki for CodeCombat. These documents are designed to give you everything you need to know, technical and non-technical, to dive into the project. If you see an opportunity to improve the docs, go ahead!

###Index:
* [Contact Us](#contact-us)
* [Starting Off](#starting-off)
* [Reading Material](#reading-material)
* [FAQ](#faq)

####Contact Us

There are a variety of ways to get help with CodeCombat related things.  We have a developer chat room at [HipChat](http://www.hipchat.com/g3plnOKqa).  Most people are in US Pacific Time (~GMT-8) but there are usually a few other players awake at other times.  We have room for off-topic talking [here](http://www.hipchat.com/gaXOD7lQ8) where you can talk about anything!

The [Discourse Forum](http://discourse.codecombat.com/) is another useful place to get help.  For more information check out the [main HipChat Room page](https://github.com/codecombat/codecombat/wiki/HipChat-Room).

####Starting Off
1. Setup the [Developer Environment](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-General-Information).
1. Make a small first commit such as [creating a new Thang name](https://github.com/codecombat/codecombat/issues/53), [adding tips to the loading screen](https://github.com/codecombat/codecombat/issues/710) or [adding documentation](https://github.com/codecombat/codecombat/issues/1237).
1. Check out the [Good for Newbies Issues](https://github.com/codecombat/codecombat/labels/good-for-newbies).
1. Browse the wiki to learn something new!
1. Fix [bugs](https://github.com/codecombat/codecombat/labels/bug).
1. Bring up new ideas in our [HipChat room](https://www.hipchat.com/g3plnOKqa).

####Reading Material
######General:
* [[Mission Statement]]
* [Developer Environment](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-General-Information) - Start here to get CodeCombat set up on your computer.
* [[Developer Organization]]
* [[Coding Guidelines]]
* [[Technical Overview]]
* [[Third Party Software and Services]]
* [[JSON-Schema]]
* [[Coco Models]]
* [[Testing]]

######Frontend Development:

* [[Client Models]]
* [[Views]]
* [[Events, Subscriptions, Shortcuts]]

######Backend Development:

* [[File System]]

######Key Systems:

* [[Versioning]]
* [[Permissions]]

######Game Engine:

* CodeCombat uses a [[Thang Component System]] architecture.
    * A [[Thang]] can be an ogre, a land, an arrow--anything.
    * Thangs are just clusters of [[Component]]s.
    * [[System]]s organize the Components.
* [[World]]s simulate deterministically.
* The [[Surface]] is what we call our graphics layer.
* The [[Tome]] is our spell editor.
* [[Multiplayer]].

######Side Projects:

* [[Treema]], our general interface for editing JSON data with schemas.
* [[Aether]], our transpiler.

####FAQ
######How do I learn Git?

Doing [this](https://www.codeschool.com/courses/try-git) quick course should get you up to speed with Git.

######Can you help with setting up my [development environment](https://github.com/codecombat/codecombat/wiki/Dev-Setup:-General-Information)?

We'll try! It should be a cinch on Linux or Mac, but it's pretty hard to get right on Windows right now. If you can't find us for help on Windows, you might try installing it on a Linux VM.  Anyone who can help with updating the Windows version is welcome to!  A good platform to setup your VM on is [Ubuntu](http://www.ubuntu.com/) which can have a desktop or only a terminal.  Also, [VirtualBox](https://www.virtualbox.org/) is easy to setup with and it free.

######What are some larger projects I can do?
[[Here's out big project ideas list|Project Ideas List]], which should give you some ideas about what you can contribute on.