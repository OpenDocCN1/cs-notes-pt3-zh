# Observations about B⁺-trees

+   - Since the inter-node connections are done by pointers, “logically” close blocks need not be “physically” close.
+   - The non-leaf levels of the B⁺-tree form a hierarchy of sparse indices.
+   - The B⁺-tree contains a relatively small number of levels
+     - Level below root has at least 2* ⌈n/2⌉ values
+     - Next level has at least 2* ⌈n/2⌉ * ⌈n/2⌉ values
+     - .. etc.
+     - If there are K search-key values in the file, the tree height is no more than ⌈log⌊n/2⌋(K)⌉
+     - thus searches can be conducted efficiently.
+   - Insertions and deletions to the main file can be handled efficiently, as the index can be restructured in logarithmic time (as we shall see).