# Index Update: Insertion

+   Single-level index insertion:

+   Perform a lookup using the search-key value appearing in the record to be inserted.

+   Dense indices – if the search-key value does not appear in the index, insert it.

+   Sparse indices – if index stores an entry for each block of the file, no change needs to be made to the index unless a new block is created.

+   If a new block is created, the first search-key value appearing in the new block is inserted into the index.

+   Multilevel insertion and deletion: algorithms are simple extensions of the single-level algorithms