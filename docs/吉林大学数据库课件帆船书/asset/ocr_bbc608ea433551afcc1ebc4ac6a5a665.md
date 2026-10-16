# Selections Involving Comparisons

+   - Can implement selections of the form σₐ≤ᵥ(r) or σₐ≥ᵥ(r) by using
+     - a linear file scan,
+     - or by using indices in the following ways:

+   - A5 (**primary index, comparison**). (Relation is sorted on A)
+     - For σₐ≥ᵥ(r) use index to find first tuple ≥ v and scan relation sequentially from there
+     - For σₐ≤ᵥ(r) just scan relation sequentially till first tuple > v; do not use index

+   - A6 (**secondary index, comparison**).
+     - For σₐ≥ᵥ(r) use index to find first index entry ≥ v and scan index sequentially from there, to find pointers to records.
+     - For σₐ≤ᵥ(r) just scan leaf pages of index finding pointers to records, till first entry > v
+     - In either case, retrieve records that are pointed to
+       - requires an I/O for each record
+       - Linear file scan may be cheaper