---
layout: post
title:      "BST,DFS,BFS-JS"
date:       2021-01-26 15:51:33 -0500
permalink:  bst_dfs_bfs-js
---


Lets code some JS and implement our Binary Search tree with all the good stuffs like Depth First Searches and Breadth First Search. Good thing about BST is that it is sorted. If you need to find a specific element in a tree, then you can cut the size in half in every iteration. 

To build BST, we have to start from the root Node. Node has a value , left and right pointer. BST node can have only 2 pointers;left and right. In a way, linked list has also similar pattern. If you remember, linked list also has a node that has a pointer to another node.

First thing first, we need to create the Node class inorder to keep creating nodes in a BST. 

```
class Node {
  constructor(value){
    this.value = value 
    this.left = null
    this.right = null
  }
}
```

Above node class takes in a value as argument, and then sets its "value" property to that argument, "left" and "right" to null.


Now, we create the BST like so 
```
class BST {
  constructor(value){
    this.root = new Node(value)
    this.count = 1
  }
}
```

Above BST class takes an argument value, then setsup the root node by creating new Node object, which will then setsup BST class "root" property to that node object, and initializes "count" property to 1. 


Now, inside the BST we can start writing our methods : 

```
count(){
    return this.count
  }
```

count() will just return the total number of nodes in a BST

```
insert(value){
    this.count ++
    let currentNode = this.root
    let newNode = new Node(value)
    let digDeeper = node => {
      if (value < node.value){
        if(!node.left){
          node.left = newNode
        }
        else{digDeeper(node.left)}
      }
      else if(value > node.value){
        if(!node.right){
          node.right = newNode
        }
        else{digDeeper(node.right)}

      }
    }
		
		  digDeeper(currentNode)
  }		
		
```

insert() method takes in a value as an argument. Immediately, we will increment the node count. Then I've saved the root node to the "currentNode" variable. Then newNode object is created passing the argument value. Since, we have to keep comparing the node to decide whether to place the newNode left or right, we need a recursive function which will keep looking for the empty space for the newNode.

```
 min(){
    let currentNode=this.root
    while(currentNode.left){
      currentNode = currentNode.left
    }
    return currentNode.value

  }
  max(){
    let currentNode=this.root
    while(currentNode.right){
      currentNode = currentNode.right
    }
    return currentNode.value
  }
	
```

Similarly, min() and max() function will have a while loop which will keep running until the last node is found. min() will keep looking left since farthest left is the minimum in the tree and vice versa for max().

```
dfsInOrder(){
    let currentNode= this.root
    let result = []
    let digDeeper = node => {
      if(node.left){
        digDeeper(node.left)
      }
      result.push(node.value)

      if(node.right){
        digDeeper(node.right)
      }
    }
    digDeeper(currentNode)
    return result

  }

```

dfsInOrder() prints the farthest left leaf node first, then its root node, then right leaf node. We will do that to the entire tree.

```
dfsPreOrder(){
    let currentNode= this.root
    let result = []
    let digDeeper = node =>{
      result.push(node.value)
      if(node.left){
        digDeeper(node.left)
      }
      if(node.right){
        digDeeper(node.right)
      }
    }
    digDeeper(currentNode)


    return result

  }
```

Similarly, dfsPreOrder() prints the root node first, then left and then right.

```
dfsPostOrder(){
    let currentNode= this.root
    let result =[]
    let digDeeper = node => {
      if(node.left){
        digDeeper(node.left)
      }
      if(node.right){
        digDeeper(node.right)
      }
      result.push(node.value)
    }
    digDeeper(currentNode)
    return result

  }
```

Similarly dfsPostOrder() prints the left node, right node and root node in order.


```
bfs(){
    let result = []
    let queue = []
    
    queue.push(this.root)
    while(queue.length){
      let currentNode = queue.shift()
      result.push(currentNode.value)
      
      if(currentNode.left){
        queue.push(currentNode.left)
      }
      if(currentNode.right){
        queue.push(currentNode.right)
      }
    }

    return result
  }
```

Since, bfs checks nodes from level to level, we are implementing a queue where we can insert node and their respective child nodes in FIFO order.
