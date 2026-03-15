# 分布式系统：18：拜占庭容错（BFT）

![](img/d4beda8365d45e28673a93d3c44daabb_1.png)

![](img/d4beda8365d45e28673a93d3c44daabb_3.png)

![](img/d4beda8365d45e28673a93d3c44daabb_4.png)

![](img/d4beda8365d45e28673a93d3c44daabb_6.png)

![](img/d4beda8365d45e28673a93d3c44daabb_7.png)

![](img/d4beda8365d45e28673a93d3c44daabb_9.png)

![](img/d4beda8365d45e28673a93d3c44daabb_10.png)

## 概述

![](img/d4beda8365d45e28673a93d3c44daabb_11.png)

![](img/d4beda8365d45e28673a93d3c44daabb_13.png)

![](img/d4beda8365d45e28673a93d3c44daabb_15.png)

![](img/d4beda8365d45e28673a93d3c44daabb_16.png)

![](img/d4beda8365d45e28673a93d3c44daabb_17.png)

在本节课中，我们将继续讨论容错主题。我们将从三个不同的技术角度来探讨：首先是在存在故障时如何达成**共识**，我们会介绍拜占庭将军问题；其次是从网络角度处理故障，即实现某种程度的**可靠通信**；最后是**分布式提交**问题，它提供了原子性属性，并展示了如何处理故障。

![](img/d4beda8365d45e28673a93d3c44daabb_19.png)

上一讲我们介绍了容错的基本概念，本节我们将深入探讨这些具体技术。

## 共识与拜占庭将军问题

![](img/d4beda8365d45e28673a93d3c44daabb_21.png)

![](img/d4beda8365d45e28673a93d3c44daabb_23.png)

上一节我们介绍了容错的基本思想，本节我们来看看在分布式系统中，一组进程应如何就某个计算的结果达成一致。这个计算可以是任何请求，例如数据库查询、RPC调用或HTTP请求。

![](img/d4beda8365d45e28673a93d3c44daabb_25.png)

![](img/d4beda8365d45e28673a93d3c44daabb_26.png)

![](img/d4beda8365d45e28673a93d3c44daabb_27.png)

![](img/d4beda8365d45e28673a93d3c44daabb_28.png)

![](img/d4beda8365d45e28673a93d3c44daabb_30.png)

我们将讨论两种故障类型：**崩溃故障**和**拜占庭故障**。

![](img/d4beda8365d45e28673a93d3c44daabb_32.png)

![](img/d4beda8365d45e28673a93d3c44daabb_33.png)

![](img/d4beda8365d45e28673a93d3c44daabb_35.png)

![](img/d4beda8365d45e28673a93d3c44daabb_36.png)

### 崩溃故障

在崩溃故障中，进程在正常运行时产生正确结果，但由于错误，进程可能挂起或崩溃，此时不产生任何输出。进程只有两种状态：正常运行或完全崩溃。

![](img/d4beda8365d45e28673a93d3c44daabb_38.png)

![](img/d4beda8365d45e28673a93d3c44daabb_40.png)

![](img/d4beda8365d45e28673a93d3c44daabb_42.png)

![](img/d4beda8365d45e28673a93d3c44daabb_44.png)

**问题**：如果一个系统需要容忍单个组件的 `k` 个并发故障，那么需要多少个副本来处理崩溃故障？

![](img/d4beda8365d45e28673a93d3c44daabb_46.png)

**答案**：需要 `k + 1` 个副本。例如，要容忍1个故障（`k=1`），需要2个副本；要容忍2个故障，需要3个副本。公式如下：

```
所需副本数 = k + 1
```

### 拜占庭故障

在拜占庭故障中，进程可能仍在运行，但会产生**不正确的结果**。这可能是由于程序错误，或者系统被恶意攻击者入侵所致。故障进程可以运行，但会产生错误或恶意的结果。

![](img/d4beda8365d45e28673a93d3c44daabb_48.png)

![](img/d4beda8365d45e28673a93d3c44daabb_50.png)

**问题**：要容忍 `k` 个拜占庭故障，需要多少个副本？

