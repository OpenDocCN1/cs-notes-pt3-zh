
## Introduction to Algorithms

- Practice and contest
  - New OJ: http://acm.buaa.edu.cn
- Slides
  - 发大班邮箱？建一个学习群？
- Paper, project to submit
  - songyou@buaa.edu.cn

## 1 The Role of Algorithms in Computing

- **What** are algorithms?
- Why is the study of algorithms **worthwhile**?
  - （为什么算法研究非常有意义）
- What is the **role** of algorithms relative to other technologies used in computers?
  - （相比计算机科学的其他技术，算法的角色和地位）

### 1.1 What are algorithms

- Computing: information processing
- Scientific computing (modeling, computing, verifying)
  - 数学：公理、规则 => 定理
    - “上帝创造”。描述客观世界，给人们带来无穷乐趣和痛苦。
  - 例如：Pi的小数点后面是否存在1000个连续的7
  - 1900, Hilbert, 巴黎世界数学家大会，“是否存在一个通用的过程（算法），可以自动判定任意命题是否正确？”
  - Turing (1912~1954), 1931, undergraduate in Cambridge Univ.
  - Before 1936, no scientific computing. Turing, 论可计算数及其在判定问题中的应用, 1936.
  - John von Neumann (1903~1957), 1946, first electronic computer.
  - 算法：过程、工具
    - “人创造”。方便人们研究数学；解决实际问题。

1. Algorithm is any well-defined computational procedure

   （算法：一个定义明确的可计算过程）

   ![](img/09c68ab421cfce4995ddad1430ef2637_14_0.png)

   ```
   < 31,41,59,26,12,58 >
   <31,41,26,12,58,59>
   <31,26,12,41,58,59>
   ......
   <12,26,31,41,58,59>
   ```

   “冒泡”排序是可计算过程

   - Well-defined: know what to do each step; always halts with correct answer.
   - Efficiency: good or bad?

2. Algorithm is a tool for solving a well-specified computational problem

   Problem? general questions needed to be computed

   Algorithm (a tool)

   instance (input)?

   - input1 ?
   - input2 ?
   - input3 ?
   - ……

   output

   ![](img/09c68ab421cfce4995ddad1430ef2637_15_0.png)

   ![](img/09c68ab421cfce4995ddad1430ef2637_15_1.png)

   Sorting is a fundamental operation in computer science

   **Example: Sorting problem**

   **Problem:** to sort a sequence of numbers into nondecreasing order

   **Input:** A sequence of n numbers <a₁,a₂,…,aₙ>

   **Output:** A permutation (reordering) <a₁',a₂',…,aₙ'> of the input sequence such that a₁' ≤ a₂' ≤ … ≤ aₙ'

   **An instance of the sorting problem**

   **Input:** <31,41,59,26,41,58>

   **Output:** <26,31,41,41,58,59>

- **The characteristics of the algorithm**
  - **Output:** at least one.
  - **Correct:** An algorithm is said to be correct if, for every input instance, it halts with the correct output
  - **Incorrect algorithm**
    - might not halt at all on some input instances, or
    - might halt with an answer other than the desired one
    - can sometimes be useful (if error rate can be controlled)
  - **Feasible** (可行性，可编程实现)
  - **Practical** (feasible actually，实际可行)

#### 1.1.1 What kinds of problems are solved by algorithms

- **Genome Project**
- **Internet**
  - finding good routes; search engine
- **Electronic commerce**
  - keeping information; digital signatures
- **Manufacturing and other commercial settings**
  - placing wells; buying campaign advertising
- **Finding the shortest path from one vertex to another**
- **Matrices product:** $A_1 A_2 A_3 A_4$
  - $A_1(A_2(A_3 A_4))$; $A_1((A_2 A_3)A_4)$; $(A_1 A_2)(A_3 A_4)$
  - ......

**Common characteristics of many algorithms**

- Many candidate solutions
  - (one of which is best, but finding it can present quite a challenge.)
  - for example, $A_1 A_2 A_3 A_4$
  - $A_1(A_2(A_3 A_4))$; $A_1((A_2 A_3)A_4)$; $(A_1 A_2)(A_3 A_4)$
- Practical application
  - shortest paths: a transportation (lower labor, fuel costs)

#### 1.1.2 Data structures

- A data structure is a way to **store** and **organize** data in order to facilitate access and modifications
- No single data structure works well for all purposes
- It is important to know the strengths and limitations of data structure
- Data structures: static
- Algorithms: dynamic
- The Art of Computer programming
  - Static + Dynamic
