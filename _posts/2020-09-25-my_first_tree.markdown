---
layout: post
title:      "My First Tree"
date:       2020-09-25 04:46:33 +0000
permalink:  my_first_tree
---


As I continue to study data structures I finally arrived at trees. The first tree I was introduced to was the Binary Search Tree. Binary Search Trees are ordered trees that as the name suggests, are ideal for searching, with a Big O (log n) which is much more efficient than the linear time of arrays. The basics of Binary Search Trees are pretty simple, each node may have two branches, the left is reserved for items of lesser value and the right branch is for larger values. For example if the parent node is 5 then 3 would go to the left and 8 would go to the right. If duplicates are allowed they are typically sorted to the right. While I won’t be going over removing items in this post the idea is pretty simple, if the node has no children it is just erased, otherwise is removed by the leftmost node in the right branch below it - which should be the next largest value in the tree. Anywho let us begin building the tree.

### The Node Class

Just like when building a Linked List, it is generally a good idea to create a separate Node class as it will help dry up the code later. Each node will need three items - a pointer to the left node, a pointer to the right node, and its value.

```
class Node {
    constructor(value) {
        this.left = null
        this.right = null
        this.value = value
    }
}
```

Left and right nodes are set to null so the tree always has a defined edge. That is all there is to the class as it is really there to help reduce repetition.

### Search Tree Class and Insert Method

The Binary Search Tree class is initialized with just a root value set to null, from there we use the insert method to add items. The main thing to keep in mind when inserting into a tree is that we have to keep moving the current node down the tree until we find a node with an opening on the correct side and then we update the pointers. Here is an example of how one might look ...

```
 constructor() {
        this.root = null
    }

    insert(value) {
        const newNode = new Node(value)
        if (this.root === null) {
            this.root = newNode
        } else {
            let currentNode = this.root
            while(true) {
                if (value < currentNode.value) {
                    if (!currentNode.left) {
                        currentNode.left = newNode
                        return this
                    }
                    currentNode = currentNode.left           
                } else {
                    if (!currentNode.right) {
                        currentNode.right = newNode
                        return this
                    }
                    currentNode = currentNode.right
                }
            }
        }
    }
```

Above the insert method starts by creating a new node and then checks if there is a root node. If there is a root node the code will then use a while loop until it reaches the correct node. Similiar to the insert method is the lookup method.

### The Lookup Method

Much like the insert method, the lookup method traverses the tree for a match, returning null if none is found. Other than that the code is pretty straigthforward, here is an example ... 

```
    lookup(value) {
        if (!this.root) {
            return false
        }
        let currentNode = this.root
        while (currentNode) {
            if (value < currentNode.value) {
                currentNode = currentNode.left
            } else if (value > currentNode.value) {
                currentNode = currentNode.right
            } else if (currentNode.value === value) {
                return currentNode
            }
        }
        return false
    }
}
```

This is the search method that gives log n time as each progression removes approximately half of the remaining values to search. 

### Conclusion

This is an example of how to build a basic Binary Search Tree in JavaScript. Binary Search Trees are useful due to their O(log n) lookup times. In a future blog I will be going over the removal of nodes as that is a bit more complicated of a concept and I believe warrants its own blog. 





