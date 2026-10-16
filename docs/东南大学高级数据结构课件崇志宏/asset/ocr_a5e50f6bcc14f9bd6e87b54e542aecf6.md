# Related Work

+   - **P-Grid (CoopIS’01)**
+     - Based on a binary prefix tree structure.
+     - Can not guarantee *log N search* step boundary
+   - **P-Tree (WebDB’04)**
+     - Based on B+-tree structure and uses CHORD as overlay framework
+     - Each node maintains a branch of the B+-tree
+     - *Expensive* cost to keep consistency knowledge among nodes
+   - **Multi-way tree (DBISP2P’04)**
+     - Each node maintains links to its parent, its siblings, its neighbors, and its children
+     - Can not guarantee *log N search* step boundary