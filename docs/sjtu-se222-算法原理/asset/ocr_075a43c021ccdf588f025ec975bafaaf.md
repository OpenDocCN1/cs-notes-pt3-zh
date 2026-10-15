# Shortest-path properties

Notation: We fix the source to be s.

λ[v]: the length of path computed by our algorithms from s to v.

δ[v]: the length of the shortest path from s to v.

Triangle property
δ[v] <= δ[u] + w(u,v) for any edge (u,v).

Upper-bound property
δ[v] <= λ[v] for any vertex v.

Convergence property
If s⇒ u→v is a shortest path, and if λ[u] = δ[u], then after relax(u,v), we have λ[v] = δ[v].