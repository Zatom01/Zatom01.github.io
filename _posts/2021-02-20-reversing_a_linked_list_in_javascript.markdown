---
layout: post
title:      "Reversing a Linked List in Javascript"
date:       2021-02-20 23:37:43 +0000
permalink:  reversing_a_linked_list_in_javascript
---




Today, we will be solving one of the important algorithm questions and that is how to reverse a singly LinkedList.

Just like arrays, Linked list is a type of datastructure that stores a value. Actually,  it is a collection of Nodes that stores a value. Unlike Arrays, each Node has a pointer to next Node. In Arrays, each element has an index while LinkedList doesnot. In order to retrieve specific element from the middle, we have to start lookups from the root Node in LinkedList. But, it has its own ups and downs just like any other data structures. One important benefit of Linkedlist compared to the Array is that they are efficient from a memory allocation point of view.  Their size is not pre-defined unliked Arrays, and insertion and deletion can be done easily by just updating the pointers on Linkedlist whereas we have to check and shift every element in Arrays to new memory location just to insert or delete an element.

Alright, so a LinkedList consists of Nodes that has value and pointer to next Node like following:

```
class Node {
  constructor(value){
    this.value = value 
    this.next = null 
  }
}
```


Now that we have our Node class ready, lets go ahead and create our LinkedList class

```
class LinkedList {
  constructor(value){
    this.root = new Node(value)
  }
}
```

let ll = new LinkedList(50)

As you can see, whenever we create an instance of this Linkedlist class, it takes an argument of a value which will be assigned to the "root". "ll.root" will be the head node. In order to retrieve the value(50) of this node, we do "ll.value". Right now, "ll.next" is null. But, lets go ahead and add some data to our linkedlist.

> Right now, if you print ll, it will return `LinkedList { root: Node { value: 50, next: null } }`

We want something like "ll.add(60) " inorder to add Nodes to this LinkedList, and we will do by following:
```
class LinkedList {
  constructor(value){
    this.root = new Node(value)
  }

  add(value){
    let newNode = new Node(value)
    let digger = node => {
      if(!node.next){
        node.next = newNode
      }
      else {
        digger(node.next)
      }
    }
    digger(this.root)
  }
}
```

We just defined a function called "add" which takes a value as an argument. It will immediately create new Node by passing that value to the instance of Node Class.  Then with the help of recursion we will assign the next property of our root node to our new Node. 

Lets add some values: 
```
ll.add(60)
ll.add(70)
ll
```

This will return: 
```
LinkedList {
  root: Node { value: 50, next: Node { value: 60, next: [Node] } }
}

```

Now, lets create a function that reverses our linkedlist.
```
reverseLL(){
    let p1 = null 
    let p2= this.root 
    while(p2){
      let save = p2.next
      p2.next = p1 
      p1 = p2 
      p2 = save
    }

    return p1

  }
```

Inside above function, we have two pointers. p1 is pointed to null and p2 is pointed to our root Node.
Using the while loop with the condition of "as long as our p2 exists", we have logic that basically keeps updating our pointers. p1 starts from the root node and keeps updating its pointer to the root.next until it reaches to the last element where p2 becomes invalid. We then return p1 which is the now the head.

So, there you go, we have our linkedlist reversed. Final outcome looks like this:
```
Node {
  value: 70,
  next: Node { value: 60, next: Node { value: 50, next: null } }
}
```

