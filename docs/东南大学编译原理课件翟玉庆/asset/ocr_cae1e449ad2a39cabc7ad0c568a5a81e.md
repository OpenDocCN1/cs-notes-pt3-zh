```
for each node n in the parse tree do
    for each attribute a of the grammar symbol at n do
        construct a node in the dependency graph for a;
for each node n in the parse tree do
    for each semantic rule b=f(c1,c2,......,ck)
        associated with the production used at n do
        for (i=1, i<=k ,i++)
            construct an edge from the node for ci to the node for b;
```