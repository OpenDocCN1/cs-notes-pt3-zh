
## Where are we?

- Merge sort
- Quick sort

## Quick sort

Quicksort honored as one of the top 10 algorithms of the 20th century in science and engineering.

## Mergesort

- Java sort for objects.
- Perl, C++ stable sort, Python stable sort, Firefox JavaScript, ...

## Quicksort

- Java sort for primitive types.
- C `qsort`, Unix, Visual C++, Python, MATLAB, Chrome JavaScript, ...

## Quick sort

- Shuffle the array.
- Partition so that, for some `j`:
  - Entry `a[j]` is in place.
  - No larger entry to the left of `j`.
  - No smaller entry to the right of `j`.
- Sort each piece recursively.

## Partition #1

```text
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

## Partition #1

10  
*i*  
13  
*j*  
6  
24  
43  
1  
51  
9

## Partition #2

- By Sedgewick

```java
private static int partition(Comparable[] a, int lo, int hi)
{
    int i = lo, j = hi+1;
    while (true)
    {
        while (less(a[++i], a[lo]))
            if (i == hi) break;

        while (less(a[lo], a[--j]))
            if (j == lo) break;

        if (i >= j) break;
        exch(a, i, j);
    }

    exch(a, lo, j);
    return j;
}
```

## Complexity

Best case: array always split into two equal-sized subarrays, similar to mergesort, `O(N log N)`.

Worst case: array always split into a 0-sized and an `N - 1`-sized subarray, similar to selection sort, `O(N²)`.

Average case:

`C_N = (N + 1) + (C_0 + C_{N-1})/N + (C_1 + C_{N-2})/N + ... + (C_{N-1} + C_0)/N`

`C_N ~ 2(N + 1) ln N ≈ 1.39 N lg N`

## Complexity

- Laptop executes `10⁸` compares/second.
- Supercomputer executes `10¹²` compares/second.

|  | Insertion sort (`N²`) |  |  | Mergesort (`N log N`) |  |  | Quicksort (`N log N`) |  |  |
|---|---|---|---|---|---|---|---|---|---|
| Compute | Thousand | Million | Billion | Thousand | Million | Billion | Thousand | Million | Billion |
| Home | Instant | 2.8 hours | 317 years | Instant | 1 second | 18 min | Instant | 0.6 sec | 12 min |
| Super | Instant | 1 second | 1 week | Instant | Instant | Instant | Instant | Instant | Instant |

*Good algorithms are better than supercomputers.*

*Great algorithms are better than good algorithms.*

## Duplicate keys

Chicago 09:25:52  
Chicago 09:03:13  
Chicago 09:21:05  
Chicago 09:19:46  
Chicago 09:19:32  
Chicago 09:00:00  
Chicago 09:35:21  
Chicago 09:00:59  
Houston 09:01:10  
Houston 09:00:13  
Phoenix 09:37:44  
Phoenix 09:00:03  
Phoenix 09:14:25  
Seattle 09:10:25  
Seattle 09:36:14  
Seattle 09:22:43  
Seattle 09:10:11  
Seattle 09:22:54

B A A B A B B B C C C  
A A A A A A A A A A A

Dijkstra’s 3-way partition

## Quiz

Give the array that results after applying quicksort partitioning to the following array by using:

- a) Partition #1
- b) Partition #2
- c) Dijkstra’s 3-way partition

`H J B R H R H B C V S`

- A. `C B H H B H R J R V S`
- B. `H C B B H H R R J V S`
- C. `C B B H H H R R V S J`
- D. None of the above

## Sort summary

|  | In-place? | Stable? | Worst | Average | Best | Remarks |
|---|---|---|---|---|---|---|
| Selection | x |  | N² / 2 | N² / 2 | N² / 2 | N exchanges |
| Insertion | x | x | N² / 2 | N² / 4 | N | Use for small N or partially ordered |
| Shell | x |  | ? | ? | N | Tight code, subquadratic |
| Quick | x |  | N² / 2 | 2 N ln N | N lg N | N log N probabilistic guarantee; fastest in practice |
| 3-way quick | x |  | N² / 2 | 2 N ln N | N | Improves quicksort in the presence of duplicate keys |
| Merge |  | x | N lg N | N lg N | N lg N | N log N guarantee, stable |

## Exercise

- Download `hw4.pdf` from our course homepage.
- Due next Tuesday.
