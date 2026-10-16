
## 求主析取范式的方法之二：等值演算法

- 利用十六个命题公式、命题定理，用等值演算法的方法一步步将它化为主析取范式。
- 第一步：将公式化为析取范式，“消去”含有矛盾式的简单合取式，这是因为（P∧¬P∧Q）∨G⇔G，而P∧P用P代替。
- 第二步：若析取范式中的简单合取式项不是极小项，即该项中缺命题变项，则添加（Pᵢ∨¬Pᵢ）再用分配律展开。
  - 例如：公式中含P、Q、R，某合取项为P∧¬R，缺Q。则P∧¬R⇔P∧¬R∧（Q∨¬Q）⇔（P∧Q∧¬R）∨（P∧¬Q∧¬R）
- 第三步：用幂等律将重复的极小项删去，即mᵢ∨mᵢ⇔mᵢ，然后将各极小项按顺序排列。

## 例：求（（P∨Q）→R）→P的主析取范式

解：原公式⇔¬（¬（P∨Q）∨R）∨P
⇔（（P∨Q）∧¬R）∨P
⇔（P∧¬R）∨（Q∧¬R）∨P（析取范式）
⇔P∨（Q∧¬R）（析取范式）
⇔（P∧（Q∨¬Q）∧（R∨¬R））∨（（Q∧¬R）∧（P∨¬P））
⇔（P∧Q∧R）∨（P∧Q∧¬R）∨（P∧¬Q∧R）∨（P∧¬Q∧¬R）∨（P∧Q∧¬R）∨（¬P∧Q∧¬R）
（六个极小项，其中重复了一个）
⇔（P∧Q∧R）∨（P∧Q∧¬R）∨（P∧¬Q∧R）∨（P∧¬Q∧¬R）∨（¬P∧Q∧¬R）
⇔m₂∨m₄∨m₅∨m₆∨m₇ ⇔Σ(2,4,5,6,7)

## Normal or Canonical Forms(范式)

- Unique representations of a proposition
- Examples:
  - Construct a simple proposition of two variables which is true only when
    - P is true and Q is false:
      $P \land \lnot Q$
    - P is true and Q is true:
      $P \land Q$
    - P is true and Q is false or P is true and Q is true:
      $(P \land \lnot Q) \lor (P \land Q)$

## Normal or Canonical Forms

- A disjunction of conjunctions where
  - every variable or its negation is represented once in each conjunction （合取式）
    (a *minterm*)
  - each minterm appears only once

## Disjunctive Normal Form (DNF)（析取范式）

- Important in switching theory, simplification in the design of circuits.
- Method: To find the minterms of the DNF.
  - Use the rows of the truth table where the proposition is 1 or True
  - If a zero appears under a variable, use the negation of the propositional variable in the minterm
  - If a one appears, use the propositional variable.

## Example

- Find the DNF of $(P \lor Q) \to \lnot R$

| P | Q | R | $(P \lor Q) \to \lnot R$ |
|---|---|---|---|
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 0 |

## Example

There are 5 cases where the proposition is true, hence 5 minterms. Rows 1,2,3, 5 and 7 produce the following disjunction of minterms:

$(P \lor Q) \rightarrow \lnot R$

$\Leftrightarrow (\lnot P \land \lnot Q \land \lnot R) \lor (\lnot P \land \lnot Q \land R) \lor (\lnot P \land Q \land \lnot R)$

$\lor (P \land \lnot Q \land \lnot R) \lor (P \land Q \land \lnot R)$

Note that you get a *Conjunctive Normal Form* (CNF) （合取范式） if you negate a DNF and use DeMorgan’s Laws.

## 主合取范式（Major conjunctive normal form）

- 若干个极大项的合取。
- 如公式中共有N个命题变项P₁，……，Pₙ，这N个变项的析取式中，每个变项Pᵢ或其否定¬Pᵢ均出现且两者仅出现一个，并且按命题变项的下标排列（字母按字典序列），这样的简单析取式称为极大项。

## 极大项的记法

| 极大项 | 对应的赋值 | 十进制数 | 记法 |
|---|---|---|---|
| P ∨ Q ∨ R | 000 | 0 | M₍₀₀₀₎或M₀ |
| P ∨ Q ∨ ¬R | 001 | 1 | M₍₀₀₁₎或M₁ |
| P ∨ ¬Q ∨ R | 010 | 2 | M₍₀₁₀₎或M₂ |
| P ∨ ¬Q ∨ ¬R | 011 | 3 | M₍₀₁₁₎或M₃ |
| ¬P ∨ Q ∨ R | 100 | 4 | M₍₁₀₀₎或M₄ |
| ¬P ∨ Q ∨ ¬R | 101 | 5 | M₍₁₀₁₎或M₅ |
| ¬P ∨ ¬Q ∨ R | 110 | 6 | M₍₁₁₀₎或M₆ |
| ¬P ∨ ¬Q ∨ ¬R | 111 | 7 | M₍₁₁₁₎或M₇ |

## 例：用真值表的方法求¬（P∧Q）的主合取范式

解：
- ¬（P∧Q）的真值表
- 找使公式为假的赋值。
- 11对应的极大项是
  - ¬P ∨ ¬Q（M₃）

则原公式的主合取范式是
¬（P∧Q） ⇔ ¬P ∨ ¬Q ⇔ M₃

| P | Q | P∧Q | ¬（P∧Q） |
|---|---|---|---|
| 0 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 0 |

## 求主合取范式的方法之二：等值演算法

- 利用十六个命题公式、命题定理，用等值演算法的方法一步步将它化为主合取范式。
- 第一步：将公式化为合取范式，“消去”含有永真式的简单析取式，这是因为（P ∨ ¬P ∨ Q）∧ G ⇔ G，而P ∨ P用P代替。
- 第二步：若合取范式中的简单析取式项不是极大项，即该项中缺命题变项，则添加（Pᵢ ∧ ¬Pᵢ）再用分配律展开。
  - 例如：公式中含P、Q、R，某析取项为P ∨ ¬R，缺Q。则P ∨ ¬R ⇔ P ∨ ¬R ∨（Q ∧ ¬Q） ⇔ （P ∨ Q ∨ ¬R） ∧ （P ∨ ¬Q ∨ ¬R）
- 第三步：用幂等律将重复的极大项删去，即Mᵢ ∧ Mᵢ ⇔ Mᵢ，然后将各极大项按顺序排列。

## Disjunctive Normal Form

- A propositional formula is in *disjunctive normal form* if it consists of a disjunction of $(1,\ldots,n)$ disjuncts where each disjunct consists of a conjunction of $(1,\ldots,m)$ atomic formulas or the negation of an atomic formula.
- Yes
  - $(p \land \neg q) \lor (\neg p \lor q)$
- No
  - $p \land (p \lor q)$

## Disjunctive Normal Form

**Example:** Show that every compound proposition can be put in disjunctive normal form.

**Solution:** Construct the truth table for the proposition. Then an equivalent proposition is the disjunction with *n* disjuncts (where *n* is the number of rows for which the formula evaluates to **T**). Each disjunct has *m* conjuncts where *m* is the number of distinct propositional variables. Each conjunct includes the positive form of the propositional variable if the variable is assigned **T** in that row and the negated form if the variable is assigned **F** in that row. This proposition is in disjunctive normal form.
