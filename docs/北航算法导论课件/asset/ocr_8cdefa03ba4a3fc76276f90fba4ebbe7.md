# Exam2 Multiplication of two integers (整数相乘)

two *n*-digit numbers X and Y, Complexity(X × Y) = ?

+   - Divide and Conquer algorithm

Let      X = a b
Y = c d

where *a*, *b*, *c* and *d* are *n*/2 digit numbers, e.g. 1364=13×10²+64.

Let *m* = *n*/2. Then

XY = (10^m a + b)(10^m c + d)
=10^{2m}ac + 10^m(bc + ad) + bd