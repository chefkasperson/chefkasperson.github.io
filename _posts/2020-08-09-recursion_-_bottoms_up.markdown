---
layout: post
title:      "Recursion - Bottoms up"
date:       2020-08-09 09:24:32 +0000
permalink:  recursion_-_bottoms_up
---



In Computer Science, recursion is a way of solving a problem by having the problem call itself. Perhaps the most commonly used example of recursion for algorithms is the Fibonacci sequence. Fibonacci is calculated by adding the sum of the two previous numbers or :
    Fib(n) = Fib(n-1) + FIb(n-2)
Assuming n is a positive integer, this can be written in Ruby as follows:
	def fib(n)
	 if n > 2
		 return fib(n-1) + fib(n-2)
	 else
		 return 1
	 end
	end


While this works, this is a very inefficient way to solve the problem because the method will have to recalculate the same occurrences over and over again. This will lead to approximately a Big O time of 2**n.

A common way to improve the efficiency of recursion solutions is to use a bottom up approach, which in this case should result in an O(n) time. The bottom up approach follows its name and starts at the bottom and works its way up so that each step only needs to be counted once.

For this problem I will start by making an array and include 2 values so that I can use the array to calculate the next values. Then, beginning at 2 I will use the previous two elements of the array to calculate the next value until I reach input value. Here is what my final solution looked like:

	def fib(n)
	 array = [0, 1 ]

	 if n < 2
		 return array[n]
	 else
		 i = 2
		 while i < n + 1 do
			 array.push(array[i-1] + array[i-2])
			 i += 1
		 end
	 end
	 array[n]
	end


I began the array with 0 so that n would be the correct index of the array and that the loop went until i < n+1 so that n would be included.

In conclusion, when a problem calls itself to produce the solution then it can be solved with recursion. Recursion in its simplest form is inefficient for computers as they will wastefully recalculate the same computations until it reaches the answer. However, by coding a bottom up approach we can improve the efficiency by keeping track of previously calculated numbers so that each computation is only made once.

