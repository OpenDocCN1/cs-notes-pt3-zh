```
function closure(I);
{ do { for (each item (A→α•Bβ,a) in I,
    each production B → γ in G`,
    and each terminal b in FIRST(βa)
    such that (B→•γ ,b) is not in I )
    add (B→•γ ,b) to I;
}while there is still new items add to I;
    return I
}
```