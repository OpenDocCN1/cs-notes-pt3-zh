

## Searching solution space

- Searching for solutions equals to traverse the state space tree
- Node has three states during expending a tree
  1. Live node: A node that has been reached, but not all of its children have been explored
  2. Dead node: A node where all of its children have been explored
  3. E-Node (expansion node): A live node in which its children are currently being explored.
- Search strategy
  1. Backtrack: A variant version of depth first search with a bound function
  2. Branch-bound(Best first search): an enhancement of backtracking

Bounding is a boolean function to kill a live node

## Bounding function for Subset sum problem

- Simple bounding: B(X(1),⋯,X(k))=true iff

\(\sum_{i=1}^k W(i)X(i) + \sum_{i=k+1}^n W(i) < M\) (1)

- Simple bounding: B(X(1),...,X(k))=true iff

\[
\sum_{i=1}^{k} W(i)X(i)+\sum_{i=k+1}^{n} W(i)<M
\tag{1}
\]

- Tighter bounding: B(X(1),...,X(k))=true iff (1) and

\[
\sum_{i=1}^{k} W(i)X(i)+W(k+1)>M
\tag{2}
\]

when sorting W(i) by non-decreasing order

## Subset sum algorithm with bounding

**Algorithm 2:** Subset sum problem: pseudo code

```text
Let s=w(1)+⋯+w(k−1);
    r′=w(k)+⋯+w(n), assumed s+r′≥M;
Expanding left child node;
if S + W(k) > M then
    stop expanding;
    r′=r−w(k);
    Expanding right child node;
else
    x(k)=1;
    s=s+w(k);
    r′=r−w(k);
    let (x(1),⋯,x(k)) be E-Node;
Expanding right child node;
if s+r′ < M or s+w(k+1) > M then
    stop expanding;
else
    x(k)=0
```

## State space tree with bounding

### Subset sum problem

M=30,n=6 and w=(5,10,12,13,15,18)

UPDATED

![](img/4208ee4325ab94ec0c685a689680f88f_277_0.png)

Numbers in a rectangle node corresponds to s, k and r values respectively. Circle nodes correspond to answer states, There are only 23 nodes, but 2<sup>7</sup> − 1 = 63 nodes without bounding

## Outline

1. Definition and Representations
2. Two-Ship-Loading Problem:TSLP
3. 0/1 Knapsack
4. Max Clique
5. Traveling Sales Problem

## Problem statement

- Given two ships with capacities \(c_1\) and \(c_2\), and \(n\) containers with weights \((w_1, \cdots, w_n)\), such that

$$
\sum_{i=1}^n w_i \leq c_1 + c_2
\tag{3}
$$

- We wish to determine whether there is a way to load all \(n\) containers into ships without sinking.

Note that

- When \(\sum_{i=1}^n w_i = c_1 + c_2\), it is equivalent to the sum-of-subset problem
- When \(c_1 = c_2\), it is equivalent to the partition problem

## Solution

1. load the first ship as close to its capacity as possible and
2. put the remaining containers into the second ship.

To load the first ship as close to capacity as possible, we need to select a subset of containers with total weight as close to \( c_1 \) as possible.

Using fixed length tuple \( x = (x_1, \cdots, x_n) \) (\( x_i = 1 \), if container i is loaded) as solution space representation, just need

\[ \max \sum_{i=1}^n w_i x_i \tag{4} \]

An example of state space tree is shown below.

![](img/4208ee4325ab94ec0c685a689680f88f_281_0.png)

