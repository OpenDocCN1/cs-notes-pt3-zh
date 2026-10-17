

## 银行家算法例

### T₀时刻是否安全？

从表中可找出一个序列(P₁、P₃、P₄、P₂、P₀) 使各进程顺序地一个个地执行完成。

|   | Max |   |   | Allocation |   |   | Need |   |   | Available (分配资源前) |   |   | Available (释放资源后) |   |   |
|---|-----|---|---|------------|---|---|------|---|---|------------------------|---|---|------------------------|---|---|
|   | A   | B | C | A          | B | C | A    | B | C | A                      | B | C | A                      | B | C |
| P₀ | 7   | 5 | 3 | 0          | 1 | 0 | 7    | 4 | 3 | <=                     | 10 | 4 | 7                      | ⑤ | 10 | 5 | 7 |
| P₁ | 3   | 2 | 2 | 2          | 0 | 0 | 1    | 2 | 2 | <=                     | 3 | 3 | 2                      | ① | 5 | 3 | 2 |
| P₂ | 9   | 0 | 2 | 3          | 0 | 2 | 6    | 0 | 0 | <=                     | 7 | 4 | 5                      | ④ | 10 | 4 | 7 |
| P₃ | 2   | 2 | 2 | 2          | 1 | 1 | 0    | 1 | 1 | <=                     | 5 | 3 | 2                      | ② | 7 | 4 | 3 |
| P₄ | 4   | 3 | 3 | 0          | 0 | 2 | 4    | 3 | 1 | <=                     | 7 | 4 | 3                      | ③ | 7 | 4 | 5 |

安全序列为{P₁、P₃、P₄、P₂、P₀}，T₀时刻系统是安全的。

### Example P₁ Request (1,0,2) (Cont.)

- Check that Request ≤ Available (that is, (1,0,2) ≤ (3,3,2) ⇒ true。检查请求小于有效（就是说，(1,0,2) ≤ (3,3,2)为真）

| Process | Allocation A B C | Need A B C | Available A B C |
|---|---|---|---|
| P₀ | 0 1 0 | 7 4 3 | 2 3 0 |
| P₁ | 3 0 2 | 0 2 0 | |
| P₂ | 3 0 1 | 6 0 0 | |
| P₃ | 2 1 1 | 0 1 1 | |
| P₄ | 0 0 2 | 4 3 1 | |

- Executing safety algorithm shows that sequence ⟨P₁, P₃, P₄, P₀, P₂⟩ satisfies safety requirement。
- 执行安全算法表明序列⟨P₁, P₃, P₄, P₀, P₂⟩满足要求

- Can request for (3,3,0) by P₄ be granted?
- Can request for (0,2,0) by P₀ be granted?

P₄的(3,3,0)可以通过？P₀的(0,2,0)可以通过？

## 8.6 Deadlock Detection

## 死锁检测

- Allow system to enter deadlock state 允许进入死锁状态
- Detection algorithm 检测死锁
- Recovery scheme 恢复策略

## 8.6.1 Single Instance of Each Resource Type

### 每一种资源类型只有一个实例

- Maintain _wait-for_ graph, that is a variant of the resource-allocation graph
- 维护等待图

- Nodes are processes.
- 节点是进程

- \(P_i \rightarrow P_j\) if \(P_i\) is waiting for \(P_j\).
- \(P_i \rightarrow P_j\) 表示\(P_i\)在等待\(P_j\).

- Periodically invoke an algorithm that searches for a cycle in the graph.
- 定期调用算法来检查是否有环

- An algorithm to detect a cycle in a graph requires an order of \(n^2\) operations, where \(n\) is the number of vertices in the graph.
- 一个检查图中是否有环的算法需要\(n^2\)的操作来进行，n为图中的节点数

## Fig 8.7 Resource-Allocation Graph and Wait-for Graph
资源分配图和等待图

![](img/ba81f478b8c7b785e80053d010189a68_342_0.png)

Resource-Allocation Graph Corresponding wait-for graph

## 8.6.2 Several Instances of a Resource Type

一个资源类型的多个实例

- **Available:** A vector of length *m* indicates the number of available resources of each type.
- 可用：一个长度*m*的向量代表每一种资源类型有效的数目

- **Allocation:** An *n* × *m* matrix defines the number of resources of each type currently allocated to each process.
- 分配：一个 *n* × *m* 的矩阵定义了当前分配的每一种资源类型的实例数目

- **Request:** An *n* × *m* matrix indicates the current request of each process. If *Request* [*i*,*j*] = *k*, then process *Pᵢ* is requesting *k* more instances of resource type *Rⱼ*.
- 请求：一个 *n* × *m* 的矩阵使命了当前的进程请求。如果 *Request* [*i*,*j*] = *k*，那么进程 *Pᵢ* 请求 *k* 个资源 *Rⱼ* 的实例

![](img/ba81f478b8c7b785e80053d010189a68_343_0.png)

## Detection Algorithm检测算法

1. Let *Work* and *Finish* be vectors of length *m* and *n*, respectively. Initialize:
   让*Work*和*Finish*作为长度为*m*和*n*的向量
   (a) *Work* = *Available*
   (b) For *i* = 1, 2, ..., *n*, if *Allocationᵢ* ≠ 0, then *Finish*[*i*] = false; otherwise, *Finish*[*i*] = true.

2. Find an index *i* such that both:
   找到下标*i*
   (a) *Finish*[*i*] == false
   (b) *Requestᵢ* ≤ *Work*
   If no such *i* exists, go to step 4.
   如果没有这样的存在，转4

