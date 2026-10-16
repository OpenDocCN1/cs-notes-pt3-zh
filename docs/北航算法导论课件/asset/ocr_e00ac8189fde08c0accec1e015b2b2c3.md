# 15.5 Optimal binary search trees

+   - Every search is either successful or unsuccessful, we have
+     $$\sum_{i=1}^{n} p_i + \sum_{i=0}^{n} q_i = 1 \quad (15.15)$$

+   - We have probabilities of searches for each (dummy) key, we can determine the expected cost of a search in a given BST $T$.

+   - Assume that the actual cost of a search is the number of nodes examined. Then the expected cost of a search in $T$ is
+     $$\mathrm{E}[\text{search cost in } T]=\sum_{i=1}^{n}(\text{depth}_T(k_i)+1)\cdot p_i + \sum_{i=0}^{n}(\text{depth}_T(d_i)+1)\cdot q_i$$
+     $$=1+\sum_{i=1}^{n}\text{depth}_T(k_i)\cdot p_i + \sum_{i=0}^{n}\text{depth}_T(d_i)\cdot q_i, \quad (15.16)$$

where $\text{depth}_T$ denotes a node's depth in the tree $T$.