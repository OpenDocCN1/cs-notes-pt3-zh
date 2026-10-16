

## 2 入门

- 2.1 插入排序：描述算法的框架
- 2.2 插入排序：分析算法
- 2.3 归并排序：设计算法

## 2.1 插入排序

问题：将一组数字排序为非递减顺序

输入：n 个数字的序列 <a₁,a₂,…,aₙ>

输出：输入序列的一个排列 <a₁',a₂',…,aₙ'>，使得 a₁' ≤ a₂' ≤ … ≤ aₙ'

![](img/09c68ab421cfce4995ddad1430ef2637_70_0.png)

### 2.1 插入排序

- **伪代码**
  在许多方面与 C、Pascal 或 Java 相似
- **伪代码与真实代码之间的差异**
  - pseudocode is clear and concise to specify a given algorithm (清晰、准确)
  - Pseudocode is not typically concerned with issues of software engineering (data abstraction, modularity(模块化), error handling) (不用考虑太多技术细节)
  - 用伪代码可以体现算法的本质
  - 永远不会过时

### 2.1 插入排序

```
INSERTION-SORT(A)
1   for(j = 2; j <= length[A]; j++) // loop header
2   {      key = A[j]
3       // Insert A[j] into the sorted sequence A[1 .. j-1]
4       i <- j-1
5       while(i > 0 && A[i] > key)
6       {      A[i+1] = A[i]
7           i = i-1
8       }
9       A[i+1] = key
10  }   // loop body below
```

算法正确吗？

![](img/09c68ab421cfce4995ddad1430ef2637_72_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_72_1.png)

![](img/09c68ab421cfce4995ddad1430ef2637_72_2.png)

### 2.1.1 循环不变量与插入排序的正确性

- **循环不变量**

**Loop invariant:** At the start of each iteration of **for** loop, the subarray *A[1 .. j-1]* consists of the elements originally in *A[1 .. j-1]* but in sorted order.

它可以帮助我们理解为什么算法是正确的。

- **循环不变量的三个性质**
  （初值、维持、终值） （初始化、保存、终止）

- **Initialization:** it is true prior to the first iteration of the loop.(base case)

- **Maintenance:** if it is true before an iteration of the loop, it remains true before the next iteration. (inductive step) ( [i-1] true => [i] true )

- **Termination:** When the loop terminates, the invariant show that the algorithms is correct. (stopping the “induction” when the loop terminates; the inductive step of mathematical induction is used infinitely. 类似于数学归纳法，但数学归纳法能用于无限情况)

当前两个性质成立时，循环不变量在循环的每次迭代之前都为真。它类似于数学归纳法。

### 2.1.1 循环不变量与插入排序的正确性

- 插入排序满足三个性质

Loop invariant: original A[1 .. j-1] is permuted to A'[1 .. j-1] but in sorted order

- Initialization: j=2, A[1 .. j-1] consists of just the single A[1], which is the original element in A[1], and is sorted. Obviously, the loop invariant holds prior to the first iteration of the loop.

- Maintenance: A'[1 .. j-1] is in sorted order, sorting A[j] into A'[1 .. j-1], s.t. <a'₁, a'₂, ..., a'ₖ, aⱼ, a'ₖ₊₁, ..., ..., a'ⱼ₋₁>, obviously, it is sorted. The second property holds for the outer loop.

- Termination: when j=n+1. A'[1 .. j-1] = A'[1 .. n] consists of the elements originally in A[1 .. n], but in sorted order. A'[1 .. n] is the entire array! Hence, the algorithm is correct.

### 2.1.2 伪代码约定

- Indentation indicates block structure. （缩排）
- The looping constructs (**while**, **for**, **repeat**) and the conditional constructs (**if**, **then**, **else**) have interpretations similar to those in Pascal, C.
- “//” or “▷” indicates a comment.
- A multiple assignment *i←j←e* is equivalent to *j←e* then *i←j*.
- Variables are local to the given procedure.
- Array elements access: *A[i]*； *A[1..j] = <A[1], A[2],…, A[i]>*
- Compound data are typically organized into objects.
- Parameters are passed to a procedure by value.
- The boolean operators “and” and “or” are short circuiting: for example “*x* and (or) *y*”: whether or not evaluate *y* rely on the evaluating of *x*.

