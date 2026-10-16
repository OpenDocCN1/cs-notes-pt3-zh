
## How many operations?

- If \(A = \{a, b\}\), how many binary operations can be defined on \(A\)?
  - Every binary operation \(*\) on \(A\) can be described by a table.
- There are \(2 \cdot 2 \cdot 2 \cdot 2 = 2^4\) or 16 ways to complete the table.

![](img/c25dfd82fc242c2db53bc942dcad6885_852_0.png)

## Properties of Binary Operations

- For all elements \(a\), \(b\), and \(c\) in \(A\):
- Commutative(交换律)
  - \(a * b = b * a\)
- Associative(结合律)
  - \(a * (b * c) = (a * b) * c\)
- Idempotent(等幂律)
  - \(a * a = a\)

## Commutative - 交换律

- A binary operation on a set \(A\) is said to be commutative if \(a * b = b * a\) for all elements \(a\) and \(b\) in \(A\).
- Example:
  - The binary operation of addition on \(\mathbb{Z}\) is commutative.
  - The binary operation of subtraction on \(\mathbb{Z}\) is not commutative, since \(2 - 3 \neq 3 - 2\).

## Commutative

- A binary operation that is described by a table is commutative if and only if the entries in the table are symmetric with respect to the main diagonal.

## Example 12

- Which of the following binary operations on \(A = \{a, b, c, d\}\) are commutative?

(a)

| * | a | b | c | d |
|---|---|---|---|---|
| a | a | c | b | d |
| b | b | c | b | a |
| c | c | d | b | c |
| d | a | a | b | b |

(b)

| * | a | b | c | d |
|---|---|---|---|---|
| a | a | c | b | d |
| b | c | d | b | a |
| c | b | b | a | c |
| d | d | a | c | d |

## Associative - 结合律

- A binary operation \(*\) on a set \(A\) is said to be associative if \(a * (b * c) = (a * b) * c\) for all elements \(a\), \(b\), and \(c\) in \(A\).
- Example:
  - The binary operation of addition on \(\mathbb{Z}\) is associative.
  - The binary operation of subtraction on \(\mathbb{Z}\) is not associative, since \(2 - (3 - 5) \neq (2 - 3) - 5\).

## Example 15

- Let \(L\) be a lattice. The binary operation defined by \(a * b = a \wedge b\) is commutative and associative.
- It also satisfies the idempotent property \(a \wedge a = a\).

## Example 16

- Let \(*\) be a binary operation on a set \(A\), and suppose that \(*\) satisfies the following properties for any \(a\), \(b\), and \(c\) in \(A\):
  - \(a = a * a\) (Idempotent property)
  - \(a * b = b * a\) (Commutative property)
  - \(a * (b * c) = (a * b) * c\) (Associative property)
- Define a relation \(\leq\) on \(A\) by \(a \leq b\) if and only if \(a = a * b\).
- Show that \((A, \leq)\) is a poset, and for all \(a, b\) in \(A\), \(\operatorname{GLB}(a, b) = a * b\).

## Example 16: Solution

- We must show that
  - \(\leq\) is reflexive, antisymmetric and transitive.
  - \(a * b = a \wedge b\) for all \(a\) and \(b\) in \(A\).

### \(\leq\) is reflexive

- \(a \leq b\) if and only if \(a = a * b\).
- Since \(a = a * a\), \(a \leq a\) for all \(a\) in \(A\), and \(\leq\) is reflexive.

### \(\leq\) is antisymmetric

- \(a \leq b\) if and only if \(a = a * b\).
- Now suppose that \(a \leq b\) and \(b \leq a\).
- Then, by definition and property 2, \(a = a * b = b * a = b\), so \(a = b\).
- Thus \(\leq\) is antisymmetric.

### \(\leq\) is transitive

- \(a \leq b\) if and only if \(a = a * b\).
- If \(a \leq b\) and \(b \leq c\), then \(a = a * b = a * (b * c) = (a * b) * c = a * c\).
- Therefore \(a \leq c\), and \(\leq\) is transitive.

### \(a * b = a \wedge b\), for all \(a\) and \(b\) in \(A\)

- \(a \leq b\) if and only if \(a = a * b\).
- We have \(a * b = a * (b * b) = (a * b) * b\), so \(a * b \leq b\).
- In a similar way \(a * b \leq a\).
- So \(a * b\) is a lower bound for \(a\) and \(b\).
- Now, if \(c \leq a\) and \(c \leq b\), then \(c = c * a\) and \(c = c * b\) by definition.
- Thus \(c = (c * a) * b = c * (a * b)\).
- So \(c \leq a * b\).
- This shows that \(a * b\) is the greatest lower bound of \(a\) and \(b\).

## Homework

- 20 @ 323
- 24, 28 @ 324
