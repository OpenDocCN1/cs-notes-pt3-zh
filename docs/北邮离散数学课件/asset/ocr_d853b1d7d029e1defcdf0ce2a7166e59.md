# Prim’s algorithm

+   - **Procedure** Prim(*G*:weighted connected undirected graph with n vertices)
+   - *T*:= a minimum-weighted edge
+   - For *i*:=1 to *n*-2
+   - **Begin**
+   - *e*:=an edge of minimum weight incident to a vertex in *T* and not forming a simple circuit in *T* if added to *T*
+   - T:= T with e added
+   - **End**{*T* is a minimum spanning tree of *G*}