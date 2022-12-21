### Question #4

What do the following lines output, and why?

```JavaScript
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);
```

<details>
<summary>Answer</summary>

```JavaScript
console.log(1 < 2 < 3) // true;
console.log(3 > 2 > 1) // false;
```

The JavaScript engine cant deal with operator associativity with `<` and `>`.
Instead, it compares left to right, so `3 > 2 > 1` JavaScript translates to `(3 > 2) > 1`, which translates to `true > 1`. `true` has the value of 1, so it being translted to `1 > 1` which is false.

same logic can be applied to the first expression:

`1 < 2 < 3` -> `(1 < 2) < 3` -> `false < 3` -> `0 < 3` -> `true`

</details>

<br>

[Back To Index](../index.md)
