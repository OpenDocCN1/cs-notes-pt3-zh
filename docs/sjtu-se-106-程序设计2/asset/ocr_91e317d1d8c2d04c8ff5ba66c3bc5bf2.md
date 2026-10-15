# Designing a Graph Interface

+   - To take maximum advantage of the intuition that people have with graphs, it makes sense to design a graph package in C++ so that it adheres as closely as possible to the way graphs in mathematics. In particular, the idea that a graph is a set of nodes together with a set of arcs should be clear from the definition.
+   - Both nodes and arcs have some properties that are closely tied to the graph in which they belong. Each node, for example, must keep track of the arcs that lead to its neighbors. In much the same way, each arc needs to know what nodes it connects.
+   - At the same time, both nodes and arcs are likely to contain other information that depends on the application, such as the name of a node or the cost of traversing an arc.