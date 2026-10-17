
## Example

+   Let S = {1, 2, 3} and
+   let R = {(1,1), (2,2), (3,3), (1, 2), (3,1), (3,2)}

![](img/47b87ec6fe4fa238d13429358848c545_826_0.png)

2 ≲ 2      3 ≺ 2

## Example

+   - Show that ≥ is a partial order on the set of integers
+     - It is reflexive: $a \ge a$ for all $a \in \mathbf{Z}$
+     - It is antisymmetric: if $a \ge b$ then the only way that $b \ge a$ is when $b = a$
+     - It is transitive: if $a \ge b$ and $b \ge c$, then $a \ge c$

+   - Note that ≥ is the partial ordering on the set of integers

+   - $(\mathbf{Z}, \ge)$ is the partially ordered set, or poset

## More example

+   Consider the power set of {a, b, c} and the subset relation. (P({a,b,c}), ⊆)

+   Draw a graph of this relation.

## Comparable / Incomparable

+   - The elements *a* and *b* of a poset $(S, \preceq)$ are called **comparable** if either $a \preceq b$ or $b \preceq a$.
+   - When *a* and *b* are elements of *S* such that neither $a \preceq b$ nor $b \preceq a$, *a* and *b* are called **incomparable**.

+   - **Example:** Consider the power set of $\{a,b,c\}$ and the subset relation. $(P(\{a,b,c\}), \subseteq)$
+   
+     $\{a,c\} \nsubseteq \{a,b\}$ and $\{a,b\} \nsubseteq \{a,c\}$
+   
+   - So, $\{a,c\}$ and $\{a,b\}$ are **incomparable**.

## Total order, Chain

+   - If (S, ≤ ) is a poset and every two elements of S are comparable, S is called *totally ordered* or *linearly ordered* set, and ≤ is called a *total order* or a *linear order*.
+   - A totally ordered set is also called a *chain*.

## Examples

+   □ Is ≤ on the set of reals a total order?
+     ▸ Yes. For any reals x and y, either x ≤ y or y ≤ x.
+   □ | on the set of positive integers?
+     ▸ No. Neither 2 divides 3, nor 3 divides 2.
+   □ ⊆ on the power set of a set?
+     ▸ No. For x ≠ y, neither {x} ⊆ {y}, nor {y} ⊆ {x}.
+   □ Lexicographic order on English words?
+     ▸ Yes. For any two words, either x precedes y or y precedes x (or both if they are the same).

## Generalized lexicographic order

If $(A_1, \preceq_1)$, $(A_2, \preceq_2)$, ..., $(A_n, \preceq_n)$ are posets, the lexicographic order on the Cartesian product $A_1 \times A_2 \times \cdots \times A_n$ is defined recursively: $(a_1, a_2, \ldots, a_n) \preceq (b_1, b_2, \ldots, b_n)$ if

+   - $a_1 \preceq_1 b_1$, or
+   - $a_1 = b_1$ and $(a_2, \ldots, a_n) \preceq (b_2, \ldots, b_n)$

## Lexicographic order on strings

If $x = (x_1, x_2, ..., x_n)$ and $y = (y_1, y_2, ..., y_m)$ are two strings, we define lexicographic order on them as an extension of the previous that takes care of different lengths. Let $k = \min(n, m)$; then $x \leqslant y$ if

+   - $(x_1, x_2, ..., x_k) \leqslant (y_1, y_2, ..., y_k)$ or
+   - $(x_1, x_2, ..., x_k) = (y_1, y_2, ..., y_k)$ and $k = n < m$

## Hasse diagrams

What is the directed graph representation of a partial order?

+   - There will be loops at every node
+   - Transitivity will produce many "extra" edges
+   - There will be a particular direction for edges

Hasse diagrams simplify the graph by removing loops, removing extra edges implied by transitivity, and putting nodes in order (bottom to top) so that arrows can be omitted

+   - Start with a directed graph of the relation in which all arrows point upward. Then eliminate:
+     - the loops at all the vertices,
+     - all arrows whose existence is implied by the transitive property,
+     - the direction indicators on the arrows.

## More Hasse diagram examples

+   • “divides” on {1, 2, 3, 4, 5, 6, 10, 12, 15, 20, 30, 60} (all divisors of 60)

![](img/47b87ec6fe4fa238d13429358848c545_836_0.png)

## More Hasse diagram examples

□ “⊆” on the power set of {a, b, c, d}

![](img/47b87ec6fe4fa238d13429358848c545_837_0.png)

## Maximal and minimal elements

+   - An element x of a poset (A, ≤ ) is called
+     - minimal, if there is no other element that precedes it, i.e., there is no y ∈ A such that y < x
+     - maximal, if there is no other element that follows it, i.e., there is no y ∈ A such that x < y

+   - Existence
+     - Guaranteed for finite sets

+   - Uniqueness
+     - Generally not unique
