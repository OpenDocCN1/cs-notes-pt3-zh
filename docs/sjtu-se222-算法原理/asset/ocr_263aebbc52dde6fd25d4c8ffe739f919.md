# Binary searching

2, 4, 5, 6, 8, 9, 9, 12, 25, 30, 44, 56, 67, 93, 96

mid

low

high

```
Algorithm 1.2 BinarySearch
Input: An array A[1..n] of n elements sorted in nondecreasing order and an element x.
Output: j if x = A[j], 1 ≤ j ≤ n, and 0 otherwise.
1. low ← 1; high ← n; j ← 0
2. while low ≤ high and j = 0
3.   mid ← ⌊(low + high)/2⌋
4.   if x = A[mid] then j ← mid
5.   else if x < A[mid] then high ← mid − 1
6.   else low ← mid + 1
7. end while
8. return j
```