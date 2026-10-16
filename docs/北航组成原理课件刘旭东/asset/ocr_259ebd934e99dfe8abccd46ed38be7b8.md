# 2.1 无符号数乘法

# 算法推导（以定点整数为例）

$$M=M_{n-1}M_{n-2}\cdots M_0$$

$$Q=Q_{n-1}Q_{n-2}\cdots Q_0$$

$$=Q_{n-1}2^{n-1}+Q_{n-2}2^{n-2}+\cdots+Q_0 2^0$$

$$M\times Q=M\ast\left(Q_{n-1}2^{n-1}+Q_{n-2}2^{n-2}+\cdots+Q_0 2^0\right)$$

$$=\frac{1}{2}Q_{n-1}M2^n+\frac{1}{4}Q_{n-2}M2^n+\frac{1}{8}Q_{n-3}M2^n+\cdots+\frac{1}{2^n}Q_0M2^n$$

$$=\frac{1}{2}\left\{Q_{n-1}M2^n+\frac{1}{2}\left[Q_{n-2}M2^n+\frac{1}{2}\left(Q_{n-3}M2^n+\cdots+\frac{1}{2}\left(Q_1M2^n+\frac{1}{2}Q_0M2^n\right)\cdots\right)\right]\right\}$$