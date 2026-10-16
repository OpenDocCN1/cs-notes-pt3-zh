# Updates on B⁺-Trees: Insertion (Cont.)

+   Splitting a leaf node:
+   - take the n (search-key value, pointer) pairs (including the one being inserted) in sorted order. Place the first ⌈n/2⌉ in the original node, and the rest in a new node.
+   - let the new node be p, and let k be the least key value in p. Insert (k,p) in the parent of the node being split.
+   - If the parent is full, split it and propagate the split further up.

+   Splitting of nodes proceeds upwards till a node that is not full is found.
+   - In the worst case the root node may be split increasing the height of the tree by 1.

![](bbox=[0.13, 0.71, 0.95, 0.82])

Result of splitting node containing Brandt, Califieri and Crick on inserting Adams
Next step: insert entry with (Califieri,pointer-to-new-node) into parent