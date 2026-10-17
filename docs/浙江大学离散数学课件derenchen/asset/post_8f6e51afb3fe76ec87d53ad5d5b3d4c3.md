

## Relations关系

(4) \( (R - S)^c = (R \cap \overline{S})^c \)

\( \xrightarrow{ii} R^c \cap \overline{S}^c \xrightarrow{iii} R^c \cap \overline{S}^c = R^c - S^c \)

(7) \( (S \cdot T)^c = T^c \cdot S^c \)

证：

对 \( \forall (x, y) \in (S \cdot T)^c \)，有

\( \Leftrightarrow (y, x) \in S \cdot T \)

\( \Leftrightarrow \exists z \in B, \) 使 \( (y, z) \in S \)，

\( (z, x) \in T \)

即： \( (z, y) \in S^c \)，

\( (x, z) \in T^c \)

\( \Leftrightarrow (x, y) \in T^c \cdot S^c \)

## Relations关系

(10) 证：

∀ \( (x, y) \in R^c \Rightarrow (y, x) \in R \)

⇒ \( (y, x) \in S \Rightarrow (x, y) \in S^c \)

注：

\( R \cdot T \cap S \cdot T \subseteq (R \cap S) \cdot T \) 不一定成立，

由于 \( (R \cap S) \cdot T \subseteq R \cdot T \cap S \cdot T \)

若上式成立，

则 \( (R \cap S) \cdot T = R \cdot T \cap S \cdot T \)

证明：等式不成立

若 ∀ \( a \in A \)，\( b_1, b_2 \in B \)，\( c \in C \)，且

\( (a, b_1) \in R \)，\( (a, b_2) \in S \)，

\( (b_1, c) \notin S \)，\( (a, b_2) \notin R \)，

\( (b_1, c) \in T \)，\( (b_2, c) \in T \)，

显然 \( (a, c) \in R \cdot T \cap S \cdot T \)

但 \( (a, c) \notin (R \cap S) \cdot T \)

## Relations关系

[定义2]：称 \( R \cup R^c \) 是 \( R \) 的对称闭包/symmetric closure of \( R \)，记为 \( s(R) \)。

[定理2]：设 \( R \) 是 \( A \) 上的二元关系，则 \( R \cup R^c \) 是对称的，包含 \( R \) 的最小关系，（其中 \( R^c \) 是 \( R \) 的逆关系）。

证明：若 \( (a, b) \in R \cup R^c \)，则 \( (a, b) \in R \) 或 \( (a, b) \in R^c \)，

\( \Rightarrow (b, a) \in R^c \) 或 \( (b, a) \in R \)，

故 \( (b, a) \in R \cup R^c \)（对称性），

