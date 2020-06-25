# Arrays and Strings

arrays and strings are fairly straightgforward, so there is no need to elborate on this.
having said that, arrays and strings interview questions often aren't that simple. you should be familiar with some concepts that will improve you code runtime complexity.

## Hash Table

A hash table is a data structure that maps kets to values for highly efficient lookup.
originally, the implementation uses an array of linked lists and a hash code function.
to insert a key-value pair:
1. compute the key's hash code (two different keys could have the same hash code - there are infinite number of keys and finite number of ints)
2. map the hash code to an index in the array (there are many ways to do this, often we do it with `hash(key) % array.length`)
3. at this index, there is a linked list of keys and values. Store the key and value in this index. We use a linked list beacuse of collisions: you could have two different keys with the same hash code, or two different hash codes that map to the same index

To retrieve the value pair by its key, you repeat this process. Compute the hash code from the key, and then compute the index from the hash code. Then seatch through the linked list for the value with this key.

let's talk about runtime complexity - at the worst case you could have a huge amount of collisions, which leads the runtime to be `O(n)`, where ***N*** is the number of keys.
however, we generally assume a good implementation that keeps collisions to a minimum, in which case the lookup time is `O(1)`.




in JavaScript, we don't really need this implementation of hash map, because we can use a simple object (Map is also an option).
