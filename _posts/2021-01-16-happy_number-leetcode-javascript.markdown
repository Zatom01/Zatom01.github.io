---
layout: post
title:      "Happy Number-Leetcode-Javascript"
date:       2021-01-16 22:18:44 +0000
permalink:  happy_number-leetcode-javascript
---


Today, I will be discussing about one of the question from Leetcode; Happy Number.

Question is given a positive integer number as an argument to the function isHappy(n), we have to replace the number with the square of its digits. Keep repeating until the number reaches to 1. If it reaches 1, return true, else false. For example; 
```
Example 1:

Input: n = 19
Output: true
Explanation:
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
Example 2:

Input: n = 2
Output: false
```

Since the question requires us to keep checking until we reach the value 1, I thought of using recurssion to solve this. I set up my base case saying if a integer argument equals to 1, then return true, else call itself. Here is the interesting thing about this question; Not all integer reach to value 1. Some will go to infinite loop.

Inorder for my function to go to infinite loop, I defined a counter and set its value to 0 which will increment when a function calls itself. And to detect infinity loop, I put a if else statement basically saying, if a function calls itself more than 8 times, thats an inifinite loop, and return false which will completely shutdown the infinite loop.

Another roadblock for me while solving this was I was just calling the function itself after else statement which was not returning any boolean when a task was completed. So, I defined a varaible result and saved the output of the recurssive call to that variable and returned it 



```
function breakItDown(n){
  let arr= n.toString().split("")
  let sum= 0
  for(let i =0 ; i < arr.length ; i++){
    sum += (parseInt(arr[i]))** 2
  } 
  return sum 
}


var isHappy = function(n, counter =0) {

  if(counter > 8){
    return false
  }
  if (n == 1 ) {
    return true 
  }
  else {
    counter ++
    result = isHappy(breakItDown(n),counter)
    return result
  }
  return false 
    
};
```
