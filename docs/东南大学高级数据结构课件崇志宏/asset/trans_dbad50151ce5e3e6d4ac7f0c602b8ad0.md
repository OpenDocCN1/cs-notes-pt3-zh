

## 高效实现

**高效实现。** 我们描述 O(n²) 时间实现。

- **表示男性和女性。**
  - 假设男性命名为 1, ..., n。
  - 假设女性命名为 1′, ..., n′。
- **订婚。**
  - 维护一个自由男性的列表，例如在队列中。
  - 维护两个数组 `wife[m]` 和 `husband[w]`。
    - 若未匹配则将条目设为 0
    - 若 m 匹配到 w 则 `wife[m]=w` 且 `husband[w]=m`
- **男性求婚。**
  - 对每个男性，维护一个按偏好排序的女性列表。
  - 维护一个数组 `count[m]` 用于计数男性 m 已做出的求婚次数。

### 女性拒绝/接受。

- 女性 w 是否更喜欢男性 m₁ 而非男性 m₂？
- 对每个女性，创建男性偏好列表的逆序。
- 在 O(n) 预处理后，每个查询可实现常数时间访问。

| Amy | 1st | 2nd | 3rd | 4th | 5th | 6th | 7th | 8th |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Pref | 8 | 3 | 7 | 1 | 4 | 5 | 6 | 2 |

| Amy | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|-----|---|---|---|---|---|---|---|---|
| Inverse | 4th | 8th | 2nd | 5th | 6th | 7th | 3rd | 1st |

```
for i = 1 to n
inverse[pref[i]] = i
```

Amy 更喜欢男性 3 而非 6，因为 inverse[3] < inverse[6]（2nd < 7th）。

## 流式算法

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_165_0.png)

MEM: poly(1/ε, log N)

Query/Update: poly(1/ε, log N)

- N: 流大小或窗口大小
- ε: 误差参数

## 数据流和查询

- 数据流
  - 数字（例如数据包的头部）
  - 结构化元组（例如 Web 日志）
  - XML 文档（例如 pub/sub 系统）
- 查询
  - 连续/临时查询
  - 可能具有不同的复杂度
    - 计数
    - 结构化查询（SQL）
    - 数据分析和挖掘

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_166_0.png)

## 与频率相关的问题

- Top-k 最频繁元素
- 找出占尾部 0.1% 的元素。
- 均值 + 方差？
- 中位数？
- 元素 3 的频率是多少？
- 找出所有频率 > 0.1% 的元素
- 元素 8 到 14 之间的总频率是多少？

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_167_0.png)

| 8 | 3 | 11 | 6 | 2 |
|---|---|---|---|---|
| 7 | 0 | 1 | 14 | 8 |
| 2 | 5 | 5 | 10 | 8 |
| 8 | 2 | 6 | 2 | 12 |

Estimate(6) = min(2, 8, 2, 2) = ?

- 低空间复杂度：$O(\varepsilon^{-1}\log M)$
- 快速的每元组处理成本
- 高召回率和精确率

![](img/e8cfdb0a049dc5ab9d802234ebc2190e_169_0.png)

## 阅读材料

### What’s Hot and What’s Not: Tracking Most Frequent Items Dynamically

Graham Cormode  
Center for Discrete Mathematics and Computer Science (DIMACS)  
Rutgers University, Piscataway NJ  
graham@dimacs.rutgers.edu

S. Muthukrishnan  
Department of Computer Science  
Rutgers University, Piscataway NJ  
muthu@cs.rutgers.edu

WebDB.cn Open Group, Southeast University

## 分布式数据结构

Zhihong Chong

http://cse.seu.edu.cn/people/zhchong/

## 内容

- 为什么需要高级数据结构？
  - Week1: 数据结构与计算机科学、算法、数据库、WWW...
- 数据结构原理—如何？
  - Week2: 为什么以及如何实现 O(log n) 访问时间？
  - Week3: 动态数据结构和分析
  - Week4: 随机化数据结构
  - Week5: 增强数据结构
  - Week6: 分布式环境中的数据结构
- 新问题—应用
  - Week7: 研究前沿的数据结构
  - Week8: 考试

## 大纲

- CAN
- Chord
- Baton

## CAN: 概述

- 在键值对 (K,V) 上支持基本哈希表操作：插入、搜索、删除
- CAN 由各个节点组成
- 每个节点存储哈希表的一个块（区域）
  - 表中 (K,V) 对的一个子集
- 每个节点存储关于邻居区域的状态信息
- 针对某个键的请求（插入、查找或删除）由中间节点使用贪婪路由算法路由
- 无需集中控制（完全分布式）
- 每个节点的少量状态与系统中的节点数量无关（可扩展）
- 节点可以绕过故障进行路由（容错）

