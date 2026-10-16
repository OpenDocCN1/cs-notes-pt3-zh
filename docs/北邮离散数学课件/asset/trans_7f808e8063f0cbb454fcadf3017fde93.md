

## 否定量化表达式

考虑 ∀x J(x)

“你班上的每个学生都上过 Java 课程。”
这里 \(J(x)\) 表示“x 上过 Java 课程”，
域是你的班级的学生。

否定原命题得到“并非你班上的每个学生都上过 Java。”
这意味着“你班上有某个学生没有上过 Java。”

符号上 ¬∀x J(x) 和 ∃x ¬J(x) 是等价的

## 否定量化表达式（续）

- 现在考虑 ∃ x J(x)
- “这个班上有某个学生上过 Java 课程。”
- 其中 J(x) 表示“x 上过 Java 课程。”

- 否定原命题得到“并非这个班上有某个学生上过 Java。”这意味着“这个班上的每个学生都没有上过 Java”
- 符号上 ¬∃ x J(x) 和 ∀ x ¬J(x) 是等价的

## 量词的德摩根律

否定量词的规则是：

| TABLE 2 De Morgan's Laws for Quantifiers. |
| Negation | Equivalent Statement | When Is Negation True? | When False? |
| ¬∃x P(x) | ∀x ¬P(x) | For every x, P(x) is false. | There is an x for which P(x) is true. |
| ¬∀x P(x) | ∃x ¬P(x) | There is an x for which P(x) is false. | P(x) is true for every x. |

表中推理表明：

¬∀x P(x) ≡ ∃x ¬P(x)

¬∃x P(x) ≡ ∀x ¬P(x)

这些很重要。你会用到这些。

## 从英语到逻辑的翻译

### Examples:

- 1. “Some student in this class has visited Mexico.”

**Solution:** Let $M(x)$ denote “$x$ has visited Mexico” and $S(x)$ denote “$x$ is a student in this class,” and $U$ be all people.

```
$\exists x\,(S(x)\land M(x))$
```

- 2. “Every student in this class has visited Canada or Mexico.”

**Solution:** Add $C(x)$ denoting “$x$ has visited Canada.”

```
$\forall x\,(S(x)\to(M(x)\lor C(x)))$
```

## 系统规范示例

- 谓词逻辑用于指定系统必须满足的属性。
- 例如，翻译成谓词逻辑：
  - “大于一兆字节的每封邮件消息都将被压缩。”
  - “如果用户处于活跃状态，至少有一条网络链路可用。”
- 为变量确定谓词和域（此处隐含）：
  - 设 L(m, y) 表示“邮件消息 m 大于 y 兆字节。”
  - 设 C(m) 表示“邮件消息 m 将被压缩。”
  - 设 A(u) 表示“用户 u 处于活跃状态。”
  - 设 S(n, x) 表示“网络链路 n 的状态为 x。”
- 现在我们有：∀m(L(m, 1) → C(m))
  ∃u A(u) → ∃n S(n, available)

## 刘易斯·卡罗尔示例

![](img/c25dfd82fc242c2db53bc942dcad6885_320_0.png)

Charles Lutwidge Dodgson
(AKA Lewis Caroll)
(1832-1898)

前两个被称为 *前提*，第三个被称为 *结论*。

- 1. “All lions are fierce.”
- 2. “Some lions do not drink coffee.”
- 3. “Some fierce creatures do not drink coffee.”

下面是一种将这些陈述翻译成谓词逻辑的方法。
设 P(x)、Q(x) 和 R(x) 为命题函数“x 是狮子”、“x 凶猛”以及“x 喝咖啡”。

- 1. ∀x (P(x) → Q(x))
- 2. ∃x (P(x) ∧ ¬R(x))
- 3. ∃x (Q(x) ∧ ¬R(x))

稍后我们将看到如何证明结论由前提得出。

## 一些谓词演算定义（可选）

- 涉及谓词和量词的断言如果对
  - 所有域
  - 断言中谓词可被替换的每个命题函数
  都为真，则称为 *valid*。

**Example:** ∀x ¬S(x) ↔ ¬∃x S(x)

- 涉及谓词的断言如果对
  - 某些域
  - 可被替换为断言中谓词的某些命题函数
  为真，则称为 *satisfiable*。

否则它是 *unsatisfiable*。

**Example:** ∀x (F(x) ↔ T(x))      not valid but satisfiable

**Example:** ∀x (F(x) ∧ ¬F(x))      unsatisfiable

## 更多谓词演算定义（可选）

量词的作用域是变量被该量词绑定的断言的一部分。

**Example:** ∀x(F(x) ∨ S(x))      x has wide scope

**Example:** ∀x(F(x)) ∨ ∀y(S(y))      x has narrow scope

