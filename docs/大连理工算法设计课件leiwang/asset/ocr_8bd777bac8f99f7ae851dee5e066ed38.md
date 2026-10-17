# # Minimizing running time

We’ve been analyzing running time in terms of _h_ (the height of the binary search tree), instead of _n_ (the number of nodes in the tree).

+   - **Problem:** Worst case for binary search tree is \(\Theta(n)\)—no better than linked list.

+   - **Solution:** Guarantee small height (balanced tree)—_h_ = _O_(lg_n_).

In later chapters, by varying the properties of binary search trees, we will be able to analyze running time in terms of _n_.

+   - **Method:** Restructure the tree if necessary. Nothing special is required for querying, but there may be extra work when changing the structure of the tree (inserting or deleting).