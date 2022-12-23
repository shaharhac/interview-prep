### Question #6

What’s the difference between `bind()`, `call()`, and `apply()`?

<details>
<summary>Answer</summary>

#### bind

The `bind()` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called

```JavaScript
const module = {
  x: 42,
  getX: function() {
  return this.x;
  }
};

const unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope
// expected output: undefined

const boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
// expected output: 42

```

#### call

The `call()` method calls a function with a given this value and arguments provided individually.

```JavaScript
function Product(name, price) {
this.name = name;
this.price = price;
}

function Food(name, price) {
Product.call(this, name, price);
this.category = 'food';
}

console.log(new Food('cheese', 5).name);
// output: "cheese"

```

#### Apply

The `apply()` method is identical to `call()`, except `apply()` requires an array as the second parameter. The array represents the arguments for the target method.

</details>

<br>

[Back To Index](../index.md)
