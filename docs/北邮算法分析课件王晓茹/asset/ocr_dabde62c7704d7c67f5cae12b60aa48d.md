# § 1 Greedy Algorithms

# 【Example】

| job | j₁ | j₂ | j₃ | j₄ |
|-----|----|----|----|----|
| time | 15 | 8 | 3 | 10 |

# Schedule 1

![](bbox=[0.234, 0.172, 0.719, 0.266])

# Schedule

> > Best scheduling is to make { tᵢₖ } nondecreasing 不减少，递增.

# In general:

![](bbox=[0.234, 0.574, 0.836, 0.699])

Total Cost \( C = \sum_{k=1}^{N} (N - k + 1)t_{i_k} = (N + 1)\sum_{k=1}^{N} t_{i_k} - \sum_{k=1}^{N} k \cdot t_{i_k} \)