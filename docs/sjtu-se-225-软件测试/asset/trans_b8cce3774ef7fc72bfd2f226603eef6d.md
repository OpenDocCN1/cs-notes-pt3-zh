

## 如何寻找McCabe路径？

### 图的搜索与遍历算法！

- 深度优先算法
- 广度优先算法

![](img/8454895dcf92bedbe5b40d0487077d64_320_0.png)

## Essential Complexity

一般而言，当程序结构良好时，即仅由结构化编程构造组成，它始终可以简化为具有一条路径的图。

![](img/8454895dcf92bedbe5b40d0487077d64_321_0.png)

## 7.1.4 Insights from a Venn Diagram

基于路径的测试，从另一个角度去考虑程序测试的完备性，但是没有考虑数据功能，即使满足DD-路径覆盖，和考虑圈复杂度指标，也仅是测试的下限指标。

如左图：

- S：已说明行为的路径集合；
- P：已编程实现的路径集合；
- T：拓扑可达的路径集合；

区域：

- 1：测试的重点，可测；
- 2、6：已实现的，就应该是拓扑可行的，
- 3：已实现和可达的，应该是有用的！
- 4：已描述的，拓扑可达，却没有实现的；要增加，可测；
- 5：没有实现的已说明路径，不可测，
- 7：未说明，未实现，拓扑可达，测试无意义！

![](img/8454895dcf92bedbe5b40d0487077d64_322_0.png)

可行的和在拓扑结构上可能的路径

## 7.2 Data Flow Testing

数据流测试是指关注变量接收值的位置以及这些值被使用的位置的结构化测试形式。

### 7.2.1 Define/Use Testing

1. 程序图 G(P) 如第 4 章所述构造，以语句片段作为节点，以表示节点序列的边。

2. 节点 n ∈ G(P) 是变量 v ∈ V 的定义节点，记为 DEF(v, n)，当且仅当变量 v 的值由对应于节点 n 的语句片段定义。

3. 节点 n ∈ G(P) 是变量 v ∈ V 的使用节点，记为 USE(v, n)，当且仅当变量 v 的值在对应于节点 n 的语句片段中被使用。

4. 使用节点 USE(v, n) 是谓词使用，记为 P-use，当且仅当语句 n 是谓词语句；否则，USE(v, n) 是计算使用，记为 C-use。

5. 关于变量 v 的定义/使用路径，记为 du-path，是 PATHS(P) 中的一条路径，使得对于某个 v ∈ V，存在定义节点和用法节点 DEF(v, m) 和 USE(v, n)，使得 m 和 n 是该路径的初始节点和最终节点。

6. 关于变量 v 的定义清晰路径，记为 dc-path，是 PATHS(P) 中的一条定义/使用路径，其初始节点和最终节点为 DEF(v, m) 和 USE(v, n)，使得路径中没有其他节点是 v 的定义节点。

### Example: the commission problem

（P162 Figure 9.1，8分钟阅读）

```
7.  lockPrice=45.0
8.  stockPrice=30.0
9.  barrelPrice=25.0
10. totalLocks=0
11. totalStocks=0
12. totalBarrels=0

13. Input(locks)
14. While NOT(locks==-1)
15. Input(stocks,barrels)
16. totalLocks=totalLocks+locks
17. totalStocks=totalStocks+stocks
18. totalBarrels=totalBarrels+barrels
19. Input(locks)
20. ENDWhile
```

p5=<16,17,18,19,20,21>
p6=<16,17,18,19,20,21,22,23,24>

两者都存在循环迭代问题，因此两者都不是定义清晰的。

其他变量的分析由学生自行阅读。

## Define/Use Test Coverage Metrics

- All-Defs criterion: 对于程序 P，当且仅当对于每个变量 v ∈ V，T 包含从 v 的每个定义节点到 v 的使用的定义清晰路径。

- All-Uses criterion: 对于程序 P，当且仅当对于每个变量 v ∈ V，T 包含从 v 的某个定义节点到 v 的每个使用的定义清晰路径，以及到每个 USE(v, n) 的后继节点。

- All-P-Uses/Some C-Uses criterion: 对于程序 P，当且仅当对于每个变量 v ∈ V，T 包含从 v 的每个定义节点到 v 的每个谓词使用的定义清晰路径；并且如果 v 的一个定义没有 P-use，则定义清晰路径通向至少一个计算使用。

- All-C-Uses/Some P-Uses criterion: 对于程序 P，当且仅当对于每个变量 v ∈ V，T 包含从 v 的每个定义节点到 v 的每个计算使用的定义清晰路径；并且如果 v 的一个定义没有 C-use，则定义清晰路径通向至少一个谓词使用。

### Example

- ⊙ Variable locks have 2 use nodes (14, 16) and 2 defining nodes (13, 19), then:

  ```
  S1: S(locks,13) = {13}
  S2: S(locks,14) = {13,14,19,20}
  S3: S(locks,16) = {13,14,16,19,20}
  S4: S(locks,19) = {19}
  ```

- ⊙ stocks and barrels variables are to be influenced by the loop variable locks, so

  ```
  S5: S(stocks,15) = {15}?
  S5: S(stocks,15) = {13,14,15,19,20}
  S6: S(stocks,17) = {13,14,15,17,19,20}
  S7: S(barrels,15) = {13,14,15,19,20}
  S8: S(barrels,18) = {13,14,15,18,19,20}
  ```

