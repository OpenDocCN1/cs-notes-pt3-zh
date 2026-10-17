# 设 \( n_h \) 是高度为 \( h \) 的平衡二叉树的最小结点数.

| h   | n_h   | F_h   |
|-----|-------|-------|
| 0   | 1     | 1     |
| 1   | 2     | 1     |
| 2   | 4     | 2     |
| 3   | 7     | 3     |
| 4   | 12    | 5     |
| 5   | 20    | 8     |
| 6   | 33    | 13    |
| 7   | 54    | 21    |
| 8   | 88    | 34    |
| 9   | ......|       |

\(\Rightarrow \quad n_h = n_{h-1} + n_{h-2} + 1\)

\(\Rightarrow \quad n_h = F_{h+2} - 1, \quad (\text{对 } h \ge 0)\)

\(F_i \approx \frac{1}{\sqrt{5}} \left( \frac{1+\sqrt{5}}{2} \right)^i\)

\(\Rightarrow \quad n_h \approx \frac{1}{\sqrt{5}} \left( \frac{1+\sqrt{5}}{2} \right)^{h+2} - 1\)

\(\Rightarrow \quad h = O(\log_2 n)\)

□ 给定结点数为 \( n \) 的 AVL 树的最大高度为 \( O(\log_2 n) \)!