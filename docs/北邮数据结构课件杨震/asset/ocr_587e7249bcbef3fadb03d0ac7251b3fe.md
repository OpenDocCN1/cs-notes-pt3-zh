7. 试给出下列有关并查集的操作序列的运算结果：
merge(1,2), merge(3,4), merge(3,5), merge(1,7),
merge(3,6), merge(8,9), merge(1,8), merge(3,10),
merge(3,11), merge(3,12), merge(3,13),
merge(14,15), merge(16,0), merge(14,16), merge(1,3),
merge(1,14)。

# 要求

+   （1）对于merge(i,j)，以i作为j的双亲；
+   （2）按和为根的树的高度实现merge(i,j)，高度大者为高度小者的双亲；
+   （3）按和为根的树的结点个数实现merge(i,j)，结点个数大者为结点个数小者的双亲。