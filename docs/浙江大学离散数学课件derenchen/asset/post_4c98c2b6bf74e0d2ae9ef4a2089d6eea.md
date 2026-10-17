
## 命题的语句形式

### 陈述句

### 非命题语句：
- 疑问句
- 命令句
- 感叹句

### 非命题陈述句：悖论语句

## 命题的符号表示：

大小写英文字母：P、Q、R、p、q、r、...

## 命题真值（Truth Values）的表示：

真： T、 1
假： F、 0

命题语句真值确定的几点说明：

- 1、时间性
- 2、区域性
- 3、标准性

命题真值间的关系表示：

## 真值表（Truth Table）

### DEFINITION 1（p的否定）

Let p be a proposition. The statement

"It is not the case that p."

is another proposition, called the negation of p.

The negation of p is denoted by ¬ p. The proposition ¬ p is read "not p."

| P | ¬ P |
|---|---|
| T | F |
| F | T |

### DEFINITION 2（p和q的合取）

Let p and q be propositions. The proposition "p and q," denoted by \( p \land q \), is the proposition that is true when both p and q are true and is false otherwise. The proposition \( p \land q \) is called the conjunction of p and q.

The truth table for \( p \land q \) is shown in Table 2.

### TABLE 2
**The Truth Table for the Conjunction of Two Propositions.**

| p | q | p ∧ q |
|---|---|---|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

### EXAMPLE 4

Find the conjunction of the propositions p and q where p is the proposition "Today is Friday" and q is the proposition "It is raining today."

**Solution:**

The conjunction of these propositions, \( p \land q \), is the proposition "Today is Friday and it is raining today." This proposition is true on rainy Fridays and is false on any day that is not a Friday and on Fridays when it does not rain.

### DEFINITION 3（p和q的析取）

Let p and q be propositions. The proposition "p or q," denoted by p∨q, is the proposition that is false when p and q are both false and true otherwise. The proposition p∨q is called the disjunction of p and q.

The truth table for p∨q is shown in Table 3.

### TABLE 3
**The Truth Table for the Disjunction of Two Propositions.**

| p | q | p ∨ q |
|---|---|-------|
| T | T | T |
| T | F | T |
| F | T | T |
| F | F | F |

### EXAMPLE 5

What is the disjunction of the propositions p and q where p and q are the same propositions as in Example 4?

**Solution:**

The disjunction of p and q, p ∨ q, is the proposition

"Today is Friday or it is raining today."

This proposition is true on any day that is either a Friday or a rainy day (including rainy Fridays). It is only false on days that are not Fridays when it also does not rain.

### DEFINITION 4（p和q的对称差）

Let p and q be propositions. The exclusive or of p and q, denoted by p ⊕ q, is the proposition that is true when exactly one of p and q is true and is false otherwise.

The truth table for the exclusive or of two propositions is displayed in Table 4.

### TABLE 4
**The Truth Table for the Exclusive Or of Two Propositions.**

| p | q | p ⊕ q |
|---|---|---|
| T | T | F |
| T | F | T |
| F | T | T |
| F | F | F |

### TABLE 5

| p   | q   | p→q   |
|-----|-----|-------|
| T   | T   | T     |
| T   | F   | F     |
| F   | T   | T     |
| F   | F   | T     |

### EXAMPLE 6

What is the value of the variable x after the statement

if 2+2=4 then x := x+1

if x = 0 before this statement is encountered? (The symbol := stands for assignment. The statement x := x + 1 means the assignment of the value of x + 1 to x.)

**Solution:**

Since 2 + 2 = 4 is true, the assignment statement x := x + 1 is executed. Hence, x has the value 0+1=1 after this statement is encountered.

### EXAMPLE 7

**Logic 命题逻辑**

Find the converse and the contrapositive of the implication

"If today is Thursday, then I have a test today."

**Solution:**

The converse is

"If I have a test today, then today is Thursday."

And the contrapositive of this implication is

"If I do not have a test today, then today is not Thursday."

### DEFINITION 6（p当且仅当q，双条件、等价）

Let p and q be propositions. The biconditional p ↔ q is the proposition that is true when p and q have the same truth values and is false otherwise.

The truth table for p ↔ q is shown in Table 6.

p当且仅当q（双条件，等价）
