
The total disk accesses is at most
h+2(h-1)+3=3h+1

The average number of disk accesses is, however, approximately h+1 for larger m.

To show this, suppose we start with an empty B-tree and insert N elements into it.

Let p be the number of internal nodes in the final B-tree with N elements, then the total number of nodes split is at most p-2. Because
- Each time a node splits, at least one additional node is created.
- The splitting of the root node create two additional nodes and the root is the first to split.
- The first node created from no splitting.

## As shown in the following:

(a) p=1,s=0

(b) p=3,s=1

![](img/15e8d7d94d8ddf02cb6839870195a31e_839_0.png)

(c) p=4, s=2

A B-tree of order m with p nodes has at least

$1 + (\lceil m/2 \rceil - 1)(p-1)$ elements.

*(root)* *(other nodes)*

The average number of splitting s_avg

$s_{avg} = (\text{total number of splits})/N$

$\le (p-2)/\{1 + (\lceil m/2 \rceil - 1)(p-1)\}$

$< 1/(\lceil m/2 \rceil - 1)$

For m=200, $s_{avg} < 1/99$.

The number of disk accesses in an insertion is h+2s+1, where s is the number of nodes split.

So the average disk accesses is

h+2 s_avg +1 < h+2/99+1≈h+1.

## 11.2.4 Deletion from a B-Tree

Suppose the key of the element to be deleted is x.

First, search for x. If x is in a nonleaf node z and x = Eᵢ.K, then the corresponding element may be replaced by either the element with smallest key in the subtree Aᵢ or the element with largest key in the subtree Aᵢ₋₁. Both are in leaf nodes.

The deletion from a nonleaf node is thus transformed into a deletion from a leaf, as shown in the next slide.

![](img/15e8d7d94d8ddf02cb6839870195a31e_843_0.png)

### 4 cases of deleting from a leaf node p:

(1) p is the root, if p is left with at least 1 key, p is written to disk, done. Otherwise the B-tree is empty following the deletion.

In the remaining cases, p is not the root.

(2) Following the deletion, p has at least ⌈m/2⌉-1 keys. The modified p is written to disk, done.

(3) p has ⌈m/2⌉-2 keys, and its nearest sibling, q, has at least ⌈m/2⌉ keys. A rotation is performed as shown in the next slide (suppose q be the nearest right sibling of p, r be parent of p and q).

the changed p, q and r are written to disk, done.

(4) p has ⌈m/2⌉-2 keys, and q has ⌈m/2⌉-1 keys. A combination is performed as shown below:

![](img/15e8d7d94d8ddf02cb6839870195a31e_846_0.png)

Now p has (⌈m/2⌉-2)+(⌈m/2⌉-1)+1=2⌈m/2⌉-2 ≤ m-1 keys. p is written to disk.

The number of keys in the parent, r, has been reduced by 1.

If r does not become deficient (i.e., it has at least 1 element if it is the root and ⌈m/2⌉-1 elements if it is not the root), the changed r is written to disk, done.

When r becomes deficient, if it is the root, it is discarded. Otherwise r has ⌈m/2⌉-2 keys, we can first attempt a rotation with one of its

nearest siblings. If this is not possible, a combine is done. This process of combining can continue up the B-tree until the children of the root are combined.

A high-level description of the deletion algorithm is given in the next slide:

```
// Delete element with key x from a B-tree of order m
Search the B-tree for node p containing the element with key x;
if (there is no such node p) return;  // no element to delete
Let p be of the form: n, A₀, (E₁, A₁), …, (Eₙ, Aₙ) and Eᵢ.K=x;
if (p is not a leaf) {
    Replace Eᵢ with the smallest key element in subtree Aᵢ;
    write the altered p to disk;
    Let p be the leaf of Aᵢ from which the smallest was taken;
    Let p be of the form: n, A₀, (E₁, A₁), …, (Eₙ, Aₙ);
    i = 1;
}

// the following deletes Eᵢ from leaf node p
```

```
Delete (E_i, A_i) from p; n--;
**while** (n<⌈m/2⌉-1) && (p!=root)
    **if** (p has a nearest right sibling q) {
        Let q: n_q, A^q_0, (E^q_1 A^q_1), ..., (E^q_{n_q} A^q_{n_q});
        Let r: n_r, A^r_0, (E^r_1 A^r_1), ..., (E^r_{n_r} A^r_{n_r}) be parent of p and q;
        Let A^r_j=q and A^r_{j-1}=p;
        **if** (n_q >= ⌈m/2⌉) { // rotation
            (E_{n+1}, A_{n+1})=(E^r_j, A^q_0); n=n+1;   // update p
            E^r_j=E^q_1;                                 // update r
            (n_q,A^q_0,(E^q_1 A^q_1),...)=(n_q-1,A^q_1,(E^q_2 A^q_2),...); // update q
            **write** p, q, r to disk; **return**;
        }
        // combine nodes p, E^r_j, and q
        s=2*⌈m/2⌉-2;
```
