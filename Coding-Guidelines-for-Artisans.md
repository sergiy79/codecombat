We're teaching people [JavaScript](http://en.wikipedia.org/wiki/JavaScript). Therefore it is important that we have a consistent and clear coding style that is as close to standard JavaScript as possible. Every [Artisan](http://www.codecombat.com/contribute/artisan) should apply this coding standard in his levels to keep the code through all the levels consistent. This will lead to nice code, that can easily be read and prevents any form of confusion for players.

**Note:** This code style is heavily based on [this original JavaScript Coding Style](http://neil.rashbrook.org/Js.htm) and is influenced by the [Mozilla Coding Style](https://developer.mozilla.org/en-US/docs/Developer_Guide/Coding_Style).

# JavaScript Style Guide

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
* No space after keywords, e.g. if(x > 0).
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
* Use _interCaps_ for names and enumeration values; other constants should be in _UPPER_CASE_.
* Use an underscore (“_”) as the private prefix for properties and methods.
* Enumeration values should be prefixed with the letter k, e.g. const kDisplayModeNormal = 0;.
* Global variables should be prefixed with the letter g, e.g. var gFormatToolbar;.
* Arguments (parameter names) should be prefixed with the letter a.
* Event handler functions should be prefixed with the word on,
  * in particular try to use the names _onLoad, onDialogAccept, onDialogCancel_ etc. where this is unambiguous.
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
* If you are unsure if an object member exists, use "name" in aObject, or if you are expecting a particular type you may use typeof aObject.name == "function" (or whichever type you are expecting).
* Use [value, ...] to create a JavaScript array in preference to using new Array(value, ...) which can be confusing;
  * new Array(length) will actually create a physically empty array with the given logical length.
  * [value] will always create a 1-element array.
  * You cannot actually guarantee to be able to preallocate memory for an array.
* Use { member: value, ... } to create a JavaScript object;
  * a useful advantage over new Object() is the ability to create initial properties
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
  * For instance, to check that aString is not completely whitespace use /\S/.test(aString);
  * only use aString.search if you need to know the position of the result, or aString.match if you need to collect matching substrings (delimited by parentheses in the regular expression).
* Regular expressions are less useful if the match is unknown in advance, or to extract substrings in known positions in the string.
  * For instance, aString.slice(-1) returns the last letter in aString, or the empty string if aString is empty.
* Do not compare x == true or x == false. Use (x) or (!x) instead. x == true, in fact, is different from if (x)!
* Compare objects to null, numbers to 0 or strings to "" if there is chance for confusion.
* It's always worth reading the [JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference).
  * For instance, don't forget that you can index a string as if it was an array.