# Interoperator Parallelism

# Pipelined parallelism

+   - Consider a join of four relations
+     - r1 ⋈ r2 ⋈ r3 ⋈ r4

+   - Set up a pipeline that computes the three joins in parallel
+     - Let P1 be assigned the computation of
+       temp1 = r1 ⋈ r2
+     - And P2 be assigned the computation of temp2 = temp1 ⋈ r3
+     - And P3 be assigned the computation of temp2 ⋈ r4

+   - Each of these operations can execute in parallel, sending result tuples it computes to the next operation even as it is computing further results
+     - Provided a pipelineable join evaluation algorithm (e.g., indexed nested loops join) is used