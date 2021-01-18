---
layout: post
title:      "Understanding Binary Search Algorithm "
date:       2021-01-18 15:58:31 -0500
permalink:  understanding_binary_search_algorithm
---


Today I will be presenting you a simple illustration of Binary Search Algorithm in Javascript. This algorithm has a  better time complexity than linear. It has a time complexity of O(log n) while linear is O(n). 

To use this algorithm, input array must be sorted first. For example, we are given an array of integers and told to find a specific integer in that array. 

```
let arr=[1,2,3,4,5,6,7,9,11,23,55,66,70,13,14,81,82,83,85,86,88,89,90] , target integer = 90
```

There is a brute force method where we can check each element and see if they equals to our target integer. This array has a size of 23. That means, it would take 23 step to finally find our target integer. Imagine if we have array size of 1 million and we have to find the last integer. It would be a disaster. 

Well this is where Binary Search Algorithm comes to rescue. 

Lets first sort this array
```
let array = arr.sort((a,b)=> (a-b))
```

Then lets define our low and high pointers. Low equals to the first index and high equals to the last index of our array.
```
let low = 0
let high = arr.length - 1
```

Since Binary Search Algorithm divides the input size into half every time, lets define our middle pointer as well. Also, lets set our variable found equals to false
```
let mid = 0
let found = false
```

Inside while loop, lets keep mutating our mid varaible. It will always be the middle value of low and high pointer. Here, floor() returns just the integer ignoring all the decimals.

```
mid = Math.floor((low+high)/2)

```

We will now set up our base condition (stopping point). Here we will say if array[mid] equals target integer, than return that target integer. At some point, our low and high will be the same and array[mid] will equal to the target integer.

```
 if (array[mid] == num){
    found = true
		return num
 }
```

If arr[mid] is not equal to the num, then will have two options; either target integer is less than arr[mid] or greater than arr[mid].  If it is greater, than we will update our low to mid+1, else update our high to mid - 1.  

```
else if (num > array[mid]){
      low= mid+1
}
else if (num < array[mid]){
      high = mid -1
}

```

 
 Final code for both bruteforce and binary search implementation looks like the following:

```
let arr=[1,2,3,4,5,6,7,9,11,23,55,66,70,13,14,81,82,83,85,86,88,89,90]

function forLoop(arr,num){
  let array= arr.sort((a,b)=> (a-b))
  let count = 0
  for(let i =0 ; i < array.length ; i++ ){
    count++
    if (arr[i] == num ){
      console.log("Forloop :",num, "found after", count, "th try")
    }
  }
}

forLoop(arr,90)

function binarySearch(arr,num){
  let array = arr.sort((a,b)=> (a-b))
  let count = 0
  let low = 0
  let high = arr.length - 1
  let mid = 0
  let found = false
  while(found == false){
    count++
    mid = Math.floor((low+high)/2)
    if (array[mid] == num){
      found = true
      console.log("BinarySearch: ",num,"found after",count,"th try")
    }
    else if (num > array[mid]){
      low= mid+1
    }
    else if (num < array[mid]){
      high = mid -1
    }
  }
   
}
binarySearch(arr,90)
```

The outputs will look like this:
```
Forloop : 90 found after 23 th try
BinarySearch:  90 found after 5 th try
```

We can see  by the brute force method, it took 23 steps to find our targeted integer '90' where as it only took 5 steps for our binary search algorithm.  This is huge!  Time complexity of Binary search is O(log n) meaning for time, complexity grows in proportion to  the logarithmic size of the input size. For example, if it takes x time for input size of 10, it would take 2x time for input size of 100. On the other hand O(n) means for input size of 100, it would take 100 time, and so on. 
















