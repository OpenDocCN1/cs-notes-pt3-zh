# CHAPTER 4  Syntax ANALYSIS

# Section 2 TOP-DOWN PARSING

# 8、 Transition diagram based Predictive Parsers

# 2) Transition diagram based predictive parsing

+   - Begins in the start state for the start symbol;
+   - When it is in state s with an edge labeled by terminal a to state t, and the next input symbol is a, then the parser moves the input cursor and goes to state t
+   - When it is in state s with an edge labeled by non-terminal A to state t, then the parser instead goes to the start state for A, without moving the input cursor. If it ever reaches the final state for A, it immediately goes to state t, in effect having read A from the input during the time it moved from state s to t.