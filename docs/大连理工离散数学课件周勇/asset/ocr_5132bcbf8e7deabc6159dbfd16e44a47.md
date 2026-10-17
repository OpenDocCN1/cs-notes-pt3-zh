# # 格的性质： 对偶原理

定义8.2 设 \( f \) 是含有格中元素以及符号 \( =, \leqslant, \geqslant, \lor \) 和 \( \land \) 的命题。  
令 \( f^* \) 是将 \( f \) 中的 \( \leqslant \) 替换成 \( \geqslant \)，\( \geqslant \) 替换成 \( \leqslant \)，\( \lor \) 替换成 \( \land \)，\( \land \) 替换成 \( \lor \)  
所得到的命题。称 \( f^* \) 为 \( f \) 的**对偶命题**。

例如，在格中令 \( f \) 是 \( (a \lor b) \land c \leqslant c \)，\( f^* \) 是 \( (a \land b) \lor c \geqslant c \)。  
格的**对偶原理**

设 \( f \) 是含有格中元素以及符号 \( =, \leqslant, \geqslant, \lor \) 和 \( \land \) 等的命题。若 \( f \) 对一切格为真，则 \( f \) 的对偶命题 \( f^* \) 也对一切格为真。

例如，如果对一切格 \( L \) 都有 \( \forall a, b \in L, a \land b \leqslant a \)，那么对一切格 \( L \)  
都有 \( \forall a, b \in L, a \lor b \geqslant a \)

+   - 注意： 对偶是相互的，即 \( (f^*)^* = f \)