### Question #4

**String Rotation**: Assume you have a method `isSubstring` which checks if one word is a substring of another. Given two strings, `sl` and `s2`, write code to check if `s2` is a rotation of `sl` using only one call to `isSubstring` (e.g., "waterbottle" is a rotation of "erbottlewat").

(If a string is a rotation of another, then it's a rotation at a particular point. For example,
a rotation of waterbottle at character 3 means cutting waterbottle at character 3
and putting the right half (erbottle) before the left half (wat))

<details>
<summary>Answer</summary>

If a `s2` is a rotation of `s1`, it means that there is a pivot point at `s1`, which divides the string to two. let's call the two parts `x` and `y`.
if the left half of `s1` is "wat", and the right one is "erbottle", we can denote it like this:

`s1 = waterbottle = xy`

and s2 will be:
`s2 = erbottlewat = yx`

if we concatinate s2 to itself, we'll get:
`s2s2 = erbottlewaterbottlewat = yxyx`

and we can see that:
`xy ⊆ yxyx`

code:

```JavaScript
// mimic `isSubstring` in JS
const isSubstring = (string, subString) => {
  return string.includes(subString)
}

const isRotation = (s1, s2) => {
return isSubstring((s2 + s2), s1)
}

```

Runtime complexity of this algorithm is `O(n)`.

</details>

<br>

[Back To Index](../index.md)
