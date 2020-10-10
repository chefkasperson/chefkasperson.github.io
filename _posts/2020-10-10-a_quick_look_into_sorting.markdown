---
layout: post
title:      "A Quick Look Into Sorting"
date:       2020-10-10 10:24:46 +0000
permalink:  a_quick_look_into_sorting
---


When it comes to understanding data, sorting is perhaps one of the most useful tools we have to help make sense of a data set. Many different algorithms have been developed over the years to improve the speed in which data can be sorted and the ones I will be comparing here are bubble sort, insertion sort, selection sort, mergesort, and quicksort. Hopefully after reading this you will be able to understand how each of these methods work and when (if ever) should they be used in sorting. We will begin with bubble sort.

### Bubble Sort

Bubble sort is perhaps the most straightforward way of sorting as it passes through an array comparing each item with its neighbor and swapping their positions as needed. It will keep passing over the array until all the items are sorted. 
function bubbleSort(array) {
   const length = array.length
   for (let i=0; i < length; i++) {
       for (let j=0; j < length; j++) {
           if (array[j] > array[j + 1]) {
               let temp = array[j]
               array[j] = array[j+1]
               array[j+1] = temp
           }
       }
   }
}

Because it uses nested for loops it has a Big O of n^2 making it a very inefficient way of sorting. Today it is used mostly as a way of teaching sorting algorithms as it is easy to understand and provides a good introduction into sorting. 

### Selection Sort

Selection sort works by finding the minimum value of an array and placing it first. Next it creates a subarray containing the unsorted elements and again finds the minimum value and places it in front of the subarray. For example the array of [ 5, 3, 1, 4, 2] will first get sorted to [1, 5, 3, 4, 2] and then will get sorted to [ 1, 2, 5, 3, 4] and so on. 

function selectionSort(array) {
   const length = array.length
   for (let i=0; i < length; i++) {
       let min = i
       let temp = array[i]
       for (let j = i+1; j < length; j++) {
           if (array[j] < array[min]) {
               min = j
           }
       }
 
       array[i] = array[min]
       array[min] = temp
   }
   return array
}

Like bubble sort it has a Big O of n^2 and is mostly used in teaching and should not be used  when sorting actual data.

### Insertion Sort

Insertion sort works by checking each number with the previous number, if the number is less it moves it to the left and then searches the left side for its proper place. If the number is greater it gets moved to the right one spot making room for a future item that may reside there.
function insertionSort(array) {
   const length = array.length
   for (let i = 1; i < length; i++) {
       if (array[i] < array[0]) {
           array.unshift(array.splice(i,1)[0])
       } else {
           if (array[i] < array[i-1]) {
               for (let j = 1; j < i; j++) {
                   if (array[i] >= array[j-1] && array[i] < array[j]){
                       array.splice(j,0,array.splice(i,1)[0])
                   }
               }
           }
       }
   }
}

Like the previous methods discussed insertion sort has a Big O of n^2 and is generally not to be used. However, insertion sort tends to perform very well when adding items to previously sorted arrays and maybe used in such circumstances with good results.

### Mergesort

Mergesort is the first of two algorithms that can be used to sort data in any circumstances with good results. It works by continually dividing the array into a left and right half until only single digits remain. It will then compare the right half to the left half and sort them if necessary. Once each level is sorted it moves up another level until the entire array is sorted. 

function mergeSort(array) {
   if (array.length === 1) {
       return array
   }
 
   const length = array.length
   const middle = Math.floor(length/2)
   const left = array.slice(0, middle)
   const right = array.slice(middle)
 
   return merge(
       mergeSort(left),
       mergeSort(right)
   )
}
 
function merge(left, right) {
    const result = []
    let leftIndex = 0
    let rightIndex = 0
   while (leftIndex < left.length && rightIndex < right.length) {
       if(left[leftIndex] < right[rightIndex]) {
           result.push(left[leftIndex])
           leftIndex++
       } else {
           result.push(right[rightIndex])
           rightIndex++
       }
   }
   return result.concat(left.slice[leftIndex]).concat(right.slice(rightIndex))
}

With a Big O of n log n mergesort is a good choice for sorting any data set. However, it does have a drawback of requiring a space complexity of O(n). Therefore if space is an issue quicksort may be a better choice.

### Quicksort

Quicksort uses a pivot to divide the array moving items of lesser value to one side and greater value to the other leaving the pivot in its appropriate spot. It then picks a pivot in each sub array and repeats the process until each item is in its proper place. 

function quickSort(array, left, right) {
   const length = array.length
   let pivot
   let partitionIndex
 
   if(left < right) {
       pivot = right
       partitionIndex = partition(array,pivot, left, right)
 
       quickSort(array, left, partitionIndex - 1)
       quickSort(array, partionIndex + 1, right)
   }
 
   return array
}
 
function partition(array, pivot, left, right) {
   let pivotValue = array[pivot]
   let partitionIndex = left
 
   for (let i = left; i < right; i++) {
       if (array[i] < pivotValue) {
           swap(array, i, partitionIndex)
           partitionIndex++
       }
       swap(array, right, partitionIndex)
       return partitionIndex
   }
}
 
function swap(array, firstIndex, secondIndex) {
   let temp = array[firstIndex]
   array[firstIndex] = array[secondIndex]
   array[secondIndex] = temp
}

Like mergesort it has an average Big O of n log n and will often outpace mergesort. WIth a space complexity of O(log n) it is often preferable to mergesort when space is an issue. Its speed does depend somewhat on how good of a pivot was chosen and has a worst case speed of O(n^2). This means that if speed is your biggest concern then it may be better to choose mergesort and if space is an issue quicksort would be the better option.

### Conclusion

Sorting is an important part of working with data and choosing the correct sorting method can save a lot of time. Methods like bubble sort, selection sort, and insertion sort are great for teaching the principles of sorting while quicksort and mergesort are the algorithms one would typically choose to sort with. Hopefully this guide provides a basic understanding of each method and when it might be good to use one method over another.





