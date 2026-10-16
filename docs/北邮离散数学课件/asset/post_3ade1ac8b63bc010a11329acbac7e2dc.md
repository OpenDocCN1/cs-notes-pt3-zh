
![](img/c25dfd82fc242c2db53bc942dcad6885_1392_0.png)

## E7: Call Graphs

![](img/c25dfd82fc242c2db53bc942dcad6885_1393_0.png)

## Precedence graph of statement execution

© The McGraw-Hill Companies, Inc. all rights reserved.

- S₁ a := 0
- S₂ b := 1
- S₃ c := a + 1
- S₄ d := b + a
- S₅ e := d + 1
- S₆ e := c + d

![](img/c25dfd82fc242c2db53bc942dcad6885_1395_0.png)

## Roadmaps

![](img/c25dfd82fc242c2db53bc942dcad6885_1396_0.png)

This is a GPS trajectory dataset collected in (Microsoft Research Asia) [GeoLife](https://www.microsoft.com/en-us/research/publication/geolife-gps-trajectory-dataset-user-guide/) project by 182 users in a period of over two years (from April 2007 to August 2012). This trajectory dataset can be used in many research fields, such as mobility pattern mining, user activity recognition, location-based social networks, location privacy, and location recommendation. The following heat maps visualize its distribution in Beijing.

## § 10.2: Graph Terminology

You need to learn the following terms:

- *Adjacent, connects, endpoints, degree, initial, terminal, in-degree, out-degree, complete, cycles, wheels, n-cubes, bipartite, subgraph, union.*

### [定义]孤立顶点：

若 a ∈ V，a 不与其他顶点相邻，称 a 为孤立顶点/isolated。

### [定义]自回路：

若 (a, a) ∈ E（或 {a, a} ∈ E），称边 (a, a)（或 {a, a}）是自回路/loop。

### [定义]顶点的次：

在无向图 G 中，与 a 相邻的顶点的数目称为 a 的次或度/degree。记为 deg(a) 或 d(a)。

在有向图 G 中，以 a 为终点的边的条数称为 a 的入次或入度/in-degree。记为 deg⁻(a) 或 d⁻(a)。以 a 为起点的边的条数称为 a 的出次或出度/out-degree。记为 deg⁺(a) 或 d⁺(a)。

### Adjacency

Let G be an undirected graph with edge set E. Let e∈E be (or map to) the pair {u,v}. Then we say:

- u, v are adjacent / neighbors / connected.
- Edge e is incident with vertices u and v.
- Edge e connects u and v.
- Vertices u and v are endpoints of edge e.

### Degree of a Vertex

- Let $G$ be an undirected graph, $v \in V$ a vertex.
- The *degree* of $v$, $\deg(v)$, is its number of incident edges. (Except that any self-loops are counted twice.)
- A vertex with degree 0 is called *isolated*.
- A vertex of degree 1 is called *pendant*.

### Handshaking Theorem

- Let $G$ be an undirected (simple, multi-, or pseudo-) graph with vertex set $V$ and edge set $E$. Then

  $$\sum_{v\in V} \deg(v) = 2|E|$$

- **Corollary:** Any undirected graph has an even number of vertices of odd degree.

### Directed Adjacency

- Let $G$ be a directed (possibly multi-) graph, and let $e$ be an edge of $G$ that is (or maps to) $(u,v)$. Then we say:
  - $u$ is adjacent to $v$, $v$ is adjacent from $u$
  - $e$ comes from $u$, $e$ goes to $v$.
  - $e$ connects $u$ to $v$, $e$ goes from $u$ to $v$
  - the initial vertex of $e$ is $u$
  - the terminal vertex of $e$ is $v$

### Directed Degree

- Let G be a directed graph, v a vertex of G.
  - The in-degree of v, **deg⁻(v)**, is the number of edges going to v.
  - The out-degree of v, **deg⁺(v)**, is the number of edges coming from v.
  - The degree of v, **deg(v)** := **deg⁻(v)** + **deg⁺(v)**, is the sum of v's in-degree and out-degree.

### Directed Handshaking Theorem

- Let $G$ be a directed (possibly multi-) graph with vertex set $V$ and edge set $E$. Then:

  $$\sum_{v\in V}\deg^-(v)=\sum_{v\in V}\deg^+(v)=\frac{1}{2}\sum_{v\in V}\deg(v)=|E|$$

- Note that the degree of a node is unchanged by whether we consider its edges to be directed or undirected.

### Special Graph Structures

Special cases of undirected graph structures:

- Complete graphs Kₙ
- Cycles Cₙ
- Wheels Wₙ
- n-Cubes Qₙ
- Bipartite graphs
- Complete bipartite graphs Kₘ,ₙ

### Complete Graphs

- For any $n \in \mathbb{N}$, a *complete graph* on $n$ vertices, $K_n$, is a simple graph with $n$ nodes in which every node is adjacent to every other node: $\forall u, v \in V: u \neq v \leftrightarrow \{u, v\} \in E$.

![](img/c25dfd82fc242c2db53bc942dcad6885_1408_0.png)

> Note that $K_n$ has $\sum_{i=1}^{n-1} i = \frac{n(n-1)}{2}$ edges.
