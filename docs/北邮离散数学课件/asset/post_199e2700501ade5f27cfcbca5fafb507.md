
## Trees as Models

- Can use trees to model the following:
  - Saturated hydrocarbons
  - Organizational structures
  - Computer file systems
- In each case, would you use a rooted or a non-rooted tree?

- 树：连通且无回路的无向图。
- 树叶：树中度数为1的结点。
- 分枝或内点：度数大于1的结点。
- 森林：每个连通分支是树的无向图。

## 化学同分异构物

- 甲烷

  ![](img/c25dfd82fc242c2db53bc942dcad6885_1801_0.png)

- 乙烷

  ![](img/c25dfd82fc242c2db53bc942dcad6885_1801_1.png)

- 丙烷

  ![](img/c25dfd82fc242c2db53bc942dcad6885_1801_2.png)

- 丁烷

  ![](img/c25dfd82fc242c2db53bc942dcad6885_1801_3.png)

- 异丁烷

  ![](img/c25dfd82fc242c2db53bc942dcad6885_1801_4.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1802_0.png)

家族树，图书十进制分类，一个组织结构的层次体系，各种运算表达式，判断树。

## 北京邮电大学

### 学术委员会

- 通信工程学院
- 计算机科学与技术学院
- 信息工程学院
- 自动化学院
- 电子工程学院
- 经济管理学院
- 语言学院
- 文法经济学院
- 理学院
- 邮政学院
- 职业技术学院
- 继续教育学院
- 体育部
- 图书馆
- 信息网络中心
- 电路中心
- 出版社
- 校医院
- 北邮通信集团
- 后勤服务产业集团

### 校长

- 学校办公室
- 教务处
- 研究生院
- 监察审计处
- 科技处
- 人事处
- 财务处
- 资产管理处
- 学生事务管理处
- 外事处
- 后勤办公室
- 校园管理与保卫处
- 离退休工作处
- 教育基金会
- 校友会

## Training Dataset

This follows an example from Quinlan's ID3.

| age | income | student | credit_rating | buys_computer |
|---|---|---|---|---|
| <=30 | high | no | fair | no |
| <=30 | high | no | excellent | no |
| 31...40 | high | no | fair | yes |
| >40 | medium | no | fair | yes |
| >40 | low | yes | fair | yes |
| >40 | low | yes | excellent | no |
| 31...40 | low | yes | excellent | yes |
| <=30 | medium | no | fair | no |
| <=30 | low | yes | fair | yes |
| >40 | medium | yes | fair | yes |
| <=30 | medium | yes | excellent | yes |
| 31...40 | medium | no | excellent | yes |
| 31...40 | high | yes | fair | yes |
| >40 | medium | no | excellent | no |

## Output: A Decision Tree for “buys_computer”

![](img/c25dfd82fc242c2db53bc942dcad6885_1807_0.png)

## Presentation of Classification Results

```
dbminer
File Edit Query View Window Options Help
Dim: cost Level: Level0 Class%: 95

revenue(0.00-2000.00)
cost(0.00-1000.00)
region(Europe)
region(Far East)
region(North America)
cost(1000.00-2000.00)
revenue(2000.00-4000.00)
revenue(4000.00-6000.00)
revenue(6000.00+)
revenue(Not Specified)

Classification attribute product
Environmental Line
GO Sport Line
Outdoor Products
```

## Visualization of a **Decision Tree** in SGI/MineSet 3.0

![](img/c25dfd82fc242c2db53bc942dcad6885_1809_0.png)

## Some Tree Theorems

- A tree with n nodes has n-1 edges.
- A full m-ary tree with i internal nodes has n = mi + 1 nodes, and ℓ = (m - 1)i + 1 leaves.
  - Proof: There are mi children of internal nodes, plus the root. And, ℓ = n - i = (m - 1)i + 1. □
  - Thus, given m, we can compute any of i, n, and ℓ from any of the others.

## More Theorems

- **Definition:** The *level* of a node is the length of the simple path from the root to the node.
  - The *height* of a tree is maximum node level.
  - A rooted *m*-ary tree with height *h* is *balanced* if all leaves are at levels *h* or *h*−1.
- **Theorem:** There are at most *m*^h leaves in an *m*-ary tree of height *h*.
  - **Corollary:** An *m*-ary tree with *ℓ* leaves has height *h* ≥ ⌈logₘ ℓ⌉. If *m* is full and balanced then *h* = ⌈logₘ ℓ⌉

## 定理

设有完全 m 叉树，其树叶 leaves 为 t，分支点 nonleaves 数为 i，则 (m - 1)i = t - 1。

![](img/c25dfd82fc242c2db53bc942dcad6885_1812_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1812_1.png)

## 例：28盏灯拟用一个电源插座，问需要多少块四插座接线板？

(m - 1)i = t - 1

(4 - 1)i = 28 - 1，i = 9

需要9个接线板。

## 例：一台三地址计算机，用一个加法指令可求三个数之和，现要计算12个数之和，至少要几次加法指令？

解：

(m - 1)i ≥ t - 1
(3 - 1)i ≥ 12 - 1 = 11
i ≥ 11/2 = 5.5
i = 6，但这种树不唯一，见图示。

![](img/c25dfd82fc242c2db53bc942dcad6885_1815_0.png)

### 图 b

![](img/c25dfd82fc242c2db53bc942dcad6885_1816_0.png)

### 图 c

![](img/c25dfd82fc242c2db53bc942dcad6885_1816_1.png)
