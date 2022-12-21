### Question #8

What is a generator function in Javascript? what it can be used for?

<details>
<summary>Answer</summary>

a generator function is a special type of function that can be used to create an iterator.
it is denotes with the `function*` syntax, and can be paused at any point using the `yield` syntax

an example for a generator function:

```Javascript
function* range(start, end) {
  for (let i = start; i <= end; i++) {
    yield i;
  }
}

const iterator = range(1, 5);

console.log(iterator.next());  // { value: 1, done: false }
console.log(iterator.next());  // { value: 2, done: false }
console.log(iterator.next());  // { value: 3, done: false }
console.log(iterator.next());  // { value: 4, done: false }
console.log(iterator.next());  // { value: 5, done: false }
console.log(iterator.next());  // { value: undefined, done: true }

```

another example:

```JavaScript
function* idCreator() {
  let i = 0;
  while (true) yield i++;
}

const ids = idCreator();

console.log(ids.next().value); // 0
console.log(ids.next().value); // 1
console.log(ids.next().value); // 2
```

when the generator function is called, it does not execute the code inside it immediately. it returns an iterator object that can be used to execute the function step-by-step.

each time the `next()` method of the iterator it being called, the function executes until it encounters a `yield` statement. the value of the yield expression is returned to the caller and the generator is paused until the `next()` method is called again.

use cases:

1. lazy evaluation: can be used to create lazy sequences of data, where each sequence is created on demand
2. infinite sequences
3. custom iterators: can be used to create custom iterators that can be used with `for-of` loop

</details>

<br>

[Back To Index](../index.md)
