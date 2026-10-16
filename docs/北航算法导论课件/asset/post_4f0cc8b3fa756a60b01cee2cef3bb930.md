
## 2.1.1 Loop invariants and the correctness of insertion sort

- three properties hold for insertion sort

Loop invariant: original A[1 .. j-1] is permuted to A'[1 .. j-1] but in sorted order

- Initialization: j=2, A[1 .. j-1] consists of just the single A[1], which is the original element in A[1], and is sorted. Obviously, the loop invariant holds prior to the first iteration of the loop.

- Maintenance: A'[1 .. j-1] is in sorted order, sorting A[j] into A'[1 .. j-1], s.t. <a'₁, a'₂, ..., a'ₖ, aⱼ, a'ₖ₊₁, ..., ..., a'ⱼ₋₁>, obviously, it is sorted. The second property holds for the outer loop.

- Termination: when j=n+1. A'[1 .. j-1] = A'[1 .. n] consists of the elements originally in A[1 .. n], but in sorted order. A'[1 .. n] is the entire array! Hence, the algorithm is correct.

## 2.1.2 Pseudocode conventions

- Indentation indicates block structure. （缩排）
- The looping constructs (**while**, **for**, **repeat**) and the conditional constructs (**if**, **then**, **else**) have interpretations similar to those in Pascal, C.
- “//” or “▷” indicates a comment.
- A multiple assignment *i←j←e* is equivalent to *j←e* then *i←j*.
- Variables are local to the given procedure.
- Array elements access: *A[i]*； *A[1..j] = <A[1], A[2],…, A[i]>*
- Compound data are typically organized into objects.
- Parameters are passed to a procedure by value.
- The boolean operators “and” and “or” are short circuiting: for example “*x* and (or) *y*”: whether or not evaluate *y* rely on the evaluating of *x*.

## 2.2 Analyzing algorithms

- Analyzing an algorithm means predicting the resources
  - Resources:
    - memory (space)
    - communication bandwidth
    - primary concern computer hardware
    - computational time (in CPU, I/O, ...)
  - By analyzing several candidate algorithms for a problem, a most efficient one can be identified, but several inferior are discarded (最优方案选取)

- Computing model (计算模型)
  - Turing (图灵机，计算的原始模型：符号体系，读写介质，I/O，......)
    M = (Q, Γ, I, δ, B, q₀, q_f)
  - RAM
    Random-access machine,
    随机存取器

![](img/09c68ab421cfce4995ddad1430ef2637_42_0.png)

- **RAM model: Algorithms will be implemented as computer programs.**
  - RAM, a generic one-processor, instructions are executed one after another, with no concurrent operations.
  - RAM contains instructions commonly
    - Arithmetic (add, subtract, multiply, divide, remainder, floor, ceiling)
    - Data movement (load, store, copy)
    - Control (conditional and unconditional branch, subroutine call and return)
  - Each such instruction takes a constant amount of time.

- Analyzing a simple algorithm can be a challenge
  - Mathematics required: combinatorics, probability theory, algebraic dexterity
    (数学功底好)
  - An ability to identify the most significant terms in a formula
    (洞察能力强，能抓住最重要的部分)
  - Summarizing an algorithm in simple formulas
    (抽象思维强，能将算法的本质特征归纳成简单形式)

### 2.2.1 Analysis of insertion sort

- **Running time of a program is described as a function of the size of its input.** （通常，程序的运算时间是输入规模的函数）
  - **input size n**: *number of items in the input, depends on the problem*
    - sorting array A: n = length of A
    - graph: n can be the numbers of verices and edges
  - **Running time T(n)**: on a particular input, *the number of primitive operations or “steps” executed* （基本操作数）
    运行时间满足如下一致性原则
    - The steps are machine-independent（基本操作独立于机器）
    - A constant amount of time cᵢ is required to execute the iᵗʰ line pseudocode （每行指令的执行时间为常数）

```
INSERTION-SORT(A)
1   for(j = 2; j <= length[A]; j++)
2   {   key = A[j]
3       // Insert A[j] into the sorted sequence A[1 .. j-1]
4       i = j-1
5       while(i > 0 && A[i] > key)
6       {   A[i+1] = A[i]
7           i = i-1
8       }
9       A[i+1] = key
10  }
```

| cost | times |
|------|-------|
| c₁ | n |
| c₂ | n-1 |
| 0 | n-1 |
| c₄ | n-1 |
| c₅ | Σⱼ=2ⁿ tⱼ |
| c₆ | Σⱼ=2ⁿ (tⱼ -1) |
| c₇ | Σⱼ=2ⁿ (tⱼ -1) |
| c₈ | n-1 |

T(n) = c₁ n + c₂ (n-1) + c₄ (n-1) + c₅ Σⱼ=2ⁿ tⱼ + c₆ Σⱼ=2ⁿ (tⱼ -1) + c₇ Σⱼ=2ⁿ (tⱼ -1) + c₈ (n-1)

![](img/09c68ab421cfce4995ddad1430ef2637_46_0.png)
