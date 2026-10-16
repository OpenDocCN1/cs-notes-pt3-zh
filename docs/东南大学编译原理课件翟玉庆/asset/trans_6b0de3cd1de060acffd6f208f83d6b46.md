

## 第5章 语法制导翻译

### 第1节 语法制导定义

#### 6、依赖图

**2) 为给定的语法树构造依赖图**

```pseudo
for each node n in the parse tree do
    for each attribute a of the grammar symbol at n do
        construct a node in the dependency graph for a;
for each node n in the parse tree do
    for each semantic rule b = f(c1, c2, ..., ck)
        associated with the production used at n do
        for i = 1 to k do
            construct an edge from the node for ci to the node for b;
```

- 例如，当以下产生式在语法树中使用时，构造依赖图。

| 产生式 | 语义规则 |
|---|---|
| E → E^(1) + E^(2) | E.val = E^(1).val + E^(2).val |

![](img/353f619caa6c5715591f2105bdfa2865_386_0.png)

#### 7、求值顺序

**1) 基本思想**

在 DAG 的拓扑排序中

**2) DAG 的拓扑排序**

节点 m1, m2, ..., mk 的任意一种排序，使得边从排序中靠前的节点指向靠后的节点。

说明：从依赖图的拓扑排序中，我们得到语义规则的求值顺序。

**3) 一个例子**

从此拓扑排序，我们得到以下程序。 （ai 为依赖图中编号为 i 的节点所关联的属性。）

- a4 = real;
- a5 = a4;
- addtype(id3.entry, a5);
- a7 = a5;
- addtype(id2.entry, a7);
- a9 = a7;
- addtype(id1.entry, a9);

**4) 求值语义规则的方法**

语法树方法

为每个输入的语法树构造的依赖图进行拓扑排序，从而得到求值顺序。

说明：如果特定语法树的依赖图存在环，则会失败。

(2) 基于规则的方法

在编译器构造时，与产生式关联的语义规则会被分析。

说明：对于每个产生式，其顺序是预先确定的。

(3) 无视方法

在不考虑语义规则的情况下选择求值顺序。

说明：其顺序限制了可以实现语法制导定义的类别。

说明：基于规则的方法和无视方法无需在编译时显式构造依赖图，因此在编译时间和空间的使用上可以更高效。

#### 8、如何使用语法制导定义来指定翻译

- S-属性定义的自底向上求值
- L-属性定义自顶向下翻译

#### 10、L-属性定义

如果语法制导定义是 L-属性的，则在 A → X1X2...Xn 右侧的 Xj 的每个继承属性，1 ≤ j ≤ n，仅依赖于

1. 产生式中位于 Xj 左侧的符号 X1, X2, ..., Xj-1 的属性，以及

2. A 的继承属性。

- L-属性总能按深度优先顺序求值。
- “L” 表示“left”，因为 L-属性信息似乎从左到右流动。
- 每个 S-属性定义都是 L-属性的，因为定义中的限制仅适用于继承属性。

