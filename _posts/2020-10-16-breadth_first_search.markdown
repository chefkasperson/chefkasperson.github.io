---
layout: post
title:      "Breadth First Search"
date:       2020-10-16 09:29:12 +0000
permalink:  breadth_first_search
---


There are two main ways to traverse a tree data structure, breadth first search (BFS) and depth first search (DFS). As the name suggests BFS travels the trees width first, visiting each node layer by layer until the end is finally reached. For example, in the tree below BFS will travel the following path: [A, B, C, D, E, F, G, H, I, J, K, L]

![](https://web.cecs.pdx.edu/~sheard/course/Cs163/Graphics/CompleteBinary.jpg)

So when should one use BFS? Well BFS is preferable to DFS when searching for nodes believed to be close to the original node, when finding the shortest path, or when the tree is particularily deep relative to its width. The biggest con to  BFS is that it must save a reference to each node on a level in order to visit the next level in order. This means it tends to require more memory than DFS, particularily when the tree is wider. 

There are two main ways of writing BFS methods in JavaScript, the iterative and recursive approaches. Neither holds any real advantage over the other in terms of performance so it comes to personal preference when deciding between the two. Here are examples of BFS methods to be used inside a tree class in JavaScript:

##### The Iterative Approach

```
BreadthFistSearch() {
  let currentNode = this.root
	let list = []
	let queue = []
	queue.push(currentNode)
	
	while (queue.length > 0) {
	  currentNode = queue.shift()
		list.push(currentNode.value)
		
		if (currentNode.left) {
		  queue.push(currentNode.left)
		}
		
		if (currentNode.right) {
		  queue.push(currentNode.right)
		}
	}
	
	return list
}
```

Looking at the code above we start by visiting the tree's root node and then save the value into the list, we then push any children into the queue beginning with the left nodes. We then begin the loop over again by choosing the first item from the queue and continuing until we have no more nodes left to visit.

##### The Recursive Approach

```
BreadthFirstSearch(queue, list) {
  if (!queue.length) {
	  return list
	}
	
	const currentNode = queue.shift()
	list.push(currentNode.value)
	
	if (currentNode.left) {
	  queue.push(currentNode.left)
	}
	
	if (currentNode.right) {
	  queue.push(currentNode.right)
	}
	
	return this.BreadthFirstSearch(queue, list)
}
```

Like the iterative approach, this also saves the value of the current  node to the list and then passes the children into the queue before moving to the next node. The main difference here is that because recursion calls the same method over and over again, the queue and list need to be passed in as arguments in order to avoid the values being reset each time the method is called.

##### Conclusion

Breadth first search is one method used to traverse trees and excels at finding nodes close to each other or the shortest path. It does require extra memory in order to save references for each node in a layer and should possibly be avoided when dealing with wider trees. The code itself is pretty simple, we save the value of the current node to a list and then place each of the node's children into the queue before moving to the queue's next node. One can use either the iterative approach or the recursive approach when writing the method with only personal preference to differentiate them.  

