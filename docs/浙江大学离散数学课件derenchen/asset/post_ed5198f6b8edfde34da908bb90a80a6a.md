

| p | q | p ↔ q |
|---|---|---|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | T |

## EXAMPLE 8

## Logic 命题逻辑

How can the following English sentence be translated into a logical expression?

"You can access the Internet from campus only if you are a computer science major or you are not a freshman,"

Solution:
a → (c ∨ ¬ f ).

## EXAMPLE 9

## Logic 命题逻辑

## How can the following English sentence be translated into a logical expression?

"You cannot ride the roller coaster if you are under 4 feet tall unless you are older than 16 years old."

Solution:
(r∧¬s) → ¬q.

说离散数学是枯燥无味的或毫无价值的，那是不对的。

**P：** 离散数学是有味道的；

**Q：** 离散数学是有价值的；

## EXAMPLE 11

Web Page Searching. Most Web search engines support Boolean searching techniques, which usually can help find Web pages about particular subjects. For instance, using Boolean searching to find Web pages about universities in New Mexico, we can look for pages matching NEW AND MEXICO AND UNIVERSITIES. The results of this search will include those pages that contain the three words NEW, MEXICO, and UNIVERSITIES.

## DEFINITION 7.

## Logic 命题逻辑

A bit string is a sequence of zero or more bits.The length of this string is the number of bits in the string.

## TABLE 7

## Tables for the Bit Operators OR, AND, and XOR.

| x | y | x ∨ y | x ∧ y | x ⊕ y |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 | 0 |

## EXAMPLE 12

Find the bitwise OR, bitwise AND, and bitwise XOR of the bit strings 01 1011 0110 and 11 0001 1101. (Here, and throughout this book, bit strings will be split into blocks of four bits to make them easier to read.)

**Solution:**

The bitwise OR, bitwise AND, and bitwise XOR of these strings are obtained by taking the OR, AND, and XOR of the corresponding bits, respectively. This gives us

```
01 1011 0110
11 0001 1101
11 1011 1111    bitwise OR
01 0001 0100    bitwise AND
10 1010 1011    bitwise XOR
```

## Logic 命题逻辑

P、Q、R...... 称为原子命题（Atomic Proposition）。
原子命题或加上逻辑联结词组成的表达式成为复合命题（Compositional Proposition）。
从命题常量 到 命题变量(Propositional Variable)

+ 命题公式：
+ 1、原子命题是命题公式；
+ 2、设P是命题公式，则￢P也是命题公式；
+ 3、设P、Q是命题公式，则（P∧Q）、（P∨Q）、（P→Q）、（P↔Q）也是命题公式；
+ 4、有限次地使用1、2、3所得到的也是命题公式。

## Proposition Formulas, Well-Formed Formulas(wff)

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

+ （1）设P是永真命题公式，则P的否定公式是永假命题公式；
+ （2）设P是永假命题公式，则P的否定公式是永真命题公式；
+ （3）设P、Q是永真命题公式，则P（P ∧ Q）、（P ∨ Q）、（P → Q）、（P ↔ Q）也是永真命题公式

## 小结

+ 1、命题的概念：定义、逻辑值、符号化表示
+ 2、从简单命题到复合命题：
   逻辑联接词：运算方法、运算优先级
+ 3、从命题常量到命题变量，
   从复合命题到命题公式：
   命题公式的真值描述：真值表
+ 4、命题公式的分类：
   永真公式、永假公式、可满足公式、一般公式

## 进一步的思考：

+ 1、从二值逻辑到多值逻辑
+ 2、从确定值到模糊值
   模糊逻辑（Fuzzy Logic）

## 练习题：

2、7、21（d）、25（d）

## 1.1.2 命题演算

## Propositional Equivalences

## 1、命题(Proposition)

## 2、从简单命题(atomic proposition)到复合命题(compositional proposition)

## 3、从命题常量(propositional constant)到命题变量(propositional variable)

## 4、从复合命题(compositional proposition)到命题公式(propositional formulas)

复合命题(compositional proposition)

命题变量(propositional variable)

命题公式(propositional formulas)

## 永真命题公式（Tautology）

公式中的命题变量无论怎样代入，公式对应的真值恒为T。

## 永假命题公式（Contradiction）

公式中的命题变量无论怎样代入，公式对应的真值恒为F。

## 可满足命题公式（Satisfaction）

公式中的命题变量无论怎样代入，公式对应的真值总有一种情况为T。

## 一般命题公式（Contingency）

既不是永真公式也不是永假公式。

## EXAMPLE 1

We can construct examples of tautologies and contradictions using just one proposition. Consider the truth tables of p ∨ ¬ p and p ∧ ¬ p, shown in Table 1.

Since p ∨ ¬ p is always true, it is a tautology. Since p ∧ ¬ p is always false, it is a contradiction.

