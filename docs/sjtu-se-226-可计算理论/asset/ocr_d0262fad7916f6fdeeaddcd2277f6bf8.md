# Effective Denumerable Set

4. If x > 0 then it has a unique expression as

x = 2^{a1} + 2^{a1+a2+1} + ... + 2^{a1+a2+...+a_{k-1}}.

The function a(i,x) = a_i is primitive recursive:

a(i,x) = b(i,x), if i = 0 or i = 1,
a(i + 1,x) = (b(i + 1,x) - b(i,x)) - 1, if i ≥ 1.

We conclude that a1, a2, a3, ..., a_k can be calculated by primitive recursive functions.