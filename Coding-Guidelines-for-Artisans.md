We're teaching people [JavaScript](http://en.wikipedia.org/wiki/JavaScript). Therefore it is important that we have a consistent and clear coding style that is as close to standard JavaScript as possible. Every [Artisan](http://www.codecombat.com/contribute/artisan) should apply this coding standard in his levels to keep the code through all the levels consistent. This will lead to nice code, that can easily be read and prevents any form of confusion for players.

**Note:** This code style is heavily based on [this original JavaScript Coding Style](http://neil.rashbrook.org/Js.htm) , [the airbnb JavaScript guide](https://github.com/airbnb/javascript#guide-guide) and is influenced by the [Mozilla Coding Style](https://developer.mozilla.org/en-US/docs/Developer_Guide/Coding_Style) and materials found on it.

**Remark:** It might be a good idea to let this guide be translated by the [Diplomats](http://www.codecombat.com/contribute/diplomat), to keep it available to as many people as possible. Links to the different language pages can be listed here, once they become available.

# JavaScript Style Guide

## Table of Contents
1. [Whitespace](#whitespace)
2. [Symbols](#symbols)
3. [Code Style](#code-style)
4. [Function and variable naming](#function-and-variable-naming)
5. [JavaScript features](#javascript-features)

## Whitespace
* The basic indentaion is two spaces. Tabs are not to be used at all.
* Try to keep lines to 80 characters or less.
* When wrapping lines, try to indent to line up with a related item on the previous line. Example:
```
var result =
  prompt(
    aMessage,
    aInitialValue,
    aCaption
    );
```
* Lines should not contain trailing spaces, even after binary operators, commas or semicolons.
* Separate binary operators with spaces.
* One space after commas and semicolons, but not before.
* No space after keywords, e.g. _if(x > 0)_.
* One blank line between block definitions.
* Consider breaking up large code blocks with a blank line.

## Symbols
* Spaces around braces used for in-line functions or objects, except before commas or semicolons, e.g. 
```
function valueObject(aValue) { return { value: aValue }; };
```
* Otherwise function braces must always be on their own line, i.e.
```
function multiply(a, b)
{
  return a * b;
}
```
* Prefer double quotes, except in in-line event handlers or when quoting double quotes.
* Braces are not indented relative to their parent statement. Stick to the coding style in all situations. e.g.
```
if (x < y)
{
  x += 1;
}
else
{
  x = 0;
}
```

## Code style
* Always put else on its own line, as shown above.
* Don't use else after return, i.e.
```
if (x < y)
  return -1;
if (x > y)
  return 1;
return 0;
```
* Both i++ and ++i are acceptable.
* Name inline functions, this makes it easier to debug them. Just assigning a function to a property doesn't name the function, you should to do this:
```
var offlineObserver = {
  observe: function offlineObserve(aSubject, aTopic, aState)
  {
    if (aTopic == "network:offline-status-changed")
      setOfflineUI(aState == "offline");
  }
}
```

## Function and variable naming
* Use __interCaps__ for names and enumeration values; other constants should be in __UPPER_CASE__.
* Use an underscore (“_”) as the private prefix for properties and methods.
* Enumeration values should be prefixed with the letter k, e.g. _const kDisplayModeNormal = 0;_.
* Global variables should be prefixed with the letter g, e.g. _var gFormatToolbar;_.
* Arguments (parameter names) should be prefixed with the letter a.
* Event handler functions should be prefixed with the word on,
  * in particular try to use the names __onLoad_, _onDialogAccept_, _onDialogCancel__ etc. where this is unambiguous.
* Function names, local variables and object members have no prefix.
* Try to declare local variables as near to their use as possible; try to initialize every variable.
* Use inline comments liberally

## JavaScript features
* Make sure that your code doesn't generate any strict JavaScript warnings, such as:
  * Duplicate variable declaration
  * Mixing return; with return value;
  * Trailing comma in JavaScript object declarations
  * Undeclared variables or members.
* If you are unsure if an array value exists, compare the index to the array's length.
* If you are unsure if an object member exists, use _"name"_ in _aObject_, or if you are expecting a particular type you may use _typeof aObject.name == "function"_ (or whichever type you are expecting).
* Use _[value, ...]_ to create a JavaScript array in preference to using _new Array(value, ...)_ which can be confusing;
  * _new Array(length)_ will actually create a physically empty array with the given logical length.
  * _[value]_ will always create a 1-element array.
  * You cannot actually guarantee to be able to preallocate memory for an array.
* Use _{ member: value, ... }_ to create a JavaScript object;
  * a useful advantage over _new Object()_ is the ability to create initial properties
* Use extended JavaScript syntax to define getters and setters.
* If having defined a constructor you need to assign default properties it is preferred to assign an object literal to the prototype property. For example:
```
function SupportsString(data)
{
  this.data = data;
}
SupportsString.prototype = {
  toString: function toString()
  {
    return data;
  }
};
```
* Use regular expressions, but use them wisely.
  * For instance, to check that _aString_ is not completely whitespace use _/\S/.test(aString);_
  * only use _aString.search_ if you need to know the position of the result, or _aString.match_ if you need to collect matching substrings (delimited by parentheses in the regular expression).
* Regular expressions are less useful if the match is unknown in advance, or to extract substrings in known positions in the string.
  * For instance, _aString.slice(-1)_ returns the last letter in _aString_, or the empty string if _aString_ is empty.
* Do not compare _x == true_ or _x == false_. Use _(x)_ or _(!x)_ instead. _x == true_, in fact, is different from _if (x)!_
* Compare objects to null, numbers to 0 or strings to "" if there is chance for confusion.
* It's always worth reading the [JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference).
  * For instance, don't forget that you can index a string as if it was an array.