# Overview of FP-Growth: Ideas

+   - Compress a large database into a compact, *Frequent-Pattern tree* (**FP-tree**) structure
+     - highly compacted, but complete for frequent pattern mining
+     - avoid costly repeated database scans

+   - Develop an efficient, FP-tree-based frequent pattern mining method (**FP-growth**)
+     - A divide-and-conquer methodology: decompose mining tasks into smaller ones
+     - Avoid candidate generation: sub-database test only.