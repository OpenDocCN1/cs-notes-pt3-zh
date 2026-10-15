
## Graph Terminology
- Mathematicians often use the words *vertex* and *edge* for the structures that computer scientists call *node* and *arc*. We’ll stick with the computer science names, but you might see their mathematical counterparts in algorithmic descriptions.
- The nodes to which a particular node is connected are called its *neighbors*.
- In an undirected graph, the number of connections from a node is called its *degree*. In a directed graph, the number of arcs leading outward is called the *out-degree*, and the number of arcs leading inward is called the *in-degree*.
- A series of arcs that connect two nodes is called a *path*. A path that returns to its starting point is called a *cycle*.
- A graph in which there is a path between every pair of nodes is said to be *connected*.

## 图计算
- 最近我们试图将淘宝的交易记录中的物品和人组成一个对分网络（bipartite network）。对于这个网络的，我们有许多有趣的问题：这个网络中节点的度分布会是什么样？在这个网络中，是否也存在“权威节点”？是否也有所谓的“小世界现象”。工欲善其事必先利其器，在回答这个问题前，如何存储这个图（上亿个节点，几十亿条边），如何快速地将图算法应用到这个图上

## 幂律分布
![](img/af430dff16b82a0fe61ce7dee05dcf9c_678_0.png)
![](img/af430dff16b82a0fe61ce7dee05dcf9c_678_1.png)

## 无标度网络(自然图)
![](img/af430dff16b82a0fe61ce7dee05dcf9c_679_0.png)
Internet、电子邮件网络、电影演员合作网络、引文关系网络的节点的度都符合幂律分布

## Internet拓扑图
![](img/af430dff16b82a0fe61ce7dee05dcf9c_680_0.png)

## Designing a Graph Interface
- To take maximum advantage of the intuition that people have with graphs, it makes sense to design a graph package in C++ so that it adheres as closely as possible to the way graphs in mathematics. In particular, the idea that a graph is a set of nodes together with a set of arcs should be clear from the definition.
- Both nodes and arcs have some properties that are closely tied to the graph in which they belong. Each node, for example, must keep track of the arcs that lead to its neighbors. In much the same way, each arc needs to know what nodes it connects.
- At the same time, both nodes and arcs are likely to contain other information that depends on the application, such as the name of a node or the cost of traversing an arc.

## Three Strategies
- 1. *Use low-level structures.* This design uses the structure types `Node` and `Arc` to represent the components of a graph. This model gives clients complete freedom to extend these structures but offers no support for graph operations.

## The low-level graphtypes.h Interface
```
/*
 * File: graphtypes.h
 * -------------------
 * This file defines low-level data structures that represent graphs.
 */

#ifndef _graphtypes_h
#define _graphtypes_h

#include <string>
#include "map.h"
#include "set.h"

struct Node;      /* Forward references to these two types so  */
struct Arc;       /* that the C++ compiler can recognize them. */

/*
 * Type: SimpleGraph
 * -----------------
 * This type represents a graph and consists of a set of nodes, a set of
 * arcs, and a map that creates an association between names and nodes.
 */

struct SimpleGraph {
    Set<Node *> nodes;
    Set<Arc *> arcs;
    Map<std::string,Node *> nodeMap;
};
```

## The low-level graphtypes.h Interface
```
/*
 * Type: Node
 * --------
 * This type represents an individual node and consists of the
 * name of the node and the set of arcs from this node.
 */

struct Node {
    std::string name;
    Set<Arc *> arcs;
};

/*
 * Type: Arc
 * --------
 * This type represents an individual arc and consists of pointers
 * to the endpoints, along with the cost of traversing the arc.
 */

struct Arc {
    Node *start;
    Node *finish;
    double cost;
};

#endif
```

## Three Strategies
- 1. *Use low-level structures.* This design uses the structure types `Node` and `Arc` to represent the components of a graph. This model gives clients complete freedom to extend these structures but offers no support for graph operations.
- 2. *Define classes for each of the component types.* This design uses the `Node` and `Arc` classes to define the structure. In this model, clients define subclasses of the supplied types to particularize the graph data structure to their own application.
- 3. *Adopt a hybrid strategy.* This design defines a `Graph` class but parameterizes that class so that it can use any structures or objects as the node and arc types. This strategy retains the flexibility of the low-level model and avoids the complexity associated with the class-based approach.
