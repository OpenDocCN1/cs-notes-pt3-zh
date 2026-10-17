

## 对偶原理

例：若 \((P \land Q) \lor (\neg P \lor (\neg P \lor Q)) \Leftrightarrow \neg P \lor Q\)，试证明  
\((P \lor Q) \land (\neg P \land (\neg P \land Q)) \Leftrightarrow \neg P \land Q\)

证明：设 \(A = (P \land Q) \lor (\neg P \lor (\neg P \lor Q))\)  
\(B = \neg P \lor Q\)

则 \(A^* = (P \lor Q) \land (\neg P \land (\neg P \land Q))\)  
\(B^* = \neg P \land Q\)

由于 \(A \Leftrightarrow B\)  
因此 \(A^* \Leftrightarrow B^*\)

## 对偶原理

- 试证明：(1) \((P \leftrightarrow Q) \rightarrow (\neg P \lor Q) \Leftrightarrow T\) (2) \((P \leftrightarrow Q) \land (\neg P \land Q) \Leftrightarrow F\)

证明：\((P \leftrightarrow Q) \land (\neg P \land Q)\)  
\(\Leftrightarrow ((P \land Q) \lor (\neg P \land \neg Q)) \land (\neg P \land Q) \quad E_{26}\)  
由 \((P \leftrightarrow Q) \rightarrow (\neg P \lor Q)\)  
\(\Leftrightarrow ((\neg P \lor \neg Q) \land (P \lor Q)) \lor (\neg P \lor Q) \quad E_{11}, E_{12}\)  
知 \((P \leftrightarrow Q) \land (\neg P \land Q)\) 和 \((P \leftrightarrow Q) \rightarrow (\neg P \lor Q)\) 互为对偶式  
由于 \(T\) 的对偶式是 \(F\)，因此由定理1.5-1知  
\((P \leftrightarrow Q) \land (\neg P \land Q) \Leftrightarrow F\)

## 对偶原理

- 定理1.3：  
  若 \(A \Rightarrow B\)，且 \(A\)、\(B\) 为命题变元 \(P_1, P_2, \cdots, P_n\) 及联结词 \(\land, \lor, \neg\) 构成的公式，则 \(B^* \Rightarrow A^*\)。

- 证明：
  - \(A \Rightarrow B\) 意味着 \(A(P_1, P_2, \cdots, P_n) \rightarrow B(P_1, P_2, \cdots, P_n)\)
  - 由逆反律得 \(\neg B(P_1, P_2, \cdots, P_n) \rightarrow \neg A(P_1, P_2, \cdots, P_n)\)
  - 根据定理1.1 \(B^*(\neg P_1, \neg P_2, \cdots, \neg P_n) \rightarrow A^*(\neg P_1, \neg P_2, \cdots, \neg P_n)\)
  - 永真
  - 利用带入规则，以 \(\neg P_i (i = 1, 2, \cdots, n)\) 取代 \(P_i\) 得 \(B^*(P_1, P_2, \cdots, P_n) \rightarrow A^*(P_1, P_2, \cdots, P_n)\)
  - 永真
  - 即 \(B^* \Rightarrow A^*\)

## 1.5 范式和判定问题

公式的标准形式——范式

用来在有限步内判定公式永真、永假、可满足的

## 析取范式和合取范式

- 定义：

- 若一个命题公式是一些命题变元及其否定的积，则称之为基本积；若这个命题公式是一些变元及其否定之和，称为基本和。

基本积：\(P, Q, \neg P, \neg Q, \neg P \wedge Q, P \wedge Q, \neg P \wedge P, \neg Q \wedge P \wedge Q\)

基本和：\(P, \neg P, Q, \neg Q, P \vee \neg Q, P \vee Q, \neg P \vee P\)

- 一个由**基本积的和**组成的公式，如果与给定的公式 **A** 等价，则称它是 **A** 的析取范式。

析取范式：\(P, Q, \neg P, \neg Q, \neg P \wedge Q, (P \wedge Q) \vee (\neg P \wedge Q)\)

- 一个由**基本和的积**组成的公式，如果与给定的命题公式 **A** 等价，则称它是 **A** 的合取范式。

合取范式：\(P, \neg P, Q, \neg Q, P \vee \neg Q, (P \vee Q) \wedge (\neg P \vee P)\)

## 析取范式和合取范式

- 定理1.4：一个基本积是永假式，当且仅当它含有 \(P, \neg P\) 形式的两个因子。

