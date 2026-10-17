# Hasse diagrams

What is the directed graph representation of a partial order?

+   - There will be loops at every node
+   - Transitivity will produce many "extra" edges
+   - There will be a particular direction for edges

Hasse diagrams simplify the graph by removing loops, removing extra edges implied by transitivity, and putting nodes in order (bottom to top) so that arrows can be omitted

+   - Start with a directed graph of the relation in which all arrows point upward. Then eliminate:
+     - the loops at all the vertices,
+     - all arrows whose existence is implied by the transitive property,
+     - the direction indicators on the arrows.