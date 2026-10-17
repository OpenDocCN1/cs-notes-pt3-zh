# Rules for →

# ▪ **Introduction rule:** →I

```
[A]
⋮
B
-----------
A → B
```

▪ **If Γ, A ⊢ B, then Γ ⊢ A → B**
  ▸ We may drop any number of assumptions equal to A from the proof of A.

# ▪ **Elimination rule:** →e

```
A → B        A
----------------
       B
```

▪ **If Γ ⊢ A → B and Γ ⊢ A, then Γ ⊢ B**