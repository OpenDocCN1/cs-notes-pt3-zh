# 5.3.2 Randomly permuting an array

# (2) RANDOMIZE-IN-PLACE

```
RANDOMIZE-IN-PLACE(A, n)
for (i=1; i<=n; i++)
    swap(A[i], A[RANDOM(i, n)])
```

Lemma  RANDOMIZE-IN-PLACE computes a uniform random permutation.

Proof  Loop invariant: Pr{A[1..i-1] contains each (i-1)-permutation} = (n-i+1)!/n!.

+   - **Maintenance:**

… …

Pr{E₂ ∩ E₁} = Pr{E₂|E₁} Pr{E₁}.

The algorithm choose xᵢ randomly from the n-i+1 possibilities in A[i..n] => Pr{E₂|E₁} = 1/(n-i+1)? Thus,

| i | i+1 | … | n |
|---|---|---|---|
| A(jᵢ) | A(jᵢ₊₁) | … | A(jₙ) |

Pr{E₂ ∩ E₁} = Pr{E₂|E₁} Pr{E₁}

= 1/(n-i+1) · (n-i+1)!/n! = (n-i)!/n!