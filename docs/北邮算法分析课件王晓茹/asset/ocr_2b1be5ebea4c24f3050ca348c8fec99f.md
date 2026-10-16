# # 一个例子

n=3, c=6, w={4, 3, 2}, v={5, 2, 1} 。

m(i,j) = \begin{cases} \max \{m(i+1,j), m(i+1,j-w_i)+v_i\} & j \geq w_i \\ m(i+1,j) & 0 \leq j < w_i \end{cases}

![](bbox=[0.141, 0.188, 0.909, 0.962])