![](img/d4beda8365d45e28673a93d3c44daabb_52.png)

![](img/d4beda8365d45e28673a93d3c44daabb_53.png)

![](img/d4beda8365d45e28673a93d3c44daabb_54.png)

**答案**：需要 `3k + 1` 个副本。例如，要容忍1个拜占庭故障（`k=1`），需要4个副本。这是一个很高的成本。

```
所需副本数 = 3k + 1
```

![](img/d4beda8365d45e28673a93d3c44daabb_56.png)

![](img/d4beda8365d45e28673a93d3c44daabb_58.png)

接下来，我们通过拜占庭将军问题来深入理解为什么需要这么多副本。

![](img/d4beda8365d45e28673a93d3c44daabb_60.png)

![](img/d4beda8365d45e28673a93d3c44daabb_61.png)

![](img/d4beda8365d45e28673a93d3c44daabb_62.png)

![](img/d4beda8365d45e28673a93d3c44daabb_64.png)

![](img/d4beda8365d45e28673a93d3c44daabb_65.png)

![](img/d4beda8365d45e28673a93d3c44daabb_66.png)

## 拜占庭将军问题

![](img/d4beda8365d45e28673a93d3c44daabb_68.png)

![](img/d4beda8365d45e28673a93d3c44daabb_70.png)

![](img/d4beda8365d45e28673a93d3c44daabb_71.png)

![](img/d4beda8365d45e28673a93d3c44daabb_73.png)

![](img/d4beda8365d45e28673a93d3c44daabb_75.png)

### 两将军问题（不可解）

首先考虑一个简化场景：两个进程通过一个**拜占庭故障网络**进行通信。它们只能发送单比特消息（0或1）。网络可能：
1.  正确传递消息。
2.  完全丢弃消息。
3.  翻转消息（例如，发送0却传递1）。

**问题**：在这类故障网络下，这两个进程能否进行通信、协调并达成共识？

这个问题的经典形式是“两将军问题”：两支军队的将军需要通过信使在敌对领土上传递消息，以协调进攻时间。信使可能被俘、消息可能丢失或被篡改。

![](img/d4beda8365d45e28673a93d3c44daabb_77.png)

![](img/d4beda8365d45e28673a93d3c44daabb_78.png)

![](img/d4beda8365d45e28673a93d3c44daabb_80.png)

![](img/d4beda8365d45e28673a93d3c44daabb_82.png)

![](img/d4beda8365d45e28673a93d3c44daabb_83.png)

**结论**：这是一个**不可能解决的问题**。两个完美的进程（将军）在存在不可靠信道（网络）的情况下，永远无法达成共识。这涉及到“共同知识”的概念——即每个人都知道某事，并且每个人都知道其他人也知道此事。在这种不可靠的通信中，无法建立共同知识。

![](img/d4beda8365d45e28673a93d3c44daabb_85.png)

### 多将军问题（可解）

![](img/d4beda8365d45e28673a93d3c44daabb_87.png)

![](img/d4beda8365d45e28673a93d3c44daabb_89.png)

![](img/d4beda8365d45e28673a93d3c44daabb_90.png)

现在，我们假设网络是可靠的（例如，通过TCP），但**进程本身可能出现拜占庭故障**（即将军中可能出现叛徒）。

![](img/d4beda8365d45e28673a93d3c44daabb_92.png)

考虑一个有 `n` 个将军的例子，其中 `m` 个是叛徒。叛徒可以发送不一致的、错误的信息，或者不发送信息。

![](img/d4beda8365d45e28673a93d3c44daabb_93.png)

**目标**：忠诚的将军们需要识别出故障进程（叛徒），将其排除在决策之外，并就某个值（例如，各自的兵力）达成一致。

![](img/d4beda8365d45e28673a93d3c44daabb_95.png)

![](img/d4beda8365d45e28673a93d3c44daabb_96.png)

