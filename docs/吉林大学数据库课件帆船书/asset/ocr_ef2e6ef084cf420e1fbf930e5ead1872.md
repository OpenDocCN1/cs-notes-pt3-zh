# Handling of Bucket Overflows (Cont.)

+   - **Overflow chaining** – the overflow buckets of a given bucket are chained together in a linked list.
+   - Above scheme is called **closed hashing**.
+     - An alternative, called **open hashing**, which does not use overflow buckets, is not suitable for database applications.

![](bbox=[0.21, 0.46, 0.815, 0.96])