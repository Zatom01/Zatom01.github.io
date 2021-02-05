---
layout: post
title:      "Memoization & Fibonacci problem ( JavaScript )"
date:       2021-02-05 23:22:53 +0000
permalink:  memoization_and_fibonacci_problem_javascript
---


Today, we will talk about Memoization and how we can use this while solving recurssive problems.  Memoization is a technique to speed up our calculation by storing the results for specific input and returning it if same input comes up again. This way, we don't repeat calculations that has been done already. 

Best example for understanding this technique is by using it to solve Fibonacci problem. Fibonacci sequence is 0,1,1,2,3,5,8,13,.....etc . Basically, Fibo(5) is the sum of Fibo(4) and Fibo(3), meaning sum of previous two numbers. Following is the brute force approach without Memoization.

```
let count = 0

let fibNoMemo = n => {
  count ++
  console.log(count)
  if (n === 0 || n===1) {
    return n
  }
  else {
    let result = fibNoMemo(n-1) + fibNoMemo(n-2)
    return result
  }
}

fibNoMemo(6)
```

Here, in order to see exactly how many times the function calls itself, we have set up variable "count" to 0 initially. If you run the above code,  you will see count = 25 , meaning the function called itself 25 times inorder to finally give the result. Imagine, finding fiboNoMemo(1000). Cost is exponential and it is not practical. 

Thats where memoization comes to play .  Now how to even start? Its simple, a plain hashmap would do. We create an empty hassmap and keep storing the result for specific input. And when a function calls itself, it will check if a result for that input already exist. Below is the code with the memoization technique. 

```
let memo ={}
let count = 0

let fibMemo = n => {
  count++
  console.log(count)
  if (n === 0 || n===1) {
    return n
  }
  else if(memo[n]){
    return memo[n]
  }
  else {
    let result = fibMemo(n-1) + fibMemo(n-2)
    memo[n] = result 
    return result
  }
}
fibMemo(6)
```

If you run the above code, you will see the final value of "count"  to be only 11 compare to 25 from earlier. This is much efficient than without memoization technique. You will see this technique becoming the integral part while solving Dynamic Programming problems. 

To sumup , Memoization is cool and not that complex as it sounds like. This is an important technique every programmer needs to be famiiliar with inorder to optimize solutions.
