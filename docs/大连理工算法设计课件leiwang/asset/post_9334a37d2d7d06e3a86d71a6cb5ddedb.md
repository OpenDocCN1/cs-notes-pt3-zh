

## ITERATIVE-TREE-SEARCH(x, k)

```
while x ≠ NIL and k ≠ key[x]
   do if k < key[x]
      then x ← left[x]
      else x ← right[x]
return x
```

## TREE-MINIMUM(x)

```
while left[x] ≠ NIL
   do x ← left[x]
return x
```

## TREE-MAXIMUM(x)

```
1 while right[x] ≠ NIL
2 do x ← right[x]
3 return x
```

## TREE-SUCCESSOR(x)

```
if right[x] ≠ NIL
then return TREE-MINIMUM(right[x])
y ← p[x]
while y ≠ NIL and x = right[y]
do x ← y
y ← p[y]
return y
```

```
TREE-INSERT(T, z)
1  y ← NIL
2  x ← root[T]
3  while x ≠ NIL
4      do y ← x
5         if key[z] < key[x]
6             then x ← left[x]
7             else x ← right[x]
8  p[z] ← y
9  if y = NIL
10     then root[T] ← z
11     else if key[z] < key[y]
12             then left[y] ← z
13             else right[y] ← z
```

> ▷ Tree T was empty

```
TREE-DELETE(T, z)

1 if left[z] = NIL or right[z] = NIL
2 then y ← z
3 else y ← TREE-SUCCESSOR(z)
4 if left[y] ≠ NIL
5 then x ← left[y]
6 else x ← right[y]
7 if x ≠ NIL
8 then p[x] ← p[y]
9 if p[y] = NIL
10 then root[T] ← x
11 else if y = left[p[y]]
12 then left[p[y]] ← x
13 else right[p[y]] ← x
14 if y ≠ z
15 then key[z] ← key[y]
16 copy y’s satellite data into z
17 return y
```

![](img/5e59105b951890406cf98b2a964cb2f9_117_0.png)

Figure 12.4 Deleting a node z from a binary search tree. Which node is actually removed depends on how many children z has; this node is shown lightly shaded. (a) If z has no children, we just remove it. (b) If z has only one child, we splice out z. (c) If z has two children, we splice out its successor y, which has at most one child, and then replace z's key and satellite data with y's key and satellite data.

![](img/5e59105b951890406cf98b2a964cb2f9_118_0.png)

**Figure 12.5** A radix tree storing the bit strings 1011, 10, 011, 100, and 0. Each node’s key can be determined by traversing the path from the root to that node. There is no need, therefore, to store the keys in the nodes; the keys are shown here for illustrative purposes only. Nodes are heavily shaded if the keys corresponding to them are not in the tree; such nodes are present only to establish a path to other nodes.

# Introduction to Algorithms

# 6.046J/18.401J

![](img/5e59105b951890406cf98b2a964cb2f9_119_0.png)

# LECTURE 1

# Analysis of Algorithms

+   - Insertion sort
+   - Asymptotic analysis
+   - Merge sort
+   - Recurrences

Prof. Charles E. Leiserson

# Course information

+   1. Staff
+   2. Distance learning
+   3. Prerequisites
+   4. Lectures
+   5. Recitations
+   6. Handouts
+   7. Textbook

+   8. Course website
+   9. Extra help
+   10. Registration
+   11. Problem sets
+   12. Describing algorithms
+   13. Grading policy
+   14. Collaboration policy

![](img/5e59105b951890406cf98b2a964cb2f9_121_0.png)

# Analysis of algorithms

*The theoretical study of computer-program performance and resource usage.*

What’s more important than performance?

+   - modularity
+   - correctness
+   - maintainability
+   - functionality
+   - robustness

+   - user-friendliness
+   - programmer time
+   - simplicity
+   - extensibility
+   - reliability

![](img/5e59105b951890406cf98b2a964cb2f9_122_0.png)

# Why study algorithms and performance?

+   - Algorithms help us to understand *scalability*.
+   - Performance often draws the line between what is feasible and what is impossible.
+   - Algorithmic mathematics provides a *language* for talking about program behavior.
+   - Performance is the *currency* of computing.
+   - The lessons of program performance generalize to other computing resources.
+   - Speed is fun!

# Insertion sort

```
INSERTION-SORT (A, n) ▷ A[1 . . n]
for j ← 2 to n
    do key ← A[j]
    i ← j − 1
    while i > 0 and A[i] > key
        do A[i+1] ← A[i]
        i ← i − 1
    A[i+1] = key
```

# Insertion sort

```
INSERTION-SORT(A, n) ▷ A[1 . . n]
for j ← 2 to n
    do key ← A[j]
    i ← j − 1
    while i > 0 and A[i] > key
        do A[i+1] ← A[i]
        i ← i − 1
    A[i+1] = key
```

![](img/5e59105b951890406cf98b2a964cb2f9_125_0.png)

