First try to solve the questions, and then read the explantion

## Questions

<details>
<summary>How to Enable "strict" mode?</summary>
simply write

```jsx
"use strict";
```

before any statement (on the global scope or in a specific function)
</details>
<details>
<summary>Why does the "use strict" syntax is just a string literal?</summary>
To allow "strict mode" to be implemented in every script that ever wrote, even on old browsers (worst case scenario - the browser will ignore the string literal and no side effect will take place) 

for more information
[Why is "use strict" still a string literal?](https://stackoverflow.com/questions/27448784/why-is-use-strict-still-a-string-literal)
</details>
<details>
<summary>What is "strict" mode?</summary>
its a way to opt in to a restricted variant of JavaScript. in this mode, several changes to normal JavaScript are being made:

1. Eliminates some JavaScript silent errors by changing them to throw errors
2. Fixes Mistakes that make it difficult for JavaScript engines to perform optimizations
3. Prohibits some syntax likely to be defined in future versions of ECMAScript
</details>
<details>
<summary>State 3 advantages of "strict" mode</summary>

- Prevents accidental globals

- Disallows duplicate parameter values

- Throws error on invalid usage of delete

- backwards compatible - no side effects

- optimized variable usage

- Disallows assigning non-writable global variables such as NaN and undefined

- Disallows object declaration with duplicates properties names

- Forbids leading zero octal syntax

- Forbids setting properties on primitive values

- Eliminates this coercion
</details>
<details>
<summary>Explain what happens (in strict mode and in sloppy mode) when you mistype a variable name</summary>
sloppy mode - defining new variable on the global object (window.mistypedVariable)

strict mode - throws ReferenceError
</details>
<details>
<summary>Explain what happens (in strict mode and in sloppy mode) when you declare a function with duplicate parameters</summary>
sloppy mode - duplicated argument hides previous identically-name arguments

strict mode - throws SyntaxError
</details>
<details>
<summary>How do you access a duplicated named parameter on a function, with sloppy mode?</summary>
using arguments[i]

```jsx
function foo(a, a, b) {
	console.log(arguments[0]) // prints the first a
}
```
</details>

## Strict Mode

JavaScript's strict mode, introduced in ECMAScript 5, is a way to **opt in** to a restricted variant of JavaScript - thereby implicitly opting-out of "sloppy mode"

Strict mode makes several changes to normal JavaScript semantics:

1. Eliminates some JavaScript silent errors by changing them to throw errors
2. Fixes Mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be e made to run faster identical code that's not strict mode.
3. Prohibits some syntax likely to be defined in future versions of ECMAScript (features that are confusing or poorly thought out).

### Enable Strict Mode

To enable strict mode on your code, put the exact statement **"use strict";** before any other statements.

```jsx
// Whole-script strict mode syntax
'use strict';
var v = "Hi! I'm a strict mode script!";
```

You can also enable strict mode to a specific function:

```jsx
function strict() {
  // Function-level strict mode syntax
  'use strict';
  function nested() { return 'And so am I!'; }
  return "Hi!  I'm a strict mode function!  " + nested();
}
function notStrict() { return "I'm not strict."; }
```

## Converting mistakes into errors

### Accidentally create global variables

In normal JavaScript mistyping a variable in an assignment creates a new property on the global object and continues to "work" (would create window.myVariable). Assignments, which would accidentally create global variables, instead throw an error in strict mode:

```jsx
'use strict';
                       // Assuming no global variable mistypedVariable exists
mistypeVariable = 17;  // this line throws a ReferenceError due to the 
                       // misspelling of variable
```

non strict mode: 

```jsx
// no strict mode

mistypedVariable = 17 // accidently creates window.mistypedVariable
```

### Illegal assignments

In normal JavaScript, assigning values to protected variables (non-writeable global variables such as undefined, NaN, Infinity, and so on) would fail silently. In **strict mode**, it throws errors. For example, the following:

```jsx
let undefined = '5';
let NaN = 42;
```

This also applies to non-writable properties defined with **Object.defineProperty**

```jsx
var obj = {};
Object.defineProperty(obj, 'a', { value: 42, writable: false });
obj1.a = 42;
```

### Attempt to Delete Undeleteable Properties

strict mode makes attempts to delete undeletable properties throw an error (where before the attempt would simply have no effect):

```jsx
'use strict';
delete Object.prototype; // throws a TypeError
```

### Unique Literal Object Keys

in normal JavaScript we can declare on object with duplicates properties names, with the last one determining the property's value.

strict mode throws a syntax error in that case.

```jsx
'use strict';
const o = { p: 1, p: 2 }; // syntax error
```

non strict mode:

```jsx
// normal mode
const o = { p: 1, p: 2 }; // o = { p:2 }
```

### Unique Function Parameter Names

In normal mode, a function can have parameters with duplicate names (duplicated argument hides previous identically-name arguments, while they are still available through arguments[i]). In strict mode, the function parameter name must be unique.

```jsx
'use strict';
function sum(a, a, c) { // !!! syntax error
	// logic
}
```

### forbids octal syntax

The octal syntax isn't part of ECMAScript 5, but it's supported in all browsers by prefixing the octal number with a zero: 0644 === 420 and "\045" === "%". In ECMAScript 2015 Octal number is supported by prefixing a number with "0o". i.e.

```jsx
const a = 0o10; // ES2015: Octal
```

A leading zero syntax for the octals is rarely useful and can be mistakenly used, so strict mode makes it a syntax error:

```jsx
'use strict';
var sum = 015 + // syntax error
          197 +
          142;

var sumWithOctal = 0o10 + 8; // valid
console.log(sumWithOctal); // 16
```

### Forbids setting properties on primitive values

strict mode forbids settings properties on primitive values - and throws TypeError.

```jsx
'use strict';

false.true = '';         // TypeError
(14).sailing = 'home';   // TypeError
'with'.you = 'far away'; // TypeError
```

## Simplifying variable uses

Strict mode simplifies how variable names map to particular variable definitions in the code.

JavaScript sometimes makes this basic mapping of name to variable definition in the code impossible to perform until runtime. Strict mode removes most cases where this happens, so the compiler can better optimize strict mode code.

### With command

Strict mode prohibits the "with" command. The problem with "with" is that any name inside the block might map either to a property of the object passed to it, or to a variable in surrounding (or global) scope, at runtime: it's impossible to know which beforehand.

Strict mode makes "with" a syntax error, so there's no chance for a name in a with to refer to an unknown location at runtime:

```jsx
'use strict';
var x = 17;
with (obj) { // !!! syntax error
  // If this weren't strict mode, would this be var x, or
  // would it instead be obj.x?  It's impossible in general
  // to say without running the code, so the name can't be
  // optimized.
  x;
}
```

### New variables on "eval" command

in normal code, eval can introduce a new variable into the  surrounding function or the global scope.

in strict mode "eval" creates variables only for the code being evaluated, so "eval" can't affect whether a name refers to an outer variable or some local variable

### Deleting plain names

strict mode forbids deleting plain names.

```jsx
'use strict';

var x;
delete x; // syntax error
```
