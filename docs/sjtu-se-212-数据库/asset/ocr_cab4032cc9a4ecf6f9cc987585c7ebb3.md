# File scan

+   - **Algorithm A1 (linear search).** Scan each file block and test all records to see whether they satisfy the selection condition.
+     - Cost estimate = $b_r$ block transfers + 1 seek
+       - $b_r$ denotes number of blocks containing records from relation $r$
+     - If selection is on a key attribute, can stop on finding record
+       - cost = $(b_r / 2)$ block transfers + 1 seek