- 证明：
  - （充分性）由于 \(P \land \neg P\) 是永假式，而 \(Q \land F \iff F\)，所以含有 \(P\) 和 \(\neg P\) 形式的两个因子时基本积是永假式。
  - （必要性）用反证法。设基本积为假但不含 \(P\) 和 \(\neg P\) 形式的因子，于是给这个基本积中的命题变元指派真值 \(T\)，给带有否定的命题变元指派真值 \(F\)，得基本积的真值是 \(T\)，与假设矛盾。证毕。

## 析取范式和合取范式

- 定理1.5：一个基本和是永真式，当且仅当它含有 \(P, \neg P\) 形式的两个因子。

## 析取范式和合取范式

例：求命题公式 \(P \land (Q \rightarrow R)\) 的析取范式

解：\(P \land (Q \rightarrow R) \Leftrightarrow P \land (\neg Q \lor R)\)

/*这是一个合取范式*/

\(\Leftrightarrow (P \land \neg Q) \lor (P \land R)\)

/*使用与对或的分配律，化成析取范式*/

## 析取范式与合取范式

例：求命题公式 \((\neg P \land Q) \leftrightarrow (P \rightarrow Q)\) 的合取范式

解：\((\neg P \land Q) \leftrightarrow (P \rightarrow Q)\)

\(\leftrightarrow (((\neg P \land Q) \land (P \rightarrow Q)) \lor (\neg (\neg P \land Q) \land \neg (P \rightarrow Q))\)

/*消↔*/

\(\leftrightarrow (((\neg P \land Q) \land (\neg P \lor Q)) \lor ((P \lor \neg Q) \land (P \land \neg Q))\)

/*消→ 并且否定深入到单个变元前*/

\(\leftrightarrow (\neg P \land Q) \lor (P \land \neg Q)\) /\*析取范式*/

\(\leftrightarrow ((\neg P \land Q) \lor P) \land ((\neg P \land Q) \lor \neg Q)\)

\(\leftrightarrow (P \lor Q) \land (\neg P \lor \neg Q)\)

/*使用或对与的分配律及补余律，现在是合取范式的形式*/

## 析取范式和合取范式

例：求 \(\neg(P \lor Q) \leftrightarrow (P \land Q)\) 的析取范式。

解：\(\neg(P \lor Q) \leftrightarrow (P \land Q)\)

\(\Leftrightarrow \neg(P \lor Q) \land (P \land Q) \lor \neg(\neg(P \lor Q)) \land \neg(P \land Q)\)

\(\Leftrightarrow (\neg P \land \neg Q \land P \land Q) \lor ((P \lor Q) \land (\neg P \lor \neg Q))\)

\(\Leftrightarrow F \lor (P \lor Q) \land (\neg P \lor \neg Q)\)

\(\Leftrightarrow (P \lor Q) \land (\neg P \lor \neg Q)\)

\(\Leftrightarrow ((P \lor Q) \land \neg P) \lor (((P \lor Q) \land \neg Q)\)

\(\Leftrightarrow P \land \neg P \lor \neg P \land Q \lor P \land \neg Q \lor Q \land \neg Q\)

\(\Leftrightarrow F \lor \neg P \land Q \lor P \land \neg Q \lor F\)

\(\Leftrightarrow (\neg P \land Q) \lor (P \land \neg Q)\)

## 析取范式和合取范式

例：求 \(\neg(P \lor Q) \leftrightarrow (P \land Q)\) 的合取范式。

解：令 \(A \Leftrightarrow \neg(P \lor Q) \leftrightarrow (P \land Q)\)，那么

\(\neg A \Leftrightarrow \neg(\neg(P \lor Q) \leftrightarrow (P \lor Q))\)

\(\Leftrightarrow \neg(\neg(P \lor Q) \land (P \land Q)) \lor (\neg(\neg(P \lor Q) \land \neg(P \land Q)))\)

\(\Leftrightarrow \neg((\neg P \land \neg Q \land P \land Q) \lor ((P \lor Q) \land (\neg P \lor \neg Q)))\)

\(\Leftrightarrow \neg P \land \neg Q \lor P \land Q\)

由于 \(A \Leftrightarrow \neg\neg A = \neg(\neg P \land \neg Q \lor P \land Q)\)

所以 \(A \Leftrightarrow (P \lor Q) \land (\neg P \lor \neg Q)\)

## 主析取范式

定义1.10：在含n个变元的基本积中，若每个变元与其否定不同时存在，而二者之一必出现且仅出现一次，则称这种基本积为极小项。

例：
- 两个命题变元P、Q的极小项为  
  \(P \land Q, P \land \neg Q, \neg P \land Q, \neg P \land \neg Q\)

n个变元，极小项个数 \(2^n\)

