# Step 1: The structure of an optimal BST

+   - A detail, “empty” subtrees
+   - Suppose that in a subtree with keys $k_i$, ..., $k_j$,  
+     - We select $k_i$ as the root, left subtree of $k_i$ contains no keys. Bear in mind, however, that subtrees also contain dummy keys $d_{i-1}$.
+     - Symmetrically, if we select $k_j$ as the root, right subtree of $k_j$ contains the keys $k_{j+1}$, ..., $k_j$; this right subtree contains no actual keys, but it does contain the dummy key $d_j$.

![](bbox=[0.62, 0.38, 0.94, 0.78])