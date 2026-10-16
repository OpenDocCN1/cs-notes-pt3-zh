
## B⁺-Tree Node Structure

+   Typical node

| P₁ | K₁ | P₂ | ... | Pₙ₋₁ | Kₙ₋₁ | Pₙ |

+   Kᵢ are the search-key values

+   Pᵢ are pointers to children (for non-leaf nodes) or pointers to records or buckets of records (for leaf nodes).

+   The search-keys in a node are ordered

+   K₁ < K₂ < K₃ < ... < Kₙ₋₁

+   (Initially assume no duplicate keys, address duplicates later)

## Leaf Nodes in B⁺-Trees

Properties of a leaf node:

- For i = 1, 2, . . . , n−1, pointer P_i points to a file record with search-key value K_i,
- If L_i, L_j are leaf nodes and i < j, L_i’s search-key values are less than or equal to L_j’s search-key values
- P_n points to next leaf node in search-key order

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_508_0.png)

## Non-Leaf Nodes in B⁺-Trees

Non leaf nodes form a multi-level sparse index on the leaf nodes. For a non-leaf node with m pointers:

- All the search-keys in the subtree to which P₁ points are less than K₁
- For 2 ≤ i ≤ n − 1, all the search-keys in the subtree to which Pᵢ points have values greater than or equal to Kᵢ₋₁ and less than Kᵢ
- All the search-keys in the subtree to which Pₙ points have values greater than or equal to Kₙ₋₁

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_509_0.png)

## Example of B⁺-tree

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_510_0.png)

B⁺-tree for *instructor* file (n = 6)

- Leaf nodes must have between 3 and 5 values (⌈(n−1)/2⌉ and n −1, with n = 6).
- Non-leaf nodes other than root must have between 3 and 6 children (⌈(n/2)⌉ and n with n =6).
- Root must have at least 2 children.

## Observations about B⁺-trees

- Since the inter-node connections are done by pointers, “logically” close blocks need not be “physically” close.
- The non-leaf levels of the B⁺-tree form a hierarchy of sparse indices.
- The B⁺-tree contains a relatively small number of levels
  - Level below root has at least 2* ⌈n/2⌉ values
  - Next level has at least 2* ⌈n/2⌉ * ⌈n/2⌉ values
  - .. etc.
  - If there are K search-key values in the file, the tree height is no more than ⌈log⌊n/2⌋(K)⌉
  - thus searches can be conducted efficiently.
- Insertions and deletions to the main file can be handled efficiently, as the index can be restructured in logarithmic time (as we shall see).

## Queries on B⁺-Trees

Find record with search-key value V.

+   1. C=root
+   2. While C is not a leaf node {
+      1. Let i be least value s.t. V ≤ Kᵢ.
+      2. If no such exists, set C = last non-null pointer in C
+      3. Else { if (V= Kᵢ ) Set C = Pᵢ₊₁ else set C = Pᵢ }
+      }
+   3. Let i be least value s.t. Kᵢ = V
+   4. If there is such a value i, follow pointer Pᵢ to the desired record.
+   5. Else no record with search-key value k exists.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_512_0.png)

## Handling Duplicates

- With duplicate search keys
  - In both leaf and internal nodes,
    - we cannot guarantee that $K_1 < K_2 < K_3 < \ldots < K_{n-1}$
    - but can guarantee $K_1 \leq K_2 \leq K_3 \leq \ldots \leq K_{n-1}$
  - Search-keys in the subtree to which $P_i$ points
    - are $\leq K_i$, but not necessarily $< K_i$,
    - To see why, suppose same search key value $V$ is present in two leaf node $L_i$ and $L_{i+1}$. Then in parent node $K_i$ must be equal to $V$

## Handling Duplicates

- We modify find procedure as follows
  - traverse P_i even if V = K_i
  - As soon as we reach a leaf node C check if C has only search key values less than V
    - if so set C = right sibling of C before checking whether C contains V

- Procedure printAll
  - uses modified find procedure to find first occurrence of V
  - Traverse through consecutive leaves to find all occurrences of V

** Errata note: modified find procedure missing in first printing of 6th edition

## Queries on B⁺-Trees (Cont.)

- If there are K search-key values in the file, the height of the tree is no more than ⌈log⌊n/2⌋(K)⌉.
- A node is generally the same size as a disk block, typically 4 kilobytes
  - and n is typically around 100 (40 bytes per index entry).
- With 1 million search key values and n = 100
  - at most log₅₀(1,000,000) = 4 nodes are accessed in a lookup.
- Contrast this with a balanced binary tree with 1 million search key values — around 20 nodes are accessed in a lookup
  - above difference is significant since every node access may need a disk I/O, costing around 20 milliseconds
