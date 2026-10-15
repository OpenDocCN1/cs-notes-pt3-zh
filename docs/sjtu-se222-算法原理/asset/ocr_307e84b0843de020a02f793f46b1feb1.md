```
Procedure cp(low, high)
1. p ← high − low + 1
2. if high − low + 1 ≤ 3 then compute δ
3. else
4.   mid ← ⌊(low + high)/2⌋
5.   x₀ ← x(S[mid])
6.   δₗ ← cp(low, mid)
7.   δᵣ ← cp(mid + 1, high)
8.   δ ← min{δₗ, δᵣ}
9.   k ← 0
10.  for i ← 1 to n
11.    if |x(Y[i]) − x₀| ≤ δ then
12.      k ← k + 1; T[k] ← Y[i] end if
13.  end for
14.  δ′ ← δ
15.  for i ← 1 to k − 1
16.    for j ← i + 1 to min{i + 7, k}
17.      if d′(T[i], T[j]) < δ′ then δ′ ← d′(T[i], T[j])
18.    end for
19.  end for
20. end if
21. return δ′
```