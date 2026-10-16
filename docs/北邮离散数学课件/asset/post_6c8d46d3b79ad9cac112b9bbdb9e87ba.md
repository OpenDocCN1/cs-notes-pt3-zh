
## Flows

- Mathematically, a *flow* （流量） in a network $N$ is a function that assigns to each edge $(i, j)$ of $N$ a nonnegative number $F_{ij}$ that does not exceed $C_{ij}$.
- *Conservation of flow* （流量守恒）
- *Value of the flow*

## Flows

- We can represent a flow F by labeling each edge (i, j) with the pair (C_ij, F_ij)

![](img/c25dfd82fc242c2db53bc942dcad6885_1725_0.png)

- Here value(F) = 5

## # Maximum Flows（最大流量）

- For any network an important problem is to determine the maximum value of a flow through the network and to describe a flow that has the maximum value.
- For obvious reasons this is commonly referred to the *maximum flow problem*.

## Example 2

- Even for a small network, we need a systematic procedure for solving the maximum flow problem.

![](img/c25dfd82fc242c2db53bc942dcad6885_1727_0.png)

(a)

![](img/c25dfd82fc242c2db53bc942dcad6885_1727_1.png)

(b)

## Virtual Flow

- Let N be a network and let G be the symmetric closure of N.
- Choose a path in G and let an edge (i,j) in this path.
- If (i,j) ∈ N and e_ij = C_ij - F_ij > 0, then we say this edge has positive excess capacity.
- If (i,j) is not an edge of N then we are traveling this edge in the wrong direction. E_ij = F_ji if F_ji > 0. Increasing flow through edge(i,j) will have the effect of reducing F_ji.

## LABELING ALGORITHM

- Let N be a network with n nodes and G be the symmetric closure of N. All edges and paths used are in G.
- Begin with all flows set to 0.
- As we proceed, it will be convenient to track the excess capacities in the edges and how they change rather than tracking the increasing flows.
- When the algorithm terminates, it is easy to find the maximum flow from the final excess capacities.

## Step 1

- Let $N_1$ be the set of all nodes connected to the source by an edge with positive excess capacity.
- Label each $j$ in $N_1$ with $[E_j, I]$, where $E_j$ is the excess capacity $e_{Ij}$ of edge $(I, j)$.
- The I in the label indicates that $j$ is connected to the source, node I.

## Step 2

- Let node \(j\) in \(N_1\) be the node with smallest node number and let \(N_2(j)\) be the set of all unlabeled nodes, other than the source, that are joined to node \(j\) and have positive excess capacity.
- Suppose that node \(k\) is in \(N_2(j)\) and \((j,k)\) is the edge with positive excess capacity. Label node \(k\) with \([E_k,j]\), where \(E_k\) is the minimum of \(E_j\) and the excess capacity \(e_{jk}\) of edge \((j,k)\).
- When all the nodes in \(N_2(j)\) are labeled in this way, repeat this process for the other nodes in \(N_1$. Let
\[
N_2 = \bigcup_{j\in N_1} N_2(j)
\]

## Step 3

- Repeat Step 2, labeling all previously unlabeled nodes $N_3$ that can be reached from a node in $N_2$ by an edge having positive excess capacity.
- Continue this process forming sets $N_4$, $N_5$. . . until after a finite number of steps either
- (i) the sink has not been labeled and no other nodes can be labeled. It can happen that no nodes have been labeled; remember that the source is not labeled. or
- (ii) the sink has been labeled.

## Step 4

- In case (i), the algorithm terminates and the total flow then is a maximum flow.

## Step 5

- In case (ii) the sink, node n, has been labeled with [$E_n$, $m$] where $E_n$ is the amount of extra flow that can be made to reach the sink through a path $\pi$.

## Step 5

- We examine π in reverse order.
- If edge (i, j) ∈ N, then we increase the flow in (l, j) by E_n and decrease the excess capacity e_ij by the same amount. Simultaneously, we increase the excess capacity of the (virtual) edge (j, i) by E_n since there is that much more flow in (i, j) to reverse.
- If, on the other hand, (i, j) ∉ N, we decrease the flow in (j, i) by E_n and increase its excess capacity by E_n. We simultaneously decrease the excess capacity in (i, j) by the same amount, since there is less flow in (i, j) to reverse.
- We now have a new flow that is E_n units greater than before and we return to Step 1.
