# Trees

A tree is a data structure composed of nodes. Each tree has a root node, which has zero or more child nodes.
Each child node has zero or more child nodes, and so on.
The tree cannot contain cycles.

## Binary Tree

A binary tree is a tree in which each node has up to two children. Not all trees are binary trees.
Since each element in a binary tree can have only two children we typically can name them left and right childs.

![Binary Tree](https://www.geeksforgeeks.org/wp-content/uploads/binary-tree-to-DLL.png)

## Binary Search Tree

A Binary search tree is a binary tree in which every node fits a specific ordering property.
* The left subtree of a node contains only nodes with keys lesser than the node's key.
* The right subtree of a node contains only nodes with keys greater than the node's key.
* The left and right subtree each must also be a binary search tree.

![Binary Search Tree](https://media.geeksforgeeks.org/wp-content/uploads/BSTSearch.png)


<details>
  <summary>Implementation using Javascript</summary>
  
  ```jsx
  class Node { 
    constructor(data) { 
        this.data = data; 
        this.left = null; 
        this.right = null; 
    } 
} 

class BinarySearchTree {
  constructor() {
    this.root = null
  }

  insert(data) {
    const newNode = new Node(data);

    if(this.root === null){
      this.root = newNode;
    } else {
      this.insertNode(this.root, newNode)
    }
  }

  insertNode(node, newNode) {
    if(newNode.data > node.data) { // Go Right
      if(node.right === null) {
        node.right = newNode;
      } else {
        this.insertNode(node.right, newNode)
      }
    } else { // Go Left
      if(node.left === null) {
        node.left = newNode;
      } else {
        this.insertNode(node.left, newNode)
      }
    }
  }

  
  remove(data) {
    this.root = this.removeNode(this.root, data)
  }

  removeNode(node, key) {
    if(node === null) return null;
    else if(key > node.data) { // Go right
      node.right = this.removeNode(node.right, key);
      return node;
    } else if(key < node.data) { // Go left
      node.left = this.removeNode(node.left, key);
      return node;
    } else { // Delete this node

      // Case 1: delete a leaf
      if(node.left === null && node.right === null) {
        node = null;
        return node;
      }

      // Case 2: delete a node with one child
      if(node.left === null) {
        node = node.right;
        return node;
      }
      else if(node.right === null) {
        node = node.left;
        return node;
      }

      // Case 3: delete a node with two children
      const successor = this.findMinNode(node.right);
      node.data = successor.data;

      node.right = this.removeNode(node.right, successor.data);
      return node;
    }
  }

  findMinNode(node) { 
    // if left of a node is null 
    // then it must be minimum node 
    if(node.left === null) 
      return node; 
    else
      return this.findMinNode(node.left); 
    } 
}
  ```
</details>


### Insert

A new key os always inserted as leaf. We start searching a key from root till we hit a leaf node. Oncea leaf node is found, the new node is added as a child of the lead node.

         100                               100
        /   \        Insert 40            /    \
      20     500    --------->          20     500 
     /  \                              /  \  
    10   30                           10   30
                                              \   

### Remove

When we want to remove a node from a binary tree, there are three cases that can happen:
1) Node to be removed is a leaf: simply remove from the tree

              50                            50
           /     \         delete(20)      /   \
          30      70       --------->    30     70 
         /  \    /  \                     \    /  \ 
       20   40  60   80                   40  60   80

2) Node to be removed has only one child: copy the child to the node and delete the child

              50                            50
           /     \         delete(30)      /   \
          30      70       --------->    40     70 
            \    /  \                          /  \ 
            40  60   80                       60   80

3) Node to be removed has two children: find inorder successor of the node, Copy contens of the inorder successor to the node and remove the inorder successor

              50                            60
           /     \         delete(50)      /   \
          40      70       --------->    40    70 
                 /  \                            \ 
                60   80                           80

## Types of Binary Trees

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

***Algorithm for in-order***:

1) Perform in-order on left subtree
2) Visit the root
3) Perform in-order on right subtree

<details>
  <summary>Implemantation using Javascript</summary>
  
  ```jsx
  inorder(node) { 
    if(node !== null) { 
        this.inorder(node.left); 
        console.log(node.data); 
        this.inorder(node.right); 
    } 
  } 
  ```
</details>

### Pre-Order Traversal

Pre-order traversal visits the current node before its child nodes (hence the name "pre-order").
in pre-order traversal, the root is always the first node visited.

***Algorithm for pre-order***:

1) Visit the root
2) Perform pre-order on left subtree
3) Perform pre-order on right subtree


<details>
  <summary>Implemantation using Javascript</summary>
  
  ```jsx
  preorder(node) { 
    if(node !== null) { 
        console.log(node.data); 
        this.preorder(node.left); 
        this.preorder(node.right); 
    } 
  } 
  ```
</details>

### Post-Order Traversal

Post-order traversal visits the current node after its child nodes (hence the name "post-order").
in a post-order traversal, the root is alwats the last node visited.

***Algorithm for post-order***:

1) Perform post-order on left subtree
2) Perform post-order on right subtree
3) Visit the root


<details>
  <summary>Implemantation using Javascript</summary>
  
  ```jsx
  postorder(node) { 
    if(node !== null) { 
        this.postorder(node.left); 
        this.postorder(node.right); 
        console.log(node.data); 
    } 
  } 
  ```
</details>

## Runtime Complexity

### Binary Tree

#### Searching

At the worst case scenraio, we will go over every element in the tree, ***resulting in `O(n)` runtime complexity.***

#### Insert & Remove

At the worst case scenario, we will have to go over every element, ***resulting in `O(n)` runtime complexity.***

### Binary Search Tree

#### Searching

Searching in a BST has `O(h)` worst-case runtime complexity, where `h` is the height of the tree. Since a binary search tree with n nodes has a minimum of O(log n) levels, it takes at least ***`O(log n)`*** comparisons to find a particular node. Unfortunately, a binary serch tree can degenerate to a linked list (every node will have exactly one child), reducing the search time to ***`O(n)`***.

#### Insert & Remove

Agian, the runtime of insertation and removing of an element will be identical to the runtime of searching en element, resulting in `O(log n)` at the best case, and `O(n)` at the worst case.

## Binary Heaps (Min Heaps and Max Heaps)

We'll just discuss min-heaps here. Max-heaps are essentially equivalent, but the elemnts are in descending order rather than ascending order.

A min-Heap is ***complete*** binary tree (that is, totally filled other than the rightmost elemnts on the last level) which each node is smaller than its children.
The root, therefore, is the minimum element in the tree.

![Min Heap](https://camo.githubusercontent.com/c8a60ba2f777cfcd853df066ed0b822fe101cfd2/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f352f35632f42696e6172792d686561702e706e67)
