# Combining Sets in Kruskal’s Algorithm

+   - Implementing the Pathfinder version of Kruskal’s algorithm requires you need to build a new graph containing the spanning tree. As you do, you will generate sets of disconnected graphs.
+   
+   - When you choose a new arc, there are four possibilities for the sets formed by the nodes at the endpoints:
+     1. *Neither node is yet in a set.* In this case, create a new set and add both nodes to it.
+     2. *One node is in a set and the other isn’t.* In this case, add the new node to the same set.
+     3. *The endpoints are in different existing sets.* In this case, you need to merge the two sets to create a new one containing the union of the existing ones.
+     4. *The endpoints are in the same set.* In this case, there is already a path between these two nodes, so you don’t need this arc.