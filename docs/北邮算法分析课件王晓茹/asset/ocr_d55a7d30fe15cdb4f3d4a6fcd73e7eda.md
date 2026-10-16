# # 动态规划的求解？

记 \( b[j] = \max_{1 \leq i \leq j} \{\sum_{k=i}^{j} a[k]\} \, 1 \leq j \leq n \)，则所求的最大子段和为

\( \max_{1 \leq i \leq j \leq n} \sum_{k=i}^{j} a[k] = \max_{1 \leq j \leq n} \max_{1 \leq i \leq j} \sum_{k=i}^{j} a[k] = \max_{1 \leq j \leq n} b[j] \)

当 \( b[j-1] > 0 \) 时 \( b[j] = b[j-1] + a[j] \)，否则 \( b[j] = a[j] \)。由此可得计算 \( b[j] \) 的动态规划递归式

\( b[j] = \max\{b[j-1] + a[j], \, a[j]\}, \, 1 \leq j \leq n \)