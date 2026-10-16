

## 更多等价律

- *分配律：*  $p \lor (q \land r) \Leftrightarrow (p \lor q) \land (p \lor r)$
  $p \land (q \lor r) \Leftrightarrow (p \land q) \lor (p \land r)$
- *德摩根律：*
  $\lnot(p \land q) \Leftrightarrow \lnot p \lor \lnot q$
  $\lnot(p \lor q) \Leftrightarrow \lnot p \land \lnot q$
- *平凡的永真式/矛盾式：*
  $p \lor \lnot p \Leftrightarrow \mathbf{T}$      $p \land \lnot p \Leftrightarrow \mathbf{F}$

![](img/c25dfd82fc242c2db53bc942dcad6885_235_0.png)

## 通过等价定义算子

利用等价，我们可以用其他算子来*定义*算子。

- 异或：$p \oplus q \Leftrightarrow (p \lor q) \land \lnot (p \land q)$
  $p \oplus q \Leftrightarrow (p \land \lnot q) \lor (q \land \lnot p)$
- 蕴含：$p \rightarrow q \Leftrightarrow \lnot p \lor q$
- 双条件：$p \leftrightarrow q \Leftrightarrow (p \rightarrow q) \land (q \rightarrow p)$
  $p \leftrightarrow q \Leftrightarrow \lnot (p \oplus q)$

## 重新审视永真式

- 我们已通过示例 $p \lor \lnot p$ 引入了永真式的概念
- 现在，你已了解更多算子，因此可以表述更多永真式，例如 $(p \lor q) \leftrightarrow \lnot(\lnot p \land \lnot q)$
$(p \rightarrow q) \leftrightarrow (\lnot q \rightarrow \lnot p)$，等等

## 表 4

# 表 4

证明 $p \vee (q \wedge r)$ 与 $(p \vee q) \wedge (p \vee r)$ 在逻辑上等价的演示。

| p | q | r | q ∧ r | p ∨ (q ∧ r) | p ∨ q | p ∨ r | (p ∨ q) ∧ (p ∨ r) |
|---|---|---|-------|-------------|-------|-------|-------------------|
| T | T | T | T | T | T | T | T |
| T | T | F | F | T | T | T | T |
| T | F | T | F | T | T | T | T |
| T | F | F | F | T | T | T | T |
| F | T | T | T | T | T | T | T |
| F | T | F | F | F | T | F | F |
| F | F | T | F | F | F | T | F |
| F | F | F | F | F | F | F | F |

## 构造新的逻辑等价式

- 我们可以通过发展一系列逻辑等价的陈述来证明两个表达式在逻辑上等价。
- 要证明 $A \equiv B$，我们从 A 开始以 B 结束产生一系列等价式。
  $A \equiv A_1$
  $\vdots$
  $A_n \equiv B$
- 请记住，只要命题（由命题变量表示）在前面列出的等价式中出现，它就可以被任意复杂的复合命题所替代。

## 等价证明

例：证明 ¬(p ∨ (¬p ∧ q)) 在逻辑上等价于 ¬p ∧ ¬q

# 解：

¬(p ∨ (¬p ∧ q)) ≡ ¬p ∧ ¬(¬p ∧ q) 根据第二条德摩根律

≡ ¬p ∧ [¬(¬p) ∨ ¬q] 根据第一条德摩根律

≡ ¬p ∧ (p ∨ ¬q) 根据双重否定律

≡ (¬p ∧ p) ∨ (¬p ∧ ¬q) 根据第二分配律

≡ F ∨ (¬p ∧ ¬q) 因为 ¬p ∧ p ≡ F

≡ (¬p ∧ ¬q) ∨ F 根据析取的交换律

≡ (¬p ∧ ¬q) 根据 F 的同一律

## 例 5

- 证明 ¬(p∨(¬ p∧q)) 与 ¬ p∧ q 在逻辑上等价。
- 

¬(p∨(¬p∧q)) ⇔ ¬p∧¬(¬p∧q)
⇔ ¬p∧[¬(¬p)∨¬q]
⇔ ¬p∧(p∨¬q)
⇔ (¬p∧p)∨(¬p∧¬q)
⇔ F∨(¬p∧¬q)
⇔ (¬p∧¬q)∨F
⇔ ¬p∧¬q

## 一个例题

- 使用符号推导检查是否 $(p \land \lnot q) \rightarrow (p \oplus r) \Leftrightarrow \lnot p \lor q \lor \lnot r.$

$(p \land \lnot q) \rightarrow (p \oplus r)$      [展开 → 的定义]
$\Leftrightarrow \lnot(p \land \lnot q) \lor (p \oplus r)$      [展开 ⊕ 的定义]
$\Leftrightarrow \lnot(p \land \lnot q) \lor ((p \lor r) \land \lnot(p \land r))$      [德摩根律]
$\Leftrightarrow (\lnot p \lor q) \lor ((p \lor r) \land \lnot(p \land r))$      cont.

## 例继续...

($\neg p \vee q$) $\vee$ (($p \vee r$) $\wedge$ $\neg$($p \wedge r$)) $\Leftrightarrow$ [$\vee$ 可交换]
$\Leftrightarrow$ ($q \vee \neg p$) $\vee$ (($p \vee r$) $\wedge$ $\neg$($p \wedge r$)) [$\vee$ 可结合]
$\Leftrightarrow$ $q \vee$ ($\neg p \vee$ (($p \vee r$) $\wedge$ $\neg$($p \wedge r$))) [$\vee$ 对 $\wedge$ 分配]
$\Leftrightarrow$ $q \vee$ ((( $\neg p \vee$ ($p \vee r$)) $\wedge$ ($\underline{\neg p} \vee$ $\neg$($p \wedge r$)))
[结合] $\Leftrightarrow$ $q \vee$ ((( $\neg p \vee p$) $\vee r$) $\wedge$ ($\neg p \vee \neg$($p \wedge r$)))
[平凡永真式] $\Leftrightarrow$ $q \vee$ (($\mathbf{T} \vee r$) $\wedge$ ($\neg p \vee \neg$($p \wedge r$)))
[支配律] $\Leftrightarrow$ $q \vee$ ($\mathbf{T} \wedge$ ($\neg p \vee \neg$($p \wedge r$)))
[同一律]      $\Leftrightarrow$ $q \vee$ ($\neg p \vee \neg$($p \wedge r$)) $\Leftrightarrow$ cont.

