# Property of Counting Sort

+   - Counting sort doesn’t sort in place
+   - Counting sort is stable
+     - That is, the same value appear in the output array in the same order as they do in the input array.

# Radix Sort Algorithm

+   - Idea of Radix sort algorithm
+     - Use stable sort algorithm
+     - Sort the n d-digit elements from the lowest digit to the highest digit

| 329 | 720 | 720 | 329 |
| 457 | 355 | 329 | 355 |
| 657 | 436 | 436 | 436 |
| 818 | 457 | 839 | 457 |
| 436 | 657 | 355 | 657 |
| 720 | 329 | 457 | 720 |
| 355 | 839 | 657 | 839 |

+   - Radix sort algorithm
+     - Input: Array A, each element is a number of d digit.
+     - Radix-Sort(A, d)
+     - for i ← 1 to d do
+     - use a stable sort to sort array A on digit i;

+   - Time complexity of Radix sort algorithm
+     - Using Counting sort algorithm, 0 ≤ A[i] ≤ k-1
+     - The time complexity is O(d(n+k))

+   - Extension of Radix sort
+     - Input: n b-digit number, any r ≤ b
+     - Radix sort can sort these numbers in Θ(b/r)(n + 2^r)
+     - Why
+       - View each number as d[⌊b/r⌋] digits of r bits each.
+       - Each digit is an integer in the range 0 to 2^r -1
+       - Use counting sort with k= 2^r -1

# Bucket Sort

+   - Assumption of Bucket Sort
+     - Input is elements uniformly distributed in [0, 1)
+   - Idea of Bucket Sort
+     - Divide [0, 1) into n equal-sized bucket
+     - Distribute the input into the n bucket
+     - Sort the numbers in each bucket
+     - List all the sorted numbers in each bucket in order

A | B
.78 | 0 /
.17 | 1 | .12 | .17
.39 | 2 | .21 | .23 | .26
.26 | 3 | .39
.72 | 4 /
.94 | 5 /
.21 | 6 | .68
.12 | 7 | .72 | .78
.23 | 8 /
.68 | 9 | .94

+   - Bucket Sort Algorithm
+     - Bucket-Sort(A)
+     1. n=length[A];
+     2. For i=1 To n Do
+     3. Insert A[i] into list B[⌊nA[i]⌋];
+     4. For i=0 To n-1 Do
+     5. Sort list B[i] with insert sort;
+     6. concatenate lists B[0], ..., B[n-1]

A | B
.78 | 0 /
.39 | 1 | .12 | .17
.26 | 2 | .21 | .23 | .26
.72 | 3 | .39
.94 | 4 /
.21 | 6 | .68
.12 | 7 | .72 | .78
.23 | 8 /
.68 | 9 | .94