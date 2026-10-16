# 16.3.3 Correctness of Huffman’s algorithm

+   Lemma 16.3 (optimal-substructure property)

C : {c₁, …, cₘ, x, y}, C′ : {c₁, …, cₘ, z},        T′ optimal ==> T optimal

![](bbox=[0.04, 0.32, 0.48, 0.58])

Here, B(T) = B(T′) + f[x] + f[y]

Suppose that T is not optimal, T″ is. Then B(T″) < B(T). Without loss of generality (by Lemma 16.2), T″ has x and y as siblings. Let T‴ be the tree T″ with the common parent of x and y replaced by a leaf z with frequency f[z]=f[x]+f[y]. Then B(T‴) = B(T″)-f[x]-f[y] < B(T)-f[x]-f[y] = B(T′), yielding a contradiction to the assumption that T′ represents an optimal prefix code for C′. Thus, T must represent an optimal prefix code for the alphabet C.

![](bbox=[0.04, 0.68, 0.48, 0.95])