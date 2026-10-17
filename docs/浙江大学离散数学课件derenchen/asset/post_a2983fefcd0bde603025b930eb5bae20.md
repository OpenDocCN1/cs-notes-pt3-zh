

## EXAMPLE 6

What is the value of the variable x after the statement
if 2+2=4 then x := x+1
if x = 0 before this statement is encountered? (The symbol := stands for assignment. The statement x := x + 1 means the assignment of the value of x + 1 to x.)

**Solution:**

Since 2 + 2 = 4 is true, the assignment statement x := x + 1 is executed. Hence, x has the value 0+1=1 after this statement is encountered.

## implication p→q

The converse of p→q : q→p

The contrapositive of p→q :¬q→ ¬p

## EXAMPLE 7

## Logic 命题逻辑

Find the converse and the contrapositive of the implication
"If today is Thursday, then I have a test today."

Solution:
The converse is
"If I have a test today, then today is Thursday."
And the contrapositive of this implication is
"If I do not have a test today, then today is not Thursday."

## DEFINITION 6.

Let p and q be propositions, The biconditional p ↔ q is the proposition that is true when p and q have the same truth values and is false otherwise.

The truth table for p ↔q is shown in Table 6.

P当且仅当q 双条件，等价

## TABLE 6

## The Truth Table for the Biconditional p ←→ q.

| p | q | p ←→ q |
|---|---|---|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | T |

## EXAMPLE 8

How can the following English sentence be translated into a logical expression?

> "You can access the Internet from campus only if you are a computer science major or you are not a freshman,"

**Solution:**  
\(a \to (c \lor \lnot f)\).

## EXAMPLE 9

How can the following English sentence be translated into
a logical expression?

"You cannot ride the roller coaster if you are under 4 feet
tall unless you are older than 16 years old."

Solution:
(r∧¬s)→¬q.

## EXAMPLE 10

## Logic 命题逻辑

说离散数学是枯燥无味的或毫无价值的，那是不对的。

P: 离散数学是有味道的；

Q: 离散数学是有价值的；

## APPLICATION 2

## Logic
命题逻辑

A bit string is a sequence of zero or more bits.

The length of this string is the number of bits in the string.

+   The bitwise of two strings of the same length:
+   
+   - Bitwise OR
+   - Bitwise AND
+   - Bitwise XOR

## 命题公式的运算规则：

## 逻辑联接词的优先级：

¬、∧、∨、→、↔

## 命题公式的表达式的运算规律：

同代数表达式

## 命题公式的运算方法：

所有公式中的命题变量用指定命题（真值）代入（或指派），得到一个公式对应的真值。

## 性质1：

如果一个命题公式有N个互异的命题变量，则命题公式对应的真值有2的N次幂种可能分布。

## 永真命题公式（Tautology）

公式中的命题变量无论怎样代入，公式对应的真值恒为T。

## 永假命题公式（Contradiction）

公式中的命题变量无论怎样代入，公式对应的真值恒为F。

## 可满足命题公式（Satisfaction）

公式中的命题变量无论怎样代入，公式对应的真值总有一种情况为T。

## 一般命题公式（Contingency）

既不是永真公式也不是永假公式。

## 性质2：

+   (1) 设P是永真命题公式，则P的否定公式是永假命题公式；
+   (2) 设P是永假命题公式，则P的否定公式是永真命题公式；
+   (3) 设P、Q是永真命题公式，则（P ∧ Q）、（P ∨ Q）、（P → Q）、（P ↔ Q）也是永真命题公式

## 小结

+   1、命题的概念：定义、逻辑值、符号化表示  
+   2、从简单命题到复合命题：  
+      逻辑联接词：运算方法、运算优先级  
+   3、从命题常量到命题变量，  
+      从复合命题到命题公式：  
+      命题公式的真值描述：真值表  
+   4、命题公式的分类：  
+      永真公式、永假公式、可满足公式、一般公式

## 进一步的思考：

+   1、从二值逻辑到多值逻辑
+   2、从确定值到模糊值
+   　　模糊逻辑（Fuzzy Logic）

## 练习题：

1、2、7、9、25（d）、30（b）

## 基础部分：

+   逻辑(Logic)
+   集合(Sets)
+   算法(Algorithms)
+   数论(Number Theory)

## 1.1.1 命题逻辑

Proposition Logic

逻辑学：

研究推理的一门学科

数理逻辑：

用数学方法研究推理的一门数学学科

-------- 一套符号体系 + 一组规则

## 数理逻辑的内容：

## 古典数理逻辑：

命题逻辑、谓词逻辑

## 现代数理逻辑：

公理化集合论、递归论、模型论、证明论

## 命题逻辑

## Proposition Logic

## Proposition:

一个有确定真或假意义的语句。

## All the following statements are propositions.

+   1. Washington, D.C., is the capital of the United States of America.
+   2. Toronto is the capital of Canada.
+   3. 1+1=2.
+   4. 2+2=3.

> > Propositions 1 and 3 are true, whereas 2 and 4 are false.

## EXAMPLE 2

## Consider the following sentences.

+   1. What time is it?

+   2. Read this carefully.

+   3. x+1 = 2.

+   4. x+y = z.

Sentences 1 and 2 are not propositions because they are not statements. Sentences 3 and 4 are not propositions because they are neither tree nor false, since the variables in these sentences have not been assigned values. Various ways to form propositions from sentences of this type will be discussed in Section 1.3.

