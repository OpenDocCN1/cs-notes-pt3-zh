# Insertion Sort

*Insertion sort* begins with the 2nd element. It compares the 2nd element with the 1st and puts it before the first if it is not larger.

+   - Next the 3rd element is put into the correct position among the first 3 elements.
+   - In each subsequent pass, the n+1st element is put into its correct position among the first n+1 elements.
+   - Linear search is used to find the correct position.

```
procedure insertion sort
(a₁,...,aₙ:
    real numbers with n ≥ 2)
for j := 2 to n
    i := 1
    while aⱼ > aᵢ
        i := i + 1
    m := aⱼ
    for k := 0 to j − i − 1
        aⱼ₋k := aⱼ₋k₋1
    aᵢ := m
{Now a₁,...,aₙ is in increasing order}
```