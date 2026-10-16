# Bitmap Indices (Cont.)

+   - Bitmap indices are useful for queries on multiple attributes
+     - not particularly useful for single attribute queries

+   - Queries are answered using bitmap operations
+     - Intersection (and)
+     - Union (or)
+     - Complementations (not)

+   - Each operation takes two bitmaps of the same size and applies the operation on corresponding bits to get the result bitmap
+     - E.g. 100110 AND 110011 = 100010
+       100110 OR 110011 = 110111
+       NOT 100110 = 011001
+     - Males with income level L1: 10010 AND 10100 = 10000
+       - Can then retrieve required tuples.
+       - Counting number of matching tuples is even faster