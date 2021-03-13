---
layout: post
title:      "Graph Search Algorithms - Javascript"
date:       2021-03-13 23:34:09 +0000
permalink:  graph_search_algorithms_-_javascript
---



Suppose you are given a list of Airports and routes between them ,  how would you check if there exists a route between any two airports? Thats exactly what will be solving in this blog. 


We can represent this in a Graph. A Graph has nodes and edges. Edges can have weights, but we are not worried about that in this question. Individual airport will be a single node and routes between them will be edges. Lets say our edges are undirected. Meaning, if there exists a route between two airports, then it is a two way route. 

Example; we are given list of airports and routes like this : 

```
 "PHX BKK OKC JFK LAX MEX EZE HEL LOS LAP LIM"
 const routes = 
 [ 
  ['PHX', "LAX"], 
  ['PHX', 'JFK'],
  ['JFK', 'OKC'],
  ['JFK', 'HEL'],
  ['JFK', 'LOS'],
  ['MEX', 'LAX'],
  ['MEX', 'BKK'],
  ['MEX', 'LIM'],
  ['MEX', 'EZE'],
  ['LIM', 'BKK']
]
 
```

Lets go ahead and split airports and save these airports in an array

```
const airports = "PHX BKK OKC JFK LAX MEX EZE HEL LOS LAP LIM".split(" ")
```


Main question would be how to create an adjacency list or show all the connected airports related to each airport. 
Also, to find a route between two airports, for example between "PHX" and "MEX" . 


Since, each airport would have multiple airports connected to it, we will use a Map() function inorder to show adjacency list. This is how we will create a graph

```
const adjacencyList = new Map()
```

Now, in a graph, we need to start adding nodes. So, we will write a function that takes in a airport and creates an empty list.

```
const addNode = airport => {
adjacencyList.set(airport, []}
```

Lets iterate over all airports and start creating nodes.
```
airports.forEach(airport => addNode(airport));
```

At the moment, our graph looks like this 
```
Map {
  'PHX' => [],
  'BKK' => [],
  'OKC' => [],
  'JFK' => [],
  'LAX' => [],
  'MEX' => [],
  'EZE' => [],
  'HEL' => [],
  'LOS' => [],
  'LAP' => [],
  'LIM' => []
}

```

They don't have the edges yet. We have not defined the edges. So, lets iterate over the routes that was provided, and add edges. 

```
const addEdge = (origin,destination) => {
  adjacencyList.get(origin).push(destination)
  adjacencyList.get(destination).push(origin)
}

routes.forEach(route => addEdge(...route))
```

Here, addEdge takes in single route which consists of two airports. Then it gets the first airport from the graph and maps the second airport to it and vice versa since it is a undirected graph. Now, our edges are all defined an our graph looks like this
```
Map {
  'PHX' => [ 'LAX', 'JFK' ],
  'BKK' => [ 'MEX', 'LIM' ],
  'OKC' => [ 'JFK' ],
  'JFK' => [ 'PHX', 'OKC', 'HEL', 'LOS' ],
  'LAX' => [ 'PHX', 'MEX' ],
  'MEX' => [ 'LAX', 'BKK', 'LIM', 'EZE' ],
  'EZE' => [ 'MEX' ],
  'HEL' => [ 'JFK' ],
  'LOS' => [ 'JFK' ],
  'LAP' => [],
  'LIM' => [ 'MEX', 'BKK' ]
}
```

This answers our first question.  Now given two airports "PHX", "MEX", lets try to find out routes between them. Since, there is no direct route, we will have to check from airport to airport. For example, PHX => "LAX", then check if "LAX" has direct route to "MEX". If there is no direct route, then we will keep digging their connected nodes and so on. 

This is exactly what Depth First Search or Breadth First Search algorithm does. 

Here, I will show you how Breadth First Search works in our scenario. 

```
const bfs = (start,dest) => {
  let queue = [start]
  const visited = new Set()

  while(queue.length){
    const airport = queue.shift()
    console.log(airport)
    const destinations = adjacencyList.get(airport)
    destinations.forEach(destination =>{
      
      if(destination === dest){
        console.log('found it :', destination)
        queue = []
      }
      else {
        if(!visited.has(destination)){
          visited.add(destination )
          queue.push(destination)
        }
      }
    }

    )
  }
}

bfs('PHX',"MEX")
```

Here, in bfs, we use a queue datastructure to store our children nodes. To make sure we visit each node only once, we will be using Set() to track all the visited nodes/airports. 

As long as the queue's length exists, it will keep popping the first node from the queue and keep checking the node's childrens. If any children/airport equals to the destination airport, then we found the airport.

here bfs('PHX',"MEX") results
```
PHX
LAX
found it : MEX
```

Another example : bfs("PHX","EZE") results
```
PHX
LAX
JFK
PHX
MEX
found it : EZE
```

And that answers our second question too

