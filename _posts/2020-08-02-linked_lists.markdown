---
layout: post
title:      "Linked Lists"
date:       2020-08-02 06:39:23 +0000
permalink:  linked_lists
---


#### What is a linked list?

It is a data structure representing a sequence of nodes, in a singly linked list each node will only point to the next node in the list. In a doubly linked list each node will also point to the previous node. Linked lists can also be made circular by pointing the last node back to the first. They are like arrays that have been broken apart and the indices have been replaced with directions to the next node.

#### Why use a linked list?

The main benefit of a linked list is that since the nodes can be stored separately, items can be added or removed without having to reallocate or reorganize the entire structure. Where they struggle is in the retrieval of elements, since there are no indices in order to get the nth item of the list you have to traverse each item that comes before it.

#### Where are linked lists used?

Linked lists can be used in creating stacks, queues, trees and graphs and are often preferable to arrays when the size of the list is unknown or changes frequently. 

#### Creating a linked list in Ruby

In order to create a linked list in Ruby two classes are needed, a List class and a Node class.

Example of Node class:

class Node
   attr_accessor :next_node
   attr_reader :value
 
   def initialize(value)
       @value = value
       @next_node = nil
   end
 
end


The node class simply allows the creation of an object with a value and a pointer to the next node. The Linked List class will handle the rest, here is an example of a Linked List Class:
class Node
   attr_accessor :next_node
   attr_reader :value
 
   def initialize(value)
       @value = value
       @next_node = nil
   end
 
end
 
class LinkedList
 
   def initialize(value)
       @head = nil
   end
 
   def append(value)
       if @head
           find_tail.next_node = Node.new(value)
       else
           @head = Node.new(value)
       end
   end
 
   def find_tail
       node = @head
 
       return node if !node.next_node
       return node if !node.next_node while (node = node.next_node)
   end
 
   def append_after(target, value)
       node = find(target)
       return unless node
 
       old_next = node.next_node
       node.next_node = Node.new(value)
       node.next_node.next_node = old_next
 
 
   def find(value)
       node = @head
 
       return false if !node.next_node
       return node if node.value == value
       while (node = node.next_node)
           return node if node.value == value
       end
   end
 
   def delee(value)
       if @head.value = value
           @head = @head.next_node
           return
       end
 
       node = find_before(value)
       node.next_node = node.next_node.next_node
   end
 
   def find_before(value)
       node = @head
       return false if !node.next_node
       return node if node.next_node.value == value
 
       while (node = node.next_node)
           return node if node.next_node && node.next_node.value == value
       end
   end
 
   def print
       node = @head
       puts node
       while (node = node.next_node)
           puts node
       end
   end
  
end

This implementation of a linked list includes methods like append, find_tail, find_before, delete, and print methods and uses them to help create, locate, update, and delete items in the list.

#### Conclusion

Linked lists are a data type that excel in adding and removing items and can be used when creating more complicated structures such as trees, stacks, and queues. They can be created in Ruby using 2 classes, a node class and a list class. They are a bit more difficult to implement and work with than arrays so they are most often used with larger data sets, where their advantages of arrays are valuable enough to make the extra effort worth it.

