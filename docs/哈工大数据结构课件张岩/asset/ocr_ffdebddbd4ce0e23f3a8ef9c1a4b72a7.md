# 3.7 树型结构的应用（Cont.）

用树结构表示集合

+   集合的存储结构

```
#define n 元素的个数
typedef int MFSET[n+1];
/* 集合的“型”为MFSET,元素的“型”为int */
```

+   基本操作的实现

```
void Union(int i, int j ,MFSET parent)
{ parent[i]=j;/* 归并，结果树之根为j */
}//O(1)
```

![](bbox=[0.07, 0.65, 0.75, 0.9])