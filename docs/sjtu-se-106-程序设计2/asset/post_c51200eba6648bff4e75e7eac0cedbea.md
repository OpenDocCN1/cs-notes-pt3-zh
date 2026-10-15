
## 7、基数排序

- 1、基数排序：

e.g: B = 5、2、9、7、18、17、52 用基数排序法进行排序。

B = 2、52、5、7、17、18、9（第一次收集的结果）

![](img/af430dff16b82a0fe61ce7dee05dcf9c_349_0.png)

根据箭头所指向的数，进行分配动作，将其分配到相应的口袋。和第一次不同，这次根据右起第二位数字（十位数字）进行分配。

口袋：

| 口袋 | 数据 |
|------|------|
| B₀ | 2、5、7、9 |
| B₁ | 17、18 |
| B₂ |  |
| B₃ |  |
| B₄ |  |
| B₅ | 52 |
| B₆ |  |
| B₇ |  |
| B₈ |  |
| B₉ |  |

分配完毕，按照红色箭头所指的方向进行第二次收集动作。注意：收集后的序列已经按照右起第一位（个位数字）、右起第二位（十位数字）排好序了。

收集后的序列：2、5、7、9、17、18、52 已是排好序的序列。

## Radix Sort

- *Can we prove it will work?*
- Inductive argument:
  - Assume lower-order digits {j: j<i} are sorted
  - Show that sorting next digit i leaves array correctly sorted
    - If two digits at position i are different, ordering numbers by that digit is correct (lower-order digits irrelevant)
    - If they are the same, numbers are already sorted on the lower-order digits. Since we use a stable sort, the numbers stay in the right order

## Radix Sort

- *What sort will we use to sort on digits?*
- Bucket sort is a good choice:
  - Sort *n* numbers on digits that range from 1..*N*
  - Time: O(*n* + *N*)
- Each pass over *n* numbers with *d* digits takes time O(*n*+*k*), so total time O(*d n*+*d k*)
  - When *d* is constant and *k*=O(*n*), takes O(*n*) time

## Radix Sort Example

- **Problem: sort 1 million 64-bit numbers**
  - Treat as four-digit radix 2^16 numbers
  - Can sort in just four passes with radix sort!
  - Running time: 4(1 million + 2^16) ≈ 4 million operations
- **Compare with typical O(n lg n) comparison sort**
  - Requires approx lg n = 20 operations per number being sorted
  - Total running time ≈ 20 million operations

## Radix Sort

- In general, radix sort based on bucket sort is
  - Asymptotically fast (i.e., O(n))
  - Simple to code
  - A good choice
- *Can radix sort be used on floating-point numbers?*

## Summary: Radix Sort

- Radix sort:
  - Assumption: input has *d* digits ranging from 0 to *k*
  - Basic idea:
    - Sort elements by digit starting with *least* significant
    - Use a stable sort (like bucket sort) for each stage
  - Each pass over *n* numbers with 1 digit takes time O(*n*+*k*), so total time O(*d n*+*d k*)
    - When *d* is constant and *k*=O(*n*), takes O(*n*) time
  - Fast, Stable, Simple
  - Doesn’t sort in place

## Sorting Algorithms: Running Time

- Assuming an input sequence of length n
  - Bubble sort
  - Insertion sort
  - Selection sort
  - Merge sort
  - Quick sort
  - Bucket sort
  - Radix sort

## Sorting Algorithms: In-Place Sorting

- A sorting algorithm is said to be *in-place* if
  - it uses no auxiliary data structures (however, O(1) auxiliary variables are allowed)
  - it updates the input sequence only by means of operations replaceElement and swapElements
- Which sorting algorithms seen so far can be made to work in place?
  - Bubble, Insertion, Selection, Merge, Quick, Bucket, Radix
