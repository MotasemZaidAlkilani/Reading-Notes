# graphs
non-linear data strcture that can be looked at as a collection of vertics , and those vertics connected through line segments called edges .

-vertex (node) data object , can have zero or more adjacent vertices

-Edge the connection between two vertices 

-neighbor :the neighbor of the vertice , are vertices connected with egdes with the vertice

-Degree : the number of edges connected to vertex

## Undirected graph 
is graph that its edges are undirected , dont move to any direction

## directed graph
is graph that its edges are directed ,so each vertex direct to another vertex.

__________

## types of graphs

#### 1 - Complete graph
each vertex/node are connected to all the rest vertices.

#### 2 - Connected graph
connected graph mean each vertex have at least one edge .

note : tree is form of connected graph

#### 3 - disconnected graph
mean some vertex dont have any edges

______________

## Acyclic vs Cyclic

## acyclic graphs

Acyclic graph is directed graph without cycle , so the vertex will not back to it.


note : directed acycle graph also called DAG , can be represented as what we know as a tree.

## cyclic graphs
graph that have a cycles 

cycle graph can traversed through and potentially end up back at itself

a cycle is defined as path the start and end at same vertex 

____________________
## graph representation 
through the following :

1- Adjacency Matrix 

2-Adjacency List

#### Adjacency Matrix
represented as 2 dimensional array , so if n vertex , n X n boolean matrix 

each row and column represent vertex , if there connection between the other vertex put 1 , otherwise put 0.

#### Adjacency List 
is most common way to represent graphs 

collection of linked lists or array that list all other connected vertices .

Adjacency List make it easy to view the connected vertices.

_________
## Weighted Graphs
is a graph with number assigned to each edge , the numbers are called weights.

when representing the weighted graph in matrix ,you set th weight number instead of 1 , and still the same for no connection , u put 0.

using Adjacency List you must include both weight and the name of vertex 

_______
## Traversals
traversal through the graph like traversal in tree 

there two way to do it :

#### Breadth First 

u starting  at specific vertex , so must be defined when breathFirst() called .

-note : when using for cycle graph will lead to infinite loop , so what we do ?  u must define what u visited already .

```
ALGORITHM BREADTHfIRST(vertex)
      DECLARE nodes <-- new List()
      DEClARE breadth <-- new Queue
      DECLARE visited <-- new SET()
      
      breadth.Enqueue(vertex)
      visited.Add(vertex)
      
      while (breath is not empty )
             DECLARE front <-- breadth.Dequeue()
             nodes.Add(front)
             
             for each child in front.children
                 if (child is not visited )
                     visited.Add(child)
                     breadth.Enqueue(child)
                     
      return nodes;
```     

note : use queue to visit all children at a given level.

note : breadthFirst will not travrese through disconnected graphs.

#### Depth First 
      
note : use stack to visit all children at a given level.
      
algorithm for a depth first :

1-push the root node into stack and mark as visited , start a while loop that runs as long as the stack is not empty 

2- pop the top node off of the stack and check its neighbors, if a neighbor hasn't been visited ,push it onto the stack and mark as visited 

repeat until stack is empty.

____________
## Real World Uses of Graphs 

1-GPS and Mapping 

2-Driving Directions

3-Social Networks

4-Airline Traffic 

5-Netflix uses graphs for suggestions of products.

_________


