---
layout: post
title:      "Two Pointers - Removing LinkedList Duplicates"
date:       2021-02-28 00:22:41 +0000
permalink:  two_pointers_-_removing_linkedlist_duplicates
---


I would like to give you an example of using Two Pointer Technique effectively. Here, we are working with a Linked List and it has some duplicates. Our job is to remove the duplicates. So, you are given  a Linked List with duplicates and need to return a Linked List without repeating any node values. 

Since it is not possible to do LinkedList.lenght() like in Array.length inorder to iterate over every element, we are going to use a while loop and go through each node by updating our pointer to node.next . First thing first, lets go ahead and create Node and LL class.

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
}
```

And also insert function to add nodes to our LinkedList.

```
insert(value){
    let newNode = new Node(value)
    let digger = node => {
      if(!node.next){
        node.next = newNode
      }
      else{digger(node.next)}
    }
    digger(this.head)
  }
```

Above function keeps calling itself until "node.next" doesnot exists. Once it reaches the end, it adds the newNode at that position.


To visually see all available node values, I've created a function that returns an array of all the node values in our LL.

```
printNodes(){
    let arr= [] 
    let currentNode= this.head
    while(currentNode){
      arr.push(currentNode.value)
      currentNode = currentNode.next
    }
    return arr
  }
```


Now, lets go ahead and create an instance of LL and start adding some nodes.

```
let ll = new LL(30)
ll.insert(40)
ll.insert(40)
ll.insert(50)
ll.printNodes()
```

The above code returns `[ 30, 40, 40, 50 ]`

Now, we need to write a function that would remove the duplicate and return just `[ 30, 40, 50 ]`. 
This is where we are going to use implement our Two Pointers. Pointer A would point to NULL initially, and Pointer B to the head of the LL. And they will be moving one step to the right on every iteration. Meaning, after 1st iteration, A will become B, and B will become B.next node until B.next node doesnot exists. Thats when our while loop stops.

```
removeDups(){
    let hass= {}
    let prev= null
    let head = this.head
    let current = head
    while(current){
      if(!hass[current.value]){
        hass[current.value] = true
        prev = current
        current = current.next
      }
      else{
        prev.next = current.next
        current= prev.next
      }
    }
    return head
  }
```

I have used Hash map inorder to store our node values and to check whether they already exists or not. We can also use Set inorder to get the same result. So, if the hash map does not have current.value as a key, then it will go ahead and create one whereas it will update the Pointer A and B if it already has current.value as a key; Pointer A.next will point to current.next instead of just "current". This completely removes "current" node out of the LL. 

```
let ll = new LL(30)
ll.insert(40)
ll.insert(40)
ll.insert(50)
ll.removeDups()
ll.printNodes()
```

Now the above code will give us just `[ 30, 40, 50 ]` and we 've successfully removed duplicates from our LL.


