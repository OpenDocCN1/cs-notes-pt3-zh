# Worst-Case Complexity of Bubble Sort

**Example:** What is the worst-case complexity of bubble sort in terms of the number of comparisons made?

```
procedure bubblesort(a₁,...,aₙ: real numbers
with n ≥ 2)
  for i := 1 to n−1
    for j := 1 to n − i
      if aⱼ > aⱼ₊₁ then interchange aⱼ and aⱼ₊₁
{a₁,..., aₙ is now in increasing order}
```

**Solution:** A sequence of n−1 passes is made through the list. On each pass n − i comparisons are made.

(n − 1) + (n − 2) + ... + 2 + 1 = n(n−1)/2

The worst-case complexity of bubble sort is Θ(n²) since n(n−1)/2 = ½ n² − ½ n.