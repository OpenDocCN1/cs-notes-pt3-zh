# CHAPTER 4  Syntax ANALYSIS

# Section 2 TOP-DOWN PARSING

# 8、 Transition diagram based Predictive Parsers

# 1) Transition diagram

+   Note:
+   1. There is one diagram for each non-terminal;
+   2. The labels of edges are tokens or non-terminals;
+   3. If the edge is labeled by a non-terminal A, the parser instead goes to the start state for A, without moving the input cursor;
+   4. When an edge labeled by a non-terminal is followed, a potentially recursive procedure call is made