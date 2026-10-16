# Static Hashing

+   - A **bucket** is a unit of storage containing one or more records (a bucket is typically a disk block).
+   - In a **hash file organization** we obtain the bucket of a record directly from its search-key value using a **hash function**.
+   - Hash function *h* is a function from the set of all search-key values *K* to the set of all bucket addresses *B*.
+   - Hash function is used to locate records for access, insertion as well as deletion.
+   - Records with different search-key values may be mapped to the same bucket; thus entire bucket has to be searched sequentially to locate a record.