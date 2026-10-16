Recall that the block of a disk access (I/O) is much larger than the node of a binary tree. If we use AVL tree for index, accessing a node is actually accessing a block of which most part are useless, as shown below:

![](bbox=[0.07, 0.43, 0.93, 0.73])

an AVL node in a disk block