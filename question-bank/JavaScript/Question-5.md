### Question #5

What will be printed to the console?

```JavaScript
function foo() {
 var a = 1;
 const b = 2;
 let c = 3;

 if (b < 10) {
    var a = 10;
    const b = 11;
    let c = 12;

    console.log(a, b, c);
 }

 console.log(a, b, c);

 console.log(d, e);

 var d = 4;
 const e = 5;
}

foo();
```

<details>
<summary>Answer</summary>

This question covers: [Variables](../../coding/javascript/variables.md),

```
10 11 12
10 2 3
Uncaught ReferenceError: e is not defined
```

</details>

<br>

[Back To Index](../index.md)
