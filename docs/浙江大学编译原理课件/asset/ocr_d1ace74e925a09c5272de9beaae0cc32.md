# 5.3.2 Disambiguating Rules for Parsing Conflicts

+   - two kinds of parsing conflicts in SLR(1) parsing
+     - shift-reduce conflicts
+     - reduce-reduce conflicts.
+   - In the case of shift-reduce conflicts, **there is a natural disambiguating rule**
+     - always prefer the shift over the reduce.
+   - The case of reduce-reduce conflicts is more difficult
+     - such conflicts often (but not always) indicate an error in the design of the grammar.

![](bbox=[0.78, 0.665, 1.0, 0.99])

![](bbox=[0.0, 0.91, 0.09, 0.99])