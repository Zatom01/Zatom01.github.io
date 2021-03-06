---
layout: post
title:      "Rotating LinkedList clockwise n times- JavaScript"
date:       2021-03-06 20:57:03 +0000
permalink:  rotating_linkedlist_clockwise_n_times-_javascript
---



You are told to write a function that takes in a linkedlist and an integer(n) as an argument and returns a rotated linkedlist clockwise. You need to rotate the linkedlist n times. 

For example, given linkedlist ll = [1,2,3,4] , integer n = 2, function rotate( ll, 2)  should return linkedlist  [4,3,1,2] . 


In order to solve this, we are using two pointers which will keep udpating through out the rotation steps. As usual, lets go ahead and create Node class, Linkedlist class an insert some values. 

```
class Node {
  constructor(value){
    this.value = value 
    this.next = null
  }
}

class LL {
  constructor(value){
    this.head = new Node(value)
  }


  insert(value){
    let newNode = new Node(value)
    let digger = node => {

      if(!node.next){
        node.next = newNode 
      }
      else {
        digger(node.next)
      }
    }
    digger(this.head)
  }

}


let ll = new LL(1)
ll.insert(2)
ll.insert(3)
ll.insert(4)

```

We have created a Linkedlist object called ll and insert values 1,2,3 & 4. 

Now lets create a function to rotate that takes in 2 arguments ; ll & n

```
function rotate(ll, n){

}
```

The very first thing we need to think is how many times does it needs to be rotated. If n = 2 , it needs to be rotated 2 times clockwise which means every Node in ll needs to move 2 steps forward. Last Node needs to come at the beginning and so on. Immediately, you can think of using some sort of loop for n times.  Each time every element inside the ll moves forward 1 step. 

Here, I have initialized and assigned variable count to 1 . Then used a while loop that will run as long as it is less or equals to n . Inside that while loop, we can put our logic. 

```
function rotate(ll, n){
  let count = 1 
  let head = ll.head 
  let curr = head
  let prev = null

  while(count > n){
    while(curr.next){
      prev = curr
      curr = curr.next  
    }
    curr.next = head 
    head = curr
    prev.next = null 
    count ++ 
    
  }
  
  return head

}

```

rotate(ll,2)

The nested while loop's whole purpose to get to the very last Node and stop. Thats when we can manipulate Node's references. Above nested while loop keeps running as long as curr.next exists. When that while loop stops, we have out last Node as curr, second last Node as prev. Now, we will point reference for curr.next to head and prev.next to null . This completely removes curr from the ll, and puts it at the beginning of the ll. Prev.next is null meaning our last Node is now prev. We update our variable head to curr and increment count. 

This above process will repeat until outer while loop stops. And we just return our head which is the first node of our ll. 
Congratulations! we now have our linkedlist rotated n times. 
