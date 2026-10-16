
finger[3].interval = [finger[3].start, 1)

finger[1].start = 2

finger[1].interval = [finger[1].start, finger[2].start)

finger[3].start = 5

finger[2].start = 3

finger[2].interval = [finger[2].start, finger[3].start)

(a)

(b)

finger table keys
start int. succ. 6
1 [1,2) 1
2 [2,4) 3
4 [4,0) 0

finger table keys
start int. succ. 1
2 [2,3) 3
3 [3,6) 3
5 [5,1) 0

finger table keys
start int. succ. 2
4 [4,5) 0
5 [5,7) 0
7 [7,3) 0

(a) The finger intervals associated with node 1. (b) Finger tables and key locations for a net with nodes 0, 1, and 3, and keys 1, 2, and 6.

## Scalable key Location

- With high probability (or under standard hardness assumption), the number of nodes that must be contacted find a successor in an $N$-node network is $O(\log N)$.

## Node Joins

- Each node in Chord maintains a *predecessor pointer*, and can be used work counterclockwise around the identifier circle.
- When a node *n* joins the network:
  - Initialize the predecessor and fingers of node *n*.
  - Update the fingers and predecessors of existing nodes to reflect the addition of *n*.
  - Notify the higher layer software so that it can transfer state (e.g. values) associated with keys that node *n* is now responsible for.

## Failures and Replication

- When a node *n* fails, nodes whose finger tables include *n* must find *n*’s successor.
- Each Chord node maintains a “successor-list” of its r nearest successor on the Chord ring.
- A typical application using Chord might store replicas of the data associated with key at the *k* nodes succeeding the key.

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_202_0.png)

The mean and 1st and 99th percentiles of the number of keys stored per node in a 10⁴ node network.

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_204_0.png)

(a)

The path length as a function of network size.

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_205_0.png)

(b)

The PDF of the path length in the case of a 2¹² node network.

## BATON
A Balanced Tree Structure
for Peer-to-Peer Networks

H. V. Jagadish, Beng Chin Ooi, Quang Hieu Vu

## Related Work

- **P-Grid (CoopIS’01)**
  - Based on a binary prefix tree structure.
  - Can not guarantee *log N search* step boundary
- **P-Tree (WebDB’04)**
  - Based on B+-tree structure and uses CHORD as overlay framework
  - Each node maintains a branch of the B+-tree
  - *Expensive* cost to keep consistency knowledge among nodes
- **Multi-way tree (DBISP2P’04)**
  - Each node maintains links to its parent, its siblings, its neighbors, and its children
  - Can not guarantee *log N search* step boundary

## BATON Architecture

- BATON: BAlanced Tree Overlay Network
- Definition: A tree is balanced if and only if at any node in the

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_208_0.png)

Node m: level=3, number=6 parent=f, leftchild=null, rightchild=r leftadjacent=f, rightadjacent=r

Left routing table:

|  | Node | Left child | Right child | Lower bound | Upper bound |
|---|---|---|---|---|---|
| 0 | l | null | null | l_lower | l_upper |
| 1 | k | p | q | k_lower | k_upper |
| 2 | i | null | null | i_lower | i_upper |

Right routing table:

|  | Node | Left child | Right child | Lower bound | Upper bound |
|---|---|---|---|---|---|
| 0 | n | null | null | n_lower | n_upper |
| 1 | o | s | t | o_lower | o_upper |

Binary Balanced Tree Index Architecture

## Theorems

- *Theorem 1*: The tree is a balanced tree if every node in the tree that has a child also has both its left and right routing tables full (*).

- *Theorem 2*: If a node, say *x*, contains a link to another node, say *y*, in its left or right routing tables, parent node of *x* must also contain a link to parent node of *y* unless the same node is parent of both *x* and *y*.

(*) A routing table is full if none of the valid links is NULL.
