# Insertion in Extendable Hash Structure (Cont)

To split a bucket j when inserting record with search-key value K_j:

+   - If i > i_j (more than one pointer to bucket j)
+     - allocate a new bucket z, and set i_j = i_z = (i_j + 1)
+     - Update the second half of the bucket address table entries originally pointing to j, to point to z
+     - remove each record in bucket j and reinsert (in j or z)
+     - recompute new bucket for K_j and insert record in the bucket (further splitting is required if the bucket is still full)

+   - If i = i_j (only one pointer to bucket j)
+     - If i reaches some limit b, or too many splits have happened in this insertion, create an overflow bucket
+     - Else
+       - increment i and double the size of the bucket address table.
+       - replace each entry in the table by two entries that point to the same bucket.
+       - recompute new bucket address table entry for K_j
+         Now i > i_j so use the first case above.