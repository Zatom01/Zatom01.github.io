---
layout: post
title:      "Sliding Window Technique Algorithm"
date:       2021-01-09 18:39:32 -0500
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

Here,  I have a Set called set, left and right pointers. Set will store only unique characters and both pointers will start from 0. As we start from index 0, we will be saving each characters to the set until we see a duplicate character that is already in the set. So, when we first start, we focus on "abbceed". By the time, we reach 3rd character "b", our set will already have {'a', 'b'} and maxLength will be 2, right pointer at index 2 and left at 0. Here, at index 2, there is "b" which is already in the set, so we will delete "b" from our set and increase right pointer by 1. Now our set will be {'a'} and focus on "bbceed". We then substring from left pointer to right pointer and check if there is duplicate. If there is , we will delete the character left pointer is pointing in the set.  If there is no duplicate, we will increment our right pointer and keep adding unique character to the set until the end.

This Sliding window technique works by checking substring inbetween 2 pointers and adding it to a Set until duplicate is found. When found, we delete character at left pointer in our set and increment our left pointer and check again. If there is no duplicates with in the range, we keep incrementing right pointer and check for duplicates.


