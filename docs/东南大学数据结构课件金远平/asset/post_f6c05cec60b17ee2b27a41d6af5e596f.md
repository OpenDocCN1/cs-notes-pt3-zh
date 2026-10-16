
# 10.2 AVL Trees

**Dynamic** collections of elements may also be maintained as binary search trees.
Fig. 10.8 shows the binary search tree obtained by entering the months JAN to DEC into an initially empty binary search tree by using function **Insert** (Program 5.21).

![](img/15e8d7d94d8ddf02cb6839870195a31e_766_0.png)

**Comparisons:**  
**Maximum:** 6  
**Average:** 3.5

Fig. 10.8

Fig. 10.9 shows the binary search tree obtained by entering JULY, FEB, MAY, AUG, DEC, MAR, OCT, APR, JAN, JUNE, SEPT, NOV into an initially empty binary search tree.

Comparisons:
Maximum: 4
Average: 3.1
Balanced

Fig. 10.9

Fig. 10.10 shows the binary search tree obtained
by entering the months in lexicographic order into
an initially empty binary search tree.

![](img/15e8d7d94d8ddf02cb6839870195a31e_770_0.png)

Comparisons:
Maximum: 12
Average: 6.5

# Fig. 10.10

With equal search probabilities for keys, both the maximum and average search time will be minimized if the binary search tree is maintained as a complete binary tree at all times.

However, since the dynamic situation, it is difficult to achieve this without making the time required to insert a key very high.

It is, however, possible to keep the tree balanced to ensure both average and worst-case retrieval time of O(log n) for a tree with n nodes.

AVL tree (introduced by Adelson-Velskii and Landis) is a binary search tree that is balanced with respect to the heights of subtrees.

Definition: an empty tree is height-balanced. If T is a nonempty binary tree with T_L and T_R as its left and right subtrees respectively, then T is height-balanced iff

+   (1) T_L and T_R are height-balanced and

+   (2) | h_L - h_R | ≤ 1 where h_L and h_R are the heights of T_L and T_R respectively.

Fig. 10.8 is not height-balanced.

Fig. 10.9 is height-balanced.

Fig. 10.10 is not height-balanced.

**Definition**: The balance factor, BF(T), of a node T in a binary tree is defined to be h_L - h_R . For any node T in an AVL tree BF(T)=-1, 0, or 1.

To illustrate the processes involved in maintaining an AVL tree, let’s insert MAR, MAY, NOV, AUG, APR, JAN, DEC, JULY and FEB into an empty tree.

The following show the tree as it grows and restructuring involved in keeping it balanced. The numbers above each node represent the balance factor of that node.

![](img/15e8d7d94d8ddf02cb6839870195a31e_775_0.png)

(a) Insert MAR

(b) Insert MAY

RR →

(c) Insert NOV

![](img/15e8d7d94d8ddf02cb6839870195a31e_777_0.png)

(d) Insert AUG

![](img/15e8d7d94d8ddf02cb6839870195a31e_778_0.png)

![](img/15e8d7d94d8ddf02cb6839870195a31e_778_1.png)

![](img/15e8d7d94d8ddf02cb6839870195a31e_778_2.png)

(e) Insert APR

(f) Insert JAN

![](img/15e8d7d94d8ddf02cb6839870195a31e_780_0.png)

(g) Insert DEC

(h) Insert JULY

![](img/15e8d7d94d8ddf02cb6839870195a31e_782_0.png)

(i) Insert FEB

In the proceeding example we saw that the addition of a node to a balanced binary search tree could unbalance it.

The rebalancing uses essentially 4 kinds of rotations:

LL, RR, LR, and RL.

LL and RR are symmetric, as are LR and RL.

The rotations are characterized by the nearest ancestor, A, whose BF becomes ± 2, of the inserted node Y.

LL: Y is inserted in the left subtree of the left subtree of A.

LR: Y is inserted in the right subtree of the left subtree of A.

RR: Y is inserted in the right subtree of the right subtree of A.

RL: Y is inserted in the left subtree of the right subtree of A.

As shown in the following:

# Unbalanced following insertion

# rotation type

# Rebalanced

LL

BFs need to be modified

![](img/15e8d7d94d8ddf02cb6839870195a31e_785_0.png)

# Unbalanced following insertion

# rotation type

# Rebalanced

RR

h+2

-2
A

-1
B

A_L

B_L

B_R

0
B

0
A

A_L

B_L

B_R

# Unbalanced following insertion

# rotation type

# Rebalanced

LR(a)

![](img/15e8d7d94d8ddf02cb6839870195a31e_787_0.png)

![](img/15e8d7d94d8ddf02cb6839870195a31e_787_1.png)
