# Variables & Scopes

- Resources
  - [ [recommended] var, let and const - What, why and how (video) - FunFunFunction](https://www.youtube.com/watch?v=sjyJBL5fkp8)
  - [Var, let and const- what's the difference?](https://dev.to/sarah_chima/var-let-and-const--whats-the-difference-69e)
  - [JavaScript ES6+: var, let, or const?](https://medium.com/javascript-scene/javascript-es6-var-let-or-const-ba58b8dcde75)
  - [Hoisting in Modern JavaScript — let, const, and var](https://blog.bitsrc.io/hoisting-in-modern-javascript-let-const-and-var-b290405adfda)

## var, let and const

**var** was the only way to declare a variable until ES6 was released. ES6 introduced two additional ways to declare a variable: **let** and **const**.

## Scopes

Scope is the accessibility of variables, function, and objects in some particular part of your code during runtime.

In JavaScript there are two types of scope:

- Local scope
- Global scope

Variables defined **inside a function are in local scope** while variables defined outside of a function are in the global scope. Each function when invoked creates a new scope.

### Global Scope

There is only one Global scope throughout a JavaScript document. A variable is in the Global scope if it;s defined outside of a function.

### Local Scope

Variables defined inside a function are in the local scope. And they have a different scope for every call of that function. This means that variables having the same name can be used in different function. This is because those variables are bound to their respective functions, each having different scopes, and are not accessible in other function.

```JavaScript
// Global Scope
function someFunction() {
    // Local Scope #1
    function someOtherFunction() {
        // Local Scope #2
    }
}

// Global Scope
function anotherFunction() {
    // Local Scope #3
}
// Global Scope
```

## Block Statements

Block statements like "if" and "switch" conditions or "for " and "while" loops, unlike functions, don't create a new scope. Variables defined inside of a block statement will remain in the scope they were already in.

```JavaScript
if (true) {
    // this 'if' conditional block doesn't create a new scope
    var pizza = 'Delicius'; // name is still in the global scope
}

console.log(name); // logs 'Delicius'
```

## The Scope of Var VS let

After we understood what are the differences between local scope and global scope, and what are block statements, let's understand the scope of "var".

The key difference between the **var** and **let**/**const** is the fact that **var** is not **blocked scoped.**

What does that means? lets look at an example:

```JavaScript
for(var i = 0; i < 10; i++) {
	// logic
}
console.log(i) // prints 10

for(let j = 0; j < 10; j++) {
	//logic
}
console.log(j) // j is not defined
```

While the **var** is declared on the outer scope (local or global scope), the **let** will be available only inside the for **block scope.**

## Hoisting

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. What this means is that if we do this:

```JavaScript
console.log (greeter);
var greeter = "say hello"
```

it is interpreted as this

```JavaScript
var greeter;
console.log(greeter); //greeter is undefined
greeter = "say hello"
```

So var variables are hoisted to the top of its scope and initialized with a value of undefined.

### Are let and const variables get hoisted?

let's look at this exmaple:

```JavaScript
console.log(a);
let a = 3;
```

if you try to run this example, you'll get

```JavaScript
ReferenceError: a is not defined
```

so one might say that let variables are not being hoisted, but the answer is a bit more complicated than that. All declarations (function, var, let, const and class) are hoisted in JavaScript, while the var declarations are initialized with undefined, but let and const declarations remain uninitialized.

## Re-Declaration

**var** variable can be updated but can also be re-declared**,** While **let** variable can be updated but **can not** be re-declared (and of course - **const** variable can't be updated nor re-declared).

this, as well, is a weakspot of the **var** declration. If you re-declare a variable by mistake, it can cause some hard-to-trace bugs.
