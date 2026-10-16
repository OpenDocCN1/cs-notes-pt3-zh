

## 重言式、矛盾式与偶然式

- *重言式*是始终为真的命题。
  - 示例：$p \lor \lnot p$
- *矛盾式*是始终为假的命题。
  - 示例：$p \land \lnot p$
- *偶然式*是既非重言式也非矛盾式的命题，例如 $p$

| p | ¬p | p ∨ ¬p | p ∧ ¬p |
|---|---|---|---|
| T | F | T | F |
| F | T | T | F |

## 下列哪些是重言式？

- 1. $p \to (q \to p)$
- 2. $p \to (\lnot p \to p)$
- 3. $(q \to p) \to (p \to q)$
- 4. $(q \to p) \lor (p \to q)$
- 5. $(p \to (q \to r)) \to (q \to (p \to r))$

请用真值表证明你的结论。
（提示：考虑给 p、q 和 r 赋予什么样的真值会使每个公式为假。）

## 命题等价式

两个*语法上*（即文本上）不同的复合命题可能在*语义上*相同（即具有相同的含义）。我们称它们为*逻辑等价*。逻辑等价

记号：... ↔ ...

## 用真值表证明等价

例：证明 p∨q ⇔ ¬(¬p ∧ ¬q)。

| p | q | p∨q | ¬p | ¬q | ¬p ∧ ¬q | ¬(¬p ∧ ¬q) |
|---|---|---|---|---|---|---|
| F | F | F | T | T | T | F |
| F | T | T | T | F | F | T |
| T | F | T | F | T | F | T |
| T | T | T | F | F | F | T |

## 逻辑等价式（等价式）

- $P \land T \Leftrightarrow P$  同一律（Identity）
- $P \lor F \Leftrightarrow P$
- $P \lor T \Leftrightarrow T$  零律（Domination）
- $P \land F \Leftrightarrow F$
- $P \lor P \Leftrightarrow P$  等幂律（Idempotency）
- $P \land P \Leftrightarrow P$

## 逻辑等价式（等价式）

- ¬(¬P) ⇔ P   双重否定律（Double negation）
- $P \lor Q \Leftrightarrow Q \lor P$   交换律（Commutativity）
- $P \land Q \Leftrightarrow Q \land P$
- $(P \lor Q) \lor R \Leftrightarrow P \lor (Q \lor R)$   结合律（Associativity）
- $(P \land Q) \land R \Leftrightarrow P \land (Q \land R)$

## 逻辑等价式

- $P \land (Q \lor R) \Leftrightarrow (P \land Q) \lor (P \land R)$ 分配律（Distributivity）
- $P \lor (Q \land R) \Leftrightarrow (P \lor Q) \land (P \lor R)$
- $\lnot(P \land Q) \Leftrightarrow \lnot P \lor \lnot Q$ 德·摩根律（DeMorgan's laws）
- $\lnot(P \lor Q) \Leftrightarrow \lnot P \land \lnot Q$

## 逻辑等价式

- $P \to Q \Leftrightarrow \neg P \lor Q$　　 **蕴涵等价式**（Implication）
- $P \lor \neg P \Leftrightarrow T$　　 **排中律**（Tautology）
- $P \land \neg P \Leftrightarrow F$　　 **矛盾律**（Contradiction）
- $(P \to Q) \land (Q \to P) \Leftrightarrow (P \leftrightarrow Q)$　　 **等价式**（Equivalence）
- $(P \to Q) \land (P \to \neg Q) \Leftrightarrow \neg P$　　 **归谬论**（Absurdity）

## 逻辑等价式

- $(P \to Q) \Leftrightarrow (\lnot Q \to \lnot P)$ 蕴涵逆反式（Contrapositive）
- $P \lor (P \land Q) \Leftrightarrow P$, $P \land (P \lor Q) \Leftrightarrow P$ 吸收律（Absorption）
- $(P \land Q) \to R \Leftrightarrow P \to (Q \to R)$ 输出律（Exportation）

## ↔ 和 ⇔ 有什么区别？

A ⇔ B 表示不存在任何对 A 和 B 的真值赋值能使 A ↔ B 为假。

因此，A ⇔ B 只能存在于经过恰当选择的复合命题 A 和 B 之间。例如，p∨q ⇔ ¬(¬p ∧ ¬q)。

A ↔ B 表示 A 和 B 恰好具有相同的真值。例如，

A=2+2=4。B=我在北京邮电大学教书。

A=2+2=4。B=我在北京邮电大学或北京理工大学教书。

## 判断命题公式逻辑等价的方法：

- 1、真值表
- 2、命题公式的演算
  - 基本等值定理;
  - 代入规则
  - 置换规则

## 代入规则

- 在一个永真公式中，任何一个命题变元R出现的每一处，用另一个命题公式代入，所得命题公式仍是永真式。
  - 例：求证：(p → q) ∨ ¬(p→q)为永真式
  - R∨¬R⇔T
  - 用(p → q)代入上式中所有的R

## 置换规则

- 给定公式A，它的所有子公式为A₁，A₂，...Aₙ ，设Aᵢ ⇔ Bᵢ，用Bᵢ置换Aᵢ，所得公式为B，则 A ⇔ B。
- 例：求证：
- (P → (Q → R) ⇔ P → (¬ Q ∨ R)为永真式
- 已知(Q → R) ⇔ (¬ Q ∨ R)
- 用(¬ Q ∨ R)置换原式中的(Q → R)

## 命题公式逻辑等价关系的应用：

- 1、判定是否逻辑等价；
- 2、判断是否为永真公式或永假公式；
- 3、命题公式的化简

## 等价律 - 示例

- *同一律：* $p \land T \Leftrightarrow p$    $p \lor F \Leftrightarrow p$
- *零律：* $p \lor T \Leftrightarrow T$    $p \land F \Leftrightarrow F$
- *等幂律：* $p \lor p \Leftrightarrow p$    $p \land p \Leftrightarrow p$
- *双重否定律：* $\lnot \lnot p \Leftrightarrow p$
- *交换律：* $p \lor q \Leftrightarrow q \lor p$    $p \land q \Leftrightarrow q \land p$
- *结合律：* $(p \lor q) \lor r \Leftrightarrow p \lor (q \lor r)$
  $(p \land q) \land r \Leftrightarrow p \land (q \land r)$

