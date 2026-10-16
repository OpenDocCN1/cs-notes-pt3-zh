```
// Adjust BF's of nodes on path from a to pp. d=+1 implies k
// is inserted in the left subtree of a and d=-1 in the right.
// The BF of a will be changed later.
int d;
AvlNode<K, E> *b,   // child of a
    *c;   // child of b
if (k>a→key) { b=p=a→rightChild; d=-1;}
else { b=p=a→leftChild; d=1;}
while (p!=y)
    if (k>p→key) { // height of right increases by 1
        p→bf= -1; p=p→rightChild;
    }
    else { // height of left increases by 1
        p→bf= 1; p=p→leftChild;
    }
```