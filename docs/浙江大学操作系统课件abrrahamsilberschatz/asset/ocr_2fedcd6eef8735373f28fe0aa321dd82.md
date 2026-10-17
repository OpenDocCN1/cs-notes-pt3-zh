# # Examples of Exponential Averaging

+   - **α = 0**
+   
+     \(\tau_{n+1}=\tau_n\)
+   
+     Recent history does not count.

+   - **α = 1**
+   
+     \(\tau_{n+1}=t_n\)
+   
+     Only the actual last CPU burst counts.

+   - **If we expand the formula, we get:**
+   
+     \[
+     \tau_{n+1}=\alpha t_n+(1-\alpha)\alpha t_{n-1}+\cdots
+     \]
+     \[
+     \qquad +(1-\alpha)^j\alpha t_{n-j-1}+\cdots
+     \]
+     \[
+     \qquad +(1-\alpha)^{n-1}t_n\tau_0
+     \]

+   - Since both α and (1 − α) are less than or equal to 1, each successive term has less weight than its predecessor.