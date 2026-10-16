

## FP-Growth：一个示例

## 第 1 步：构造条件模式基

- 从 FP 树中频繁项头表中底部开始
- 通过跟随每个频繁项的链接遍历 FP 树
- 累积该项的所有 **转换后的前缀路径** 以形成 **条件模式基**

| Item | head |
|---|---|
| f |  |
| c |  |
| a |  |
| b |  |
| m |  |
| p |  |

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_113_0.png)

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_113_1.png)

### Conditional pattern bases

| item | cond. pattern base |
|---|---|
| p | fcam:2, cb:1 |
| m | fca:2, fcab:1 |
| b | fca:1, f:1, c:1 |
| a | fc:3 |
| c | f:3 |
| f | {} |

## Properties of FP-Tree

- Node-link property
  - 对于任何频繁项 $a_i$，包含 $a_i$ 的所有可能频繁模式都可以通过从 FP 树头表中 $a_i$ 的头开始，沿着 $a_i$ 的节点链接跟随而获得。
- Prefix path property
  - 为了计算路径 $P$ 中节点 $a_i$ 的频繁模式，只需累积 $a_i$ 在 $P$ 中的前缀子路径，并且其频率计数应与节点 $a_i$ 相同。

## 第 2 步：构造条件 FP 树

- 对于每个模式基
  - 累积基中每个项的计数
  - 为模式基的频繁项构造条件 FP 树

| Header Table |
| Item | head |
| f | 4 |
| c | 4 |
| a | 3 |
| b | 3 |
| m | 3 |
| p | 3 |

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_115_0.png)

## FP-Growth

## 第 3 步：递归挖掘条件 FP 树

conditional FP-tree of "m": (fca:3)

Frequent Pattern

f:3
c:3
a:3

add "a"

add "c"

add "f"

conditional FP-tree of "am": (fc:3)

Frequent Pattern

f:3
c:3

conditional FP-tree of "cm": (f:3)

Frequent Pattern

f:3

add "f"

conditional FP-tree of "fm": 3

Frequent Pattern

conditional FP-tree of "fam": 3

Frequent Pattern

conditional FP-tree of "fcm": 3

Frequent Pattern

Frequent Pattern

fcam

add "f"

add "c"

conditional FP-tree of "cam": (f:3)

f:3

add "f"

## Principles of FP-Growth

- Pattern growth property
  - 设 α 是 DB 中的频繁项集，B 是 α 的条件模式基，β 是 B 中的一个项集。则 α ∪ β 是 DB 中的频繁项集当且仅当 β 在 B 中频繁。
- “fcabm” 是一个频繁模式吗？
  - “fcab” 是 m 的条件模式基的一个分支
  - “b” 在包含 “fcab” 的事务中不是频繁的
  - “bm” 不是一个频繁项集。

## Conditional Pattern Bases and
Conditional FP-Tree

| Item | Conditional pattern base | Conditional FP-tree |
|---|---|---|
| p | `{(fcam:2), (cb:1)}` | `{(c:3)}\|p` |
| m | `{(fca:2), (fcab:1)}` | `{(f:3, c:3, a:3)}\|m` |
| b | `{(fca:1), (f:1), (c:1)}` | `Empty` |
| a | `{(fc:3)}` | `{(f:3, c:3)}\|a` |
| c | `{(f:3)}` | `{(f:3)}\|c` |
| f | `Empty` | `Empty` |

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_118_0.png)

## Single FP-tree Path Generation

- 假设 FP 树 T 有一条单一路径 P。T 的完整频繁模式集合可以通过枚举 P 的子路径的所有组合来生成

{}
|
f:3
|
c:3
|
a:3
m-conditional FP-tree

All frequent patterns concerning m: combination of {f, c, a} and m

- m,
- fm, cm, am,
- fcm, fam, cam,
- fcam

## Summary of FP-Growth Algorithm

- 挖掘频繁模式可以看作是首先挖掘 1-项集，然后通过在其条件模式基上递归挖掘，逐步增长每个 1-项集
- 通过一组条件模式基，将频繁 k-项集挖掘问题转化为一系列 k 个频繁 1-项集挖掘问题

## Efficiency Analysis

**Facts: usually**

- 1. FP-tree 比 DB 的大小小得多
- 2. 模式基比原始 FP 树小
- 3. 条件 FP 树比模式基小
- ➔ 挖掘过程在一个通常要小得多的模式基和条件 FP 树集合上工作
- ➔ 分而治之和显著的规模缩小

