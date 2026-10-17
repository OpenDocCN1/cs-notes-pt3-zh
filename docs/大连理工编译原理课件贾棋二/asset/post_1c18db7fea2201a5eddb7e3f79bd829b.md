
## 4.2 S属性定义的自下而上计算

### 台式计算器的语法制导定义改成栈操作代码

| 产生式 | 代码段 |
| --- | --- |
| $L \to E\,n$ | `print(val[top-1])` |
| $E \to E_1 + T$ | `E.val := E_1.val + T.val` |
| $E \to T$ | `E.val := T.val` |
| $T \to T_1 * F$ | `T.val := T_1.val * F.val` |
| $T \to F$ | `T.val := F.val` |
| $F \to (E)$ | `F.val := E.val` |
| $F \to \text{digit}$ | `F.val := digit.lexval` |

| ... | ... |
| --- | --- |
| Z | Z.z |
| Y | Y.y |
| X | X.x |
| ... | ... |

![](img/4571939c0321e2c5dec9f0dd5554d04d_144_0.png)

| 产生式 | 代码段 |
| --- | --- |
| `L → E n` | `print(val[top-1])` |
| `E → E₁ + T` | `val[top-2] := val[top-2] + val[top]` |
| `E → T` | `E.val := T.val` |
| `T → T₁ * F` | `T.val := T₁.val * F.val` |
| `T → F` | `T.val := F.val` |
| `F → (E)` | `F.val := E.val` |
| `F → digit` | `F.val := digit.lexval` |

![](img/4571939c0321e2c5dec9f0dd5554d04d_145_0.png)

| 产生式 | 代码段 |
| --- | --- |
| $L \to E\,n$ | `print(val[top-1])` |
| $E \to E_1 + T$ | `val[top-2] := val[top-2] + val[top]` |
| $E \to T$ |  |
| $T \to T_1 * F$ | `T.val := T_1.val * F.val` |
| $T \to F$ | `T.val := F.val` |
| $F \to (E)$ | `F.val := E.val` |
| $F \to \text{digit}$ | `F.val := digit.lexval` |

![](img/4571939c0321e2c5dec9f0dd5554d04d_148_0.png)

| 产生式 | 代码段 |
| --- | --- |
| $L \to E\,n$ | `print(val[top-1])` |
| $E \to E_1 + T$ | `val[top-2] := val[top-2] + val[top]` |
| $E \to T$ |  |
| $T \to T_1 * F$ | `val[top-2] := val[top-2] × val[top]` |
| $T \to F$ |  |
| $F \to (E)$ | `val[top-2] := val[top-1]` |
| $F \to \text{digit}$ | `F.val := digit.lexval` |

| 产生式 | 代码段 |
| --- | --- |
| $L \to E\,n$ | `print(val[top-1])` |
| $E \to E_1 + T$ | `val[top-2] := val[top-2] + val[top]` |
| $E \to T$ |  |
| $T \to T_1 * F$ | `val[top-2] := val[top-2] × val[top]` |
| $T \to F$ |  |
| $F \to (E)$ | `val[top-2] := val[top-1]` |
| $F \to \text{digit}$ |  |

### 翻译输入 `3*5+4n` 所做的移动

| 输入 | state | val | 使用的产生式 |
| --- | --- | --- | --- |
| `3*5+4n` | - | - |  |
| `*5+4n` | `3` | `3` |  |
| `*5+4n` | `F` | `3` | `F → digit` |
| `*5+4n` | `T` | `3` | `T → F` |
| `5+4n` | `T*` | `3*` |  |
| `+4n` | `T* 5` | `3*5` |  |
| `+4n` | `T* F` | `3*5` | `F → digit` |
| `+4n` | `T` | `15` | `T → T*F` |
| `+4n` | `E` | `15` | `E → T` |
| `4n` | `E+` | `15+` |  |
| `n` | `E+4` | `15+4` |  |
| `n` | `E+F` | `15+4` | `F → digit` |
| `n` | `E+T` | `15+4` | `T → F` |
| `n` | `E` | `19` | `E → E+T` |
|  | `En` | `19 -` |  |
|  | `L` | `19` | `L → En` |

### 总结：

采用自底向上分析，例如LR分析，首先给出S-属性定义，然后，把S-属性定义变成可执行的代码段，这就构成了翻译程序。像一座建筑，语法分析是构架，归约处有一个“挂钩”，语义分析和翻译的代码段（语义子程序）就挂在这个钩子上。这样，随着语法分析的进行，归约前调用相应的语义子程序，完成翻译的任务。

## 4.3 L属性定义的自上而下计算

边分析边翻译的方式能否用于继承属性？

- 属性的计算次序一定受分析方法所限定的分析树结点建立次序的限制。
- 分析树的结点是自左向右生成。
- 如果属性信息是自左向右流动，那么就有可能在分析的同时完成属性计算。

### 4.3.1 L属性定义

如果每个产生式 $A \to X_1 X_2 \ldots X_n$ 的每条语义规则计算的属性是 $A$ 的综合属性；或者是 $X_j$ 的继承属性，$1 \leq j \leq n$，但它仅依赖：

- 该产生式中 $X_j$ 左边符号 $X_1, X_2, \ldots, X_{j-1}$ 的属性；
- $A$ 的继承属性。

S属性定义属于L属性定义。

### 非L-属性的语法制导定义

| 产生式 | 语义规则 |
| --- | --- |
| $A \to L M$ | `L.i := l(A.i)`<br>`M.i := m(L.s)` |
| $A \to Q R$ | `R.i := r(A.i)`<br>`Q.i := q(R.s)`<br>`A.s := f(Q.s)` |

### L属性定义的例子：变量类型声明的语法制导定义

| 产生式 | 语义规则 |
| --- | --- |
| $D \to T\,L$ | `L.in := T.type` |
| $T \to \text{int}$ | `T.type := integer` |
| $T \to \text{real}$ | `T.type := real` |
| $L \to L_1, \text{id}$ | `L_1.in := L.in; addtype(id.entry, L.in)` |
| $L \to \text{id}$ | `addtype(id.entry, L.in)` |

> 语义规则的执行时刻很重要

### 4.3.2 翻译方案

翻译方案：给出了使用语义规则进行计算的次序，这样就可把某些实现细节表示出来。

在翻译方案中，和文法符号相关**语义动作**，用花括号{}括起来，插入到产生式右部的合适位置上。

这是一种动作和分析交错的方法，以表示动作的执行时机。
