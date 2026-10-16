# Example (Cont.)

Suppose P₂ requests an additional instance of type C.

|  | Allocation |  |  | Request |  |  | Available |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  | A | B | C | A | B | C | A | B | C |
| P₀ | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| P₁ | 2 | 0 | 0 | 2 | 0 | 2 |  |  |  |
| P₂ | 3 | 0 | 3 | 0 | 0 | 1 |  |  |  |
| P₃ | 2 | 1 | 1 | 1 | 0 | 0 |  |  |  |
| P₄ | 0 | 0 | 2 | 0 | 0 | 2 |  |  |  |

State of system?

+   - Can reclaim resources held by process P₀, but insufficient resources to fulfill other processes’ requests.
+   - Deadlock exists, consisting of processes P₁, P₂, P₃, and P₄.