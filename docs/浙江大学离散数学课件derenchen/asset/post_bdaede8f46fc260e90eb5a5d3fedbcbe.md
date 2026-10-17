

If a connected planar simple graph has e edges and v vertices with v ≥ 3 and no circuits of length 3, then e ≤ 2v − 4.

The proof of Corollary 2 is similar to that of Corollary 1, except that in this case the fact that there are no circuits of length 3 implies that the degree of a region must be at least 4. The details of this proof are left for the reader (see Exercise 13 at the end of this section).

## Example 6

Use Corollary 2 to show that K_{3,3} is nonplanar.

**Solution:** Since K_{3,3} has no circuits of length 3 (this is easy to see since it is bipartite), Corollary 2 can be used. K_{3,3} has six vertices and nine edges. Since e=9 and 2v−4=8, Corollary 2 shows that K_{3,3} is nonplanar.

## Corollary 3

Generally, if every region of a planar connected graph has at least l edges, then:

e ≤ l/(l−2)(v−2)

Proof: similarly, 2e = 2e = Σ deg(Ri) ≥ lr, this imply r ≤ (2/l)e,

Using Euler’s formula e−v+2=r, we obtain

e−v+2 ≤ (2/l)e, this shows that

e ≤ l/(l−2)(v−2)

![](img/5123c27d7478faaa822d0f1f02fc503f_1528_0.png)

![](img/5123c27d7478faaa822d0f1f02fc503f_1528_1.png)

## The construction of Dodecahedron(正12面体)

the degree of every vertex is 3 and the degree of every region is 5, hence 2e=3v, and

e= l/l−2 (v−2)= 5/5−2(v−2)=(5/3)(v−2), hence

v=20, e=30 and r=12

## Theorem 2

A graph is nonplanar if and only if it contains a subgraph homeomorphic to K_{3,3} or K_5.

It is clear that a graph containing a subgraph homeomorphic to K_{3,3} or K_5, is complicated and will not be given here. The following examples illustrate how Kuratowski’s theorem is used.

Hint: homeomorphic is mainly adding or deleting a series if **vertices of degree 2**

![](img/5123c27d7478faaa822d0f1f02fc503f_1531_0.png)

## Example 8

Is the Petersen graph, shown in Figure 14(a), planar? (The Danish mathematician Julius Petersen introduced this graph in 1891; it is often used to illustrate various theoretical properties of graphs.)

![](img/5123c27d7478faaa822d0f1f02fc503f_1533_0.png)

![](img/5123c27d7478faaa822d0f1f02fc503f_1533_1.png)

## Algorithms
算法

![](img/5123c27d7478faaa822d0f1f02fc503f_1534_0.png)

Solution :The subgraph H of the Petersen graph obtained by deleting b and the three edges that have b as an endpoint ,shown in Figure 14(b),is homeomorphic to K3,3, with vertex sets {f,d,j}and {e,I,h},since it can be obtained by a sequence of elementary subdivisions,deleting {d,h} and adding {c,h} and {c,d},deleting {e,f} and adding {a,e }and {a,f},and deleting {I,j}and adding {g,I} and {g,j}.Hence,the Petersen graph is not planar.

## 7.8 Graph Coloring

## Definition 1:

A coloring of a simple graph is the assignment of a color to each vertex of the graph so that no two adjacent vertices are assigned the same color

## Vertex coloring and region coloring

**Dual graph:** A region to a vertex; edges connect two vertices if the original regions are adjacent.

![](img/5123c27d7478faaa822d0f1f02fc503f_1538_0.png)

- G=(V,E)
- 
- 1. G中每一个区域Fi用一个顶点vi来表示
- 2. 若Fi与Fj相邻，则vi与vj相邻；
- 3. 若e是区域Fi中的一条悬边，则vi点是增加一条自回路

## Definition 2

The chromatic number of a graph G is the least number of colors needed for a coloring of this graph. Denoted by x(G)

![](img/5123c27d7478faaa822d0f1f02fc503f_1539_0.png)

(1) x(G1)=3, (2)x(G2)=2

## Theorem 1

The Four Color Theorem  The chromatic number of a planar graph is no greater than four.

## Example 1

What are the chromatic numbers of the graphs G and H shown in Figure 3?

**Solution:** The chromatic number of G is at least 3, since the vertices a, b, and c must be assigned different colors. To see if G can be colored with three colors, assign red to a, blue to b, and green to c. Then d can (and must) be colored red since it is adjacent to b and c. Furthermore, e can (and must) be colored green since it is adjacent only to vertices colored red and blue, and f can (and must) be colored blue since it is adjacent only to vertices colored blue and green. This produces a coloring of G using exactly three colors. Figure 4 displays such a coloring.

