
## 直接证法

**例：** 证明公式 $S\lor R$ 可由公式 $P\lor Q$，$P\leftrightarrow R$，$\neg Q\lor S$ 推出。

**解：** 问题即证 $P\lor Q$，$P\leftrightarrow R$，$\neg Q\lor S \Rightarrow S\lor R$。

| 步骤 | 公式 | 依据 |
|---|---|---|
| 1 | $P\lor Q$ | P规则 |
| 2 | $\neg P\to Q$ | T规则和1 |
| 3 | $\neg Q\lor S$ | P规则 |
| 4 | $Q\to S$ | T规则和3 |
| 5 | $\neg P\to S$ | T规则及2和4 |
| 6 | $\neg S\to P$ | T规则和5 |
| 7 | $P\leftrightarrow R$ | P规则 |
| 8 | $(P\to R)\land(R\to P)$ | T规则和7 |
| 9 | $P\to R$ | T规则和8 |
| 10 | $\neg S\to R$ | T规则及6和9 |
| 11 | $S\lor R$ | T规则和10，得证 |

**例：** $\neg(P\to Q)\to\neg(R\lor S)$，$(Q\to P)\lor\neg R$，$R\Rightarrow P\leftrightarrow Q$。

| 步骤 | 公式 | 依据 |
|---|---|---|
| 1 | $R$ | P规则 |
| 2 | $(Q\to P)\lor\neg R$ | P规则 |
| 3 | $Q\to P$ | T规则及1和2 |
| 4 | $R\lor S$ | T规则及1 |
| 5 | $\neg(P\to Q)\to\neg(R\lor S)$ | P规则 |
| 6 | $P\to Q$ | T规则及4和5 |
| 7 | $(P\to Q)\land(Q\to P)$ | T规则及3和6 |
| 8 | $P\leftrightarrow Q$ | T规则和7 |

### 推理规则

**CP规则：** 如果能从 $R$ 和前提集合中推导出 $S$ 来，则就能够从前提集合中推导出 $R\to S$。

换句话说，当结论是 $R\to S$ 的形式的时候，可以把结论的前件当作一个附加前提使用，并且它和前提一起若能推出结论的后件，则问题得证。

实际上恒等式 $E_{28}$ 就可以推出 CP 规则：

$$
\begin{aligned}
(P\land Q)\to R
&\Leftrightarrow \neg(P\land Q)\lor R \\
&\Leftrightarrow (\neg P\lor\neg Q)\lor R \\
&\Leftrightarrow \neg P\lor(\neg Q\lor R) \\
&\Leftrightarrow P\to(Q\to R)
\end{aligned}
$$

**例：** 证明 $R\to S$ 是 $P\to(Q\to S)$，$Q$，$\neg R\lor P$ 的有效结论。

**解：**

| 依据 | 公式 | 说明 |
|---|---|---|
| {1} (1) | $R$ | P规则（附加前提） |
| {2} (2) | $\neg R\lor P$ | P规则 |
| {1,2} (3) | $P$ | T规则，(1)、(2)和 $I_9$ |
| {4} (4) | $P\to(Q\to S)$ | P规则 |
| {1,2,4} (5) | $Q\to S$ | T规则，(3)、(4)和 $I_{10}$ |
| {6} (6) | $Q$ | P规则 |
| {1,2,4,6} (7) | $S$ | T规则，(5)、(6)和 $I_{10}$ |
| {1,2,4,6} (8) | $R\to S$ | CP规则，(1)、(7) |

**例：** 证明 $R\to S$ 是前提 $P\to(Q\to S)$，$\neg R\lor(P\land Q)$ 的有效结论。

**解：** 原证明即证：$P\to(Q\to S)$，$\neg R\lor(P\land Q)\Rightarrow R\to S$。

| 步骤 | 公式 | 依据 |
|---|---|---|
| 1 | $R$ | P规则（附加前提） |
| 2 | $\neg R\lor(P\land Q)$ | P规则 |
| 3 | $P\land Q$ | T规则及1和2 |
| 4 | $P$ | T规则和3 |
| 5 | $P\to(Q\to S)$ | P规则 |
| 6 | $Q\to S$ | T规则及4和5 |
| 7 | $Q$ | T规则和3 |
| 8 | $S$ | T规则及6和7 |
| 9 | $R\to S$ | CP规则及1和8 |

**例：** 证明 $P\to(Q\to R)$，$Q$，$P\lor\neg S \Rightarrow S\to R$。

**解：**

| 步骤 | 公式 | 依据 |
|---|---|---|
| 1 | $S$ | P规则（附加前提） |
| 2 | $P\lor\neg S$ | P规则 |
| 3 | $P$ | T规则及1和2 |
| 4 | $P\to(Q\to R)$ | P规则 |
| 5 | $Q\to R$ | T规则及3和4 |
| 6 | $Q$ | P规则 |
| 7 | $R$ | T规则及5和6 |
| 8 | $S\to R$ | CP规则及1和7 |

## 证明有效结论的方法

### 3. 间接证明法（反证法）

**定义：** 设公式 $H_1,H_2,\dots,H_m$ 中的原子变元是 $P_1,P_2,\dots,P_n$。如果给各原子变元 $P_1,P_2,\dots,P_n$ 指派某一个真值集合，能使 $H_1\land H_2\land\dots\land H_m$ 具有真值 $T$，则命题公式集合 $\{H_1,H_2,\dots,H_m\}$ 称为一致的（或相容的）；

