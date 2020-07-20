# Trees

A tree is a data structure composed of nodes. Each tree has a root node, which has zero or more child nodes.
Each child node has zero or more child nodes, and so on.
The tree cannot contain cycles.

## Binary Tree

A binary tree is a tree in which each node has up to two children. Not all trees are binary trees.
Since each element in a binary tree can have only two children we typically can name them left and right childs.

![Binary Tree](https://www.geeksforgeeks.org/wp-content/uploads/binary-tree-to-DLL.png)

### Binary Search Tree

A Binary search tree is a binary tree in which every node fits a specific ordering property.
* The left subtree of a node contains only nodes with keys lesser than the node's key.
* The right subtree of a node contains only nodes with keys greater than the node's key.
* The left and right subtree each must also be a binary search tree.

![Binary Search Tree](https://media.geeksforgeeks.org/wp-content/uploads/BSTSearch.png)


### Blanaced vs. Unbalanced

A non-empty binary tree T is balanced if:
1) Left subtree of T is balanced
2) Right subtree of T is balanced
3) The difference between heights of left subtree and right subtree is not more than 1.

![Balanced vs Unbalanced tree](https://media.geeksforgeeks.org/wp-content/uploads/tree.jpg)

### Complete Binary Trees

A binary tree is a complete binary tree if all the levels are completely filled except possibbly the last level and the last level has all kets as left as possible.

***Formal defenition***:
a binary tree T with n levels is ***complete*** if all levels except possibly the last are completely full, and the last level has all its nodes to the left side.

![Complete Binary Tree](https://media.geeksforgeeks.org/wp-content/uploads/20200218123136/Side-Ways-Traversal-Input.png)

### Full Binary Trees

A full binary tree is defined as a binary tree in which all nodes have either zero or two child nodes. Conversely, there is no node in a full binary tree, which has one child node.

***Formal defenition***:
a binary tree T is ***full*** if each node is either a leaf or possesses exactly two child nodes

![Full Binary Tree](https://media.geeksforgeeks.org/wp-content/uploads/CompleteBinaryTree.png)


### Perfect Binary Trees

A Perfect binary tree is a binary tree in which all the internal nodes have two children and all lead nodes are at the same level.

![Perfect binary tree](https://i.stack.imgur.com/x8d4D.png)


## Binary Tree Traversal

### In-Order Traversal

In-order traversal means to "visit" the left breanch, then the current node, and finally, the right branch
When performed on a binary search tree, it visits the nodes in ascending order (hence the name "in-order")

### Pre-Order Traversal

Pre-order traversal visits the current node before its child nodes (hence the name "pre-order").
in pre-order traversal, the root is always the first node visited.

### Post-Order Traversal

Post-order traversal visits the current node after its child nodes (hence the name "post-order").
in a post-order traversal, the root is alwats the last node visited.


## Binary Heaps (Min Heaps and Max Heaps)

We'll just discuss min-heaps here. Max-heaps are essentially equivalent, but the elemnts are in descending order rather than ascending order.

A min-Heap is ***complete*** binary tree (that is, totally filled other than the rightmost elemnts on the last level) which each node is smaller than its children.
The root, therefore, is the minimum element in the tree.

![Min Heap](https://camo.githubusercontent.com/c8a60ba2f777cfcd853df066ed0b822fe101cfd2/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f352f35632f42696e6172792d686561702e706e67)
