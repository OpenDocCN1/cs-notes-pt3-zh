# Warshall’s Algorithm

+   - *Step1*:
+     - First transfer to $W_k$ all 1’s in $W_{k-1}$.
+   - *Step2*:
+     - List the locations $p_1, p_2, ...,$ in column $k$ of $W_{k-1}$, where the entry is 1
+     - List the locations $q_1, q_2, ...,$ in row $k$ of $W_{k-1}$, where the entry is 1
+   - *Step3*:
+     - Put 1’s in all the positions $p_i, q_j$ of $W_k$ (if they are not already there)