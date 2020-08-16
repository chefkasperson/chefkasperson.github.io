---
layout: post
title:      "Data Structures"
date:       2020-08-16 06:05:22 +0000
permalink:  data_structures
---


**What are data structures?**

Data structures are ways of storing and organizing data so that the operations we perform on them can be done efficiently in regards to time and space. There are two main types of data structures: static and dynamic.

**What are static data types**

Static data structures have fixed sizes and structures. Elements of static structures may be changed but the memory allocation for the  array will stay the same. An example of a static data type would be the array. When an array is written into memory it’s size is fixed and a new array will need to be made when adding items. Some programming languages offer dynamic arrays, which allow users the ability to add items to the array. Under the hood these arrays are still static but often will allocate extra space to the array when made so changes can be done more efficiently.

One of the main advantages to static data structures such as arrays is that they have indexes. This makes it easier to pluck out the desired element from the array. Additionally they are easy to use and implement. 

**Dynamic data types**

Dynamic data types sizes are not fixed as elements do not need to be stored next to each other. This means their size can be modified while operations are being performed on them. They tend to be more difficult to implement and work with but often will be able to perform a certain operation more efficiently than an array.  Here is a brief description of some of the dynamic data structures.

**Linked lists**

Linked lists are linear collections of data like arrays but instead of indexes, each element points to the next element in the list and are stored separately from each other. Their advantage over arrays is in the dynamicity of its size and the ease of insertions and deletions over arrays.

**Stacks and Queues **

Both stacks and queues are ordered lists that only allow insertions at the end of the lists. Stacks allow deletions from the end of the list - or Last in First out - while queues deletions are from the beginning of the list - or FIrst in First out. Both are specialized lists and are great at adding and removing items accordingly.

**Trees**

Trees are data structures like family trees and data is stored hierarchical, where each node can have any number of children and those children can have children of their own. The top of the tree is considered the root of the tree and any node without children is considered a leaf. Trees data can be randomly dispersed, however, when organized they can greatly reduce the search time for an element. Binary trees in particular can reduce search times to O(log n) from the O(n) of an array. Many different types of trees have been developed to optimize certain tasks. While they are difficult to use, they can offer valuable savings in efficiency.

**Conclusion**

Different data structures offer improvements in time and space to the different operations one might want to perform on the data. By taking advantage of different data structures strengths it is possible to improve efficiency and save some time, especially when dealing with larger data sets.

