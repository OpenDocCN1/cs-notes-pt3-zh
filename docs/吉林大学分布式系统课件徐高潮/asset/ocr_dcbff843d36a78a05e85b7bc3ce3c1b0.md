# 第五章 同步和互斥

# 5.3 系统的全局状态

# 系统的全局状态的定义

令 LSᵢ 为进程 Pᵢ 的局部状态，则全局状态 GS = (LS₁, LS₂, …, LSₙ)。

+   1）两个集合：
+   transit(LSᵢ, LSⱼ) = {m | s(m) ∈ LSᵢ ∧ r(m) ∉ LSⱼ}
+   inconsistent(LSᵢ, LSⱼ) = {m | s(m) ∉ LSᵢ ∧ r(m) ∈ LSⱼ}

集合 transit 包括了进程 Pᵢ 和进程 Pⱼ 之间的通信通道上的所有报文，集合 inconsistent 包括了所有接收事件记录在 Pⱼ 而发送事件没有记录在 Pᵢ 的报文。其中 m 是报文，s(m) 是报文 m 的发送事件，r(m) 是报文 m 的接收事件。