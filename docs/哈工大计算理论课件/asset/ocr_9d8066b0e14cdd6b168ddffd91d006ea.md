# Searching in Graphs

+   - Let’s NTM M decides A in O(log n) space
+   - Given an input w, we construct <G, s, t> in log space
+     ◦ G is a directed graph that contains a path from s to t iff M accepts w
+     ◦ The nodes of G are the configurations of M on w
+     ◦ For configuration c1 and c2 of M on w, the pair (c1, c2) is an edge of G if c2 is one of the possible next configuration of M starting from c1
+     ◦ Node s is the start configuration
+     ◦ Machine M is modified to have a unique accept configuration and it is corresponding to node t in G