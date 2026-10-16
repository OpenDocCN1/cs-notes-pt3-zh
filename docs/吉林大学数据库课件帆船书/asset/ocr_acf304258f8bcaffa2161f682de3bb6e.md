# Handling of Skew

The distribution of tuples to disks may be skewed — that is, some disks have many tuples, while others may have fewer tuples.

+   - Types of skew:
+     - **Attribute-value skew**.
+       - Some values appear in the partitioning attributes of many tuples; all the tuples with the same value for the partitioning attribute end up in the same partition.
+       - Can occur with range-partitioning and hash-partitioning.
+     - **Partition skew**.
+       - With range-partitioning, badly chosen partition vector may assign too many tuples to some partitions and too few to others.
+       - Less likely with hash-partitioning if a good hash-function is chosen.