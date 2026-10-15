# Performance goals: peak memory utilization

+   - Given some sequence of malloc and free requests:
+     - $R_0, R_1, ..., R_k, ..., R_{n-1}$
+   - Def: aggregate payload $P_k$:
+     - malloc(p) results in a block with a payload of p bytes.
+     - After request $R_k$ has completed, the aggregate payload $P_k$ is the sum of currently allocated payloads.