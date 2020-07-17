---
layout: post
title:      "Creating a Timed Loop in Javascript"
date:       2020-07-17 13:35:26 +0000
permalink:  creating_a_timed_loop_in_javascript
---



Javascript by default does not contain any way to pause or delay the code execution in loops but instead offers the asynchronous setTimeout() function. Because setTimeout is asynchronous the loop will not wait for the timeout to complete before moving to the next iteration. For example if we wanted to console log the elements of array = [5, 4, 3, 2, 1] in 1 second intervals and tried …

	array.forEach((item) => setTimeout(() => console.log(item), 1000))

we would get all the items logged together after a 1 second delay.

The way to work around this is to increment the delay with each iteration so that the first item’s timeout is set to 0, the second’s to 1000, and so on. This can be easily done by multiplying setTimeout’s second argument by the index of the array. The forEach method offers an optional second argument of index so that we can simply do …

	array.forEach((item, index) => setTimeout(() => console.log(item), 1000 * index))

and all the items would log at evenly spaced 1 second intervals. 

This same pattern can be applied to Javascript’s other loops, for example the for loop would look something like this … 

	array = [5, 4, 3, 2, 1]
	for (let i = 0; i<array.length; i++) {
		runTimer(i)
  }

  function runTimer(i) {
	  setTimeout(() => console.log(array[i]), 1000 * i)
  }

In conclusion, Javascript’s setTimeout function is asynchronous and when used with a loop one must remember to increment the delay with each iteration in order to create evenly timed events. 

