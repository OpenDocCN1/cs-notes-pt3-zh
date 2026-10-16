# Other Operations : Outer Join

+   - Modifying hash join to compute r ⟕ s
+     - If r is probe relation, output non-matching r tuples padded with nulls
+     - If r is build relation, when probing keep track of which r tuples matched s tuples. At end of s_i output non-matched r tuples padded with nulls