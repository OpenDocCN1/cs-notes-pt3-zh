# 本章作业

+   1. 设某二叉树的先序遍历序列为:ABCDEFFGGI，中序遍历序列为:BCAEDGHFI:
+      （1）试画出该二叉树对应的后序线索二叉树；
+      （2）将（1）所得的二叉树转化为对应的树或森林；
+      （3）设具有四个结点的二叉树的前序遍历序列为 a b c d；S 为长度等于四的由 a，b，c，d 排列构成的字符序列，若任取 S 作为上述算法的中序遍历序列，试问是否一定能构造出相应的二叉树，为什么？试列出具有四个结点二叉树的全部分形态及相应的中序遍历序列。

+   2. 试编写算法，判断两颗棵以二叉链表表示的二叉树 p 和 q 是否相似。
+      bool Similar(bitptr p, bitptr q) //若相似函数返回TRUE，否则为FLASE

+   3. 编写算法判断一棵二叉树是否为完全二叉树。
+      bool JudgeComplete(bitptr bt)

第2.3题算法设计时二叉树均采用如下结构存储

```
typedef struct node
{
    elemtype data ;
    struct node *lchild, *rchild;
}btnode, *bitptr ;
```