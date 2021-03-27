---
layout: post
title:      "Tries Datastructure"
date:       2021-03-27 18:32:14 -0400
permalink:  tries_datastructure
---


Tries is a type of data structure that stores various strings in a tree like structure. With tries, we can search, insert and delete efficiently. This data structure will store each character, their information and the path they create. 

For example, we have strings "pqrs", "pqqe", "prt" 

We can store each character in a linkedlist where each character points to another character.

For example, P --> Q --> R--> S-->null

But, when we have to search for a string  in a linkedlist, then we have to iterate over the whole linkedlist to verify each character exists or not. This is going to be expensive computation wise. So, we have tries to rescue. Lets try creating a tries data structure for the above three example strings. For the first string "pqrs", p will be the root node. A root node can have multiple unique childrens. So, once root node for p is created, it will create a child node with a value of q. That child node will have another child node with a value of r. That r node will have child node with a value of s. 



          p  <-- Root
				 /  \
       q    r
			/  \    \
		r     q   t
	/         \
s           e


Now, lets insert our second string "pqqe". Lets check if first character "p" exists already in the data structure. It does, so it does nothing and checks for second character q which exists already, does nothing and checks for third charater q. Here, our node with a value of q doesnot have a child node with a value of q, so it creates another child node with value q and checks for last character e. It doesnot exists so, it creates new child node with value e under last node of q.

Now that we have inserted all the above strings, lets insert "bat". We can do that here since root node is p. That is why we will have our root node Null or something so that we can add multiple starting value nodes like the following.

           null <-- Root
            /    \
           p      b
				 /  \        \
       q    r        a
			/  \    \         \
		r     q   t         t
	/         \
s           e

So, this is the basic concept on the trie data structure. We will be looking on to some code in the next one. 
