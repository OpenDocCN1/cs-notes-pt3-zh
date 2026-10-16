# NL equals to coNL

+   2. For i = 0 to m - 1:
+   3. Let c_{i+1}=1.
+   4. For each node v ≠ s in G.
+   5. Let d = 0.
+   6. For each node u in G:
+   7. Nondeterministically either perform or skip these steps:
+   8. Nondeterministically follow a path of length at most i from s and reject if it doesn’t end at u.
+   9. Increment d.
+   10. If (u,v) is an edge of G, increment c_{i+1} and go to stage 5 with the next v.
+   9. If d ≠ c_i , then reject.

compute c_{i+1} from c_i

c_{i+1} counts nodes in A_{i+1}

check if v ∈ A_{i+1}

d re-counts A_i

check if u ∈ A_i

verified that u ∈ A_i

verified that v ∈ A_{i+1}

check whether found all A_i