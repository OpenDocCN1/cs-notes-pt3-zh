# 第二种情况： 用A→M₁X₁M₂X₂···MₙXₙ进行归约

+   已知：
+   - A. i的值、及其位置
+   - 计算A. s所需要的属性值均已在栈中已知的
+     位置即各有关Xⱼ的位置上

| state | ... |  | M₁ | X₁ | M₂ | X₂ | ... | Mₙ | Xₙ |
| val | ... | A.i | X₁.i | X₁.s | X₂.i | X₂.s | ... | Xₙ.i | Xₙ.s |

top-2n 指向 A.i
top-2n+2 指向 X₁.s
top-2n+4 指向 X₂.s
top 指向 Xₙ.s

| state | ... |  | A |
| val | ... | A.i | A.s |

top-1 指向 A.i
top 指向 A.s