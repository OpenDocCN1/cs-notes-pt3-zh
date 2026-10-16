# Hash Functions

+   - Worst hash function maps all search-key values to the same bucket; this makes access time proportional to the number of search-key values in the file.
+   - An ideal hash function is **uniform**, i.e., each bucket is assigned the same number of search-key values from the set of *all* possible values.
+   - Ideal hash function is **random**, so each bucket will have the same number of records assigned to it irrespective of the *actual distribution* of search-key values in the file.
+   - Typical hash functions perform computation on the internal binary representation of the search-key.
+     - For example, for a string search-key, the binary representations of all the characters in the string could be added and the sum modulo the number of buckets could be returned.