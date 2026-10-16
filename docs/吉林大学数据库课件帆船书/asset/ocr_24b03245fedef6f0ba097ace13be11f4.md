# Bitmap Indices (Cont.)

+   - Bitmap indices generally very small compared with relation size
+     - E.g. if record is 100 bytes, space for a single bitmap is 1/800 of space used by relation.
+       - If number of distinct attribute values is 8, bitmap is only 1% of relation size
+   - Deletion needs to be handled properly
+     - **Existence bitmap** to note if there is a valid record at a record location
+     - Needed for complementation
+       - not(A=v):  *(NOT bitmap-A-v) AND ExistenceBitmap*
+   - Should keep bitmaps for all values, even null value
+     - To correctly handle SQL null semantics for NOT(A=v):
+       - intersect above result with *(NOT bitmap-A-Null)*