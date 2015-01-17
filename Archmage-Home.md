||![CodeCombat](http://www.owstartup.com/wp-content/uploads/2014/05/code-combat.png)||
|:-:|:-:|:-:|

Hello [Archmages](http://codecombat.com/contribute/archmage)! Welcome to the developer wiki for CodeCombat. These documents are designed to give you everything you need to know, technical and non-technical, to dive into the project. If you see an opportunity to improve the docs, go ahead!

###Index
* [Contact Us](#contact-us)
* [Starting Off](#starting-off)
* [Reading Material](#reading-material)
* [FAQ](#faq)

## Beginners
####Contact Us

CodeCombat has a public HipChat room at [http://www.hipchat.com/g3plnOKqa](http://www.hipchat.com/g3plnOKqa), where we hang out when we're awake. Stop by, say hi, and ask a question any time. Although the core devs are asleep during the night (US Pacific time), there are usually a few other players awake.

There's also an off-topic room at [http://www.hipchat.com/gaXOD7lQ8](http://www.hipchat.com/gaXOD7lQ8).

You can also come to the [Discourse Forum](http://discourse.codecombat.com/) or check the [main HipChat Room page](https://github.com/codecombat/codecombat/wiki/HipChat-Room).


####Starting Off
If you are new to coding or have a question, check the FAQ at the bottom of this page.

* You should set up the [[Developer Environment]].

* You should check the [good-for-newbies issues](https://github.com/codecombat/codecombat/labels/good-for-newbies). You should easily do your first commit by [creating new Thang names](https://github.com/codecombat/codecombat/issues/53), [adding new tips for the loading screen](https://github.com/codecombat/codecombat/issues/710) or [adding documentation](https://github.com/codecombat/codecombat/issues/1237).

* You should check all this wiki and understand how is CodeCombat organized. 

* You can also [fix different bugs](https://github.com/codecombat/codecombat/labels/bug) or bring up new ideas in the HipChat.


##Reading Material
####General:
* [[Mission Statement]]
* [[Developer Environment]] -- Start here to get CodeCombat set up on your computer.
* [[Developer Organization]]
* [[Coding Guidelines]]
* [[Technical Overview]]
* [[Third Party Software and Services]]
* [[JSON-Schema]]
* [[Coco Models]]
* [[Testing]]

####Frontend Development:

* [[Client Models]]
* [[Views]]
* [[Events, Subscriptions, Shortcuts]]

####Backend Development:

* [[File System]]

####Key Systems:

* [[Versioning]]
* [[Permissions]]

####Game Engine:

* CodeCombat uses a [[Thang Component System]] architecture.
    * A [[Thang]] can be an ogre, a land, an arrow--anything.
    * Thangs are just clusters of [[Component]]s.
    * [[System]]s organize the Components.
* [[World]]s simulate deterministically.
* The [[Surface]] is what we call our graphics layer.
* The [[Tome]] is our spell editor.
* [[Multiplayer]]

####Side Projects:

* [[Treema]], our general interface for editing JSON data with schemas
* [[Aether]], our transpiler

##FAQ
**I don't understand git!!**

Doing [this](https://www.codeschool.com/courses/try-git) super duper fast course should help get you comfortable.

**Can you help me [set up my dev environment](https://github.com/codecombat/codecombat/wiki/Developer-environment)?**

We'll try! It should be a cinch on Linux or Mac, but it's pretty hard to get right on Windows right now. If you can't find us for help on Windows, you might try installing it on a Linux VM. (We'll be happy when someone can take the time and help us update our Windows installer.)

**What can I do to get into [Google Summer](https://github.com/codecombat/codecombat/wiki/Summer-Project-Ideas-List) of Code in 2015?**

We can't guarantee whether CodeCombat will participate or how many slots we'll get (last year there were four), but two things are certain: 1) competition will be high, and 2) preference will have to go to those who have already been contributing to our GitHub so that we know you can be effective working with our stack. So if you'd like to get paid to hack on CodeCombat for the summer for GSoC, let's start hacking on stuff together now. (And you might want to pick a backup organization, too, in case there aren't enough slots.)