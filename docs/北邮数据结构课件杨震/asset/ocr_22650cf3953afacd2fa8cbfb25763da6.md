# 2.3 单链表

结点的物理表示

value next

数据域 指针域

first

两种基本形式

头指针first

头指针

首元结点

头结点

首元结点

头结点的 作用：插入和删除 第一个数据元素时不必 对头指针进行特殊处理。

空表：
first=NULL

first

带头节点单链表判空：
first->next!=NULL