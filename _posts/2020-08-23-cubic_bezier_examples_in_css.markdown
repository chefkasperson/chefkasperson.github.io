---
layout: post
title:      "Cubic Bezier examples in CSS"
date:       2020-08-23 08:09:35 +0000
permalink:  cubic_bezier_examples_in_css
---


So I was following a code-a-long project the other day in a React course I am taking and I came across some CSS that I hadn’t seen before. It was a pretty cool animation where when you hover over an image the picture appears to zoom in towards you and then returns back to normal when the mouse is pointed elsewhere. I have seen zooms before but this was the first time I had seen a cubic bezier function so I decided to do a bit of research on them to try and understand how they can be useful. 

What I found was that beziers can be used to customize the rates in which transitions happen. For example, you could have the transition start and end fast with a pause in the middle, or start and end slow while moving fast in the middle. Some custom beziers can even have the transition start by going backwards or end by going past the destination before returning. So how does one use the cubic bezier function.

Beziers are created by four points. The first and last point determine the start and end of the transition while the second and third points determine the shape. Since the first and last points are always fixed at (0, 0) and (1, 1) one controls the bezier with the second and third points. The cubic bezier function accepts 4 arguments, (x2 value, y2 value, x3 value, y3 value) where x represents the time the transition takes and y represents the progress. X values must be between 0 and 1 while Y values can be extended above or below this range. This can be done to create transition effects where the progress can appear to go backwards before jumping forward or go past the destination before returning to it. Typically, however these transitions are used to give a slight delay at the start and/or end of the transition to give a more natural look to transitions. Here are some examples of different patterns one can create.

Linear - cubic bezier (0, 0, 1, 1)


This is the same as not using a cubic bezier functions, the transition happens at a fixed rate. It can be calculated multiple ways as long as the x and y values are the same for each point it should remain linear. 


Ease - cubic-belzier (0.25, .1, 0.25, 1)

This transition starts fast and then slows down as it nears its end, easing into the destination.

Ease-in - cubic-bezier(0.42, 0, 1, 1)

This transition starts slowly and then accelerates as it approaches the end, then stops abruptly.

Ease-in-and-out - cubic-bezier(0.42, 0, 0.58, 1)

This one will start slow and end slow while going faster in between. This particular case has been made symmetrically so that the start and end changes are identical.

Ease-out - cubic-bezier(0, 0, 0.58, 1)

This transition starts fast and slows as it ends. 

If you would like to play around with the function and try out your own custom transitions the site https://cubic-bezier.com/ has been created so one can try out different combinations and save the ones he/she likes.

In the example I used it on in my project it was used to ease in and out of a zoom function when hovering over a section image. Here is how the code looked … 

.background-image {
     transform: scale(1.1);
     transition: transform 6s cubic-bezier(0.25, 0.45, 0.45, 0.95);
   }
 
This code was also contained in a div with the overflow set to hidden so that the image wouldn’t bleed out over the initial container it was in. The effect was really cool and something I can see myself using often in the future.

