# Pipelining

+   - **Pipelined evaluation** : evaluate several operations simultaneously, passing the results of one operation on to the next.

+   - E.g., in previous expression tree, don’t store result of
+   
+     σ_building="Watson" (department)

+   - instead, pass tuples directly to the join.. Similarly, don’t store result of join, pass tuples directly to projection.

+   - Much cheaper than materialization: no need to store a temporary relation to disk.

+   - Pipelining may not always be possible – e.g., sort, hash-join.

+   - For pipelining to be effective, use evaluation algorithms that generate output tuples even as tuples are received for inputs to the operation.

+   - Pipelines can be executed in two ways: **demand driven** and **producer driven**