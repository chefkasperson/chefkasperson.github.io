---
layout: post
title:      "Intro to Graphs"
date:       2020-10-03 09:34:31 +0000
permalink:  intro_to_graphs
---


Graphs are one of the most used and useful data structures used in computer science when it comes to modeling real life. Essentially, graphs are a set of nodes (vetricies) which are connected to each other with edges. These connections are great at representing real life relationships  such as creating a map of roads between two cities, or giving a list of autocomplete suggestions when typing out a word. Trees and linked lists are both types of graphs and there are a few characteristics we can look for to help describe the graph. 

The first characteristic to look for when dealing with graphs is to determine if it is directed or undirected. Directional trees are where the connections between different nodes can only be traveled in one direction like a singly linked list. Undirected graphs allow traveling in both directions as in a doubly linked list. 



Another characteristic of graphs is whether they are weighted or not. Graphs become weighted when the edges are given values. For example, a road map connecting two cities may have values such as distance, speed limit, and/or travel time attached to the roads so that it can easily find the fastest or shortest route.




Lastly, graphs can be either cyclic or acyclic. Cyclic graphs are ones where vertices are connected in a way where one can follow the edges and return back to the original vertex forming a circular pattern. In acyclic graphs nodes can only be visited once. A binary tree is an example of an acyclic graph.



### Building a Graph

There are three main ways one can use to build a graph, the first is an edge list. An edge list as the name suggests keeps track of edges of a graph by using arrays containing the first node and the second node as elements. Here is an example:

const graph = [[[0, 2], [2, 3], [2, 1], [1, 3]]]


The second way to build a graph is using an adjacent list. With an adjacent list the index of the array or the hash table’s key represents the nodes value and the neighbors or items connected to it with edges are represented in an array. 

const graph = [[2], [2, 3], [0, 1, 3], [1, 2]]

Lastly, there is the adjacent matrix where indexes represent values and a 1 represents a connection and a 0 no connection. 

const graph = [
   [0, 0, 1, 0],
   [0, 0, 1, 1],
   [1, 1, 0, 1],
   [0, 1, 1, 0]
]


Each of these represents the same graph.

### Building a graph from scratch

Building a basic graph from scratch is actually quite simple. For this representation I will be using the adjacency list method using a hashmap to hold the values. The graph can be made with a single class and the constructor should keep track of the number of nodes and the adjacency list. 

class Graph {
   constructor() {
       this.numberOfNodes = 0
       this.adjacentList = {}
   }
}


Next we need methods for adding vertices and edges. To add a node one simply creates a new key value pair with the node as the key and an empty array as the value.

   addVertex(node) {
       this.adjacentList[node] = []
       this.numberOfNodes++
   }
 

Adding an edge is done by pushing the value of two nodes into the adjacency list array.

   addEdge(node1, node2) {
       this.adjacentList[node1].push(node2)
       this.adjacentList[node2].push(node1)
   }

And that is all it takes to create a graph.

### Conclusion

Graphs are great at representing real life relationships and they can be described quickly using three key characteristics: directed vs undirected, cyclical vs acyclical, and weighted vs unweighted. Additionally nodes and edges can be represented using an edge list, adjacency list, or an adjacency matrix. Graphs themselves are pretty simple to build and later on we'll go over some algorithms that will make searching and manipulating graphs a bit easier as well.


