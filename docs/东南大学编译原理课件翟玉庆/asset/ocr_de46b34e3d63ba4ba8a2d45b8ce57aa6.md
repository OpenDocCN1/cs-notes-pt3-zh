# Chapter 5 Syntax-Directed Translation

# Section 1 Syntax-Directed Definitions

# 1、Definitions

4)Dependency graph

+   - A graph that represents dependencies between attributes set up by the semantic rules

Notes: (1)From the dependency graph,we can derive an evaluation order for the semantic rules

(2)Evaluation of the semantic rules defines the values of the attributes at the nodes in the parse tree

(3)Semantic rule may have side effects, e,g, printing a value