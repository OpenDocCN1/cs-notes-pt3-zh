
![](img/c25dfd82fc242c2db53bc942dcad6885_1909_0.png)

- Basis step: Clearly P(0): T₀={} is contained in every minimal spanning tree for G
- Induction Step:
  - suppose P(k): Tₖ is contained in a minimal spanning tree T′ for G.
  - By definition {t₁, t₂, …, tₖ} ⊆ T′. If tₖ₊₁ also belongs to T′, then Tₖ₊₁ ⊆ T′ and we have P(k+1) is true.
  - If tₖ₊₁ does not belong to T′, then T′ ∪ {tₖ₊₁} must contain a cycle.
  - This cycle would be for some edges s₁, s₂, …, sₖ in T′
  - The edges of this cycle cannot all be from Tₖ or Tₖ₊₁ would contain this cycle.

![](img/c25dfd82fc242c2db53bc942dcad6885_1909_1.png)

- Let sₗ be the edge with smallest index l that is not in Tₖ. When tₖ₊₁ was chosen by Prim’s algorithm, sₗ was also available. Thus the weight of sₗ is at least as large as that of tₖ₊₁.
- The spanning tree (T′ -{sₗ}) ∪{tₖ₊₁} contains Tₖ₊₁. The weight of this tree is less than or equal to the weight of T′, so it is a minimal tree for G.
- P(k+1) is true. So Tₙ₋₁=T is contained in a minimal spanning tree and must in fact be that minimal spanning tree.
- Q.E.D

## Kruskal’s algorithm

- Let G be a weighted connected undirected graph with n vertices and let S={e₁, e₂,..., eₖ} be the set of weighted edges of G.
  - Step 1 Choose an edge e₁ in S of least weight. Let E={e₁}. Replace S with S-{e₁}.
  - Step 2 Choose an edge eᵢ in S of least weight that will not make a cycle with members of E. Replace E with E ∪ {eᵢ} and S with S-{eᵢ}.
  - Step 3 Repeat step 2 until |E|=n-1.
  - End of algorithm

![](img/c25dfd82fc242c2db53bc942dcad6885_1912_0.png)

| Choice | Edge | Weight |
|---|---|---|
| 1 | {c, d} | 1 |
| 2 | {k, l} | 1 |
| 3 | {b, f} | 1 |
| 4 | {c, g} | 2 |
| 5 | {a, b} | 2 |
| 6 | {f, j} | 2 |
| 7 | {b, c} | 3 |
| 8 | {j, k} | 3 |
| 9 | {g, h} | 3 |
| 10 | {i, j} | 3 |
| 11 | {a, e} | 3 |
|  | Total: | 24 |

## (a)

## (b)

FIGURE 5 A Minimum Spanning Tree Produced by Kruskal's Algorithm.

## Example 7

Figure 7.49

Figure 7.54

## Example 8

- Use Kruskal’s algorithm to find a minimal spanning tree for the graph

![](img/c25dfd82fc242c2db53bc942dcad6885_1914_0.png)

## 最小生成树/minimum spanning tree

城市通讯网图中，最小生成树就是能保证通讯费用最小的通讯网。

[定义]

最小生成树: 设加权图G = ( V , E , W ), T = ( V , E' ) 是G的生成树, 称 w ( T ) = Σ_{e∈E'} w(e) 为 T 的权, 使权 w ( T ) 达到最小值的

## Kruskal 算法：

设 G = (V, E, W) 是连通图

- 1. 各边以权由小到大排序。
- 2. 选 E 中最小边 e₁，令 G₁ = (V, S₁)， S₁ = {e₁}， i = 1
- 3. 设 Sᵢ = {e₁, e₂, ..., eᵢ}， Gᵢ = (V, Sᵢ) 选出 Sᵢ₊₁, 从 E − Sᵢ 中选一条边 eᵢ₊₁， 满足：
  - (1) Sᵢ ∪ {eᵢ₊₁} 中不含回路；
  - (2) eᵢ₊₁ 是满足 (1) 的最小权的边。令 Sᵢ₊₁ = {e₁, e₂, ..., eᵢ, eᵢ₊₁}， Gᵢ₊₁ = (V, Sᵢ₊₁)；
- 4. i = i + 1，若 i = v − 1，则 Gᵢ = Gᵥ₋₁ 为最小生成树，否则转 3 继续。

## 解题过程：

(1) 边排序:(v1,v2),(v2,v7),(v1,v6),(v6,v7)

(v1,v4),(v5,v6),(v4,v5),(v3,v4),(v3,v8)

(v5,v8),(v2,v3),(v7,v8)

(2) 选s1={e1} e1=(v1,v2)

(3) 选e2=(v2,v7)

(4) e3=(v1,v6)

(5) e4=(v1,v4)=5

(6) e5=(v5,v6)=6

(7) e6=(v3,v4)=8

(8) e7=(v3,v8)

![](img/c25dfd82fc242c2db53bc942dcad6885_1918_0.png)

## 作业

- § 11.3 − 6, 18, 22, 34
- § 11.4 − 12, 14, 22, 24, 50, 54
- § 11.5 − 4, 8, 10, 14, 18
- Distance between two spanning trees

## 1 The Foundations: Logic and Proofs

- 1.1 Propositional Logic
- 1.2 Applications of Propositional Logic
- 1.3 Propositional Equivalences
- 1.4 Predicates and Quantifiers
- 1.5 Nested Quantifiers
- 1.6 Rules of Inference
- 1.7 Introduction to Proofs
- 1.8 Proof Methods and Strategy

## Rules of Inference

Rosen 7th ed., § 1.6

## Argument(论证)

A sequence of statements that end with a conclusion.

> “If you have a current password, then you can log onto the network.”

“You have a current password.”

Therefore

> “You can log onto the network.”

## Definition 1

- An *argument* in propositional logic is a sequence of propositions. All but the final proposition in the argument are called ***premises*** and the final proposition is called the *conclusion*. An argument is ***valid*** if the truth of all its premises implies that the conclusion is true.
