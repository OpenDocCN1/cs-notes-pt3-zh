# 17.4 Dynamic tables

+   - We might allocate space for a table, only to find out later that it is not enough. We must then reallocate the table with a larger size and copy all objects stored in the original table over into the new, larger table.
+   - Similarly, if many objects have been deleted from the table, it may be worthwhile to reallocate the table with a smaller size.
+   - We assume that the dynamic table supports the operations TABLE-INSERT and TABLE-DELETE.
+     - TABLE-INSERT inserts into the table an item that occupies a single slot, that is, a space for one item.
+     - Likewise, TABLE-DELETE removes an item from the table, thereby freeing a slot.