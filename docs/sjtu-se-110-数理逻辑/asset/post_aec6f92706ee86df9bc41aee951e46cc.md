
## homework

+   Page265 14 (Page543 31 ver6)

Determine whether the relations represented by the following graphs are reflexive, irreflexive, symmetric, antisymmetric, and/or transitive.

![](img/596a7ad0af4b255f7c4ff59547a2dbb3_173_0.png)

## Relations (3)

Wu Gang

School of Software, SJTU

## Transitive closures

+   - Connective relation R*
+     - Let R be a relation on a set A
+     - R* consists of the pairs (a,b) such that there is a path of length at least one from a to b in R

R* = ⋃_{n=1}^{∞} R^n

## examples

+   - Let R be the relation on the set of all people in the world that contains (a,b) if a has met b
+     - What is Rⁿ? What is R*?
+     - (you, Obama) ∈ R*?

## examples

+   - Let R be the relation on the set of all subway stops in shanghai that contains (a,b) if it is possible to travel from a to b without changing trains.
+   - What is Rⁿ? What is R*?
+   - (Dongchuan Road, Jianchuan Road) ∈ R⁵?
+   - (Dongchuan Road, Jianchuan Road) ∈ R⁴?

## Transitive closures

+   - Theorem
+     - The transitive closure of a relation R equals the connectivity relation R*
+       - R* contains R
+       - R* is transitive
+       - If there is a S, which is transitive and contains R, then S contains R*

## Transitive closures

+   R* = R ∪ R² ∪ R³ ∪ ... ∪ Rⁿ

M_{R*} = M_R ∨ M_R^{[2]} ∨ M_R^{[3]} ... ∨ M_R^{[n]}

## Equivalence relations

+   - Definition: A relation on a set A is an equivalence relation if it is reflexive, symmetric and transitive.

+   - Examples
+     - Let R be the relation on the set of students in this class, aRb iff a and b come from the same province--- “Lao Xiang”
+     - Congruence Modulo.
+       - R={(a,b)|a≡b(mod m)}    m>1 is positive integer, a/b are integers

## Equivalence classes

+   - Let R be an equivalence relation on set A. The set of elements that are related to an element a of A is called the equivalence class of a. denoted by [a]_R
+   - [a]_R = {s | (a,s) ∈ R}
+   - If there is only one relation under consideration, it can be denoted by [a]

## Equivalence classes

+   - Examples
+     - [zhangsan] for relation “Lao xiang”
+     - [0], [1], [5] for congruence modulo 4
+       - [0]={...-8,-4,0,4,8...}
+       - [1]={...-7,-3,1,5,9...}
+       - [5]=?
+     - Congruence classes modulo m, denoted by [a]ₘ, like [5]₄ and [1]₃

## Equivalence classes and partitions

+   Theorem1
+     Let R be an equivalence relation on set A, these statements are equivalent
+     (1) aRb;  (2) [a]=[b];  (3)[a]∩[b]≠∅

## Partial orderings

## Definition

+   - A relation R on a set S is called partial order if it is reflexive, antisymmetric and transitive.
+   - A set S together with a partial order R is called a *partially ordered set* or *poset*, denoted by (S,R)

## Partial orderings

+   - Examples
+     - (Z, ≥)
+     - Inclusion relation on the power set of set S, (P(S), ⊆)
+   - (S,R)
+     - It is not necessary that either aRb or bRa for every a and b in the set S

## Partial orderings

+   - The elements a and b of a poset (S, ≤) are called Comparable if either a ≤ b or b ≤ a, otherwise, incomparable
+   - Total ordering
+     - If (S, ≤) is a poset, and every two elements of S are comparable, S is called totally ordered set or linearly ordered set
+     - (P(S), ⊆) Total ordering?

## Partial orderings

+   Lexicographic ordering

+   ≤ on Cartesian product of N posets
+   (A₁, ≤₁) (A₂, ≤₂)... (Aₙ, ≤ₙ)

+   (a₁,a₂,...aₙ)<(b₁,b₂...bₙ) if a₁<₁b₁ or there is an integer i>0 such that a₁=b₁ a₂=b₂ ... aᵢ=bᵢ, and aᵢ₊₁<ᵢ₊₁bᵢ₊₁)

+   (a₁,a₂,...aₙ)=(b₁,b₂...bₙ) if aᵢ=bᵢ i=1,2,...n

+   How to compare 8-bit binary number?

## Partial orderings

+   - Lexicographic ordering of strings
+     - a₁a₂...aₘ, b₁b₂...bₙ
+     - let t be the minimum of m/n, then (a₁,a₂,...aₘ)<(b₁,b₂...bₙ) if (a₁,a₂,...aₜ)<ₜ(b₁,b₂...bₜ) or (a₁,a₂,...aₜ)=(b₁,b₂...bₜ) and m<n
+   - How to compare “good”, “goodbye”, “gate”, “go”
