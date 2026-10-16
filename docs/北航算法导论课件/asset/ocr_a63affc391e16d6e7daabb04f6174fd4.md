# 16.1.3 Converting a DP solution to a greedy solution

+   - **What are the subproblems?**
+     - Original problem is $S_{0,n+1}$
+     - Suppose our first choice is $a_{m_1}$
+     - Then next subproblem is $S_{m_1,n+1}$
+     - Suppose next choice is $a_{m_2}$
+     - Next subproblem is $S_{m_2,n+1}$
+     - And so on

+   - Each subproblem is $S_{m_i,n+1}$.

+   - And the subproblems chosen have finish times that increase.（所选的子问题，其完成时间是增序排列）

+   - Therefore, we can consider each activity **just once**, in monotonically increasing order of finish time.