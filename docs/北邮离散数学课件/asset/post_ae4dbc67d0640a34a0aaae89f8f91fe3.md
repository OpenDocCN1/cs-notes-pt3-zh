
## Complexity Analysis of Algorithms

Example: Describe the time complexity of the algorithm for finding the maximum element in a finite sequence.

```
procedure max(a1, a2, ..., an; integers)
max := a1
for i := 2 to n
if max < ai then max := ai
return max
{max is the largest element}
```

Solution: Count the number of comparisons.

- The max < ai comparison is made n − 1 times.
- Each time i is incremented, a test is made to see if i ≤ n.
- One last comparison determines that i > n.
- Exactly 2(n − 1) + 1 = 2n − 1 comparisons are made.

Hence, the time complexity of the algorithm is Θ(n).

## Worst-Case Complexity of Linear Search

Example: Determine the time complexity of the linear search algorithm.

```
procedure linear search(x:integer,
    a₁, a₂, ..., aₙ: distinct integers)
    i := 1
    while (i ≤ n and x ≠ aᵢ)
        i := i + 1
    if i ≤ n then location := i
    else location := 0
    return location{location is the subscript of the term that equals x, or is 0 if x is not found}
```

Solution: Count the number of comparisons.

- At each step two comparisons are made; i ≤ n and x ≠ aᵢ.
- To end the loop, one comparison i ≤ n is made.
- After the loop, one more i ≤ n comparison is made.

If x = aᵢ, 2i + 1 comparisons are used. If x is not on the list, 2n + 1 comparisons are made and then an additional comparison is used to exit the loop. So, in the worst case 2n + 2 comparisons are made. Hence, the complexity is Θ(n).

## Average-Case Complexity of Linear Search

**Example:** Describe the average case performance of the linear search algorithm. (Although usually it is very difficult to determine average-case complexity, it is easy for linear search.)

**Solution:** Assume the element is in the list and that the possible positions are equally likely. By the argument on the previous slide, if $x = a_i$, the number of comparisons is $2i + 1$.

$$\frac{3+5+7+...+(2n+1)}{n} = \frac{2(1+2+3+...+n)+n}{n} =$$

$$\frac{2\left[\frac{n(n+1)}{2}\right]}{n} + 1 = n + 2$$

Hence, the average-case complexity of linear search is $\Theta(n)$.

## Worst-Case Complexity of Binary Search

Example: Describe the time complexity of binary search in terms of the number of comparisons used.

```
procedure binary search(x: integer, a₁,a₂,...,aₙ: increasing integers)
 i := 1 {i is the left endpoint of interval}
 j := n {j is right endpoint of interval}
 while i < j
  m := ⌊(i + j)/2⌋
  if x > aₘ then i := m + 1
  else j := m
 if x = aᵢ then location := i
 else location := 0
 return location{location is the subscript i of the term aᵢ equal to x, or 0 if x is not found}
```

Solution: Assume (for simplicity) n = 2ᵏ elements. Note that k = log n.

- Two comparisons are made at each stage; i < j, and x > aₘ.
- At the first iteration the size of the list is 2ᵏ and after the first iteration it is 2ᵏ⁻¹. Then 2ᵏ⁻² and so on until the size of the list is 2¹ = 2.
- At the last step, a comparison tells us that the size of the list is the size is 2⁰ = 1 and the element is compared with the single remaining element.
- Hence, at most 2k + 2 = 2 log n + 2 comparisons are made.
- Therefore, the time complexity is Θ(log n), better than linear search.

## Worst-Case Complexity of Bubble Sort

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

## Worst-Case Complexity of Insertion Sort

Example: What is the worst-case complexity of insertion sort in terms of the number of comparisons made?

Solution: The total number of comparisons are: 2 + 3 + ⋯ + n = n(n-1)/2 - 1

Therefore the complexity is Θ(n²).

```
procedure insertion sort(a1,...,an: real numbers with n ≥ 2)
for j := 2 to n
i := 1
while aj > ai
i := i + 1
m := aj
for k := 0 to j - i - 1
a_{j-k} := a_{j-k-1}
ai := m
```
