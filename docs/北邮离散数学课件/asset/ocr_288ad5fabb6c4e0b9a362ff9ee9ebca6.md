# Why that Algorithm Works

+   - Note that:
+     $b^n = b^{n_{k-1}2^{k-1}+n_{k-2}2^{k-2}+...+n_0 2^0}$
+     $= (b^{2^{k-1}})^{n_{k-1}} \times (b^{2^{k-2}})^{n_{k-2}} \times ... \times (b^{2^0})^{n_0}$
+     The binary expansion of $n$
+     $\underbrace{= b^1 = b}$

+   - We can compute $b$ to various powers of 2 by repeated squaring.
+     - Then multiply them into the partial product, or not, depending on whether the corresponding $n_i$ bit is 1.

+   - Crucially, we can do the **mod** $m$ operations as we go along, because of the various identity laws of modular arithmetic. — All the numbers stay small.