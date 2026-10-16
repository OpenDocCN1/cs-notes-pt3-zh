# Show Paging (Cont.)

+   - Advantages of shadow-paging over log-based schemes
+     - no overhead of writing log records
+     - recovery is trivial
+   - Disadvantages :
+     - Copying the entire page table is very expensive
+       - Can be reduced by using a page table structured like a B⁺-tree
+         - No need to copy entire tree, only need to copy paths in the tree that lead to updated leaf nodes
+     - Commit overhead is high even with above extension
+       - Need to flush every updated page, and page table
+     - Data gets fragmented (related pages get separated on disk)
+     - After every transaction completion, the database pages containing old versions of modified data need to be garbage collected
+     - Hard to extend algorithm to allow transactions to run concurrently
+       - Easier to extend log based schemes