# 4 Recurrences

A recurrence is an **equation or inequality** in terms of

+   - one or more base cases, and
+   - itself, with smaller arguments.

# Examples:

(1) $T(n)=\begin{cases}1 & ,\text{if } n=1,\\ T(n-1)+1 & ,\text{if } n>1.\end{cases}$
Solution: $T(n)=n.$

(2) $T(n)=\begin{cases}1 & ,\text{if } n=1,\\ 2T(n/2)+n & ,\text{if } n>1.\end{cases}$
Solution: $T(n)=n\lg n+n.$

(3) $T(n)=\begin{cases}0 & ,\text{if } n=2,\\ T(\sqrt{n})+1 & ,\text{if } n>2.\end{cases}$
Solution: $T(n)=\lg\lg n.$

(4) $T(n)=\begin{cases}1 & ,\text{if } n=1,\\ T(n/3)+T(2n/3)+n & ,\text{if } n>1.\end{cases}$
Solution: $T(n)=\Theta(n\lg n)$