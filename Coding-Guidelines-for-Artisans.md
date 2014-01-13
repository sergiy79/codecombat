We're teaching people [JavaScript](http://en.wikipedia.org/wiki/JavaScript). Therefore it is important that we have a consistent and clear coding style that is as close to standard JavaScript as possible. Every [Artisan](http://www.codecombat.com/contribute/artisan) should apply this coding standard in his levels to keep the code through all the levels consistent. This will lead to nice code, that can easily be read and prevents any form of confusion for players.

**Note:** This code style is heavily based on [this original JavaScript Coding Style](http://neil.rashbrook.org/Js.htm) , [the airbnb JavaScript guide](https://github.com/airbnb/javascript#guide-guide) and is influenced by the [Mozilla Coding Style](https://developer.mozilla.org/en-US/docs/Developer_Guide/Coding_Style) and materials found on it.

**Remark:** It might be a good idea to let this guide be translated by the [Diplomats](http://www.codecombat.com/contribute/diplomat), to keep it available to as many people as possible. Links to the different language pages can be listed here, once they become available.

# JavaScript Style Guide

## Table of Contents
1. [Whitespace](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#whitespace)
2. [Symbols](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#symbols)
3. [Properties](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#properties)
4. [Conditional Expressions and Equality](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#conditional-expressions-and-equality)
5. [Code Style](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#code-style)
6. [Function and variable naming](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#function-and-variable-naming)
7. [Type Casting and Coercion](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#type-casting-and-coercion)
8. [JavaScript features](https://github.com/codecombat/codecombat/wiki/Coding-Guidelines-for-Artisans#javascript-features)

## Whitespace
* The basic indention is **two** spaces. Tabs are not to be used at all.
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
* No space after keywords, e.g. `if(x > 0)`.
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

## Properties
* Use dot notation when accessing properties.
```
var luke =
{
  jedi: true,
  age: 28
};

// bad
var isJedi = luke['jedi'];

// good
var isJedi = luke.jedi;
```
* Use subscript notation `[]` when accessing properties with a variable.
```
var luke =
{
  jedi: true,
  age: 28
};

function getProp(prop)
{
  return luke[prop];
}

var isJedi = getProp('jedi');
```

## Conditional Expressions and Equality
* Use `===` and `!==` over `==` and `!=`.
* Conditional expressions are evaluated using coercion with the `ToBoolean` method and always follow these simple rules:
  * **Objects** evaluate to **true**
  * **Undefined** evaluates to **false**
  * **Null** evaluates to **false**
  * **Booleans** evaluate to **the value of the boolean**
  * **Numbers** evaluate to **false if +0, -0, or NaN**, otherwise **true**
  * **Strings** evaluate to **false** if an empty string `''`, otherwise **true**
```
if ([0])
{
  // true
  // An array is an object, objects evaluate to true
}
```
* Use shortcuts.
```
// bad
if (name !== '')
{
  // ...stuff...
}

// good
if (name)
{
  // ...stuff...
}

// bad
if (collection.length > 0)
{
  // ...stuff...
}

// good
if (collection.length)
{
  // ...stuff...
}
```
* Do not compare `x == true` or `x == false`. Use `(x)` or `(!x)` instead. `x == true`, in fact, is different from `if (x)!`
* Compare objects to `null`, numbers to `0` or strings to `""` if there is chance for confusion.

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
* Both `i++` and `++i` are acceptable.
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
* Avoid single letter names. Be descriptive with your naming.
* Leading commas: **Nope**.
```
// bad
var once
  , upon
  , aTime;

// good
var once,
    upon,
    aTime;

// bad
var hero =
{
    firstName: 'Bob'
  , lastName: 'Parr'
  , heroName: 'Mr. Incredible'
  , superPower: 'strength'
};

// good
var hero =
{
  firstName: 'Bob',
  lastName: 'Parr',
  heroName: 'Mr. Incredible',
  superPower: 'strength'
};
```

## Function and variable naming
* Use `interCaps` for names and enumeration values; other constants should be in `UPPER_CASE`.
* Use an underscore (“_”) as the private prefix for properties and methods.
* Enumeration values should be prefixed with the letter k, e.g. `const kDisplayModeNormal = 0;`.
* Global variables should be prefixed with the letter g, e.g. `var gFormatToolbar;`.
* Arguments (parameter names) should be prefixed with the letter a.
* Event handler functions should be prefixed with the word on,
  * in particular try to use the names `onLoad`, `onDialogAccept`, `onDialogCancel` etc. where this is unambiguous.
* Function names, local variables and object members have no prefix.
* Try to declare local variables as near to their use as possible; try to initialize every variable.
* Use inline comments liberally

## Type Casting and Coercion
* Perform type coercion at the beginning of the statement.
* Strings:
```
this.reviewScore = 9;

// bad
var totalScore = this.reviewScore + '';

// good
var totalScore = '' + this.reviewScore;

// bad
var totalScore = '' + this.reviewScore + ' total score';

// good
var totalScore = this.reviewScore + ' total score';
```
* Use `parseInt` for Numbers and always with a radix for type casting.
```
var inputValue = '4';

// bad
var val = new Number(inputValue);

// bad
var val = +inputValue;

// bad
var val = inputValue >> 0;

// bad
var val = parseInt(inputValue);

// good
var val = Number(inputValue);

// good
var val = parseInt(inputValue, 10);
```
* If for whatever reason you are doing something wild and `parseInt` is your bottleneck and need to use Bitshift for [performance reasons](http://jsperf.com/coercion-vs-casting/3), leave a comment explaining why and what you're doing.
* **Note:** Be careful when using bitshift operations. Numbers are represented as [64-bit values](http://es5.github.io/#x4.3.19), but Bitshift operations always return a 32-bit integer ([source](http://es5.github.io/#x11.7)). Bitshift can lead to unexpected behavior for integer values larger than 32 bits. [Discussion](https://github.com/airbnb/javascript/issues/109)
```
// good
/**
 * parseInt was the reason my code was slow.
 * Bitshifting the String to coerce it to a
 * Number made it a lot faster.
 */
var val = inputValue >> 0;
```
* Booleans:
```
var age = 0;

// bad
var hasAge = new Boolean(age);

// good
var hasAge = Boolean(age);

// good
var hasAge = !!age;
```

## JavaScript features
* Make sure that your code doesn't generate any strict JavaScript warnings, such as:
  * Duplicate variable declaration
  * Mixing `return;` with `return value;`
  * Trailing comma in JavaScript object declarations
  * Undeclared variables or members.
* If you are unsure if an array value exists, compare the index to the array's length.
* If you are unsure if an object member exists, use `"name"` in `aObject`, or if you are expecting a particular type you may use `typeof aObject.name == "function"` (or whichever type you are expecting).
* Use `[value, ...]` to create a JavaScript array in preference to using `new Array(value, ...)` which can be confusing;
  * `new Array(length)` will actually create a physically empty array with the given logical length.
  * `[value]` will always create a 1-element array.
  * You cannot actually guarantee to be able to preallocate memory for an array.
* Use `{ member: value, ... }` to create a JavaScript object;
  * a useful advantage over `new Object()` is the ability to create initial properties
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
  * For instance, to check that `aString` is not completely whitespace use `/\S/.test(aString);`
  * only use `aString.search` if you need to know the position of the result, or `aString.match` if you need to collect matching substrings (delimited by parentheses in the regular expression).
* Regular expressions are less useful if the match is unknown in advance, or to extract substrings in known positions in the string.
  * For instance, `aString.slice(-1)` returns the last letter in `aString`, or the empty string if `aString` is empty.
* It's always worth reading the [JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference).
  * For instance, don't forget that you can index a string as if it was an array.