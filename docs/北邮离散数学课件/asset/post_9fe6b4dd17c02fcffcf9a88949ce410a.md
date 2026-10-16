
## Hasse Diagrams（哈斯图）

- Hasse Diagram is the digraph of a partial order on a finite set *A* that
  - deletes all self-cycles;
  - eliminates all edges that are implied by the transitive property;
  - draws the digraph with all edges pointing upward.

关系图

哈斯图

$A_3=\{2,3,6,12,24,36\}$ 中，$\le$ 为 $A_3$ 中的整除关系，$\langle A_3,\le\rangle$ 的哈斯图：

![](img/c25dfd82fc242c2db53bc942dcad6885_1264_0.png)

## Isomorphism（同构）

- Let $(A,\le)$ and $(A',\le')$ be posets and let $f:A\to A'$ be a one-to-one correspondence between $A$ and $A'$. The function $f$ is called an *isomorphism* from $(A,\le)$ to $(A',\le')$ if, for any $a$ and $b$ in $A$,
  $a\le b$ if and only if $f(a)\le' f(b)$.
- If $f:A\to A'$ is an isomorphism, we say that $(A,\le)$ and $(A',\le')$ are *isomorphic posets*.

### Isomorphism: Example

- Let $(\mathbb{Z}^+,\le)$ and $(\mathbb{E}^+,\le)$ be posets. The function $f:\mathbb{Z}^+\to\mathbb{E}^+$ given by $f(a)=2a$ is an *isomorphism* from $(\mathbb{Z}^+,\le)$ to $(\mathbb{E}^+,\le)$.
- Proof:
  - First, $f$ is onto and one-to-one.
  - Second, $a\le b$ iff $2a\le 2b$.

### Principle of Correspondence（对应性原理）

Suppose that $f:A\to A'$ is an isomorphism from a poset $(A,\leqslant)$ to a poset $(A',\leqslant')$. Suppose also that $B$ is a subset of $A$, and $B'=f(B)$ is the corresponding subset of $A'$. Then

If the elements of $B$ have any property relating to one another or to other elements of $A$, and if this property can be defined entirely in terms of the relation $\leq$, then the elements of $B'$ must possess exactly the same property, defined in terms of $\leq'$.

Two finite isomorphic posets must have the same Hasse diagram.

### Example

Let $A=\{1,2,3,6\}$ and $\le$ be the relation $|$ (divides).

Let $X=\{a,b\}$, $A'=P(X)=\{\emptyset,\{a\},\{b\},\{a,b\}\}$, and $\le'$ be set containment, $\subseteq$.

![](img/c25dfd82fc242c2db53bc942dcad6885_1268_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1268_1.png)

$f(1)=\emptyset$, $f(2)=\{a\}$, $f(3)=\{b\}$, $f(6)=\{a,b\}$.

## Extremal Elements（极值元素）

- *maximal element*（极大元）
- *minimal element*（极小元）
- *greatest element*（最大元）
  - denoted by $1$ and often called the *unit element*（单位元）
- *least element*（最小元）
  - denoted by $0$ and often called the *zero element*（零元）

### Maximal (minimal) element

- An element $a\in A$ is called a **maximal element** of $A$ if there is no element $c$ in $A$ such that $a<c$.
- An element $b\in A$ is called a **minimal element** of $A$ if there is no element $c$ in $A$ such that $c<b$.

### 定义

$\langle A,\le\rangle$ 为偏序集，且 $B$ 是 $A$ 的子集。对于 $B$ 中一个 $b$，若 $B$ 中没有任何 $x$ 满足 $b\neq x$ 且 $b\le x$，则称 $b$ 为 $B$ 的极大元；若 $B$ 中没有任何 $x$ 满足 $b\neq x$ 且 $x\le b$，则称 $b$ 为 $B$ 的极小元。

### 例

$A=\{2,3,5,7,14,15,21\}$

$B=\{2,7,3,21,14\}$

极大元集 $\{14,21\}$

极小元集 $\{2,7,3\}$

当 $B=A$ 时：

极大元为 $14,15,21$

极小元为 $2,3,5,7$

哈斯图：

![](img/c25dfd82fc242c2db53bc942dcad6885_1273_0.png)

### Theorem 1

Let $A$ be a finite nonempty poset with partial order $\le$. Then $A$ has at least one maximal element and at least one minimal element.

## Topological Sorting（拓扑排序）

- If $A$ is a poset with partial order $\le$, we sometimes need to find *a linear order* for the set $A$ that will merely be an extension of the given partial order in the sense that if $a\le b$, then $a\prec b$.
- The process of constructing a linear order such as $\prec$ is called *topological sorting*.

![](img/c25dfd82fc242c2db53bc942dcad6885_1276_0.png)

- Find a compatible total ordering for the poset $(\{1,2,4,5,12,20\}, |)$.
- Find an ordering of the tasks of a software project if the Hasse diagram for the tasks of the project is as shown. (P581 64)

### SORT Algorithm

For finding a topological sorting of a finite poset $(A,\le)$:

1. Choose a minimal element $a$ of $A$.
2. Make $a$ the next entry of SORT and replace $A$ with $A-\{a\}$.
3. Repeat steps 1 and 2 until $A=\{\}$.

End of Algorithm.

## Greatest (least) element

- An element $a\in A$ is called a **greatest element** of $A$ if $x\le a$ for all $x\in A$.
- An element $a\in A$ is called a **least element** of $A$ if $a\le x$ for all $x\in A$.
- The greatest element of a poset, if it exists, is denoted by $1$, and is often called the **unit** element. Similarly, the least element is called **zero** element.
