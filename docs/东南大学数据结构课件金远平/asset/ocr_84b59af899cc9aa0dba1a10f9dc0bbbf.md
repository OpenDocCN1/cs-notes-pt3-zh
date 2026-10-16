But it may not be the optimal binary search tree to use when different identifiers are to be searched with different probabilities.

To find an optimal binary search tree for a given static file, we must first decide on a cost measure for search trees.

In the binary search tree *search algorithm*, an identifier at level k needs k iterations to find. Thus it is reasonable to use the level number of a node as its cost.

Consider 2 search trees of Fig. 10.2.