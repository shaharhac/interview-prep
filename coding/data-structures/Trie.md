# Trie

Trie is an efficient information retrieval data structure using which search complexities can be brought to optimal limit.

Storing keys (words) in binary search tree will need time proportional to `M * log N`, Where M is maximum string length and N is the number of keys in the tree.
Using Trie, we can search the key in `O(M)` time. However - the penalty is on trie storage requirements.

## Structure

Every nod eof trie consists of multiple branches. Each branch represents a possible character of keys. We need to mark the last node of every key as the end of a word.

## Insertion

## Search
