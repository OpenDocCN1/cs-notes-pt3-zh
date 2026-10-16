# # Basic Concepts

+   - Indexing mechanisms used to speed up access to desired data.
+     - E.g., author catalog in library

Search Key - attribute to set of attributes used to look up records in a file.

An index file consists of records (called index entries) of the form

```
search-key | pointer
```

Index files are typically much smaller than the original file

Two basic kinds of indices:

+   - Ordered indices: search keys are stored in sorted order

+   - Hash indices: search keys are distributed uniformly across “buckets” using a “hash function”.