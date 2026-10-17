# Dijkstra's Algorithm

```
procedure Dijkstra(G: weighted connected simple graph with vertices a = v₀, v₁, ..., vₙ = z and positive weights w(vᵢ, vⱼ), where w(vᵢ, vⱼ) = ∞ if {vᵢ, vⱼ} is not an edge in G)
for i := 1 to n
    L(vᵢ) := ∞
L(a) := 0
S := ∅
{the labels are now initialized so that the label of a is zero and all other labels are ∞, and the distinguished set of vertices S is empty}
```