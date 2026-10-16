# 16.2 Elements of the greedy strategy

+   - **The choice that seems best at the moment is chosen**
+     - （每次决策时，当前所做的选择看起来是“最好”的）
+   - **What did we do for activity selection?**
+     1. Determine the optimal substructure.
+     2. Develop a recursive solution.
+     3. Prove that at any stage of recursion, one of the optimal choices is the greedy choice.
+     4. Show that all **but one of the subproblems resulting from the greedy choice** are empty. （通过贪婪选择，只有一个子问题非空）
+     5. Develop a recursive greedy algorithm.
+     6. Convert it to an iterative algorithm.