**解决方案（口头协议示例）**：
1.  **第一轮**：每个将军向其他所有人广播自己的兵力值。忠诚的将军发送真实值，叛徒可能发送任意值。
2.  **第二轮**：每个将军将自己从其他所有人那里收到的值向量，再次广播给所有人。
3.  **决策**：每个忠诚的将军检查收到的向量。通过比较不同将军报告的其他人的值，可以识别出哪个将军发送了不一致的信息（即叛徒）。然后，忠诚的将军们可以忽略叛徒的值，并对剩余忠诚将军的值达成一致。

![](img/d4beda8365d45e28673a93d3c44daabb_98.png)

![](img/d4beda8365d45e28673a93d3c44daabb_100.png)

![](img/d4beda8365d45e28673a93d3c44daabb_102.png)

**关键点**：要容忍 `m` 个叛徒，至少需要 `3m + 1` 个将军。如果只有 `3m` 个，忠诚的将军可能知道存在故障，但无法确定谁是叛徒，从而无法达成一致。

![](img/d4beda8365d45e28673a93d3c44daabb_104.png)

**总结**：
*   **检测故障**：需要 `2m + 1` 个进程。
*   **达成共识（容错）**：需要 `3m + 1` 个进程。

![](img/d4beda8365d45e28673a93d3c44daabb_106.png)

![](img/d4beda8365d45e28673a93d3c44daabb_108.png)

![](img/d4beda8365d45e28673a93d3c44daabb_109.png)

拜占庭容错成本高昂，因此通常只在需要极高安全性的场景中使用，例如加密货币（比特币）。大多数普通系统只处理崩溃故障。

![](img/d4beda8365d45e28673a93d3c44daabb_111.png)

![](img/d4beda8365d45e28673a93d3c44daabb_112.png)

![](img/d4beda8365d45e28673a93d3c44daabb_113.png)

![](img/d4beda8365d45e28673a93d3c44daabb_114.png)

## 可靠通信：组播

![](img/d4beda8365d45e28673a93d3c44daabb_116.png)

![](img/d4beda8365d45e28673a93d3c44daabb_117.png)

![](img/d4beda8365d45e28673a93d3c44daabb_118.png)

![](img/d4beda8365d45e28673a93d3c44daabb_119.png)

![](img/d4beda8365d45e28673a93d3c44daabb_120.png)

![](img/d4beda8365d45e28673a93d3c44daabb_122.png)

![](img/d4beda8365d45e28673a93d3c44daabb_123.png)

之前我们讨论的都是一对一（单播）通信。在分布式系统中，一对多（组播）通信也很常见，例如将数据写入多个副本。

![](img/d4beda8365d45e28673a93d3c44daabb_125.png)

![](img/d4beda8365d45e28673a93d3c44daabb_126.png)

组播意味着一个发送者，多个接收者。广播是组播的特例，发送给网络中的所有机器。

![](img/d4beda8365d45e28673a93d3c44daabb_128.png)

**问题**：如何在组播中实现可靠传递？

![](img/d4beda8365d45e28673a93d3c44daabb_130.png)

![](img/d4beda8365d45e28673a93d3c44daabb_131.png)

![](img/d4beda8365d45e28673a93d3c44daabb_132.png)

![](img/d4beda8365d45e28673a93d3c44daabb_134.png)

![](img/d4beda8365d45e28673a93d3c44daabb_135.png)

![](img/d4beda8365d45e28673a93d3c44daabb_137.png)

### 基于确认（ACK）的方案

发送者向组内所有成员发送消息，并等待每个成员的确认（ACK）。收到所有ACK后，发送者才知道消息已可靠传递。

![](img/d4beda8365d45e28673a93d3c44daabb_139.png)

![](img/d4beda8365d45e28673a93d3c44daabb_140.png)

**缺点**：当组规模（`n`）很大时，发送者需要处理 `n` 个ACK，负载很高，**可扩展性差**。

![](img/d4beda8365d45e28673a93d3c44daabb_142.png)

![](img/d4beda8365d45e28673a93d3c44daabb_144.png)

![](img/d4beda8365d45e28673a93d3c44daabb_145.png)

### 基于否定确认（NACK）的方案

![](img/d4beda8365d45e28673a93d3c44daabb_147.png)

![](img/d4beda8365d45e28673a93d3c44daabb_148.png)

