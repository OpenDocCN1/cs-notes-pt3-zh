# 16.3.3 Correctness of Huffman's algorithm

![](bbox=[0.13, 0.18, 0.38, 0.24])

![](bbox=[0.35, 0.13, 0.98, 0.33])

# Lemma 16.2

c ∈ C has frequency f[c]. x , y ∈ C, having the lowest frequencies. Then, exist an optimal prefix code for C in which the codewords for x and y have the same length and differ only in the last bit.

B(T) = Σ_{c∈C} f(c) d_T(c) (16.5)

# Proof : Let a and b are sibling leaves of maximum depth in optimal T. Assume that f[a]≤f[b], f[x]≤f[y]. f[x] and f[y] are the two lowest leaf frequencies, f[a], f[b] are two arbitrary frequencies, in order, ⇒ f[x]≤f[a], f[y]≤f[b]. Exchange the positions in T of a and x to produce a tree T', and then exchange the positions in T' of b and y to produce a tree T''. By (16.5), we have

B(T) − B(T') = Σ_{c∈C} f(c) d_T(c) − Σ_{c∈C} f(c) d_{T'}(c)
= f[x] d_T(x) + f[a] d_T(a) − f[x] d_{T'}(x) − f[a] d_{T'}(a)
= f[x] d_T(x) + f[a] d_T(a) − f[x] d_T(a) − f[a] d_T(x)
= (f[x] − f[a]) d_T(x) + (f[a] − f[x]) d_T(a)
= (f[a] − f[x]) (d_T(a) − d_T(x)) ≥ 0

Similarly, B(T') − B(T'') ≥ 0, therefore, B(T'') ≤ B(T).
Since T is optimal, B(T) ≤ B(T'').
Then B(T'') = B(T).
Thus, T'' is an optimal tree.