# Recursive Merge Sort

```
procedure sort(L = ℓ₁, ..., ℓₙ)
  if n>1 then
    m := ⌊n/2⌋ {this is rough ½-way point}
    L := merge(sort(ℓ₁, ..., ℓₘ),
               sort(ℓₘ₊₁, ..., ℓₙ))
  return L
```

+   - The merge (next slide) takes Θ(n) steps, and merge-sort takes Θ(n log n).