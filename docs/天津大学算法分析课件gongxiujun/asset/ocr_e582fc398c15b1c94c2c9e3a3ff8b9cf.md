# # Max clique: bounding

+   - Our goal is to find the max cliques of given graph G
+   - Using fixed length tuple X=x[1..n] (x[i]=1 if vertex i is included ) to represent solution space
+   - Its state space tree is a subset tree
+   - Bounding
+     - B(x)=true if the vertexes from root to i can not form a complete subgraph
+     - B(x)=true if the number of vertexes from root to i plus remained vertexes is no larger than bestn