# Example of Banker’s Algorithm

+   A system with
+   - 5 processes P₀ through P₄, and
+   - 3 resource types A (10 instances), B (5 instances), and C (7 instances).

+   Snapshot at time T₀:

| Allocation | Max | Available |
| A B C | A B C | A B C |
| P₀ | 0 1 0 | 7 5 3 | 3 3 2 |
| P₁ | 2 0 0 | 3 2 2 |  |
| P₂ | 3 0 2 | 9 0 2 |  |
| P₃ | 2 1 1 | 2 2 2 |  |
| P₄ | 0 0 2 | 4 3 3 |  |

| Need |
| A B C |
| P₀ | 7 4 3 |
| P₁ | 1 2 2 |
| P₂ | 6 0 0 |
| P₃ | 0 1 1 |
| P₄ | 4 3 1 |

![](bbox=[0.55, 0.48, 0.98, 0.88])