# Kruskal’s Algorithm

+   - In many cases, finding the shortest path is not as important as as minimizing the cost of a network as a whole. A set of arcs that connects every node in a graph at the smallest possible cost is called a *minimum spanning tree*.
+   - The following algorithm for finding a minimum spanning tree was developed by Joseph Kruskal in 1956:
+     - Start with a new empty graph with the same nodes as the original one but an empty set of arcs.
+     - Sort all the arcs in the graph in order of increasing cost.
+     - Go through the arcs in order and add each one to the new graph if the endpoints of that arc are not already connected by a path.
+   - This process can be made more efficient by maintaining sets of nodes in the new graph, as described on the next slide.