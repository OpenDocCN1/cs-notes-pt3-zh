# # An example

Adjacent matrix

0 1 4 4 8
3 0 1 5 9
2 2 0 1 8
8 8 9 0 1
8 8 2 9 0

Distance matrix of shortest path

0 1 2 3 4
3 0 1 2 3
2 2 0 1 2
5 5 3 0 1
4 4 2 3 0

matrix kayij

0 0 2 3 4
0 0 0 3 4
0 0 0 0 4
5 5 5 0 0
3 3 0 3 0

+   - we can traceback the shortest paths from matrix \( (kay_{ij}) \), for example, from 1 to 5
+     - \( kay(1,5)=4 \), \( kay(4,5)=0 \), \( 4 \rightarrow 5 \) is a sub-path
+     - \( kay(1,4)=3 \), \( kay(3,4)=0 \), \( 3 \rightarrow 4 \) is a sub-path
+     - \( kay(1,3)=2 \), \( kay(2,3)=0 \), \( 2 \rightarrow 3 \) is a sub-path