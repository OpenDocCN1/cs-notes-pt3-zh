
This construction is possible since G is connected. G is obtained after e edges are added. Let r_n, e_n, and v_n represent the number of regions, edges, and vertices of the planar representation of G_n induced by the planar representation of G, respectively.

The proof will now proceed by induction. The relationship r_1 = e_1 − v_1 + 2 is true for G_1, since e_1 = 1, v_1 = 2, and r_1 = 1. This is shown in Figure 9.

Now assume that r_n = e_n − v_n + 2. Let {a_{n+1}, b_{n+1}} be the edge that is added to G_n to obtain G_{n+1}. There are two possibilities to consider. In the first case, both a_{n+1} and b_{n+1} are already in G_n. These two vertices must be on the boundary of a common region R, or else it would be impossible to add the edge {a_{n+1}, b_{n+1}} to G_n without two edges crossing (and G_{n+1} is planar). The addition of this new edge splits R into two regions.

Consequently, in this case, r_{n+1} = r_n + 1, e_{n+1} = e_n + 1, and v_{n+1} = v_n. Thus, each side of the formula relating the number of regions, edges, and vertices increases by exactly one, so this formula is still true. In other words, r_{n+1} = e_{n+1} − v_{n+1} + 2. This case is illustrated in Figure 10(a).

In the second case, one of the two vertices of the new edge is not already in G_n. Suppose that a_{n+1} is in G_n but that b_{n+1} is not. Adding this new edge does not produce any new regions, since b_{n+1} must be in a region that has a_{n+1} on its boundary. Consequently, r_{n+1} = r_n. Moreover, e_{n+1} = e_n + 1 and v_{n+1} = v_n + 1. Each side of the formula relating the number of regions, edges, and vertices remains the same, so the formula is still true. In other words, r_{n+1} = e_{n+1} − v_{n+1} + 2. This case is illustrated in Figure 10(b).

We have completed the induction argument. Hence r_n = e_n − v_n + 2 for all n. Since the original graph is the graph G_e, obtained after e edges have been added, the theorem is true.

## Algorithms / 算法

![](img/5123c27d7478faaa822d0f1f02fc503f_1518_0.png)

### Example 4

Suppose that a connected planar simple graph has 20 vertices, each of degree 3. Into how many regions does a representation of this planar graph split the plane?

**Solution:** This graph has 20 vertices, each of degree 3, so v = 20. Since the sum of the degrees of the vertices, 3v = 3·20 = 60, is equal to twice the number of edges, 2e, we have 2e = 60, or e = 30. Consequently, from Euler’s formula, the number of regions is

r = e − v + 2 = 30 − 20 + 2 = 12.

### Corollary 1

**Degree of a region:** Suppose R is a region of a connected planar simple graph. The number of edges which surround R is called the **degree of R**, denoted by **Deg(R)**.

The region is a **closed path**.

![](img/5123c27d7478faaa822d0f1f02fc503f_1521_0.png)

- Deg(R₁) = 3
- Deg(R₂) = 6
- Deg(R₃) = 7

![](img/5123c27d7478faaa822d0f1f02fc503f_1521_1.png)

- Deg(R₁) = 12
- Deg(R₂) = 4

### Proof of Corollary 1

If G is a connected planar simple graph with e edges and v vertices where v ≥ 3, then e ≤ 3v − 6.

**Proof:** Suppose that a connected planar simple graph divides the plane into r regions. The degree of each region is at least 3 (no simple region can be surrounded by one or two different edges).

Using Euler’s formula e − v + 2 = r, we obtain

e − v + 2 ≤ (2/3)e,

this shows that

e ≤ 3v − 6.

The equality holds if and only if every region has exactly three edges.

### Example 5

Show that K₅ is nonplanar using Corollary 1.

**Solution:** The graph K₅ has five vertices and 10 edges. However, the inequality e ≤ 3v − 6 is not satisfied for this graph since e = 10 and 3v − 6 = 9. Therefore, K₅ is not planar.
