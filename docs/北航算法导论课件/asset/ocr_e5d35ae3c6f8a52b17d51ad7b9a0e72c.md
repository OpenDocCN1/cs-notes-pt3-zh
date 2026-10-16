# 3 Growth of Functions

Θ(nlgn) beats Θ(n²)? How’s 100nlgn vs 3n² (n = 2)?

We say n →∞, merge sort, Θ(nlgn), beats insertion sort, Θ(n²).

# Overview

+   - A way to describe behavior of functions in the limit. We’re studying asymptotic efficiency.（函数的渐近效率，即极限情况下的函数行为）
+   - Describe growth of functions（函数增长率的描述）
+   - Focus on what’s important by abstracting away low-order terms and constant factors.（通常忽略低阶项和常数因子）
+   - How we indicate running times of algorithms.（如何描述算法的运算时间）
+   - A way to compare “sizes” of funcitons（比较函数大小的方法）

o ≈ < ; O ≈ ≤ ; Θ ≈ = ; Ω ≈ ≥ ; ω ≈ >