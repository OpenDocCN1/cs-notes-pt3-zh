

## Height of a red-black tree

**Theorem.** A red-black tree with n keys has height \(h \le 2 \lg(n + 1)\).

**Proof.** (The book uses induction. Read carefully.)

### INTUITION:

- Merge red nodes into their black parents.
- This process produces a tree in which each node has 2, 3, or 4 children.
- The 2-3-4 tree has uniform depth \(h'\) of leaves.

![](img/5e59105b951890406cf98b2a964cb2f9_445_0.png)

### Proof (continued)

- We have \(h' \ge h/2\), since at most half the leaves on any path are red.
- The number of leaves in each tree is \(n+1\)
  - \(\Rightarrow n+1 \ge 2^{h'}\)
  - \(\Rightarrow \lg(n+1) \ge h' \ge h/2\)
  - \(\Rightarrow h \le 2\lg(n+1)\).

![](img/5e59105b951890406cf98b2a964cb2f9_446_0.png)

## Modifying operations

The operations **INSERT** and **DELETE** cause modifications to the red-black tree:

- the operation itself,
- color changes,
- restructuring the links of the tree via “rotations.”

## Insertion into a red-black tree

**IDEA:** Insert *x* in tree. Color *x* red. Only red-black property 3 might be violated. Move the violation up the tree by recoloring until it can be fixed with rotations and recoloring.

### Example:

![](img/5e59105b951890406cf98b2a964cb2f9_450_0.png)

## Insertion into a red-black tree

**IDEA:** Insert *x* in tree. Color *x* red. Only red-black property **3** might be violated. Move the violation up the tree by recoloring until it can be fixed with rotations and recoloring.

### Example:

- Insert *x* = 15.
- Recolor, moving the violation up the tree.

![](img/5e59105b951890406cf98b2a964cb2f9_451_0.png)

## Insertion into a red-black tree

**IDEA:** Insert _x_ in tree. Color _x_ red. Only red-black property 3 might be violated. Move the violation up the tree by recoloring until it can be fixed with rotations and recoloring.

### Example:

- Insert _x_=15.
- Recolor, moving the violation up the tree.
- RIGHT-ROTATE(18).

![](img/5e59105b951890406cf98b2a964cb2f9_452_0.png)

## Insertion into a red-black tree

**IDEA:** Insert _x_ in tree. Color _x_ red. Only red-black property 3 might be violated. Move the violation up the tree by recoloring until it can be fixed with rotations and recoloring.

### Example:

- Insert _x_ = 15.
- Recolor, moving the violation up the tree.
- RIGHT-ROTATE(18).
- LEFT-ROTATE(7) and recolor.

![](img/5e59105b951890406cf98b2a964cb2f9_454_0.png)

## Graphical notation

Let ▲ denote a subtree with a black root.

All ▲’s have the same black-height.

## Case 1

![](img/5e59105b951890406cf98b2a964cb2f9_457_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_457_1.png)

Recolor

> (Or, children of A are swapped.)

Push C's black onto A and D, and recurse, since C's parent may be red.

new x

## Case 2

![](img/5e59105b951890406cf98b2a964cb2f9_458_0.png)

# LEFT-ROTATE(A)

Transform to Case 3.

## Analysis

- Go up the tree performing Case 1, which only recolors nodes.
- If Case 2 or Case 3 occurs, perform 1 or 2 rotations, and terminate.

**Running time:** _O_(lg _n_) with _O_(1) rotations.
RB-DELETE — same asymptotic running time and number of rotations as RB-INSERT (see textbook).

## Introduction to Algorithms

6.046J/18.401J

![](img/5e59105b951890406cf98b2a964cb2f9_461_0.png)

### LECTURE 11

### Augmenting Data Structures

- Dynamic order statistics
- Methodology
- Interval trees

Prof. Charles E. Leiserson

## Dynamic order statistics

OS-SELECT(_i_, _S_): returns the _i_th smallest element in the dynamic set _S_.

OS-RANK(_x_, _S_): returns the rank of \(x \in S\) in the sorted order of _S_’s elements.

**IDEA:** Use a red-black tree for the set _S_, but keep subtree sizes in the nodes.

Notation for nodes:

![](img/5e59105b951890406cf98b2a964cb2f9_462_0.png)

