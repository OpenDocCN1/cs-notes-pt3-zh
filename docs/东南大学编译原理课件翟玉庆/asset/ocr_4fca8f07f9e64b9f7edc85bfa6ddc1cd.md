# Chapter 9 Code optimization

# Section 1 Basic Blocks and flow graphs

# 2. Partition into basic blocks

1) We first determine the set of leaders. The rules:

+   - (1) The first statement is a leader.
+   - (2) Any statement that is the target of a conditional or unconditional goto is a leader.
+   - (3) Any statement that immediately follows a goto or conditional goto statement is a leader.