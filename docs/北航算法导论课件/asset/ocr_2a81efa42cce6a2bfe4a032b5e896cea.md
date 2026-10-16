# 5.3.2 Randomly permuting an array

# (2) RANDOMIZE-IN-PLACE

```
RANDOMIZE-IN-PLACE(A, n)
for (i=1; i<=n; i++)
    swap(A[i], A[RANDOM(i, n)])
```

Lemma  RANDOMIZE-IN-PLACE computes a uniform random permutation.

**Proof**  **Loop invariant:** Pr{A[1 . . i−1] contains each (i−1)-permutation} = (n−i+1)!/n!.

+   - **Termination:**

At termination, i=n+1, it is true prior to the ith iteration, so we conclude that A[i . . n] is a given n-permutation with probability (n−n)!/n! = 1/n!.

■ (lemma)