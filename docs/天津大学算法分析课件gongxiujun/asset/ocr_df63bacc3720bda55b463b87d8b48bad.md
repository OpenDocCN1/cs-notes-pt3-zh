# An example

![](bbox=[0.091, 0.146, 0.998, 0.491])

+   - we can traceback the shortest paths from matrix $(k_{ayj})$, for example, from 1 to 5
+     - $key(1,5)=4$, $key(4,5)=0$, $4 \rightarrow 5$ is a sub-path
+     - $key(1,4)=3$, $key(3,4)=0$, $3 \rightarrow 4$ is a sub-path
+     - $key(1,3)=0$, $key(2,3)=0$, $2 \rightarrow 3$ is a sub-path
+     - $key(1,2)=0$, $1 \rightarrow 2$ is a sub-path