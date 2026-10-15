# Flow Networks

![](bbox=[0.08, 0.22, 0.58, 0.62])

A *flow network* is

+   1. a directed graph G<V,E>,
+   2. Weights on edges denote the *capacities*.
+   3. Two distinguished vertex: s and t, denoting *source* and *sink*.

Definition: *st-Flow* A function f: V×V→R is a *st-flow (flow)* if satisfying:

∀ u,v∈V. f(u,v) = -f(v,u).
∀ u,v∈V. f(u,v) ≤ c(u,v).
∀ u ∈ V\{s,t}. Σv∈V f(u,v) = 0.
∀ v∈V. f(v,v)=0.

The *value* of a flow f:

|f| = f(s,V) = Σv∈V f(s,v)
|f| ≥ 0