# Example *P*₁ Request (1,0,2) (Cont.)

+   ▪ Check that Request ≤ Available (that is, (1,0,2) ≤ (3,3,2) ⇒ **true**. 检查请求小于有效（就是说，(1,0,2) ≤ (3,3,2)为真）

| Process | Allocation A B C | Need A B C | Available A B C |
|---|---:|---:|---:|
| P₀ | 0 1 0 | 7 4 3 | 2 3 0 |
| P₁ | 3 0 2 | 0 2 0 | |
| P₂ | 3 0 1 | 6 0 0 | |
| P₃ | 2 1 1 | 0 1 1 | |
| P₄ | 0 0 2 | 4 3 1 | |

+   ▪ Executing safety algorithm shows that sequence ⟨P₁, P₃, P₄, P₀, P₂⟩ satisfies safety requirement.
+   执行安全算法表明序列⟨p1,p3,p4,pn,p2⟩满足要求

+   ▪ Can request for (3,3,0) by *P*₄ be granted?

+   ▪ Can request for (0,2,0) by *P*₀ be granted?

P₄的(3,3,0)可以通过？ pn的(0,2,0)可以通过？