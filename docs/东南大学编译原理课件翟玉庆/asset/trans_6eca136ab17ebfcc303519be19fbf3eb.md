

## 第4章 语法分析

### 第2节 自顶向下分析

**9. 非递归预测分析**

**1) 预测分析中的关键问题**

- 确定要对非终结符应用的产生式。

**2) 分析器的基本思想**

- 表驱动并使用栈。

**3) 非递归预测分析器的模型**

- 输入: a+b......$
- 栈: S $
- 预测分析程序
- 分析表 M
- 输出

![](img/353f619caa6c5715591f2105bdfa2865_221_0.png)

**4) 预测分析程序**

X: 栈顶的符号；a: 当前输入符号。

- 如果 X = a = $，分析器停止并宣布分析成功完成；
- 如果 X = a ≠ $，分析器将 X 弹出栈并将输入指针推进到下一个输入符号；
- 如果 X 是非终结符，程序查阅分析表 M 的条目 M[X,a]。该条目将是文法的 X-产生式或错误条目。

例如. 考虑以下文法，并分析字符串 `id+id*id$`：

1. E → TE'
2. E' → +TE'
3. E' → ε
4. T → FT'
5. T' → *FT'
6. T' → ε
7. F → id
8. F → (E)

**分析表 M**

|  | id | + | * | ( | ) | $ |
|---|---|---|---|---|---|---|
| E | E → TE' |  |  | E → TE' |  |  |
| E' |  | E' → +TE' |  |  | E' → ε | E' → ε |
| T | T → FT' |  |  | T → FT' |  |  |
| T' |  | T' → ε | T' → \*FT' |  | T' → ε | T' → ε |
| F | F → id |  |  | F → (E) |  |  |

**10. 预测分析器的构造**

**1) FIRST & FOLLOW**

**FIRST:**

- 如果 α 是文法符号的任意串，则令 FIRST(α) 为从 α 派生的串所开头的终结符集合。
- 如果 α ⟹* ε，则 ε 也在 FIRST(α) 中。
- 即：α ∈ V*，FIRST(α) = { a | α ⟹* a..., a ∈ V_T }

**FOLLOW:**

- 对于非终结符 A，FOLLOW(A) 是在某个句型中能紧跟在 A 右侧出现的终结符 a 的集合。
- 即：FOLLOW(A) = { a | S ⟹* ... Aa..., a ∈ V_T }
- 如果 S ⟹* ... A，则 $ ∈ FOLLOW(A)。

**2) 计算 FIRST(α)**

(1) 计算所有文法符号 X 的 FIRST(X)：

- 如果 X 是终结符，则 FIRST(X) 为 {X}。
- 如果 X → ε 是产生式，则将 ε 添加到 FIRST(X)。
- 如果 X 是非终结符，且 X → Y₁Y₂...Yₖ，Yⱼ ∈ (V_N ∪ V_T)，1 ≤ j ≤ k，则：

```pseudocode
{
  j = 1;
  FIRST(X) = {}; // initialize
  while (j < k and ε ∈ FIRST(Y_j)) {
    FIRST(X) = FIRST(X) ∪ (FIRST(Y_j) - {ε});
    j = j + 1;
  }
  if (j == k and ε ∈ FIRST(Y_k))
    FIRST(X) = FIRST(X) ∪ {ε};
}
```

(2) 计算任意串 α = X₁X₂...Xₙ 的 FIRST，Xᵢ ∈ (V_N ∪ V_T)，1 ≤ i ≤ n：

```pseudocode
{
  i = 1;
  FIRST(α) = {}; // initialize
  while (i < n and ε ∈ FIRST(X_i)) {
    FIRST(α) = FIRST(α) ∪ (FIRST(X_i) - {ε});
    i = i + 1;
  }
  if (i == n and ε ∈ FIRST(X_n))
    FIRST(α) = FIRST(α) ∪ {ε};
}
```

**3) 计算 FOLLOW(A)**

1. 将 $ 放入 FOLLOW(S)，其中 S 是开始符号且 $ 是输入右端标记。
2. 如果文法 G 中存在产生式 A → αBβ，则将 (FIRST(β) - {ε}) 添加到 FOLLOW(B)。
3. 如果存在产生式 A → αB，或 A → αBβ 且 FIRST(β) 包含 ε，则将 FOLLOW(A) 添加到 FOLLOW(B)。

例如. 考虑以下文法，构造每个非终结符的 FIRST & FOLLOW：

1. E → TE'
2. E' → +TE'
3. E' → ε
4. T → FT'
5. T' → *FT'
6. T' → ε
7. F → id
8. F → (E)

