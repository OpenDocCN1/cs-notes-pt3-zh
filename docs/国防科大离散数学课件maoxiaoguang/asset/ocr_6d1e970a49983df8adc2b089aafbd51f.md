# Proof: “If” direction

+   Suppose that all vertices have even degrees. We construct an Euler circuit as follows: Start at an arbitrary vertex, and construct a path randomly, until we can’t do so anymore (this will happen at some point because the graph is finite).

+   This process must terminate at v, because each time the path passes from a vertex u it subtracts 2 from the remaining edges incident to u, and those are an even number. Therefore, we can always leave any vertex other than v.