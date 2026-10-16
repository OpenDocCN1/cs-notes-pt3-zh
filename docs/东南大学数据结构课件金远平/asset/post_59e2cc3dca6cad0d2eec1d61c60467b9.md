
= \frac{1.3.5...(2n-3)(2n-1).2.4.6...(2n-2)(2n)}{(n+1)!\,n!}

= \frac{(2n)!}{(2n-n)!\,n!} \cdot \frac{1}{n+1}

= \frac{1}{n+1} \binom{2n}{n}

= O(4^n / n^{3/2})

## Exercises P323-4,5

## Chapter 6
Graphs

## 6.1 The Graph Abstract Data Type

### 6.1.1 introduction

Graphs have been widely used in:
- analysis of electrical circuits
- finding shortest routes
- project planning
- identification of chemical compounds
- statistical mechanics
- genetics
- cybernetics
- linguistics
- social science
- ...

### 6.1.2 Definitions

- graph G = (V, E)
- vertices V(G) ≠ ∅
- edges E(G)
- undirected graph: (u, v) = (v, u)
- directed graph: <u, v>, u---tail, v---head, <u,v> ≠ <v,u>

Three graphs:

G₁:

V(G₁)={0,1,2,3}

E(G₁)={(0,1),(0,2),(0,3),(1,2),(1,3),(2,3)}

G₂:

V(G₂)={0,1,2,3,4,5,6}

E(G₂)={(0,1),(0,2),,,(1,3),(1,4),(2,5),(2,6)}

G₃:

V(G₃) = {0,1,2}

E(G₃) = {<0,1>,<1,0>,<1,2>}  (directed)

(a) G₁

(b) G₂

(c) G₃

Restrictions:
1. $(v, v)$ or $\langle v, v\rangle$ is not legal, such edges are known as self edges.
2. Multiple occurrences of the same edges are not allowed. If allowed, we get a multigraph.

- The maximum number of edges in any $n$-vertex, undirected graph is $n(n-1)/2$, and in directed graph is $n(n-1)$.
- An $n$-vertex undirected graph with $n(n-1)/2$ edges is said to be complete.

- If (u, v) ∈ E(G), we say u and v are adjacent and edge (u, v) is incident on vertices u and v. If <u, v> is a directed edge, then vertex u is adjacent to v, and v is adjacent from u, <u, v> is incident to u and v.
- A subgraph of G is a graph G` such that V(G`) ⊆ V(G) and E(G`) ⊆ E(G).
- A path from u to v in G is a sequence of vertices u, i₁, i₂, ..., iₖ, v such that (u, i₁), (i₁, i₂), ..., (iₖ, v) are edges in E(G). If G` is directed, then <u, i₁>, <i₁, i₂>, ..., <iₖ, v> are edges in E(G`).
- The length of a path is the number of edges on it.

- A **simple path** is a path in which all vertices except possibly the first and last are distinct.
- A **cycle** is a simple path in which the first and last vertices are the same.
- For directed graph, we have directed paths and cycles.
- In an undirected G, u and v are **connected** iff there is a path in G from u to v (also from v to u).
- An undirected G is **connected** iff for every pair of distinct u and v in V(G), there is a path from u to v.

• A connected component is a maximal connected subgraph.

![](img/15e8d7d94d8ddf02cb6839870195a31e_453_0.png)

G₄ A graph with two connected components

- A **tree** is a connected acyclic graph.
- A directed G is **strongly connected** iff for every pair of distinct u and v in V(G), there is a directed path from u to v and also from v to u.
- A **strongly connected component** is a maximal subgraph that is strongly connected.
- The **degree** of a vertex is the number of edges incident to it.

## ADT 6.1 Graph

```
class Graph
{ // A non empty set of vertices and a set of undirected
// edges, where each edge is a pair of vertices.
public:
    virtual ~Graph(){ };
    // virtual destructor
    bool IsEmpty() const {return n==0;};
    // return true iff graph has no vertices
    int NumberOfVertices() const {return n;};
    // return the number of vertices in the graph
    int NumberofEdges() const {return e;};
    // return number of edges in the graph
    virtual int Degree(int u) const =0;
    // return number of edges incident to vertex u
```

```
```cpp
virtual bool ExistsEdge(int u, int v) const =0;
// return true iff graph has edge (u, v)
virtual void InsertVertex (int v) =0;
// insert vertex v into graph, v has no incident edges
virtual void InsertEdge (int u, int v) =0;
// insert edge (u, v) into graph
virtual void DeleteVertex (int v);
// delete v and all edges incident to it
virtual void DeleteEdge (int u, int v) =0;
// delete edge (u, v) from the graph
private:
    int n;    // number of vertices
    int e;    // number of edges
};
```
```
