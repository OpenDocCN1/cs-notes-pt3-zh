# B+-Tree File Organization (Cont.)

![](bbox=[0.05, 0.12, 0.95, 0.58])

Example of B+-tree File Organization

+   - Good space utilization important since records use more space than pointers.
+   - To improve space utilization, involve more sibling nodes in redistribution during splits and merges
+     - Involving 2 siblings in redistribution (to avoid split / merge where possible) results in each node having at least [2n/3] entries