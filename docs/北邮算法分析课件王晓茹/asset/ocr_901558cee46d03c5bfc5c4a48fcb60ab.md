# §2 Asymptotic Notation ( O, Ω, Θ, o ) 渐进性原理及表示符号

![](bbox=[0.08, 0.19, 0.18, 0.38])

The point of counting the steps is to predict the growth in run time as the N change, and thereby compare the time complexities of two programs. So what we really want to know is the asymptotic behavior of T_p.

Suppose T_p1(N) = c1 N² + c2 N and T_p2(N) = c3 N. Which one is faster?

No matter what c1, c2, and c3 are, there will be an n0 such that T_p1(N) > T_p2(N) for all N > n0.

![](bbox=[0.15, 0.75, 0.28, 0.98])

I see! So as long as I know that T_p1 is about N² and T_p2 is about N, then for sufficiently large N, P2 will be faster!