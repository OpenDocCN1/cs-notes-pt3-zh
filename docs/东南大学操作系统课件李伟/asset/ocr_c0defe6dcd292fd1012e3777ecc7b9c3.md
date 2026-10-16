# Example of Detection Algorithm

+   - Five processes *P*₀ through *P*₄; three resource types A (7 instances), B (2 instances), and C (6 instances).

+   - Snapshot at time *T*₀:

| Process | Allocation A B C | Request A B C | Available A B C |
|---|---|---|---|
| *P*₀ | 0 1 0 | 0 0 0 | 0 0 0 |
| *P*₁ | 2 0 0 | 2 0 2 | |
| *P*₂ | 3 0 3 | 0 0 0 | |
| *P*₃ | 2 1 1 | 1 0 0 | |
| *P*₄ | 0 0 2 | 0 0 2 | |

+   - Sequence ⟨*P*₀, *P*₂, *P*₃, *P*₁, *P*₄⟩ will result in *Finish*[*i*] = true for all *i*.