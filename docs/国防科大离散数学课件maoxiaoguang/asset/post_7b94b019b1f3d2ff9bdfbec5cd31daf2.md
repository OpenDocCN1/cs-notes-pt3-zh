
## 6 degrees of separation

- The idea that everybody in the world is connected by six degrees of separation
- Where 1 degree of separation means you know (or have met) somebody else

- Let R be a relation on the set of all people in the world
- (a,b) ∈ R if person a has met person b

- So six degrees of separation for any two people a and g means:
- (a,b), (b,c), (c,d), (d,e), (e,f), (f,g) are all in R

- Or, (a,g) ∈ R⁶

R* is the star closure of relation R, and it is defined as

$$R^* = \bigcup_{k=1}^{\infty} R^k$$

Def.: The transitive closure of a relation R, t(R), Is the smallest transitive relation containing R.

## Theorem: t(R) = R*.

## How long are the paths in a transitive closure?

- Let R be a relation on set A, and let A be a set with n elements
- Rephrased: consider a graph G with n nodes and some number of edges

- Lemma 1: If there is a path (of length at least 1) from a to b in R, then there is a path between a and b of length not exceeding n

- Proof preparation:
- Suppose there is a path from a to b in R
- Let the length of that path be m
- Let the path be edges (x₀, x₁), (x₁, x₂), …, (xₘ₋₁, xₘ)
- That’s nodes x₀, x₁, x₂, …, xₘ₋₁, xₘ
- If a node exists twice in our path, then it’s not a shortest path
- As we made no progress in our path between the two occurrences of the repeated node
- Thus, each node may exist at most once in the path

## How long are the paths in a transitive closure?

Proof by contradiction:

- Assume there are more than *n* nodes in the path
- Thus, *m* > *n*
- Let *m* = *n*+1
- By the pigeonhole principle, there are *n*+1 nodes in the path (pigeons) and they have to fit into the *n* nodes in the graph (pigeonholes)
- Thus, there must be at least one pigeonhole that has at least two pigeons
- Rephrased: there must be at least one node in the graph that has two occurrences in the nodes of the path
- Not possible, as the path would not be the shortest path
- Thus, it cannot be the case that *m* > *n*

If there exists a path from *a* to *b*, then there is a path from *a* to *b* of at most length *n*

## Finding the transitive closure

Let M_R be the zero-one matrix of the relation R on a set with n elements. Then the zero-one matrix of the transitive closure R* is:

M_R* = M_R ∨ M_R^[2] ∨ M_R^[3] ∨ … ∨ M_R^[n]

Nodes reachable with one application of the relation

Nodes reachable with two applications of the relation

Nodes reachable with n applications of the relation

## Rosen, section 8.4, example 7

Find the zero-one matrix of the transitive closure of the relation R given by:

M_R = [[1 0 1],[0 1 0],[1 1 0]]

![](img/47b87ec6fe4fa238d13429358848c545_802_0.png)

M_R^[2] =

![](img/47b87ec6fe4fa238d13429358848c545_802_1.png)

M_R* = M_R ∨ M_R^[2] ∨ M_R^[3]

M_R^[2] = M_R ⊙ M_R = [[1 0 1],[0 1 0],[1 1 0]] ⊙ [[1 0 1],[0 1 0],[1 1 0]] = [[1 1 1],[0 1 0],[1 1 1]]

## Rosen, section 8.4, example 7

M_R^{[3]} = M_R^{[2]} ⊙ M_R = [1 1 1; 0 1 0; 1 1 1] ⊙ [1 0 1; 0 1 0; 1 1 0] = [1 1 1; 0 1 0; 1 1 1]

![](img/47b87ec6fe4fa238d13429358848c545_803_0.png)

M_R* = [1 0 1; 0 1 0; 1 1 0] ∨ [1 1 1; 0 1 0; 1 1 1] ∨ [1 1 1; 0 1 0; 1 1 1] = [1 1 1; 0 1 0; 1 1 1]

## Transitive closure algorithm

What we did (or rather, could have done):

- Compute the next matrix M_R^{[i]}, where 1 ≤ i ≤ n
- Do a Boolean join with the previously computed matrix

For our example:

- Compute M_R^{[2]} = M_R ∘ M_R
- Join that with M_R to yield M_R ∨ M_R^{[2]}
- Compute M_R^{[3]} = M_R^{[2]} ∘ M_R
- Join that with M_R ∨ M_R^{[2]} from above

## Transitive closure algorithm

```
procedure transitive_closure (M_R: zero-one n×n matrix)
    A := M_R
    B := A
    for i := 2 to n
    begin
        A := A ⊙ M_R
        B := B ∨ A
    end { B is the zero-one matrix for R* }
```

What is the time complexity?      O(n⁴)
