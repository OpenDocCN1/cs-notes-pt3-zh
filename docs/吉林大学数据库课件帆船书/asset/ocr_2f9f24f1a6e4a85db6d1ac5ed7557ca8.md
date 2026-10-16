# Paralel Join

+   - The join operation requires pairs of tuples to be tested to see if they satisfy the join condition, and if they do, the pair is added to the join output.
+   - Parallel join algorithms attempt to split the pairs to be tested over several processors. Each processor then computes part of the join locally.
+   - In a final step, the results from each processor can be collected together to produce the final result.

![](bbox=[0.0, 0.0, 0.073, 0.091])