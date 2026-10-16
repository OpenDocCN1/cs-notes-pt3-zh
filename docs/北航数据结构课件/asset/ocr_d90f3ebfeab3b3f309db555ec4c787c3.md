在Pascal 语言中，可以如下描述一个链结点的结构：

```
TYPE
  nodeptr=↑nodetype
  nodetype=RECORD
    data : datatype;
    lchild, rchild : nodeptr;
  END;
VAR
  T : nodeptr;
```

在C 语言中，一个链结点可以描述为：

```
struct node {
  datatype  data;
  struct node *lchild, *rchild;
}
struct node *T;
```