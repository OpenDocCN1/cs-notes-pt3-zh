The numbers outside the vertices gives the sequence in which the vertices are visited during the depth-first search.

The number is called the depth-first number, dfn, of the vertex. For example, dfn(1)=2, dnf(7)=4, dfn(6)=8.

Note that if u is an ancestor of v in the depth-first tree, then dfn(u)<dfn(v).

A nontree edge (u, v) is a back edge with respect to a spanning tree T iff either u is an ancestor of v or v is an ancestor of u. (1, 4) and (6, 7) are back edges.