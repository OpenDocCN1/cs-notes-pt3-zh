# Bitmap Indices

+   - Bitmap indices are a special type of index designed for efficient querying on multiple keys
+   - Records in a relation are assumed to be numbered sequentially from, say, 0
+     - Given a number n it must be easy to retrieve record n
+       - Particularly easy if records are of fixed size
+   - Applicable on attributes that take on a relatively small number of distinct values
+     - E.g. gender, country, state, ...
+     - E.g. income-level (income broken up into a small number of levels such as 0-9999, 10000-19999, 20000-50000, 50000-infinity)
+   - A bitmap is simply an array of bits

![](bbox=[0.0, 0.04, 0.09, 0.16])