Actually, leaf nodes can be record buffer[0] to buffer[k-1]. The node number of Buffer[i] in the tree is k+i.

Now record pointed by the root (key==6) is output, buffer[3] is empty, the next record from run 3 (key ==15) is input to buffer[3].

To reconstruct the tree, tournament has to be played along the path from node 11 to the root.

As in the next slide: