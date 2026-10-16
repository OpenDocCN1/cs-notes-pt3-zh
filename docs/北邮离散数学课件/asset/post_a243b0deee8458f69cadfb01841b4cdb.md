
- (d) One possible distributive property is \(x □ (y ▽ z) = (x □ y) ▽ (x □ z)\).
  - All possible cases must be checked.
  - We can show it in a table.

| x | y | z | y ▽ z | x □ (y ▽ z) | x □ y | x □ z | (x □ y) ▽ (x □ z) |
|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |

## Binary Operations

- Definition
- Properties of Binary Operations

### Binary operations(二元运算)

- A binary operation on a set \(A\) is an **everywhere** defined function \(f: A \times A \rightarrow A\).
- A binary operation must satisfy:
  - \(f\) assigns an element \(f(a,b)\) of \(A\) to each ordered pair \((a,b)\) in \(A \times A\).
  - Since a binary operation is a function, only one element of \(A\) is assigned to each ordered pair.

### Note

- It's customary to denote binary operations by a symbol such as \(*\), instead of \(f\), and to denote the element assigned to \((a,b)\) by \(a*b\) [instead of \(*(a,b)\)].
- \(A\) is _closed_ (封闭的) _under the operation_ \(*\), if \(a\) and \(b\) are elements in \(A\), \(a*b \in A\).

### Example 1,2

- Let \(A = \mathbb{Z}\). Define \(a * b\) as \(a + b\).
  - \(*\) is a binary operation on \(\mathbb{Z}\).
- Let \(A = \mathbb{R}\). Define \(a * b\) as \(a / b\).
  - \(*\) is not a binary operation, since it is not defined for every ordered pair of elements of \(A\).
  - For example, \(3 * 0\) is not defined, since we cannot divide by zero.

### Example 3

- Let \(A = \mathbb{Z}^+\). Define \(a*b\) as \(a-b\).
  - \(*\) is not a binary operation, since it does not assign an element of \(A\) to every ordered pair of elements of \(A\); for example, \(2*5 \notin A\).

### Example 4

- Let \(A = \mathbb{Z}\). Define \(a*b\) as a number less than both \(a\) and \(b\).
  - \(*\) is not a binary operation, since it does not assign a _unique_ element of \(A\) to each ordered pair of elements of \(A\); for example, \(8*6\) could be 5, 4, 3, 1, and so on.
  - In this case, \(*\) would be a relation from \(A \times A\) to \(A\), but not a function.

### Example 5,6

- Let \(A = \mathbb{Z}\). Define \(a*b\) as \(\max\{a, b\}\).
  - \(*\) is a binary operation; for example, \(2*4 = 4\), \(-3*(-5) = -3\).
- Let \(A = P(S)\), for some set \(S\). If \(V\) and \(W\) are subsets of \(S\), define \(V*W\) as \(V \cup W\).
  - \(*\) is a binary operation on \(A\).
  - If we define \(V *' W\) as \(V \cap W\), then \(*'\) is another binary operation on \(A\).
    - Note: It's possible to define many binary operations on the same set.

### Example 7,8

- Let \(M\) be the set of all \(n \times n\) Boolean matrices for a fixed \(n\). Define \(A * B\) as \(A \lor B\).
  - \(*\) is a binary operation.
  - This is also true of \(A \land B\).
- Let \(L\) be a lattice. Define \(a * b\) as \(a \lor b\).
  - \(*\) is a binary operation on \(L\).
  - This is also true of \(a \land b\).

### Tables – 运算表

If \(A = \{a_1, a_2, \dots, a_n\}\) is a _finite_ set, we can define a binary operation on \(A\) by means of a table:

| * | \(a_1\) | \(a_2\) | \(\cdots\) | \(a_j\) | \(\cdots\) | \(a_n\) |
|---|---|---|---|---|---|---|
| \(a_1\) |  |  |  |  |  |  |
| \(a_2\) |  |  |  |  |  |  |
| \(\vdots\) |  |  |  |  |  |  |
| \(a_i\) |  |  |  | \(a_i * a_j\) |  |  |
| \(\vdots\) |  |  |  |  |  |  |
| \(a_n\) |  |  |  |  |  |  |

Figure 9.1

### Example 9

- Let \(A = \{0, 1\}\).
- Define binary operations \(\vee\) and \(\wedge\) by the following tables:

| \(\vee\) | 0 | 1 |
|---|---|---|
| 0 | 0 | 1 |
| 1 | 1 | 1 |

| \(\wedge\) | 0 | 1 |
|---|---|---|
| 0 | 0 | 0 |
| 1 | 0 | 1 |