为了减少发送者负载，可以采用NACK方案：
*   接收者成功收到消息时，**不发送任何东西**。
*   只有当接收者发现**消息丢失**（例如，通过序列号发现缺口）时，才向发送者（或其他持有消息的接收者）发送NACK，请求重传。

![](img/d4beda8365d45e28673a93d3c44daabb_150.png)

![](img/d4beda8365d45e28673a93d3c44daabb_151.png)

**优点**：在低丢失率的网络中，NACK数量远少于ACK，显著降低了发送者负载。

![](img/d4beda8365d45e28673a93d3c44daabb_153.png)

![](img/d4beda8365d45e28673a93d3c44daabb_154.png)

![](img/d4beda8365d45e28673a93d3c44daabb_155.png)

**挑战**：需要处理序列号、乱序交付、重复消息以及“最后一条消息丢失”的特殊情况（可能需要发送虚拟消息来触发NACK）。

![](img/d4beda8365d45e28673a93d3c44daabb_157.png)

![](img/d4beda8365d45e28673a93d3c44daabb_158.png)

![](img/d4beda8365d45e28673a93d3c44daabb_159.png)

## 高级组播属性

![](img/d4beda8365d45e28673a93d3c44daabb_161.png)

![](img/d4beda8365d45e28673a93d3c44daabb_162.png)

![](img/d4beda8365d45e28673a93d3c44daabb_164.png)

![](img/d4beda8365d45e28673a93d3c44daabb_165.png)

![](img/d4beda8365d45e28673a93d3c44daabb_166.png)

![](img/d4beda8365d45e28673a93d3c44daabb_167.png)

![](img/d4beda8365d45e28673a93d3c44daabb_168.png)

除了基本可靠性，组播还可以提供更强的一致性保证：

![](img/d4beda8365d45e28673a93d3c44daabb_170.png)

![](img/d4beda8365d45e28673a93d3c44daabb_171.png)

![](img/d4beda8365d45e28673a93d3c44daabb_173.png)

![](img/d4beda8365d45e28673a93d3c44daabb_175.png)

*   **FIFO排序**：来自同一发送者的消息，所有接收者都按发送顺序接收。
*   **全序排序**：所有消息（无论来自哪个发送者）在所有接收者处都以**相同的全局顺序**接收。
*   **因果排序**：如果消息A在因果上先于消息B（例如，发送B的进程在收到A之后才发送B），那么所有接收者都将在B之前收到A。

![](img/d4beda8365d45e28673a93d3c44daabb_177.png)

![](img/d4beda8365d45e28673a93d3c44daabb_178.png)

![](img/d4beda8365d45e28673a93d3c44daabb_179.png)

![](img/d4beda8365d45e28673a93d3c44daabb_181.png)

![](img/d4beda8365d45e28673a93d3c44daabb_182.png)

这些属性需要更复杂的协议来实现，但为上层应用提供了更清晰的语义。

![](img/d4beda8365d45e28673a93d3c44daabb_184.png)

![](img/d4beda8365d45e28673a93d3c44daabb_186.png)

## 原子组播与分布式提交

![](img/d4beda8365d45e28673a93d3c44daabb_188.png)

![](img/d4beda8365d45e28673a93d3c44daabb_189.png)

![](img/d4beda8365d45e28673a93d3c44daabb_190.png)

### 原子组播

![](img/d4beda8365d45e28673a93d3c44daabb_192.png)

![](img/d4beda8365d45e28673a93d3c44daabb_193.png)

原子组播要求**全有或全无**属性：要么组内所有成员都收到消息，要么没有一个成员收到。这可以防止在发送者或部分接收者崩溃时，系统状态不一致。

![](img/d4beda8365d45e28673a93d3c44daabb_195.png)

![](img/d4beda8365d45e28673a93d3c44daabb_197.png)

![](img/d4beda8365d45e28673a93d3c44daabb_198.png)

![](img/d4beda8365d45e28673a93d3c44daabb_200.png)

**实现思路（如Isis系统）**：维护一个**组视图**，跟踪当前活跃的成员。当有进程加入或离开（故障）时，进行**视图切换**。原子性保证仅针对当前视图内的成员。新进程加入后，需要由应用层负责同步错过的状态（例如，通过传输日志）。

