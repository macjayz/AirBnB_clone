Airbnb JavaScript Style Guide() {
A mostly reasonable approach to JavaScript

Note: this guide assumes you are using Babel, and requires that you use babel-preset-airbnb or the equivalent. It also assumes you are installing shims/polyfills in your app, with airbnb-browser-shims or the equivalent.

Downloads Downloads Gitter

This guide is available in other languages too. See Translation

Other Style Guides

ES5 (Deprecated)
React
CSS-in-JavaScript
CSS & Sass
Ruby
Table of Contents
Types
References
Objects
Arrays
Destructuring
Strings
Functions
Arrow Functions
Classes & Constructors
Modules
Iterators and Generators
Properties
Variables
Hoisting
Comparison Operators & Equality
Blocks
Control Statements
Comments
Whitespace
Commas
Semicolons
Type Casting & Coercion
Naming Conventions
Accessors
Events
jQuery
ECMAScript 5 Compatibility
ECMAScript 6+ (ES 2015+) Styles
Standard Library
Testing
Performance
Resources
In the Wild
Translation
The JavaScript Style Guide Guide
Chat With Us About JavaScript
Contributors
License
Amendments
Types

1.1 Primitives: When you access a primitive type you work directly on its value.

string
number
boolean
null
undefined
symbol
bigint

const foo = 1;
let bar = foo;

bar = 9;

console.log(foo, bar); // => 1, 9
Symbols and BigInts cannot be faithfully polyfilled, so they should not be used when targeting browsers/environments that don’t support them natively.

1.2 Complex: When you access a complex type you work on a reference to its value.

object
array
function

const foo = [1, 2];
const bar = foo;

bar[0] = 9;

console.log(foo[0], bar[0]); // => 9, 9
⬆ back to top

References

2.1 Use const for all of your references; avoid using var. eslint: prefer-const, no-const-assign

Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.

// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;

2.2 If you must reassign references, use let instead of var. eslint: no-var

Why? let is block-scoped rather than function-scoped like var.

// bad
var count = 1;
if (true) {
  count += 1;
}

// good, use the let.
let count = 1;
if (true) {
  count += 1;
}

2.3 Note that both let and const are block-scoped, whereas var is function-scoped.

// const and let only exist in the blocks they are defined in.
{
  let a = 1;
  const b = 1;
  var c = 1;
}
console.log(a); // ReferenceError
console.log(b); // ReferenceError
console.log(c); // Prints 1
In the above code, you can see that referencing a and b will produce a ReferenceError, while c contains the number. This is because a and b are block scoped, while c is scoped to the containing function.

⬆ back to top
