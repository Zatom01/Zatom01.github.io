---
layout: post
title:      "Arithmetic Slices Leetcode Question-JavaScript"
date:       2021-03-20 18:56:08 +0000
permalink:  arithmetic_slices_leetcode_question-javascript
---


We are given a function that takes in an array of integers. An integer array is called Arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.  

For example, [ 2,3,4,5] , [1,1,1,1,1,1], and [-6,-10,-14] are arithmetic Sequence.  Given an integer array, we are supposed to return number of arithmetic subarrays of nums .

EXAMPLE 1: 

Input: nums = [1,2,3,4] 
**Output**: 3 
**Explaination**: We have 3 arithmetic slices in nums. [1,2,3], [2,3,4] and [1,2,3,4] itself. 

EXAMPLE 2: 
**input**: nums = [1]
**Output**: 0


I will show you how I approached the problem step by step.  I created a function the following that takes in an array of integers:

```
let numberOfArithmeticSlices = nums => {
  let length = nums.length
  let diffArr = new Set() 
};
```

Here I have declared and initialized a variable diffArr as a new Set. I am going to iterate over the entire array and store the difference of all the consecutive numbers in this Set. I used Set because it store just the unique value. It won't store the same number twice. By the end of my iteration, if this array is an Arithmetic then this set should have just one value. Meaning, diffArr.size should be 1. 


```
for (let i= 1 ; i< nums.length ;i++){
          diffArr.add(nums[i] - nums[i-1])
   }
```

Above block of code shows that after each iteration Set has been updated.

Suppose we found out that Set has just a single value and our integer array is an Arithmetic. Now, we need to focus on how many subarrays of 3 can be created out of this single array. The base case scenario here is if the size of an input array is 3, the maximum subarray is array itself. If it is 4 then there will be 3 subarrays, and so on. 


After analying different size of an array I cracked the subarray pattern. And the pattern is as follows:

Arr(4) => 3 , Arr(5)=> 6 , Arr(6) => 10, Arr(7) =>15

So basically it is 3,6,10,15,.....so on. 

If you are familiar with Fibonacci series, it has a pattern too. Similar logic can be applied in this case . And the function that we can create for this pattern is : f(x) => f(x-1) + (x-2) 

Since it has a pattern I will just call this function fib so that similar logic can be applied. And best approach is Recursion.

```
let numberOfArithmeticSlices = nums => {
  let length = nums.length
  let diffArr = new Set()
  if(length >= 3){
    for (let i= 1 ; i< nums.length ;i++){
      diffArr.add(nums[i] - nums[i-1])
    }
    if(diffArr.size == 1){
      if(length === 3){
        return 1
      }
      else {
        return fib(length)
      }
    }
  }
  return 0
  
};

```

After knowing that an array is Arithmetic, we will use if/else statement to return the desired number of subarrays of 3. If the length is 3 then we return 1. If length is more than 3, we call our fib function.  


Fib function will takes integer length as an argument and will return a number for that integer position. It will have a base case of : If integer is 4, then return 3, else return fib(integer - 1) + (integer - 1) 

```
let fib = length => {
  if(length == 4){
    return 3
  }
  else {
    return fib(length - 1) + (length - 2)
  }
}

```

And this is one of many approaches to this problem. 
