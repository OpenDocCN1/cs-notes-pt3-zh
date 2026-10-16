# NL equals to coNL

# Proof Idea

+   - We compute $c$ by a nondeterministic log space procedure
+     - At least has one computation branch has the correct value of $c$
+     - All other branches reject
+   - For each $i$ from 0 to $m$, we define $A_i$ to be the collection of nodes that are at a distance of $i$ or less from $s$
+   - $A_0 = \{s\}$ and each $A_i \subseteq A_{i+1}$
+   - $A_m$ contains all nodes that are reachable from $s$
+   - Let $c_i$ be the number of nodes in $A_i$
+   - To compute $c_{i+1}$ from $c_i$, we go through all the nodes of $G$ and determines whether each is a member of $A_{i+1}$ and count the members
+   - $c = c_m$