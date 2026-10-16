
To reflect the cost of unsuccessful search, it is useful to add a special “square” node at every null link.

Doing this to the trees of Fig. 10.2 yields the trees of Fig. 10.3.

Binary tree with n nodes has n+1 null links and therefore will have n+1 square nodes.

![](img/15e8d7d94d8ddf02cb6839870195a31e_739_0.png)

(a)

(b)

Fig. 10.3 Extended binary trees corresponding to search trees of Fig. 10.2

- external (failure) nodes---square nodes.
- internal nodes---original nodes.
- extended binary tree---a binary tree with external nodes added.
- external path length, E, of a binary tree---the sum over all external nodes of the lengths of the paths from the root to those nodes.
- internal path length, I, of a binary tree---the sum over all internal nodes of the lengths of the paths from the root to those nodes.

## For Fig. 10.3(a):

I=0+1+1+2+3=7,      E=2+2+4+4+3+2=17

In general, E=I+2n.

Hence, binary trees with the maximum E also have maximum I.

Over all binary trees with n internal nodes:

- worst case: when the tree has a depth of n.

I = Σ_{i=0}^{n-1} i = n(n−1)/2

this is the maximum I.

- optimal case: as many internal nodes as close to the root as possible---complete binary tree.
I=0+2*1+4*2+8*3+......
If we number the nodes in a complete binary tree as before, the distance of node i from the root is ⌊log₂i⌋
so
I = Σ₁≤i≤n ⌊log₂i⌋ = O(n log₂n)

Now return to the problem of finding an optimal binary search tree for a set of identifiers to be searched with different probabilities.

If the binary search tree contains the identifiers $a_1, a_2, \ldots, a_n$ with $a_1 < a_2 < \cdots < a_n$, and the probability of searching for each $a_i$ is $p_i$, then the total cost of any binary search tree is

$$\sum_{1 \le i \le n} p_i \cdot \operatorname{level}(a_i)$$

when only successful searches are made.

The cost of **unsuccessful** searches should also be included.

Unsuccessful searches terminate with algorithm *search* return a 0 pointer. Every node with a null subtree defines a point at which such a termination can take place. Replace every null subtree by a failure node.

Identifiers not in the binary search tree may be partitioned into n+1 classes, Eᵢ, 0≤i≤n.

E₀={x| x<a₁}
Eᵢ={x| aᵢ<x<aᵢ₊₁}, 1≤i<n.
Eₙ={x| x>aₙ}

For all x in Eᵢ, 0≤i≤n, the search terminates at the same failure node i, and it terminates at different failure nodes for x in different classes.

If qᵢ is the probability for Eᵢ, the cost of the failure nodes is

∑₀≤ᵢ≤ₙ qᵢ·(level(failure node i)-1)

Therefore the total cost is

∑₁≤ᵢ≤ₙ pᵢ·level(aᵢ) + ∑₀≤ᵢ≤ₙ qᵢ·(level(failure node i)-1)  (10.1)

An optimal binary search tree for the identifier set a₁, a₂, ……., aₙ is the one that minimizes Eq. (10.1) over all possible binary search trees for this identifier set.

## Note

$$\sum_{1\le i\le n} p_i + \sum_{0\le i\le n} q_i = 1$$

## Example 10.1:

$(a_1, a_2, a_3)=(do, if, while)$. The possible binary search tree for it are as follows:

![](img/15e8d7d94d8ddf02cb6839870195a31e_748_0.png)

- with equal probabilities, p_i=q_j for all i and j.
  cost(tree a )=15/7;  cost(tree b)=13/7
  cost(tree c )=15/7;  cost(tree d)=15/7
  cost(tree e )=15/7
  As expected, tree b is optimal.

- with p₁=0.5, p₂=0.1, p₃=0.05, q₀=0.15, q₁=0.1, q₂=0.05, q₃=0.05
  cost(tree a )=2.65;  cost(tree b)=1.9
  cost(tree c )=1.5;  cost(tree d)=2.15
  cost(tree e )=1.6

For instance,

cost(tree d) = 0.05+2*0.5+3*0.1
+2*0.15+3*0.1+3*0.05+0.05
=2.15   (note the error in P557)

tree c is optimal.

## How to determine the optimal tree?

One way: explicitly generate all possible binary search trees, compute the cost of each tree in O(n), then determine the optimal---need

$O\left(\frac{n}{n+1}C_n^{2n}\right)=O\left(C_n^{2n}\right)$ --- no good.

Instead, we can get an efficient algorithm by making use of the properties of optimal binary search trees(b.s.t.).

Let a₁<a₂<......,<aₙ be n identifiers in a b.s.t., denote:

- • Tᵢⱼ---an optimal b.s.t. for aᵢ₊₁,......, aⱼ, i<j . Tᵢᵢ is an empty tree, 0≤i≤n. Tᵢⱼ (i>j) is not defined.
- • cᵢⱼ---the cost of Tᵢⱼ. cᵢᵢ=0.
- • rᵢⱼ---the root of Tᵢⱼ.
- • wᵢⱼ---the weight of Tᵢⱼ. wᵢⱼ= qᵢ+ Σₖ₌ᵢ₊₁ʲ (qₖ+ pₖ).
