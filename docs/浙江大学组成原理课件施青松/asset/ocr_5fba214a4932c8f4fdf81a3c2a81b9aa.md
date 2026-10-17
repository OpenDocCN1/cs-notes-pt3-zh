# # The Format of the Physical Address

![](bbox=[0.342, 0.137, 0.994, 0.334])

+   - The Index field selects
+     - The set, in case of a set-associative cache
+     - The block, in case of a direct-mapped cache
+     - Has as many bits as log2(#sets) for set-associative caches, or log2(#blocks) for direct-mapped caches

+   - The Byte Offset field selects
+     - The byte within the block
+     - Has as many bits as log2(size of block)

+   - The Tag is used to find the matching block within a set or in the cache
+     - Has as many bits as Address_size - Index_size - Byte_Offset_Size