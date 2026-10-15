
## Breadth-First Search

- The traversal strategy of breadth-first search (which you used on Assignment #2) proceeds outward from the starting node, visiting the start node, then all nodes one hop away, and so on.
- For example, consider the graph:
- Breadth-first search begins at the start node (n1), then does the one-hops (n2 and n6), then the two hops (n3, n5, and n7) and finally the three hops (n4).

![](img/af430dff16b82a0fe61ce7dee05dcf9c_704_0.png)

## Frodo’s Journey

![](img/af430dff16b82a0fe61ce7dee05dcf9c_705_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_705_1.png)

## The Middle Earth Graph

![](img/af430dff16b82a0fe61ce7dee05dcf9c_706_0.png)

## Exercise: Depth-First Search

Construct a depth-first search starting from Hobbiton (HOB):

![](img/af430dff16b82a0fe61ce7dee05dcf9c_707_0.png)

- Visiting node HOB
- Visiting node BRE
- Visiting node RIV
- Visiting node CAR
- Visiting node LOR
- Visiting node EDO
- Visiting node ISE
- Visiting node SOU
- Visiting node MIN
- Visiting node CIR
- Visiting node BLA
- Visiting node MOU
- Visiting node RAU
- Visiting node MOR

## Dijkstra’s Algorithm

- One of the most useful algorithms for computing the shortest paths in a graph was developed by Edsger W. Dijkstra in 1959.
- The strategy is similar to the breadth-first search algorithm you used to implement the word-ladder program in Assignment. The major difference are:
  - The queue used to hold the paths delivers items in increasing order of total cost rather than in the traditional first-in/first-out order. Such queues are called *priority queues*.
  - The algorithm keeps track of all nodes to which the total distance has already been fixed. Distances are fixed whenever you dequeue a path from the priority queue.

## Shortest Path

![](img/af430dff16b82a0fe61ce7dee05dcf9c_710_0.png)

## Exercise: Dijkstra’s Algorithm

Find the shortest path from Hobbiton (HOB) to Lorien (LOR):

![](img/af430dff16b82a0fe61ce7dee05dcf9c_711_0.png)

- HOB (0)
- HOB→SOU (1)
- HOB→BRE (10)
- HOB→BRE→RIV (40)
- HOB→BRE→RIV→MOR (50)
- HOB→SOU→ISE (51)
- HOB→BRE→RIV→CAR (70)
- HOB→BRE→RIV→MOR→LOR (90)
- HOB→BRE→RIV→CAR→LOR (100)
- HOB→SOU→ISE→EDO (101)

## Kruskal’s Algorithm

- In many cases, finding the shortest path is not as important as as minimizing the cost of a network as a whole. A set of arcs that connects every node in a graph at the smallest possible cost is called a *minimum spanning tree*.
- The following algorithm for finding a minimum spanning tree was developed by Joseph Kruskal in 1956:
  - Start with a new empty graph with the same nodes as the original one but an empty set of arcs.
  - Sort all the arcs in the graph in order of increasing cost.
  - Go through the arcs in order and add each one to the new graph if the endpoints of that arc are not already connected by a path.
- This process can be made more efficient by maintaining sets of nodes in the new graph, as described on the next slide.

## Combining Sets in Kruskal’s Algorithm

- Implementing the Pathfinder version of Kruskal’s algorithm requires you need to build a new graph containing the spanning tree. As you do, you will generate sets of disconnected graphs.

- When you choose a new arc, there are four possibilities for the sets formed by the nodes at the endpoints:
  1. *Neither node is yet in a set.* In this case, create a new set and add both nodes to it.
  2. *One node is in a set and the other isn’t.* In this case, add the new node to the same set.
  3. *The endpoints are in different existing sets.* In this case, you need to merge the two sets to create a new one containing the union of the existing ones.
  4. *The endpoints are in the same set.* In this case, there is already a path between these two nodes, so you don’t need this arc.
