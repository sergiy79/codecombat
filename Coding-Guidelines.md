Any given software project does well to follow certain common rules. It's not so much that any given rule is better than another, but rather consistency is valuable so that, if everyone knows and follows the rules, decision paralysis is avoided, the project is more organized and easier to work on as a group.

## Code Style

**There's still plenty of code in CodeCombat that doesn't follow these conventions. If you find any, please fix it.**

We follow the [CoffeeScript Style Guide](https://github.com/polarmobile/coffeescript-style-guide) and [CSS Style Guide](https://github.com/styleguide/css) with these additions:

* For the sake of brevity, names that need to incorporate "CodeCombat" can be abbreviated to "Coco" (for CS) or "coco" (for Sass).
* Names that have acronyms such as "id" or "html" should be all uppercase except as the first word of an identifier. So `getID()` instead of `getId()`, `ajaxToHTML` instead of `ajaxToHtml`. (Is `id` an acronym? ... Sure!)
* We don't enforce a 79-character maximum line length.
* We don't use [spaces around default parameter values](https://github.com/polarmobile/coffeescript-style-guide#whitespace-in-expressions-and-statements): `containsPoint: (p, withRotation=true)` instead of `containsPoint: (p, withRotation = true)`. (We did a lot of Python in our youth.)
* We carelessly mix single and double quotes. Guess we could [fix this](https://github.com/polarmobile/coffeescript-style-guide#strings).
* We prefer [standalone `@` instead of `this`](https://github.com/polarmobile/coffeescript-style-guide#miscellaneous).

Note that Brunch automatically fails to compile when certain rules aren't followed, using a selection of [CoffeeLint](http://www.coffeelint.org/) rules. Keep an eye out for rule failures in Brunch output for guidance here.

## Commenting

Generally try to avoid writing low value comments; they should be mainly used to flag areas in need of improvement or that really need some explaining. Ideally, code should be structured so that reading the raw logic reveals what it is doing and how it is doing it. If a function is long and convoluted, break it down into many clearly named functions. If it's not clear what a function does, rename or otherwise refactor it to make things clearer.

## Breaking CodeCombat Down Into Third-Party Modules

Aether and Treema are built from the ground up to be modular and not tied to CodeCombat because they're large projects that we could imagine being used in a variety of other projects. There are other parts of CodeCombat which could be spun off into separate, fully autonomous projects. These projects do need to be fully autonomous, though, in terms of code. Treema and Aether are built not to have anything specific to CodeCombat. If more parts are to be spun off, they need to be generalized enough to be useful to others and without irrelevant cruft.