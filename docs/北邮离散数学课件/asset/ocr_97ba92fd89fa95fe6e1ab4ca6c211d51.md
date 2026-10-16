# Analysis of Fibonacci Procedure

+   - **Theorem:** The preceding procedure for *fibonacci(n)* performs $f_{n+1}-1$ addition operations.
+     - **Proof:** By strong structural induction over $n$, based on the procedure’s own recursive definition.
+     - **Base cases:** *fibonacci(0)* performs 0 additions, and $f_{0+1}-1 = f_1 - 1 = 1 - 1 = 0$. Likewise, *fibonacci(1)* performs 0 additions, and $f_{1+1}-1 = f_2-1 = 1-1 = 0$.
+     - **Inductive step:** For $n>1$, by strong inductive hypothesis, *fibonacci(n-1)* and *fibonacci(n-2)* do $f_n-1$ and $f_{n-1}-1$ additions respectively, and *fibonacci(n)* adds 1 more, for a total of $f_n-1 + f_{n-1}-1 +1 = f_n + f_{n-1} -1 = f_{n+1}-1$. ■