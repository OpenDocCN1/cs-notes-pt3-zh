
# Logic and bit operations

- Computer bit operations correspond to the logical connectives.
- Bitwise OR bitwise AND bitwise XOR

# Bitwise Operations

- Boolean operations can be extended to operate on bit strings as well as single bits.
- E.g.:
  01 1011 0110
  11 0001 1101
  11 1011 1111 Bit-wise OR
  01 0001 0100 Bit-wise AND
  10 1010 1011 Bit-wise XOR

# 练习

1. \(P\)、\(Q\)为两个命题，当且仅当 \(P=Q=\) 时，\(P\land Q\) 的真值为1；当且仅当 \(P=Q=\) 时，\(P\lor Q\) 的真值为0。

# 4. 下面语句是真命题的为( )

- (A) 我正在说谎
- (B) 如果1+2=3,则雪是黑色的.
- (C) 如果1+2=5,则雪是黑色的.
- (D) 你上网了吗?

# 6. 给命题变元P Q R S 分别指派真值1,1,0,0求命题公式

(P ∨ (Q → (R ∧ ¬P))) ↔ (Q ∨ ¬S)

的真值.

# 解

(P ∨ (Q → (R ∧ ¬P))) ↔ (Q ∨ ¬S)

(1 ∨ (1 → (0 ∧ ¬1))) ↔ (1 ∨ ¬0)

1

# § 1.2 Applications of Propositional Logic

# Applications of Propositional Logic:
Summary

- Translating English to Propositional Logic
- System Specifications 系统规格
- Boolean Searching
- Logic Puzzles
- Logic Circuits

# Translating sentences
Example(命题翻译)

- ‘If I go to school or go home, I will not go shopping.’
  - P: I go to school
  - Q: I go home
  - R: I will go shopping
- If......P......or......Q......then....not.....R
  - $(P \lor Q) \rightarrow \lnot R$
- You can access the Internet from campus only if you are a computer science major or you are not a freshman.
- a → ( c ∨ ¬ f )

# Translating English Sentences

- Steps to convert an English sentence to a statement in propositional logic
  - Identify atomic propositions and represent using propositional variables.
  - Determine appropriate logical connectives
- “You cannot ride the roller coaster if you are under 4 feet tall unless you are older than 16 years old.”
  - p: you are under 4 feet tall,
  - q: you are older than 16 years old.
  - r: You can ride the roller coaster.

If p and ¬q then not r.      (p∧¬q) → ¬r

翻译：
她既聪明又用功
除非你努力,否则你将失败.

甲和乙中有一人且只有一人是大学生.

# 翻译

- 我和他既是弟兄又是同学。
- 别问我是谁.

# System Specifications

- System and Software engineers take requirements in English and express them in a precise specification language based on logic.

**Example**: Express in propositional logic:
“The automated reply cannot be sent when the file system is full”

**Solution**: One possible solution: Let *p* denote “The automated reply can be sent” and *q* denote “The file system is full.”

q → ¬ p

# Consistent System Specifications

**Definition:** A list of propositions is *consistent* if it is possible to assign truth values to the proposition variables so that each proposition is true.

**Exercise:** Are these specifications consistent?

- “The diagnostic message is stored in the buffer or it is retransmitted.”
- “The diagnostic message is not stored in the buffer.”
- “If the diagnostic message is stored in the buffer, then it is retransmitted.”

**Solution:** Let p denote “The diagnostic message is not stored in the buffer.” Let q denote “The diagnostic message is retransmitted.” The specification can be written as: p ∨ q, ¬p, ¬p. When p is false and q is true all three statements are true. So the specification is consistent.

- What if “The diagnostic message is not retransmitted is added.”

**Solution:** Now we are adding ¬q and there is no satisfying assignment. So the specification is not consistent.

# Logic Puzzles

![](img/c25dfd82fc242c2db53bc942dcad6885_196_0.png)

Raymond Smullyan
(Born 1919)

- An island has two kinds of inhabitants, *knights*, who always tell the truth, and *knaves*, who always lie.
- You go to the island and meet A and B.
  - A says “B is a knight.”
  - B says “The two of us are of opposite types.”

**Example**: What are the types of A and B?

**Solution:** Let *p* and *q* be the statements that A is a knight and B is a knight, respectively. So, then ¬*p* represents the proposition that A is a knave and ¬*q* that B is a knave.

- If A is a knight, then *p* is true. Since knights tell the truth, *q* must also be true. Then (*p* ∧ ¬*q*)∨ (¬*p* ∧ *q*) would have to be true, but it is not. So, A is not a knight and therefore ¬*p* must be true.
- If A is a knave, then B must not be a knight since knaves always lie. So, then both ¬*p* and ¬*q* hold since both are knaves.
