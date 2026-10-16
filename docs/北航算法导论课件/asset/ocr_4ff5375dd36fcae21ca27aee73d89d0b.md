# Solution 16.2-2 ? ? ? ? ?

+   - 输入： W, n, v = <v₁, v₂..., vₙ>, w = <w₁, w₂..., wₙ>
+   - 储存c[i, j] 在表 c[0..n, 0..W]中（行优先）， c[n,W] 为原始最大值
+   - Tracing 最优解： If c[i,w]=c[i-1,w], item i is !∈ 最优解，继续 tracing with c[i-1,w], else item i ∈ 最优解，继续 tracing with c[i-1,w-wᵢ].

```
DYNAMIC-0-1-KNAPSACK(v,w, n,W)
for w ← 0 to W
    c[0,w] ← 0
for i ← 1 to n
    c[i, 0] ← 0
    for w ← 1 to W
        if wᵢ ≤ w
            if vᵢ + c[i-1,w-wᵢ] > c[i-1,w]
                c[i,w] ← vᵢ + c[i-1,w-wᵢ]
            else c[i,w] ← c[i-1,w]
        else c[i,w] ← c[i-1,w]
```