---
layout: post
title:      "Sliding Window Technique Algorithm"
date:       2021-01-09 23:39:32 +0000
permalink:  sliding_window_technique_algorithm
---


Today, I am going to discuss how Sliding Window Technique Algorithm works for finding out the longest substring in a given string.  Ofcourse, you can use bruteforce method inorder to solve problems like this, however, time complexity will not be that great. 

For example, lets say we are given a string "abbceed". And we need to return the longest substring with return value of integer. Looking at it, you can tell "bce" is the longest substring. So, our function needs to return 3 . 

We can solve this by brute force by nested for loops and checking from the first substring to all the way to the end. This method works, but time complexity will be O(n^2).

We can optimize it by using Sliding Window Technique algorithm. Below is my function with this algorithm:
```
var lengthOfLongestSubstring = function(s) {
  let set = new Set()
  let right= 0
  let left=0
  let maxLength = 0 
 
  while(right < s.length){
    
    if(!set.has(s[right])){
      set.add(s[right])
      maxLength = Math.max(maxLength, set.size)
      right ++
    }
    else{
      set.delete(s[left])
      left ++ 
    }
  }

  return maxLength


}
```
