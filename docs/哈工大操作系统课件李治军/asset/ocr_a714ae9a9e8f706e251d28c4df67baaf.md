# 死锁避免之银行家算法实例

当前状态:

| Allocation | Need | Available |
| A B C | A B C | A B C |
| P0 | 0 1 0 | 7 4 3 | 3 3 2 |
| P1 | 2 0 0 | 1 2 2 |  |
| P2 | 3 0 2 | 6 0 0 |  |
| P3 | 2 1 1 | 0 1 1 |  |
| P4 | 0 0 2 | 4 3 1 |  |

+   - Work=[3 3 2]
+   - P₁ Work=[5 3 2]
+   - P₃ Work=[7 4 3]
+   - P₂ Work=[10 4 5]
+   - P₄ Work=[10 4 7]
+   - P₀ Work=[10 5 7]

安全序列是<P₁, P₃, P₂, P₄, P₀>