对于各原子变元的每一个真值指派，如果命题公式 $H_1,H_2,\dots,H_m$ 中至少有一个是假，从而使得 $H_1\land H_2\land\dots\land H_m$ 是假，则称命题公式集合是不一致的（或不相容的）。

**例如：** 令 $H_1=P$，$H_2=\neg P$，则 $H_1\land H_2=P\land\neg P$ 是矛盾式，所以 $P$，$\neg P$ 是不相容的。

**定理：** 若存在一个公式 $R$，使得 $H_1\land H_2\land\dots\land H_m \Rightarrow R\land\neg R$，则公式 $H_1,H_2,\dots,H_m$ 是不相容的。

**证明：**

- 设 $H_1\land H_2\land\dots\land H_m \Rightarrow R\land\neg R$。
- 则意味着 $(H_1\land H_2\land\dots\land H_m)\to(R\land\neg R)$ 是重言式。
- 而 $R\land\neg R$ 是矛盾式，所以前件 $H_1\land H_2\land\dots\land H_m$ 必永远假。
- 因此，$H_1,H_2,\dots,H_m$ 是不相容的。

**定理：** 设命题公式集合 $\{H_1,H_2,\dots,H_m\}$ 是一致的，于是从前提集合出发可以逻辑地推出公式 $C$ 的充要条件是从前提集合 $\{H_1,H_2,\dots,H_m,\neg C\}$ 出发，可以逻辑地推出一个矛盾（永假）式。

**证明：**

**必要性：** 由于 $H_1\land H_2\land\dots\land H_m \Rightarrow C$，即 $H_1\land H_2\land\dots\land H_m\to C$ 为永真式，因而使 $H_1\land H_2\land\dots\land H_m$ 为真的真值指派一定使 $C$ 为真，$\neg C$ 为假，从而使 $H_1\land H_2\land\dots\land H_m\land\neg C$ 为假。必要性证完。

**充分性：** 由于 $\{H_1\land H_2\land\dots\land H_n\land\neg C\}$ 可以逻辑地推出一个矛盾，即 $H_1\land H_2\land\dots\land H_n\land\neg C\Rightarrow F$，即 $H_1\land H_2\land\dots\land H_n\land\neg C\to F$ 为永真式，即 $H_1\land H_2\land\dots\land H_n\land\neg C$ 为假，由假设知 $\{H_1,H_2,\dots,H_n\}$ 是一致的，所以任何使 $H_1\land H_2\land\dots\land H_n$ 为真的命题变元的真值指派必然使 $\neg C$ 为假，从而使 $C$ 为真。故有

$$
H_1\land H_2\land\dots\land H_n \Rightarrow C
$$

该定理说明用直接证明法可以证明的结论，用间接证明法都可以证明，反之亦然。

因此，为了证明 $B$ 是 $A$ 的结论，可以把 $A$ 和 $\neg B$ 作为前提，然后推出一个矛盾，从而使问题得证。下面用例子说明。

**F规则：** 如果前提集合和 $\neg S$ 不相容，那么可以从前提集合中推出 $S$。

**例：** 证明 $\neg(P\land Q)$ 是 $\neg P\land\neg Q$ 的有效结论。

**解：** 把 $\neg\neg(P\land Q)$ 作为假设前提，并证明该假设前提导致一个永假式。

| 依据 | 公式 | 说明 |
|---|---|---|
| {1} (1) | $\neg\neg(P\land Q)$ | P规则（假设前提） |
| {1} (2) | $P\land Q$ | T规则，(1)和 $E_{10}$ |
| {1} (3) | $P$ | T规则，(2)和 $I_1$ |
| {4} (4) | $\neg P\land\neg Q$ | P规则 |
| {4} (5) | $\neg P$ | T规则，(4)和 $I_1$ |
| {1,4} (6) | $P\land\neg P$ | T规则，(3)、(5)和 $I_{16}$ |
| {1,4} (7) | $\neg(P\land Q)$ | F规则，(1)、(6) |

**例：** 欧洲足坛4支欧冠球队进行比赛，已知情况如下：

前提：

1. 若切尔西获冠军，则拜仁慕尼黑或巴塞罗那获得亚军。
2. 若巴塞罗那获亚军，则切尔西不能获冠军。
3. 若皇家马德里获亚军，则拜仁慕尼黑不能获亚军。
4. 最后切尔西获冠军。

结论：5. 皇家马德里未获亚军。

用推理的方法证明由 $\{1,2,3,4\}$ 能否推出 5。

解：首先将命题符号化。

令

- $P$：切尔西获冠军
- $Q$：拜仁慕尼黑获亚军
- $R$：巴塞罗那获亚军
- $S$：皇家马德里获亚军

于是问题可符号化为：

$$
P\to(Q\lor R),\quad R\to\neg P,\quad S\to\neg Q,\quad P\Rightarrow\neg S
$$

（注意：这里自然语言中的“或”表示的是排斥或，所以用 $\lor$ 来表示。）

解：

| 步骤 | 公式 | 依据 |
|---|---|---|
| 1 | $\neg\neg S$ | P规则（假设前提） |
| 2 | $S$ | T规则和1 |
| 3 | $S\to\neg Q$ | P规则 |
| 4 | $\neg Q$ | T规则及2和3 |
| 5 | $P$ | P规则 |
| 6 | $P\to(Q\lor R)$ | P规则 |
| 7 | $Q\lor R$ | T规则及5和6 |
| 8 | $R$ | T规则及4和7 |
| 9 | $R\to\neg P$ | P规则 |
