# ADT 6.1 Graph

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