# # int id₁, id₂, id₃的分析树的依赖图

```
a4:=int;
a5:=a4
addtype (id3.entry,a5);
a7:=a5;
addtype (id2.entry,a7);
a9:=a7
addtype (id1.entry,a9);
```

![](bbox=[0.05, 0.1, 0.55, 0.75])