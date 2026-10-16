# Parallel Sort

# Range-Partitioning Sort

+   - Choose processors $P_0, ..., P_m$, where $m \le n -1$ to do sorting.
+   - Create range-partition vector with m entries, on the sorting attributes
+   - Redistribute the relation using range partitioning
+     - all tuples that lie in the i$^{th}$ range are sent to processor $P_i$
+     - $P_i$ stores the tuples it received temporarily on disk $D_i$
+     - This step requires I/O and communication overhead.
+   - Each processor $P_i$ sorts its partition of the relation locally.
+   - Each processors executes same operation (sort) in parallel with other processors, without any interaction with the others (**data parallelism**).
+   - Final merge operation is trivial: range-partitioning ensures that, for $1 \le j < m$, the key values in processor $P^i$ are all less than the key values in $P_j$.