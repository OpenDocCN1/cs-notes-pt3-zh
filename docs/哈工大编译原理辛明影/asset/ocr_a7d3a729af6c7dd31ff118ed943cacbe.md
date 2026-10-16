# 复习

+   - 5．FIRSTOP 和 LASTOP 集里的元素不是真正的第一和最后
+     - FIRSTOP(A) = {b | A⇒+b... 或者 A⇒+Bb...，b∈T，B∈V}
+     - LASTOP(A) = {b | A⇒+...b 或者 A⇒+...bB，b∈T，B∈V}

+   - 6．求 FIRSTOP 的算法

+   - 1．若有产生式，A→a... 或 A→Ba...，则

a∈FIRSTOP（A）

+   - 2．if A→B...∈P, then FIRSTOP(B)⊆ FIRSTOP(A)