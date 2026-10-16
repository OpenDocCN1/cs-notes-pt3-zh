# 16.1.1 Optimal substructure of activity selection

![](bbox=[0.423, 0.143, 0.957, 0.316])

+   - Suppose that a solution to $S_{ij}$ includes $a_k$. Have 2 sub-problems:
+     - $S_{ik}$ (start after $a_i$ finishes, finish before $a_k$ starts)
+     - $S_{kj}$ (start after $a_k$ finishes, finish before $a_j$ starts)
+   - Solution to $S_{ij}$ = (solution to $S_{ik}$) ∪ {$a_k$} ∪ (solution to $S_{kj}$)
+   
+     Since $a_k$ is in neither of the subproblems, and the subproblems are disjoint, $|$ solution to $S$ $| = |$ solution to $S_{ik}$ $| + 1 + |$ solution to $S_{kj}$ $|$.
+   - **Optimal substructure:** If an optimal solution to $S_{ij}$ includes $a_k$, then the solutions to $S_{ik}$ and $S_{kj}$ used within this solution must be optimal as well. (use usual cut-and-paste argument).
+   - Let $A_{ij}$ = optimal solution to $S_{ij}$,
+   
+     so $A_{ij} = A_{ik} \cup \{a_k\} \cup A_{kj}$,                          (16.2)
+   
+     assuming: $S_{ij}$ is nonempty; and we know $a_k$.