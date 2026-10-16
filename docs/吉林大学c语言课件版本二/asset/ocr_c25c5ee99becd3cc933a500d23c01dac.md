# 遍历单向链表：

遍历是指从头到尾将链表上数据全部加工一遍。可如下左端的算法。但实用中，经常用如下右端的算法来遍历单向链表。

```
p = base;
while (p != NULL) {
    加工 p ->
    p = p-> next;
}
```

```
p0 = NULL;
p = base;
while (p != NULL) {
    加工 p ->
    p0 = p;
    p = p-> next;
}
```