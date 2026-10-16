# Step 1: The structure of an optimal parenthesization

![](bbox=[0.127, 0.192, 0.963, 0.365])

+   - Construct an optimal solution to the problem from optimal solutions to subproblems based on optimal substructure.
+   
+     （基于最佳子结构，可以从子问题的最优解构造原问题的最优解）
+   
+   - Any solution to the matrix-chain multiplication requires us to split the product, and **any optimal solution contains within it optimal solutions to subproblem instances.**
+   
+     （任何最优解必包含其子问题的最优解）
+   
+     - **Split** the problem into two subproblems (optimally parenthesizing $A_iA_{i+1}\cdots A_k$ and $A_{k+1}A_{k+2}\cdots A_j$);
+     - **find** optimal solutions to subproblem;
+     - **combine** these optimal subproblem solutions.
+   
+     （将问题分为两个问题，求子问题的最优解，合并子问题的最优解）