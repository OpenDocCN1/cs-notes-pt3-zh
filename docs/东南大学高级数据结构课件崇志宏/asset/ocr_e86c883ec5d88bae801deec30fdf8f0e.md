# Node Joins

+   - Each node in Chord maintains a *predecessor pointer*, and can be used work counterclockwise around the identifier circle.
+   - When a node *n* joins the network:
+     - Initialize the predecessor and fingers of node *n*.
+     - Update the fingers and predecessors of existing nodes to reflect the addition of *n*.
+     - Notify the higher layer software so that it can transfer state (e.g. values) associated with keys that node *n* is now responsible for.