![](img/d4beda8365d45e28673a93d3c44daabb_202.png)

![](img/d4beda8365d45e28673a93d3c44daabb_203.png)

![](img/d4beda8365d45e28673a93d3c44daabb_204.png)

### 分布式提交

![](img/d4beda8365d45e28673a93d3c44daabb_206.png)

![](img/d4beda8365d45e28673a93d3c44daabb_207.png)

![](img/d4beda8365d45e28673a93d3c44daabb_208.png)

![](img/d4beda8365d45e28673a93d3c44daabb_209.png)

原子组播是分布式提交的一个特例。分布式提交是一个更通用的抽象：**一组进程希望就“是否执行某个操作”达成一致，要求要么全部执行（提交），要么全部不执行（中止）**。这个操作可以是接收消息、写入数据库事务等。

![](img/d4beda8365d45e28673a93d3c44daabb_211.png)

![](img/d4beda8365d45e28673a93d3c44daabb_212.png)

![](img/d4beda8365d45e28673a93d3c44daabb_213.png)

![](img/d4beda8365d45e28673a93d3c44daabb_215.png)

**两阶段提交（2PC）** 是一个经典的分布式提交协议：
1.  **投票阶段**：协调者询问所有参与者：“是否可以提交？” 参与者根据自身状态回复“是”或“否”。
2.  **决策阶段**：
    *   如果**所有**参与者都回复“是”，协调者发送“提交”命令。
    *   如果**任何**参与者回复“否”，协调者发送“中止”命令。

![](img/d4beda8365d45e28673a93d3c44daabb_217.png)

![](img/d4beda8365d45e28673a93d3c44daabb_219.png)

![](img/d4beda8365d45e28673a93d3c44daabb_221.png)

![](img/d4beda8365d45e28673a93d3c44daabb_223.png)

![](img/d4beda8365d45e28673a93d3c44daabb_224.png)

2PC通过一个协调者和两轮通信实现了全有或全无的原子性。我们将在下一讲详细分析2PC及其变种（如三阶段提交，3PC）。

![](img/d4beda8365d45e28673a93d3c44daabb_226.png)

![](img/d4beda8365d45e28673a93d3c44daabb_228.png)

![](img/d4beda8365d45e28673a93d3c44daabb_230.png)

![](img/d4beda8365d45e28673a93d3c44daabb_231.png)

![](img/d4beda8365d45e28673a93d3c44daabb_233.png)

## 总结

![](img/d4beda8365d45e28673a93d3c44daabb_235.png)

![](img/d4beda8365d45e28673a93d3c44daabb_236.png)

![](img/d4beda8365d45e28673a93d3c44daabb_238.png)

![](img/d4beda8365d45e28673a93d3c44daabb_239.png)

![](img/d4beda8365d45e28673a93d3c44daabb_241.png)

本节课我们一起学习了分布式系统中的核心容错技术。

![](img/d4beda8365d45e28673a93d3c44daabb_243.png)

1.  **拜占庭共识**：我们探讨了拜占庭将军问题，理解了在进程可能恶意行为时达成共识的挑战和解决方案。关键结论是，容忍 `m` 个拜占庭故障需要至少 `3m + 1` 个副本。
2.  **可靠组播**：我们分析了一对多通信的可靠性问题，比较了基于ACK和NACK的方案，并介绍了FIFO、全序、因果序等高级组播语义。
3.  **原子性与提交**：我们引入了原子组播和更广义的分布式提交问题，为下一讲深入讲解两阶段提交协议做好了铺垫。

![](img/d4beda8365d45e28673a93d3c44daabb_245.png)

![](img/d4beda8365d45e28673a93d3c44daabb_246.png)

![](img/d4beda8365d45e28673a93d3c44daabb_247.png)

这些技术是构建健壮、可靠的分布式系统的基石，特别是在面对进程故障和网络不可靠性时。下一讲我们将继续探讨共识算法（如Paxos、Raft）以及检查点与消息恢复等技术。