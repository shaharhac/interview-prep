### Question #7

Explain what pure functions are and state some of their advantages.

<details>
<summary>Answer</summary>

we can call a function 'pure' if it have the following properties:

1. it returns the same output for a given input.
2. it does not have side effects.

an exmaple for a pure function:

```JavaScript
function add(x, y) {
  return x + y;
}
```

in contrast, the following is a impure function:

```JavaScript
let globalVariable = 0;

function addAndUpdateGlobal(x, y) {
  globalVariable += x + y;
  return globalVariable;
}
```

There are several advanteges of using pure functions:

1. **Predictability** - the fact that it always returns the same output for any given input, makes the pure function more predictable, and therefore more easy to understand, debug and modify if needed.
2. **testablitiy** - both properties of pure functions makes it easier to test the code. you can simply pass in some inputs and check that the output is as expected.
3. **Reusability** - pure functions do not rely on external state and do not change it, so it can be used anywhere needed. this turns the code to be more modular and easier to maintain.

</details>

<br>

[Back To Index](../index.md)
