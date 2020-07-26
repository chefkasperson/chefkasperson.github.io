---
layout: post
title:      "Big O notation"
date:       2020-07-26 07:11:04 +0000
permalink:  big_o_notation
---


One of the first concepts I was told to learn after graduating from my bootcamp was Big O. I had completed a practice technical interview and the assessor wanted me to optimize a solution I had come up with. I was unaware of the fact that the include method for arrays was much less efficient (O(n)) than looking up an item in a hash with the key (O(1)).  Only after a brief introduction to the concept and a pointed suggestion to use a hash I was able to optimize my solution. So what is the Big O and why is it so important?


Big companies have big data sets and needed a way to determine how algorithm’s running times would increase as the data sets increased. The solution was Big O notation, which expresses how many operations will be required to run based on the size of the data set. In order to keep things simple Big O will assume worst case scenario so that a standard search of an array of length n will result in an O(n) runtime as each item would have to be checked. It also will drop all constants and only keep the largest (slowest) piece. For example, a big O of O(3n^2 + 2n + 7) would be shortened to O(n^2). Here are some of the Big O times:

O(1)  =>  Happens instantly as the size of the input is irrelevant. Looking up items by index for in an array or looking up items in a hash by its key are examples of this.
O(log n) => Less than linear and as the input grows the difference becomes greater.
O(n) => Linear time, time grows at the same rate as the input grows. 
O(n log n) => This grows at a rate in between linear and quadratic.
O(n^2) => Quadratic, this grows exponentially with input growth. 

The Big O is useful because it allows one to analyze code and look for areas where it can be improved. As a quick example if an algorithm used a standard search method for an array and one knew that the array was sorted, runtime for that section of code could be reduced from O(n) to O(log n) by preforming a binary search of the array.

Additionally, the Big O can also be used in the same way to determine how efficiently an algorithm uses memory as input size increases. Often algorithms that are fast in time complexity use a lot of memory to do so and are hence inefficient with memory usage. If the memory usage gets too high companies may choose to sacrifice some speed in order to lessen the load.

Ultimately the Big O is a way to determine an algorithm’s efficiency and becomes extremely important as data sets increase in size where the differences can be monumental. With practice it can help developers recognize inefficient code and fix it before applying it to a large data set.





