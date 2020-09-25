# JavaScript (JS) coding standards
> Part of [Coding](/Coding/Index.md) / [Languages](/Coding/Languages/Index.md)

The following standards outline the requirements for production of JavaScript based in either the Browser or Node environments. Any environment specific advice will be noted.

## Broad structure
JS files **should** be segmented into components and modules. Usually a single module per motive.

### In-browser
Each file should contain an immediately invoked function expression (IIFE) which encapsulates any variables defined.

IIFE definitions may **optionally** begin with a semicolon (`;`) in order to protect against concatenation issues.

Example of correct use:

```
!(function($, WS) {
	// code here...
}(window.jQuery, window.WS));
```

### Node
JS files **must not** use IIFEs and can **optionally** contain globally defined variables within each file. As the scope of a single JS file within node is considered local to the module, this is a safer practice than in browsers.

Generally, unless Babel is being used to transpile the code into ES5, the CommonJS import/export syntax should be used for modules.

Examples of correct use:

**MyModule.js**

```
// MyModule.js
const moduleGlobal = 'foo';

module.exports = function() {
	let functionVariable = 'bar';

	// code here...
};
```

**Index.js**

```
const MyModule = require('./MyModule');
```

## The use of 'use strict'
As our browser support negates compatiblity with IE browsers older than version 9, all JS code **must** use the `'use strict'` statement either within each enclosing IIFE or at the top of each file in the case of Node modules.

## Semicolons
Semicolons **must** be used to terminate JS statements.

## Objects
Objects **should** be created in one of two styles:

```
// multi-line style:
let objectname = {
	property: 'value',
	property2: 'value'
};

// single-line style (for shorter datasets)
let objectname = { prop1: true, prop2: false };
```

Arbitrary line breaks **must not** be created within the object.

```
// example of a invalid style
let objectname = { prop1: true,
	prop2: true,
	prop3: true
};
```

If an object exceeds the line length requirements, it **must** be converted into a multi-line style syntax.

In all cases, property names **should not** contain quotes unless the name is reserved or would otherwise be syntactically invalid.

## Arrays
Arrays **should** be created using the JS shorthand array notation (`[]`) and not with `new Array`.

The syntactical flow for an array should largely match objects:

```
// multi-line
let arrayname = [
	'item1',
	'item2',
	'item3'
];

// single-line
let arrayname = [1, 2, 3, 4, 5];
```

## Functions and function invocations
Functions may be defined either as named functions or as variable expressions. They **must** be named with camelCase conventions:

```
// named function
function functionName() { // ... }

// variable expression
let functionName = function() { // ... }

// within an object:
let objectname = {
	functionName: function() {

	}
}
```

When using the Node environment and transpiling with Babel, arrow functions may **optionally** also be used:

```
// arrow function
var functionName = (arg) => { // .. }

// arrow function, alernative
var functionNAme = (arg) => (returned_expression);
```

