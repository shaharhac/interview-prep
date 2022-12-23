### Question #3

**One Away**: There are three types of edits that can be performed on strings: insert a character,
remove a character, or replace a character. Given two strings, write a function to check if they are
one edit (or zero edits) away.

**_EXAMPLE:_**
<br> pale, ple -> true
<br> pales, pale -> true
<br> pale, bale -> true
<br> pale, bake -> false

<details>
<summary>Answer</summary>

we want to find the characteristics of two words that are one edit away from one another.
We can notice right away that in case of an update, the strings has equal length, and in the case of insertion or deletion, one word will be longer than the other by one character.
Another thing we can notice, is that insertion and deletion are eventually the same thing - as they are inverse operations.

In case of update - we'll go through one string letter by letter, and count how many letters are different from the matching letter in the other string.
In case of insertion or deletion - we will go over the longer string, and on every iteration we will pick a letter discard from the word.

```JavaScript

const isOneEditAway = (str1, str2) => {
  let lettersDiff = 0;
  for (const [index, letter] of str1.split("").entries()) {
    if (letter !== str2[index]) {
      lettersDiff++;
    }
  }

  return lettersDiff <= 1;
};

// Same logic applies to both insert and delete
const isOneInsertionAway = (str1, str2) => {
  const longerString = str1.length > str2.length ? str1 : str2;
  const shorterString = str1.length > str2.length ? str2 : str1;

  for (const index in longerString) {
    const stringWithoutCurrentLetter = longerString
      .slice(0, Number(index))
      .concat(longerString.slice(Number(index) + 1));
    if (stringWithoutCurrentLetter === shorterString) {
      return true;
    }
  }

  return false;
};

const oneWay = (str1, str2) => {
  const lengthDiff = Math.abs(str1.length - str2.length);

  if (lengthDiff > 1) {
    return false;
  } else if (lengthDiff === 0) {
    return isOneEditAway(str1, str2);
  } else {
    return isOneInsertionAway(str1, str2);
  }
};
```

Runtime complexity of this algorithm is `O(n)`.

</details>

<br>

[Back To Index](../index.md)
