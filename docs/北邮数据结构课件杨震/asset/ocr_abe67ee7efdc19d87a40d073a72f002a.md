```
CopyGList(T->ptr.hp, L->ptr.hp);
```

// 复制求得表头T->ptr.hp的一个副本L->ptr.hp

```
CopyGList(T->ptr.tp, L->ptr.tp);
```

// 复制求得表尾T->ptr.tp 的一个副本L->ptr.tp

语句 CopyGList(T->ptr.hp, L->ptr.hp);

等价于

```
CopyGList(newhp, L->ptr.tp);
```

```
T->ptr.hp = newhp;
```