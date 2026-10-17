
## Connectivity vs Isomorphism

+   Idea: The number and size of connected components and circuits are further invariants with respect to isomorphism of simple graphs.

+   Example: Are these two graphs isomorphic?

![](img/47b87ec6fe4fa238d13429358848c545_596_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_596_1.png)

+   Solution: No, because the right graph contains circuits of length 3, while the left graph does not.

## Homework for Section 9.4

## Section 9.4

+   - 2
+   - 5
+   - 12
+   - 21

## 0812210

## Sets and Graphs

Ch 9.5 Euler and Hamilton Paths

Spring 2010
Mao Xiaoguang

## The bridges of Königsberg

The town of Königsberg (East Prussia; now Kaliningrad, Russia) is divided in four sections with seven bridges

![](img/47b87ec6fe4fa238d13429358848c545_599_0.png)

Is it possible to start somewhere and return to that point crossing all bridges exactly once?

## Euler Paths and Circuits

The Seven bridges of Königsberg

![](img/47b87ec6fe4fa238d13429358848c545_600_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_600_1.png)

## Euler Paths and Circuits

+   An *Euler path* is a path using every edge of the graph $G$ exactly once.

+   An *Euler circuit* is an Euler path that returns to its start.

## Does this graph have an Euler circuit?

No.

![](img/47b87ec6fe4fa238d13429358848c545_601_0.png)

## Necessary and Sufficient Conditions

+   - How about multigraphs?
+   - A connected multigraph has a Euler circuit iff *each of its vertices has an even degree*.
+   - A connected multigraph has a Euler path but not an Euler circuit iff *it has exactly two vertices of odd degree*.

## Proof: “Only if” direction

Suppose that a graph has an Euler circuit. Then the graph must be connected. The Euler circuit starts at a vertex v. Every time any vertex other the last vertex in the circuit is entered (including v if it is visited multiple times), the circuit must leave this vertex. Thus, the edges entering and leaving each vertex are paired, adding 2 to that vertex’s degree each time it is visited. 2 is also added to v’s degree for the first and last edge, so all vertex degrees are even.

## Proof: “If” direction

+   Suppose that all vertices have even degrees. We construct an Euler circuit as follows: Start at an arbitrary vertex, and construct a path randomly, until we can’t do so anymore (this will happen at some point because the graph is finite).

+   This process must terminate at v, because each time the path passes from a vertex u it subtracts 2 from the remaining edges incident to u, and those are an even number. Therefore, we can always leave any vertex other than v.

## Proof: “If” direction

We have therefore constructed a simple circuit. Does this use all edges? If not, consider the subgraphs obtained by deleting the circuit we just constructed. Because the original graph is connected, these subgraphs will have at least a vertex in common with our path. Follow the above process in each such subgraph, and splice the circuits together to obtain an Euler circuit for the original graph.

## Example

Which of the following graphs has an Euler circuit?

![](img/47b87ec6fe4fa238d13429358848c545_606_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_606_1.png)

![](img/47b87ec6fe4fa238d13429358848c545_606_2.png)

yes
(a, e, c, d, e, b, a)

no

no

## Example

Which of the following graphs has an Euler path?

![](img/47b87ec6fe4fa238d13429358848c545_607_0.png)

![](img/47b87ec6fe4fa238d13429358848c545_607_1.png)

![](img/47b87ec6fe4fa238d13429358848c545_607_2.png)

yes
(a, e, c, d, e, b, a)

no

yes
(a, c, d, e, b, d, a, b)

## Euler Path in Directed Graphs

![](img/47b87ec6fe4fa238d13429358848c545_609_0.png)

H₁

NO

![](img/47b87ec6fe4fa238d13429358848c545_609_1.png)

H₂

(a, g, c, b, g, e, d, f, a)

![](img/47b87ec6fe4fa238d13429358848c545_609_2.png)

H₃

(c, a, b, c, d, b)
