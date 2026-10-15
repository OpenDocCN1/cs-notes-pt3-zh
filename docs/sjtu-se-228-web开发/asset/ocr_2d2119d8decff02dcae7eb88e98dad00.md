# Transitive persistence

+   - For each basic operation of the Hibernate session there is a corresponding cascade style
+   - including persist(), merge(), saveOrUpdate(), delete(), lock(), refresh(), evict(), replicate()
+     - CascadeType.PERSIST
+     - CascadeType.MERGE
+     - CascadeType.REMOVE
+     - CascadeType.REFRESH
+     - CascadeType.DETACH
+     - CascadeType.ALL