# 有界分配格中补元惟一性

定理 设<L,∧,∨,0,1>是有界分配格. 若L中元素 a 存在补元, 则存在惟一的补元.

证 假设 b, c 是 a 的补元, 则有
$a \vee c = 1, a \wedge c = 0,$
$a \vee b = 1, a \wedge b = 0$

从而得到 $a \vee c = a \vee b, a \wedge c = a \wedge b$, 由于 L 是分配格, $b = c.$