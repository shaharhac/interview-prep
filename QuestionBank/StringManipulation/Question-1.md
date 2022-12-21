### Question #1

Implement an algorithm to determine if a string has all unique characters. You can not use any additonal data structures.
Try to solve this question with better runtime than `O(n^2)` (naive solution)

<details>
<summary>Answer</summary>

```JavaScript
const hasUniqueCharacters = (string) => {
  sortedChars = string.split("").sort();

  for (const [index, letter] of sortedChars.entries()) {
    if (sortedChars[index + 1] && letter === sortedChars[index + 1]) {
      return false;
    }
  }

  return true;
};
```

Runtime complexity of this algorithm is `O(n log n)`.

</details>

<br>

[Back To Index](../index.md)
