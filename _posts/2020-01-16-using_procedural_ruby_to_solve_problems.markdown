---
layout: post
title:      "Using Procedural Ruby to solve problems"
date:       2020-01-16 05:23:09 +0000
permalink:  using_procedural_ruby_to_solve_problems
---


Over the Holiday break I tried out the Codewars website and had quite a bit fun solving different problems with Ruby. When you first start out in Codewars the problems or Kata you are given are quite simple and are a great way to practice procedural Ruby. For this blog I figured I would go over one of the Kata I completed and explain how I approached the problem with Ruby.

The Kata I will discuss is named 'Multiples of 3 and 5'. The problem is simple, given a random number as a parameter, find the sum of all the numbers less than that number. For example given '10' the multiples less than 10 would be 9, 6, 5, 3 which add up to 23. So the solution should take in '10' and return '23'.

The first step I take when solving a problem is to break it into its steps. For this problem I broke the steps into:

1. collect all the numbers below the given number
2.  find which of those numbers are multiples of 3 or 5
3.  add them together

For the first part Ruby has a Range method which allows one to call iterating methods on the range as if it were an array. Ranges are written inside paranthesis with starting and ending values connected by two or three dots (two dots includes the final value while three dots excludes it). In our case we will opt for the three dot range so it will look like:
(1...number). This will give us all the numbers between one and the given number.

The second part we will need to find out how to check if a number is a multiple of 3 or 5 and then select the ones that are while ignoring the others. For the first step Ruby provides a Remainder method (%) which will return the remainder after two numbers are divided, for example 9%2 == 1 and 9%3 == 0. So to satisfy the problem we will test if %3 or %5 are equal to 0. In Ruby we can write this like:
( number % 5 == 0 || number % 3 == 0 )
Now we just need to choose an iterator that will only pick the numbers that satisfy this statement. In Ruby select will do this perfectly by returning an array of all the numbers that satisfy the statement in the block and we can call it directly on the range so we can now combine the two parts like this:
(1...number).select {|n| n % 3 == 0 || n % 5 == 0 }

For the final step we need to add them together. Because all the items returned when we run select are enumerables we can call #sum after select which will add together all the items returned by select and put it inside of a method. We can write it like this:
def solution(number)
  (1...number).select {|n| n % 3 == 0 || n % 5 == 0 }.sum
end

And there we have a final solution to the problem. On a final note, one nice part about Codewars is the ability to see other people's solutions and compare them to yours. It was by comparing solutions that I found out about inject and reduce (which are aliases). Either one can be used in place of sum above like this:
(1...number).select {|n| n % 3 == 0 || n % 5 == 0 }.reduce(:+)
This will give the same result as sum but an advantage using reduce or inject is that they can be used on strings as well.

Anyways Codewars is a lot of fun and is a great place to practice Procedural Ruby. Thanks for reading and have a great day.



