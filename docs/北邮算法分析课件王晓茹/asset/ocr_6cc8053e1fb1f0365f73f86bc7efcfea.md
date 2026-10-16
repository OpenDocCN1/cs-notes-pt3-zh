# # 找寻最优子结构

+   - 设 \( (y_1, y_2, \dots, y_n) \) 是 \( x_1 \sim x_n \) 的一个最优解，则可以推断，\( (y_2, y_3, \dots, y_n) \) 是一个子问题的最优解。

\(\max \sum_{i=2}^n v_i y_i\)

\(\left\{ \begin{array}{l} \sum_{i=1}^n w_i y_i \leq C - w_1 y_1 \\ y_i \in \{0,1\}, 1 \leq i \leq n \end{array} \right.\)