## Blocks and bracing
Braces follow the [OTBS](https://en.wikipedia.org/wiki/Indent_style#Variant:_1TBS_.28OTBS.29) format. Opening blocks **must not** be on their own line, and all closing blocks **must** be after a new line. Example:

```
// correct bracing style
if (expression) {
	// code goes here...
} else {
	// more code goes here...
}

function functionName() {
	// function body...
}

// incorrect bracing style
if (expression)
{
	// code goes here...
}
else
{
	// more code goes here...
}

function functionName()
{
	// function body...
}
```

Braces **must** be used whenever logical blocks are defined.

```
// don't do this
if (expression) doathing();

// or this
if (expression)
	doathing();
```

When defining evaluations or expressions within the clause of a logical block, a loop or other block-based construct, the parentheses **must not** include extraneous spacing. e.g:

```
// correctly spaced
if (a === 0)

// incorrectly spaced
if ( a === 0 )
```

## Chaining
When chaining methods of an object or function, subsequent calls **should** be on their own line and indented one extra level. E.g:

```
// correct
function()
	.then(...)
	.catch(...);

// incorrect
function().then(...).catch(...);
```

If the context of a chain of methods changes then it may **optionally** be indented one extra level. E.g:

```
$elements()
	.addClass('classname')
	.children()
		.html('Some content');
```

### Exceptions
1. If there is only one extra method in the chain and it fits within the 80 column recommended limit, it is allowed to occur on a single line.

## Variable declaration
All variables **must be** defined a the top of their scope.

When using ES6, `let` or `const` are preferred over `var`. `const` **must be** used when the variable does not change in value throughout its lifetime.

```
// correct definition
function functionName(items) {
	let a;

	for (a = 0; a < items.length; a += 1) {
		// code...
	}
}

// incorrect definition
function functionName(items) {
	for (let a = 0; a < items.length; a += 1) {
		// code...
	}
}
```

## Naming conventions

### Variables
There are currently no restrictions on general variable naming except that they **must** be named consistently. If camelCase is being used, do not switch to underscore_separated names within the same project.

### Object properties and keys
Unless referring to an object generated from an API, all property keys **should** be in camelCase. This ensures reliability with the definition of properties that transfer to the DOM as well as ensuring that properties can be referenced with dot-notation.

```
// correct property definition
const myObject = {
	propertyOne: 'value',
	propertyTwo: 'value2'
};

// correct property referencing
console.log(myObject.propertyOne)

// incorrect property definition
const myObject = {
	property_one: 'value',
	'property-two': 'value2'
};

// incorrect property referencing
console.log(myObject['property-two']);
```

#### Exceptions
1. Where a property key name cannot be controlled, dash or underscore notation may **optionally** be used.

### Modules
Modules, classes or prototypal functions which can be instantiated with the `new` prefix **must** start with an uppercase letter. The same applies to the filename in which the module resides. E.g:

```
// MyModule.js
module.exports = function() {
	// code...
};

// app.js
const MyModule = require('./MyModule');
new MyModule();
```

Equally, if a function cannot be instantiated with the `new` operator, it **must not** start with an uppercase letter.

## Commenting
Single line comments **must** occur with a new line before them and in sentence case.

```
// This is a correctly formatted comment
dosomestuff();

var a = 0;
// This comment needs a new line before it
a = a + 1;

if (a === 0) {
	// This comment is valid, because it is within a new block
	a -= 1;
}

//this comment is not valid because it is in lowercase and doesn't have a preceeding space
a = 2;

// This comment Is not valid because
// it is many single line comments separated
// over multiple lines.
a = 3;

/*
 * This is a valid comment, separated
 * On to multiple lines.
 */
a = 4;
```

### Documenting code
Every unique method or function **must** be commented in JSDoc format. A bare minimum example of this is as follows. (Note the double asterisk on the opening line):

```
/**
 * Converts a decimal number to roman numerals.
 */
function convertToRoman(num) {
	// ...
}
```

When parsed by JSDoc, this function would be described using the sentence defined within the doc block comment above. The comment should come immediately before the opening function line and without a space.

A more complex example is as follows:

```
/**
 * @param {number} num - The number to convert
 * @description
 * Converts a decimal number to roman numerals.
 * Only use if the preloaded libraries do not already contain a function of this nature.
 * @returns {string} The supplied number, as a roman numeral.
 * @see http://mydomain.com/examples/roman.html
 */
function convertToRoman(num) {
	// ..
}
```

### When to use comments
Comments **should** be used when the intent and/or nature of the preceeding code is not immediately obvious. They **should not** be used to make up for unintelligable code, and they **should not** simply repeat the code itself in natural language form.

Example of code repetition:

```
// Adds 1 to a
a = a + 1;
```

Example of an inadequate comment:

```
// Set track length
this.track_length += dt * this.outro_speed * 17 * 0.447 / this.inner_track.length;
```

If a single line of code cannot be explained with a single line of comment, consider refactoring and/or splitting the logic into smaller, more concise chunks.

### References
 * http://usejsdoc.org - Using JSDoc
 * https://www.npmjs.com/package/jsdoc - JSDoc node implementation

### Exceptions
1. If a single line comment starts at the beginning of a new block or is commented out code (which is covered in the [Git](/Admin/Git.md) guidelines), it does not require a new line before it.

## Comparison operators
When comparing values, strict operators **must** always be used. If a loose operator is required for correct functioning of the code, it **must** be refactored to support strict operators.

```
// Correct operator use:
if (a === 0) {
	// ...
}

var b = (a === 0 || c !== 2);

// Incorrect operator use:
if (a == 0 || b == null || c == "1") {
	// ...
}

// Shorthand "truthy" comparisons are still acceptable:
if (a || !b) {
	// ...
}
```

### Exceptions
1. If comparing a value that is considered "truthy" or "falsy", the shorthand comparison (such as `!` is still valid).

## Strings
When creating string literals, single quotes **should** be used at all times. If dealing with legacy code and/or are required by some other convention to use double quotes, the quote style **must** be consistent accross the whole project.

If a single quote within a string following the above convention is required, it can be escaped with a backslash, e.g:

```
var str = 'My name\'s Bob. How are you?';
```
