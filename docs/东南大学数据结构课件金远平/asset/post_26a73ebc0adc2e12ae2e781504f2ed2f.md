
```
MGraph::MGraph(const int vertices) : e(0)
{
    if (vertices < 1) throw "Number of vertices must be > 0";
    n = vertices;
    adjMultiLists = new EdgePtr[n];
    fill(adjMultiLists, adjMultiLists+n,0);
}
```

## Here is the adjacency multilists for G₁:

adjMultiLists
[0]
[1]
[2]
[3]
N0  0  1  N1  N3  edge (0,1)
N1  0  2  N2  N3  edge (0,2)
N2  0  3  0   N4  edge (0,3)
N3  1  2  N4  N5  edge (1,2)
N4  1  3  0   N5  edge (1,3)
N5  2  3  0   0   edge (2,3)

## If p points to an MGraphEdge representing (u, v), and given u, to get v we need the following test:

if (p→vertex1 == u) v = p→vertex2;else v = p→vertex1;

## And we can insert an edge in O(1):

```
void MGraph::InsertEdge(int u, int v) {
    MGraphEdge *p = new MGraphEdge;
    p→m = false; p→vertex1 = u; p→vertex2 = v;
    p→path1 = adjMultiLists[u]; p→path2 = adjMultiLists[v];
    adjMultiLists[u] = adjMultiLists[v] = p;
}
```

## 6.1.3.4 weighted Edges

Edges may have **weight**.

- In the case of adjacency matrix, A[i][j] may keep this information.
- In the case of adjacency lists, we need a **weight** field in the list node.
- A graph with weighted edges is called a **network**.

**Exercises:** P340-5, 9

## 6.2 Elementary Graph Operations

Given G = (V, E), and v in V(G), we wish to visit all vertices in G that are reachable from v.

In the following methods, we assume the graphs are undirected, although they work on the directed as well.

### 6.2.1 Depth-First Search

#### Idea:

Visit the start v first, next an unvisited w adjacent to v is selected and a depth-first search from w initiated. When u is reached such that all its adjacent vertices has been visited, we back up to the last vertex visited that has an unvisited vertex w adjacent to it and initiate a depth-first search from w. The search terminates when no unvisited vertex can be reached from any of the visited vertices.

### Example 6.1

![](img/15e8d7d94d8ddf02cb6839870195a31e_481_0.png)

Fig. 6.17 (a) Graph G

#### adjLists

![](img/15e8d7d94d8ddf02cb6839870195a31e_482_0.png)

Fig 6.17 (b) Adjacency lists of G

Started from vertex 0, the vertices in G are visited in the order: 0, 1, (0), 3, (1), 7, (3), 4, (1), (7), (back to 7), 5, 2, (0), (5), 6, (2), (7), (back to 2), (back to 5), (7), (back to 7), (6), (back to 3), (back to 1), (4), (back to 0), (2).

#### Analysis of DFS:

Initiating visited needs O(n). When G is represented by its adjacency lists, DFS examines each node at most once, so the time is O(e+n).

If adjacency matrix is used, the time to determine all vertices adjacent to v is O(n), there are n vertices, the total time is O(n²).

### 6.2.2 Breadth-First Search

In a breadth-first search, we begin from the start vertex v. Next, all unvisited vertices adjacent to v are visited. Unvisited vertices adjacent to these newly visited vertices are then visited, and so on.

```
virtual void Graph::BFS (int v)
{ // breadth-first search: begin at v, use a queue.
    visited = new bool[n];
    fill(visited, visited + n, false);
    visited[v] = true;
    Queue<int> q;
    q.Push(v);
```

```
while (!q.IsEmpty()) {
    v = q.Front();
    q.Pop();
    for (all vertices w adjacent to v)  // actual code uses an
                                         // iterator
        if (!visited[w]) {
            q.Push(w);
            visited[w] = true;
        }
    }   // end of while
delete [] visited;
}
```

#### Example 6.2:

Started from vertex 0, the vertices in G of Fig. 6.17 are visited by breadth-first search in the order:

0, 1, 2, 3, 4, 5, 6, 7.

#### Analysis of BFS:

Each visited vertex enters the queue exactly once, the while loop is iterated at most n times.

If adjacency matrix is used, the loop takes O(n) for each node visited, the total time is O(n²).

If adjacency lists are used, the loop has a total cost of d₀ + ··· + dₙ₋₁ = O(e), the total time is O(n+e).
