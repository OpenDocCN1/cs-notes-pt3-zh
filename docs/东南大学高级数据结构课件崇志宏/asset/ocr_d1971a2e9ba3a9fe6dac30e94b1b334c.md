# Operations on Splay Trees (cont)

+   - remove
+     - splay element to be removed
+       - if the element to be deleted is not in the tree, the node last visited on the search path is splayed
+     - disconnect left and right subtrees from root
+     - do one or both of:
+       - splay max item in T_L (then T_L has no right child)
+       - splay min item in T_R (then T_R has no left child)
+     - connect other subtree to empty child of root