# Partition#1

```
Algorithm 6.5 Split
Input: An array of elements A[low..high].
Output: A with its elements rearranged and w the new position of the splitting element A[low].
1. i ← low
2. x ← A[low]
3. for j ← low + 1 to high
4.   if A[j] ≤ x then
5.     i ← i + 1
6.     if i ≠ j then interchange A[i] and A[j]
7.   end if
8. end for
9. interchange A[low] and A[i]
10. w ← i
11. return A and w
```