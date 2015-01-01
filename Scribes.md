# Scribes

Programming and code aren't the only languages we use at CodeCombat — the written word makes our app easy to understand, fun to play, and a joy to contribute to. For these important tasks, we lean on our [Scribes](http://codecombat.com/contribute/scribe).

##How to Become a Scribe
1. Head over to the [Scribe description page](http://codecombat.com/contribute/scribe) on the main website. 
1. Click the "Contact Us" link to open a popup contact form. 
1. Tell us a little about yourself, your experience with programming and what sort of things you'd like to write about. We'll go from there!

##What Scribes Can Work On
If you're ready to flex your writing skills, here are the places where we can use your help the most: 
 
1. Each level has a guide with some level-specific tips and tricks in it. We want to make sure these guides nudge folks along, but keep the game challenging. Take a look through the existing guides and see if they make sense, especially to someone who is learning to code. As we create new levels, we need to write new guides for them, too. ([Example](https://www.dropbox.com/s/pv7yvxomlfa5nre/Screenshot%202014-12-31%2011.07.03.png?dl=0))

1. Article writing more your thing? Contribute by helping us teach a programming languages and concepts, so that when a concept is used in a level, we can pull in that article into a tab in the Guide. ([example](https://www.dropbox.com/s/qqlg39b77yp7lze/Screenshot%202014-12-31%2011.08.08.png?dl=0))

1. Each player-accessible method and property has its own documentation, which often doesn't get enough love and isn't written beginner-friendlily. We'd love to have those level up. ([example](https://www.dropbox.com/s/ejk9d9kl5749k6b/Screenshot%202014-12-31%2011.09.46.png?dl=0))

1. Each level, item, and hero has a short description associated with it. Too often we're too focused on just building these things to do a good job on the copywriting. We really need a pass over these to add great descriptions to things. ([example level](https://www.dropbox.com/s/nasq1e2cj6pnbqa/Screenshot%202014-12-31%2011.12.31.png?dl=0), [example item](https://www.dropbox.com/s/ntpjjlwxocehxqs/Screenshot%202014-12-31%2011.14.09.png?dl=0), [example hero](https://www.dropbox.com/s/fzvqomkcjot2xta/Screenshot%202014-12-31%2011.14.33.png?dl=0) and [editor](https://www.dropbox.com/s/mgzb3mwoibi7bvu/Screenshot%202014-12-31%2011.15.19.png?dl=0))

1. General website / community / contribute copy improvements. ([example](https://www.dropbox.com/s/8mr75w72t61pqhg/Screenshot%202014-12-31%2011.16.31.png?dl=0))

1. Keeping our [FAQ](http://discourse.codecombat.com/t/faq-check-before-posting/1027) simple and easy to understand.

1. Organizing, editing, and contributing content to our [GitHub wiki](http://discourse.codecombat.com/t/faq-check-before-posting/1027).

##How to Modify Content on the General Website
We maintain all the content on the website through GitHub. There are two ways to contribute: 
1. [Set up the dev environment on your computer](https://github.com/codecombat/codecombat/wiki/Developer-environment), so you can test your changes locally. _(Recommended)_ 

1. Make edits in the GitHub web interface, and a member of the core team will test your changes to make sure they work.

###Sample Workflow
Let's say you wanted to update the [adventurer character class copy](http://codecombat.com/contribute/adventurer). You'd follow this process:

1. Find the template you want to use by following the directories here: https://github.com/codecombat/codecombat/tree/master/app/templates -> this would eventually lead to /app/templates/contribute/adventurer.jade.

1. Make your changes to the copy. You can check out http://jade-lang.com/ for a reference on how it works, but it's basically super-compactified minimalist HTML.

1. Update our base localization file, /app/locale/en.coffee, to add or update any localization keys you created or changed in the template. If the text change is large, it's best to change to a new key and delete the old key, so that the Diplomats know to translate it into our 45+ languages. Otherwise, if the change is small, you can just update the existing key's text, and it'll change in English and still be translated in the other languages, but they might not notice and update it for most of them.

