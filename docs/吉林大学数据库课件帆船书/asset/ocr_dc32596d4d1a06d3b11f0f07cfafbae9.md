# Tuning the Database Design (Cont.)

+   - **Index tuning**
+     - Create appropriate indices to speed up slow queries/updates
+     - Speed up slow updates by removing excess indices (tradeoff between queries and updates)
+     - Choose type of index (B-tree/hash) appropriate for most frequent types of queries.
+     - Choose which index to make clustered
+   - Index tuning wizards look at past history of queries and updates (the **workload**) and recommend which indices would be best for the workload