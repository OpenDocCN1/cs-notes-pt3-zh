# 例2.4 证明： \( (p \to q) \to r \Leftrightarrow p \to (q \to r) \)

证 方法一： 真值表法，略。

方法二： 观察法。易见010是 \( (p \to q) \to r \) 的成假赋值，而它却是 \( p \to (q \to r) \) 的成真赋值，故 \( (p \to q) \to r \Leftrightarrow p \to (q \to r) \)。

方法三： 记 \( A = (p \to q) \to r \)， \( B = p \to (q \to r) \)。先将 \( A \)、\( B \) 等值演算化成易于观察真值的公式，再进行判断。

\( A = (p \to q) \to r \Leftrightarrow (\neg p \lor q) \to r \) （蕴含等值式）

\( \Leftrightarrow \neg (\neg p \lor q) \lor r \) （蕴含等值式）

\( \Leftrightarrow (p \land \neg q) \lor r \) （德摩根律）

\( B = p \to (q \to r) \Leftrightarrow \neg p \lor (\neg q \lor r) \) （蕴含等值式）

\( \Leftrightarrow \neg p \lor \neg q \lor r \) （结合律）

易见， 000， 010 是 \( A \) 的成假赋值，而它们是 \( B \) 的成真赋值。故 \( (p \to q) \to r \Leftrightarrow p \to (q \to r) \)。