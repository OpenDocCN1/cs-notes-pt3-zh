
## Example of Nested-Loop Join Costs

- Compute *student* ⨝ *takes*, with *student* as the outer relation.
- Let *takes* have a primary B⁺-tree index on the attribute *ID*, which contains 20 entries in each index node.
- Since *takes* has 10,000 tuples, the height of the tree is 4, and one more access is needed to find the actual data
- *student* has 5000 tuples
- Cost of block nested loops join
  - 400*100 + 100 = 40,100 block transfers + 2 * 100 = 200 seeks
    - assuming worst case memory
    - may be significantly less with more memory
- Cost of indexed nested loops join
  - 100 + 5000 * 5 = 25,100 block transfers and seeks.
  - CPU cost likely to be less than that for block nested loops join

## Merge-Join

- 1. Sort both relations on their join attribute (if not already sorted on the join attributes).
- 2. Merge the sorted relations to join them
  1. Join step is similar to the merge stage of the sort-merge algorithm.
  2. Main difference is handling of duplicate values in join attribute — every pair with same value on join attribute must be matched
- 3. Detailed algorithm in book

| a1 | a2 |
| --- | --- |
| a | 3 |
| b | 1 |
| d | 8 |
| d | 13 |
| f | 7 |
| m | 5 |
| q | 6 |

r
pr →

| a1 | a3 |
| --- | --- |
| a | A |
| b | G |
| c | L |
| d | N |
| m | B |

s
ps →

## Merge-Join (Cont.)

- Can be used only for equi-joins and natural joins
- Each block needs to be read only once (assuming all tuples for any given value of the join attributes fit in memory
- Thus the cost of merge join is:
  $b_r + b_s$ block transfers + $\lceil b_r / b_b \rceil + \lceil b_s / b_b \rceil$ seeks
  - + the cost of sorting if relations are unsorted.
- hybrid merge-join: If one relation is sorted, and the other has a secondary B⁺-tree index on the join attribute
  - Merge the sorted relation with the leaf entries of the B⁺-tree .
  - Sort the result on the addresses of the unsorted relation’s tuples
  - Scan the unsorted relation in physical address order and merge with previous result, to replace addresses by the actual tuples
    - Sequential scan more efficient than random lookup

## Hash-Join

- Applicable for equi-joins and natural joins.
- A hash function h is used to partition tuples of both relations
- h maps JoinAttrs values to {0, 1, ..., n}, where JoinAttrs denotes the common attributes of r and s used in the natural join.
  - r0, r1, . . ., rn denote partitions of r tuples
    - Each tuple tr ∈ r is put in partition ri where i = h(tr[JoinAttrs]).
  - r0, r1. . ., rn denotes partitions of s tuples
    - Each tuple ts ∈ s is put in partition si, where i = h(ts[JoinAttrs]).
- Note: In book, ri is denoted as Hri, si is denoted as Hsi and n is denoted as nh.

## Hash-Join (Cont.)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_610_0.png)

## Hash-Join algorithm (Cont.)

- The value *n* and the hash function *h* is chosen such that each *sᵢ* should fit in memory.
  - Typically n is chosen as ⌈bₛ/M⌉ * f where f is a “fudge factor”, typically around 1.2
  - The probe relation partitions *sⱼ* need not fit in memory
- **Recursive partitioning** required if number of partitions *n* is greater than number of pages *M* of memory.
  - instead of partitioning *n* ways, use *M − 1* partitions for s
  - Further partition the *M − 1* partitions using a different hash function
  - Use same partitioning method on *r*
  - Rarely required: e.g., with block size of 4 KB, recursive partitioning not needed for relations of < 1GB with memory size of 2MB, or relations of < 36 GB with memory of 12 MB

## Handling of Overflows

- Partitioning is said to be **skewed** if some partitions have significantly more tuples than some others
- **Hash-table overflow** occurs in partition sᵢ if sᵢ does not fit in memory. Reasons could be
  - Many tuples in s with same value for join attributes
  - Bad hash function
- **Overflow resolution** can be done in build phase
  - Partition sᵢ is further partitioned using different hash function.
  - Partition rᵢ must be similarly partitioned.
- **Overflow avoidance** performs partitioning carefully to avoid overflows during build phase
  - E.g. partition build relation into many partitions, then combine them
- Both approaches fail with large numbers of duplicates
  - Fallback option: use block nested loops join on overflowed partitions

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_614_0.png)
