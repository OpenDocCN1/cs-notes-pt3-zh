

## 逻辑编程（可选）

- Prolog（源自 *Programming in Logic*）是一种在 1970 年代由人工智能（AI）研究人员开发的编程语言。
- Prolog 程序包括 *Prolog facts* 和 *Prolog rules*。
- 以下是一个 Prolog 事实集的示例：

```
instructor(chan, math273).
instructor(patel, ee2222).
instructor(grossman, cs301).
enrolled(kevin, math273).
enrolled(juan, ee2222).
enrolled(juana, cs301).
enrolled(kiko, math273).
enrolled(kiko, cs301).
```

- 在这里，谓词 *instructor(p,c)* 和 *enrolled(s,c)* 表示教授 *p* 是课程 *c* 的授课教师，以及学生 *s* 注册了课程 *c*。

## Logic Programming (cont)

- 在 Prolog 中，以大写字母开头的名称是变量。
- 如果我们有一个谓词 *teaches(p,s)* 表示“教授 p 教授学生 s”，我们可以写出规则：
  *teaches(P,S) :- instructor(P,C), enrolled(S,C).* 
- 该 Prolog 规则可以被视为等价于逻辑中的以下陈述（使用我们对逻辑陈述的约定）。
  ∀p ∀c ∀s(I(p,c) ∧ E(s,c)) → T(p,s))

## Logic Programming (cont)

- Prolog 程序被加载到 *Prolog interpreter* 中。解释器接收 *queries* 并使用 Prolog 程序返回答案。
- 例如，使用我们的程序，可以给出以下查询：
  ?enrolled(kevin,math273).
- Prolog 产生响应：
  yes
- 请注意，? 是 Prolog 解释器给出的提示，表示它已准备好接收查询。

## Logic Programming (cont)

查询：
?enrolled(X,math273).

产生的响应：
X = kevin;
X = kiko;
no

查询：
?teaches(X,juana).

产生的响应：
X = patel;
X = grossman;
no

Prolog 解释器尝试为 X 找到一个实例化。它这样做并返回 X = kevin。然后用户键入 ; 表示请求另一个答案。当 Prolog 无法找到另一个答案时，它返回 no。

## Logic Programming (cont)

- 查询：
  ?teaches(chan,X).
  产生的响应：
  X = kevin;
  X = kiko;
  no

- 有许多非常好的 Prolog 文本可用。*Learn Prolog Now!* 就是其中之一，其免费在线版本位于 http://www.learnprolognow.org/

- Prolog 和整个逻辑编程领域还有更多内容。

## Predicate Logic（§ 1.4）

谓词逻辑

- 前两节介绍的命题与命题演算是命题逻辑的内容，其基本组成单位是原子命题。一般地，原子命题作为具有真假意义的句子至少由主语和谓语两部分组成。
- 例如，电子商务是计算机技术的一个应用，这里“电子商务”是主语，而“是……”是谓语。当主语改变为“电子政务”时就得到新的原子命题：电子政务是计算机技术的一个应用。

由此可知，主语是独立存在的个体/值/Value，而谓语用来描述该个体的性质或个体间的关系，这里我们称其为谓词/Predicate。用P表示谓词“是......”。则P（电子商务）或P（电子政务）分别等值于前述两个命题的表达。将个体用变量（称为个体变量）x推广，则P（x）表示：x是计算机技术的一个新的应用。这时该语句就不是一个命题，而是一个命题函数。

## DEFINITION 1.

- 定义 一个谓词 $P$ 连同相关的 $n$（$n\ge 0$）个个体变量组成的表达式称为 $n$ 元谓词（$n$-predicate），记 $P(x_1, x_2, \ldots, x_n)$，其中 $n$ 是该表达式中不同个体变量的数目。$n$ 元谓词也称简单命题函数。
- 复合命题函数 简单命题函数和复合命题函数，统称为命题函数（proposition function）。

## EXAMPLE 2

- Let Q(x, y) denote the statement "x = y + 3." What are the truth values of the propositions Q(1, 2) and Q(3, 0)?

Q(1, 2) = . F.

Q(3, 0) = . T.

## EXAMPLE 3

- R(x,y,z): x+y=z
- What are the truth values of the propositions R(1, 2, 3) and R(0, 0, 1)?

R(1,2,3)=. T.
R(0,0,1)=. F.

- 当n>1时，通常P给出了x_i (i=1, 2, ..., n)之间的关系。
- 例如，P(x, y, z)表示x位于y与z之间，是一个三元谓词。与x, y, z分别用操场、教学楼、宿舍代入时得到命题：操场位于教学楼与宿舍之间，其命值真值为T。再如将杭州、南京、北京代入，则得到：杭州位于南京和北京之间，真值为F。
- 与n=0时（即0元谓词），命题函数就对应一个命题。

- 为了进一步讨论命题函数P(x)的真值情况，首先需要指定个体变量x可选择的范围，即 个体域（universe of discourse, or domain）。每一个个体变量x都有自己的个体域。如果没有特别指定的个体域，则缺省为一个全个体域（total universe of discourse）即任意个体均可以作为常量对x代入。

在指定个体变量x的个体域后，该个体域中的每个个体a代入到P(x)中的所有x，就对应一个可以判定真假意义的命题P(a)。不同的个体代入后所对应的命题真值可能不同，也可能相同。

例如,P(x)表示为

x²−1=(x−1)(x+1)      x指定的个体域为全体整数,

