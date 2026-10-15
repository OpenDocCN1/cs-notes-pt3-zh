# Good Points on DNS Design

+   - Scalable in management
+     - Each zone makes its own policy decision on binding
+     - Hierarchy is great here
+   - Fault tolerant
+     - If one name server breaks, other will still work
+     - Duplicated name server for a same zone