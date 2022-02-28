# Graphs


## Usecases:
- Social network  - modeling users and their connections / "people you might know"
- Recomendation engines - when Netflix recomend you something new and interesting movie...."people also wathced/you might also like"
- Location / Mapping - like google map, when it calculates the shortest of fastest way, it works with graphs, with a bunch of data, like speed limits, traffic or road quality.
- Routing Algorithms
- Visual Hierarchy
- File System Optimizations
- Visualization of the internet


## What are graphs
A **graph data structure** consists of a finite (and possibly mutable) set of vertices or nodes or points, together with a set of unordered pairs of these vertices for an undirected **graph** or a set of ordered pairs for a directed **graph**.
So they are basically nodes, with connections. These nodes are treated equally, there is no parent node.
![[Pasted image 20220226124231.png]]


## Terminology:
-   **Vertex -** a node
-   **Edge -** connection between nodes
-   **Weighted/Unweighted -** values assigned to distances between vertices ([[Shortest Path Algorithm#Weighted Graph|Weighted Graph example]])
-   **Directed/Undirected -** directions assigned to distanced between vertices


## Implementation
### Adjacency matrix
![[Pasted image 20220226125907.png]]


### Adjacency list (with [[Array]])
![[Pasted image 20220226130109.png]]


### Adjacency list (with [[Hash Table]])
![[Pasted image 20220226130319.png]]


### BIG O
![[Pasted image 20220226130428.png]]

#### To find out the shortest path in a graph, use the [[Shortest Path Algorithm#Dijkstra's Algorithm|Dijkstra's Algorithm]]

#### Adjacency List
Pro
-   Can take up less space (in sparse graphs)
-   Faster to iterate over all edges
Con
-   Can be slower to lookup specific edge

#### Adjacency Matrix
Pro
-   Takes up more space (in sparse graphs)
-   Slower to iterate over all edges
Con
- Faster to lookup specific edge


### Adjacency List implementation with Javascript Class
#### Pseudo code
##### Adding a vertex
-   Write a method called addVertex, which accepts a name of a vertex
-   It should add a key to the adjacency list with the name of the vertex and set its value to be an empty array

##### Adding an edge
-   This function should accept two vertices, we can call them `vertex1` and `vertex2`
-   The function should find in the adjacency list the key of `vertex1` and push `vertex2` to the array
-   The function should find in the adjacency list the key of `vertex2` and push `vertex1` to the array
-   Don't worry about handling errors/invalid vertices

##### REMOVING AN EDGE
-   This function should accept two vertices, we'll call them vertex1 and vertex2
-   The function should reassign the key of vertex1 to be an array that does not contain vertex2
-   The function should reassign the key of vertex2 to be an array that does not contain vertex1
-   Don't worry about handling errors/invalid vertices

##### REMOVING A Vertex
-   The function should accept a vertex to remove
-   The function should loop as long as there are any other vertices in the adjacency list for that vertex
-   Inside of the loop, call our **removeEdge** function with the vertex we are removing and any values in the adjacency list for that vertex
-   delete the key in the adjacency list for that vertex

```js
    class Graph{
        constructor(){
            this.adjacencyList = {};
        }

        addVertex(vertex){
            if(!this.adjacencyList[vertex]) this.adjacencyList[vertex] = [];
        }

        addEdge(v1,v2){
            this.adjacencyList[v1].push(v2);
            this.adjacencyList[v2].push(v1);
        }

        removeEdge(vertex1,vertex2){
			// as a plus handle the case where the vertex we want to delete
			// does not exists
            this.adjacencyList[vertex1] = this.adjacencyList[vertex1].filter(
                v => v !== vertex2
            );
            this.adjacencyList[vertex2] = this.adjacencyList[vertex2].filter(
                v => v !== vertex1
            );
        }

        removeVertex(vertex){
            while(this.adjacencyList[vertex].length){
                const adjacentVertex = this.adjacencyList[vertex].pop();
                this.removeEdge(vertex, adjacentVertex);
            }
            delete this.adjacencyList[vertex]
        }

        depthFirstRecursive(start){
            const result = [];
            const visited = {};
            const adjacencyList = this.adjacencyList;

            (function dfs(vertex){
                if(!vertex) return null;
                visited[vertex] = true;
                result.push(vertex);
                adjacencyList[vertex].forEach(neighbor => {
                    if(!visited[neighbor]){
                        return dfs(neighbor)
                    }
                });
            })(start);

            return result;
        }

        depthFirstIterative(start){
            const stack = [start];
            const result = [];
            const visited = {};
            let currentVertex;

            visited[start] = true;
            while(stack.length){
                currentVertex = stack.pop();
                result.push(currentVertex);

                this.adjacencyList[currentVertex].forEach(neighbor => {
                if(!visited[neighbor]){
                    visited[neighbor] = true;
                    stack.push(neighbor)
                }
                });
            }
            return result;
        }

        breadthFirst(start){
            const queue = [start];
            const result = [];
            const visited = {};
            let currentVertex;
            visited[start] = true;

            while(queue.length){
                currentVertex = queue.shift();
                result.push(currentVertex);


                this.adjacencyList[currentVertex].forEach(neighbor => {
                    if(!visited[neighbor]){
                        visited[neighbor] = true;
                        queue.push(neighbor);
                    }
                });
            }
            return result;
    }
    }

    let g = new Graph();
    g.addVertex("Dallas");
    g.addVertex("Tokyo");
    g.addVertex("Aspen");
    g.addVertex("Los Angeles");
    g.addVertex("Hong Kong")
    g.addEdge("Dallas", "Tokyo");
    g.addEdge("Dallas", "Aspen");
    g.addEdge("Hong Kong", "Tokyo");
    g.addEdge("Hong Kong", "Dallas");
    g.addEdge("Los Angeles", "Hong Kong");
    g.addEdge("Los Angeles", "Aspen");
```

#### Tracersal of Graphs (visiting/updateing/checking every single vertex in a graph)
##### Examples:
-   Peer to peer networking
-   Web crawlers
-   Finding "closest" matches/recommendations
-   Shortest path problems
    -   GPS Navigation
    -   Solving mazes
    -   AI (shortest path to win the game)

##### DEPTH FIRST
Explore as far as possible down one branch before "backtracking".

###### Recursive
```
DFS(vertex):
    if vertex is empty
        return (this is base case)
    add vertex to results list
    mark vertex as visited
    for each neighbor in vertex's neighbors:
       if neighbor is not visited:
          recursively call DFS on neighbor
```

-   The function should accept a starting node
-   Create a list to store the end result, to be returned at the very end
-   Create an object to store visited vertices
-   Create a helper function which accepts a vertex
    -   The helper function should return early if the vertex is empty
    -   The helper function should place the vertex it accepts into the visited object and push that vertex into the result array.
    -   Loop over all of the values in the adjacencyList for that vertex
    -   If any of those values have not been visited, recursively invoke the helper function with that vertex
-   Invoke the helper function with the starting vertex
-   Return the result array

###### Iterative
```
DFS-iterative(start):
    let S be a stack
    S.push(start)
    while S is not empty
        vertex = S.pop()
        if vertex is not labeled as discovered:
            visit vertex (add to result list)
            label vertex as discovered
            for each of vertex's neighbors, N do
                S.push(N)
```

-   The function should accept a starting node
-   Create a stack to help use keep track of vertices (use a list/array)
-   Create a list to store the end result, to be returned at the very end
-   Create an object to store visited vertices
-   Add the starting vertex to the stack, and mark it visited
-   While the stack has something in it:
    -   Pop the next vertex from the stack
    -   If that vertex hasn't been visited yet:
        -   Mark it as visited
        -   Add it to the result list
        -   Push all of its neighbors into the stack
-   Return the result array


##### BREADTH FIRST
Visit neighbors at current depth first! In the implementation rather then using a [[Stack]] we are using [[Queues]].

-   This function should accept a starting vertex
-   Create a queue (you can use an array) and place the starting vertex in it
-   Create an array to store the nodes visited
-   Create an object to store nodes visited
-   Mark the starting vertex as visited
-   Loop as long as there is anything in the queue
-   Remove the first vertex from the queue and push it into the array that stores nodes visited
-   Loop over each vertex in the adjacency list for the vertex you are visiting.
-   If it is not inside the object that stores nodes visited, mark it as visited and enqueue that vertex
-   Once you have finished looping, return the array of visited nodes

###### Recursive
```
DFS(vertex):
    if vertex is empty
        return (this is base case)
    add vertex to results list
    mark vertex as visited
    for each neighbor in vertex's neighbors:
       if neighbor is not visited:
          recursively call DFS on neighbor
```

-   The function should accept a starting node
-   Create a list to store the end result, to be returned at the very end
-   Create an object to store visited vertices
-   Create a helper function which accepts a vertex
    -   The helper function should return early if the vertex is empty
    -   The helper function should place the vertex it accepts into the visited object and push that vertex into the result array.
    -   Loop over all of the values in the adjacencyList for that vertex
    -   If any of those values have not been visited, recursively invoke the helper function with that vertex
-   Invoke the helper function with the starting vertex
-   Return the result array

###### Iterative
```
DFS-iterative(start):
    let S be a stack
    S.push(start)
    while S is not empty
        vertex = S.pop()
        if vertex is not labeled as discovered:
            visit vertex (add to result list)
            label vertex as discovered
            for each of vertex's neighbors, N do
                S.push(N)
```

-   The function should accept a starting node
-   Create a stack to help use keep track of vertices (use a list/array)
-   Create a list to store the end result, to be returned at the very end
-   Create an object to store visited vertices
-   Add the starting vertex to the stack, and mark it visited
-   While the stack has something in it:
    -   Pop the next vertex from the stack
    -   If that vertex hasn't been visited yet:
        -   Mark it as visited
        -   Add it to the result list
        -   Push all of its neighbors into the stack
-   Return the result array
