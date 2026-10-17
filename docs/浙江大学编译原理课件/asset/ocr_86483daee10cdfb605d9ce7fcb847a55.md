# # 4.2.4 Syntax Tree Construction in LL(1) Parsing

+   - It is more difficult for LL(1) to adapt to syntax tree construction.

+   - (1) The structure of the syntax tree can be obscured by left factoring and left recursion removal;
+   - (2) The parsing stack represents only predicated structure, not structure that have been actually seen.

# ## The solution:

+   - (1) An extra stack is used to keep track of syntax tree nodes, and
+   - (2) “action” markers are placed in the parsing stack to indicate when and what actions on the tree stack should occur.

![](bbox=[0.778, 0.671, 0.998, 0.997])

![](bbox=[0.0, 0.917, 0.114, 0.997])