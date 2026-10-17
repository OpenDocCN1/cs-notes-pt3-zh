
## Example

Example I: Are the following two graphs isomorphic?

![](img/47b87ec6fe4fa238d13429358848c545_584_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_584_1.png)

Solution: Yes, they are isomorphic, because they can be arranged to look identical. You can see this if in the right graph you move vertex b to the left of the edge {a, c}.

Then the isomorphism f from the left to the right graph is:

f(a) = e, f(b) = a, f(c) = b, f(d) = c, f(e) = d.

## Example

Example II: How about these two graphs?

![](img/47b87ec6fe4fa238d13429358848c545_585_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_585_1.png)

Solution: No, they are not isomorphic, because they differ in the degrees of their vertices.
Vertex d in right graph is of degree one, but there is no such vertex in the left graph.

## Homework for Section 9.3

## Section 9.3

- 6
- 28
- 31
- 36
- 40
- 55

## 0812210

## Sets and Graphs

Ch 9.4 Connectivity

Spring 2010
Mao Xiaoguang

## Paths of Undirected Graphs

A path of length n from u to v, where n is a positive integer, in an undirected graph is a sequence of edges e₁, e₂, ..., eₙ of the graph such that f(e₁) = {x₀, x₁}, f(e₂) = {x₁, x₂}, ..., f(eₙ) = {xₙ₋₁, xₙ}, where x₀ = u and xₙ = v.

When the graph is simple, we denote this path by its vertex sequence x₀, x₁, ..., xₙ, since it uniquely determines the path.

- The path is a circuit if it begins and ends at the same vertex, that is, if u = v.
- The path or circuit is said to pass through the vertices v₁, v₂, ..., vₙ₋₁ or traverse the edges x₁, x₂, ..., xₙ.
- A path or circuit is simple if it does not contain the same edge more than once.

## Paths of Directed Graphs

- A path of length n from u to v, where n is a positive integer, in a directed multigraph is a sequence of edges e₁, e₂, ..., eₙ of the graph such that f(e₁) = (x₀, x₁), f(e₂) = (x₁, x₂), ..., f(eₙ) = (xₙ₋₁, xₙ), where x₀ = u and xₙ = v.
- When there are no multiple edges in the path, we denote this path by its vertex sequence x₀, x₁, ..., xₙ, since it uniquely determines the path.
- The path is a circuit if it begins and ends at the same vertex, that is, if u = v.
- A path or circuit is called simple if it does not contain the same edge more than once.

## Connected

- An undirected graph is called connected if there is a path between every pair of distinct vertices in the graph.
- For example, any two computers in a network can communicate if and only if the graph of this network is connected.
- Note: A graph consisting of only one vertex is always connected, because it does not contain any pair of distinct vertices.

## Examples

Are the following graphs connected?

![](img/47b87ec6fe4fa238d13429358848c545_591_0.png)

Yes.

![](img/47b87ec6fe4fa238d13429358848c545_591_1.png)

No.

![](img/47b87ec6fe4fa238d13429358848c545_591_2.png)

Yes.

![](img/47b87ec6fe4fa238d13429358848c545_591_3.png)

No.

## Theorem

- Theorem: There is a simple path between every pair of distinct vertices of a connected undirected graph.
- Proof: page 625.
- A graph that is not connected is the union of two or more connected subgraphs, each pair of which has no vertex in common. These disjoint connected subgraphs are called the connected components of the graph.

## Example

What are the connected components in the following graph?

![](img/47b87ec6fe4fa238d13429358848c545_593_0.png)

Solution: The connected components are the graphs with vertices {a, b, c, d}, {e}, {f}, {i, g, h, j}.

## Connectivity of Directed Graphs

- A directed graph is strongly connected if there is a path from a to b and from b to a whenever a and b are vertices in the graph.
- A directed graph is weakly connected if there is a path between any two vertices in the underlying undirected graph.

## Example

Are the following directed graphs strongly or weakly connected?

![](img/47b87ec6fe4fa238d13429358848c545_595_0.png)

Weakly connected, because, for example, there is no path from b to d.

![](img/47b87ec6fe4fa238d13429358848c545_595_1.png)

Strongly connected, because there are paths between all possible pairs of vertices.