若 \( R' \) 为包含 \( R \)，对称的二元关系，

则对 \( \forall (a, b) \in R \cup R^c \)，

若 \( (a, b) \in R \Rightarrow (a, b) \in R' \)；

若 \( (a, b) \in R^c \Rightarrow (b, a) \in R \)，

\( \Rightarrow (b, a) \in R' \)，

又 \( R' \) 具有对称性，\( (a, b) \in R' \)，

故 \( R \cup R^c \subseteq R' \)。

## Relations关系

[推论2]：当且仅当 \( R \) 是对称闭包时，\( R \) 具有对称性。

证明：(1) \( R \) 具有对称性，

若 \( (a, b) \in R \)，则 \( (b, a) \in R \)，

又 \( (b, a) \in R^c \)

即 \( \forall (b, a) \in R^c \)，\( (a, b) \in R \)

\( \Rightarrow (b, a) \in R \)

\( \Rightarrow R^c \subseteq R \Rightarrow R \cup R^c = R \)；

(2) \( R \) 是对称闭包时，\( R = R \cup R^c \Rightarrow R \) 具有对称性。

[定义3]：传递扩张

设 \( R = \{(a, b) \mid a \, r \, b, \, a, \, b \in A\} \)，则

称 \( R_1 = \{(a, b) \mid (a, b) \in R, \, \text{或} \exists c \in A, \)

使 \( (a, c), \, (c, b) \in R \} \) 为 \( R \) 的传递扩张。

## Relations关系

（3）当且仅当 \( R \) 是传递的，\( R = R_1 \)。

证明：“⇒” \( R \) 是传递的，（\( R \subseteq R_1 \)）

对 \( \forall (a, b) \in R_1 \)，有

\( (a, b) \in R \) 或 \( \exists c \in A \)，

使 \( (a, c), \, (c, b) \in R \)，

由 \( R \) 的传递性，\( (a, b) \in R \)，

故 \( R_1 \subseteq R \)，得 \( R = R_1 \)。

“⇐”：\( R = R_1 \)

若 \( (a, c) \in R \)，\( (c, b) \in R \)，

则 \( (a, b) \in R_1 = R \)，\( R \) 是传递的。

**注：**（1）若 \( R_1 \) 不是传递的，可扩张到 \( R_2 \)，\( R_3 \)，… \( R_k \)；

（2）若 \( R_k \) 是传递的，则 \( R_{k+1} = R_k \)。

## Relations关系

[定义3]：

设 \( R_0 = R \)，\( R_{k+1} \) 是 \( R_k \) 的传递扩张（\( k = 0, 1, 2, ... \)），则称 \( R^* = R_0 \cup R_1 \cup R_2 \cup ... \cup R_k \cup ... \) 为 \( R \) 的传递闭包/transitive closure of \( R \)，也记作 \( t(R) \)。

[定理3] 传递闭包 \( R^* = R \cup R^2 \cup ... \cup R^k \cup ... \)

证明：

\( R^2 = R \cdot R = \{ (a, b) | (a, c), (c, b) \in R \} \)

\( R_1 = \{ (a, b) | (a, b) \in R \text{ 或 } (a, c), (c, b) \in R \} \)

\( = R \cup R^2 \)

\( R_2 = \{ (a, b) | (a, b) \in R_1, \text{ 或 } (a, c), (c, b) \in R_1 \} \)

## Relations关系

故，\( R \) 的闭包 \( R^* = R \cup R_1 \cup R_2 \cup \cdots \cup R_k \cup \cdots \)

\( = \bigcup_{k=0}^{\infty} R_k \)

\( = R \cup R^2 \cup R^3 \cup \cdots \cup R^{2^k} \cup \cdots \)

\( = \bigcup_{k=1}^{\infty} R^k \)

## Relations关系

【定理4】：传递闭包 \( R^* \) 一定是传递的。

证明：设 \( (a, b) \)、\( (b, c) \in R^* \)，则

∃ \( i \)，\( j \)，使 \( (a, b) \in R^i \)，

\( (c, b) \in R^j \)；

故 \( (a, b) \in R^{(i+j)} \subseteq R^* \)

传递扩张的实际意义：

举例：

\( R = \{(a, b) \mid a \text{ 与 } b \text{ 是父子关系} \} \)

\( R \cdot R = \{(a, b) \mid a \text{ 与 } b \text{ 是祖孙关系} \} \)

\( R_1 = \{(a, b) \mid a \text{ 与 } b \text{ 是三代以内男性直系亲属} \} \)

...

## Relations关系

【定理5】：设 \( |A| = n \)，\( R \) 是 \( A \) 上二元关系，则存在正整数 \( k \)，\( k \le n \)，使 \( R^* = R \cup R^2 \cup \cdots \cup R^k \)。

# 证明：

对于 \( (x, y) \in R^* \)，∃ \( k \)，使 \( (x, y) \in R^k \)，表明在 \( A \) 中存在不同元素 \( a_1, a_2, \ldots, a_{k-1} \)，使 \( (x, a_1), (a_1, a_2), (a_2, a_3), \ldots, (a_{k-1}, y) \in R \)。若 \( k > n \)，由鸽洞原理，则 \( a_1, a_2, \ldots, a_{k-1}, y \) 中至少有两个相同，不妨设 \( a_i = y \)，\( (i \le k-1) \)。

## Relations关系

于是 \( (x, a_1), \ldots (a_i, a_{i-1}) \in R \)，

\( (a_{i-1}, y) \in R \)，

故 \( (x, y) \in R^i \)，

即 若 \( k > n \)，必存在比 \( k \) 的正整数 \( i \)，使 \( (x, y) \in R^i \)。

注：

定理说明，可用 \( R \cup R^2 \cup \ldots \cup R^n \) 来求 \( R^* \)。

例6：

设 \( A = \{1, 2, 3\} \),

\( R = \{(1, 1), (1, 2), (2, 3)\} \)

求 \( R^* \)。

