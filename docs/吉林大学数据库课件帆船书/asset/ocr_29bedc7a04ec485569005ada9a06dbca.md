# Handling Skew Using Virtual Processor Partitioning

+   - Skew in range partitioning can be handled elegantly using **virtual processor partitioning**:
+     - create a large number of partitions (say 10 to 20 times the number of processors)
+     - Assign virtual processors to partitions either in round-robin fashion or based on estimated cost of processing each virtual partition

+   - Basic idea:
+     - If any normal partition would have been skewed, it is very likely the skew is spread over a number of virtual partitions
+     - Skewed virtual partitions get spread across a number of processors, so work gets distributed evenly!