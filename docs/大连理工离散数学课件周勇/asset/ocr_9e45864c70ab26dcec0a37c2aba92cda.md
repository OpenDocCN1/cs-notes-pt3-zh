# 三、笛卡尔乘积

# 定理：设有_A,B,C_三个集合，则

(a) \( A \times (B \cup C) = (A \times B) \cup (A \times C) \)

(b) \( A \times (B \cap C) = (A \times B) \cap (A \times C) \)

(c) \( (A \cup B) \times C = (A \times C) \cup (B \times C) \)

(d) \( (A \cap B) \times C = (A \times C) \cap (B \times C) \)

证：设 \(\langle x, y \rangle\) 是 \( A \times (B \cup C) \) 的任意元素，根据 \(\land\) 对 \(\lor\) 的分配律，有：

\(\langle x, y \rangle \in A \times (B \cup C)\)

\(\Leftrightarrow x \in A \land y \in B \cup C\)

\(\Leftrightarrow x \in A \land (y \in B \lor y \in C)\)

\(\Leftrightarrow (x \in A \land y \in B) \lor (x \in A) \land y \in C)\)

\(\Leftrightarrow \langle x, y \rangle \in A \times B \lor \langle x, y \rangle \in A \times C\)

\(\Leftrightarrow \langle x, y \rangle \in (A \times B) \cup (A \times C)\) 得证。