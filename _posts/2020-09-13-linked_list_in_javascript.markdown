---
layout: post
title:      "Linked List in JavaScript"
date:       2020-09-13 08:16:07 +0000
permalink:  linked_list_in_javascript
---


A linked list is a data structure made up of nodes. Each node contains a pointer to the next item in the list but is otherwise independent from the other items in memory. Linked Lists are very efficient at appending and prepending items with a big O(1), however, they must be traversed one node at a time so that lookup, insert and delete have O(n). Javascript does not come with linked lists built in but they can be made using classes and or objects. 

Building a Linked LIst

Linked lists need a head or starting node which will then point to the next node, this can be created using objects, so if we wanted a linked list of 1 - 2 - 3, we could make it like this:

let myFirstLinkedList = {
 head: {
   value: 1,
   next: {
     value: 2,
     next: {
       value: 3,
       next: null
     }
   }
 }
}

Note that each object has a value and a next attribute that points to a new object and the last object’s next value should point to null. To make the Linked List easier to modify and also to attach methods to it we will be creating a Linked List class. The constructor of the class should keep track of the head, the tail, and the length of the Linked LIst. Here is an example of a Linked List class:

class LinkedList {
 constructor(value) {
   this.head = {
     value: value,
     next: null
     previous: null
   }
 
   this.tail = this.head
   this.length = 1
 }


Appending and Prepending Items

Next we will go over adding items to the beginning and end of the list. Because our class keeps track of the head and tail of the list both of these functions can be done fairly easily by creating an object and then adjusting the pointers to  place the object in the correct location. Additionally, because a lot of Linked LIst methods involve creating nodes, often a Node class will be created to help reduce the amount of repeated code. Here is the Node class:


class Node {
 constructor(value) {
   this.value = value
   this.next = null
 }
}

Note that the Node class will always set the next value to be null, It will be left to the Linked List class to assign it the proper value.

Here are the append and prepend methods:
append(value) {
   const newNode = new Node(value)
   this.tail.next = newNode
   this.tail = newNode
   this.length++
   return this
 }
 
 
 
prepend(value) {
   const newNode = new Node(value)
   newNode.next = this.head
   this.head = newNode
   this.length++
   return this
 }

The main concern here is to pay attention to the order of operations as both methods use values from the head and tail before reassigning them new values.

Inserting and Removing Items

Both inserting and removing can require a traversal of the list to complete. When inserting you will traverse to the item one spot before or and then adjust the pointers so the new node is in the correct place. Similarly with removing items you also grab the item one spot before and then point it to the item after the item you are deleting. Here are examples of both.

insert(index, value) {
 
   if (index === 0) {
     return this.prepend(value)
   }
 
   if (index >= this.length) {
     return this.append(value)
   }
   const newNode = new Node(value)
   let current = this.head
   for (let i = 1; i < index; i++){
     current = current.next
   }
   newNode.next = current.next
   current.next = newNode
   this.length++
   return this
 }



 remove(index) {
   let current = this.head
   let next = current.next
   for (let i=1; i < index; i++) {
     current = current.next
     next = current.next
   }
   current.next = next.next
   this.length--
   return this
 }
}
 


I used a for loop to traverse and then save a reference to the appropriate nodes, reassigning the pointers as needed and adjusting the length property on the list as well. Also, the insert method included parameter checks to help avoid errors caused by faulty inputs. 

Conclusion

Building a simple Linked List class in JavaScript is pretty straightforward and is made much easier with classes. Linked Lists are very good at appending and prepending items and are a bit slow to lookup, insert, and remove items. They are a good data structure to learn as many of the more advanced data structures, such as trees, heaps, and stack can be similar to Linked Lists.

