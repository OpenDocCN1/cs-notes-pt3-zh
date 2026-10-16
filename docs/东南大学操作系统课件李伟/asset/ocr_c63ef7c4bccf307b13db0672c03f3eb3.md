# Single Instance of Each Resource Type

+   - **Maintain** *wait-for graph*
+     - Nodes are processes.
+     - $P_i \rightarrow P_j$ if $P_i$ is waiting for $P_j$.
+   - Periodically invoke an algorithm that searches for a cycle in the graph.
+   - An algorithm to detect a cycle in a graph requires an order of $n^2$ operations, where $n$ is the number of vertices in the graph.