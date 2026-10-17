
Is it possible to join the three houses to the three utilities in such a way that none of the connections cross?

![](img/47b87ec6fe4fa238d13429358848c545_648_0.png)

## Planar Graphs

- A graph is called **planar** if it can be drawn in the plane without any edges crossing.
- A crossing of edges is the intersection of the lines or arcs representing them at a point other than their common endpoint.
- Such a drawing is called a **planar** representation of the graph.

### Example

A graph may be planar even if it is usually drawn with crossings, since it may be possible to draw it in another way without crossings.

![](img/47b87ec6fe4fa238d13429358848c545_651_0.png)

### Example

A graph may be planar even if it represents a 3-dimensional object.

![](img/47b87ec6fe4fa238d13429358848c545_652_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_652_1.png)

![](img/47b87ec6fe4fa238d13429358848c545_652_2.png)

## Planar Graphs

- We can prove that a particular graph is planar by showing how it can be drawn without any crossings.
- However, not all graphs are planar.
- It may be difficult to show that a graph is nonplanar. We would have to show that there is no way to draw the graph without any edges crossing.

## Regions

Euler showed that all planar representations of a graph split the plane into the same number of regions, including an unbounded region.

![](img/47b87ec6fe4fa238d13429358848c545_654_0.png)

### Regions for K₃,₃

In any planar representation of K₃,₃, vertex v₁ must be connected to both v₄ and v₅, and v₂ also must be connected to both v₄ and v₅.

![](img/47b87ec6fe4fa238d13429358848c545_655_0.png)

### Step 1

The four edges {v₁, v₄}, {v₄, v₂}, {v₂, v₅}, {v₅, v₁} form a closed curve that splits the plane into two regions, R₁ and R₂.

![](img/47b87ec6fe4fa238d13429358848c545_656_0.png)

### Step 2

- Next, we note that v₃ must be in either R₁ or R₂.
- Assume v₃ is in R₂. Then the edges {v₃, v₄} and {v₃, v₅} separate R₂ into two subregions, R₂₁ and R₂₂.

![](img/47b87ec6fe4fa238d13429358848c545_657_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_657_1.png)

### Step 3 - 1

Now there is no way to place vertex v₆ without forcing a crossing:

- If v₆ is in R₁ then {v₆, v₃} must cross an edge
- If v₆ is in R₂₁ then {v₆, v₂} must cross an edge
- If v₆ is in R₂₂ then {v₆, v₁} must cross an edge

![](img/47b87ec6fe4fa238d13429358848c545_658_0.png)

### Step 3 - 2

Alternatively, assume v₃ is in R₁. Then the edges {v₃, v₄} and {v₃, v₅} separate R₁ into two subregions, R₁₁ and R₁₂.

![](img/47b87ec6fe4fa238d13429358848c545_659_0.png)

### Step 4

Now there is no way to place vertex v₆ without forcing a crossing:

- If v₆ is in R₂ then {v₆, v₃} must cross an edge
- If v₆ is in R₁₁ then {v₆, v₂} must cross an edge
- If v₆ is in R₁₂ then {v₆, v₁} must cross an edge

![](img/47b87ec6fe4fa238d13429358848c545_660_0.png)

### Step 5

Consequently, the graph K₃,₃ must be nonplanar.

![](img/47b87ec6fe4fa238d13429358848c545_661_0.png)

## Euler's Formula

Let G be a connected planar simple graph with e edges and v vertices. Let r be the number of regions in a planar representation of G. Then r = e - v + 2.

![](img/47b87ec6fe4fa238d13429358848c545_663_0.png)

- Number of edges, e = 6
- Number of vertices, v = 4
- Number of regions, r = e - v + 2 = 4

- Corollary 1: If G is a connected planar simple graph with e edges and v vertices where v ≥ 3, then e ≤ 3v − 6.
- Is K₅ planar?

![](img/47b87ec6fe4fa238d13429358848c545_664_0.png)

K₅

### Euler's Formula on K₅

- K₅ has 5 vertices and 10 edges.
- We see that v ≥ 3.
- So, if K₅ is planar, it must be true that e ≤ 3v − 6.
- 3v − 6 = 3 × 5 − 6 = 15 − 6 = 9.
- So e must be ≤ 9.
- But e = 10.
- So, K₅ is nonplanar.

![](img/47b87ec6fe4fa238d13429358848c545_665_0.png)
