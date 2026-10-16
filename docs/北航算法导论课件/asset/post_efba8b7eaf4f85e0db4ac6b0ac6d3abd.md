
## 1.2.2 Algorithms and other technologies

## For example

- a web-based service that determines how to travel from one location to another
  - The implementation would rely on fast hardware, a GUI, wide-area networking, and also possibly on OO
  - It would also require algorithms for certain operations, such as finding routes, rendering maps, interpolating address（路径寻找，地图渲染，寻址）

## 1.2.2 Algorithms and other technologies

## Algorithms used in

软件学院日文应用软件开发专业研一学生栾鸿钧对总理说，最近几年我们国家对软件工程产业比较重视，但同印度相比，还存在差距。

> 温总理接着栾鸿钧的话题说：“我参观过印度的软件公司。当时我就讲，软件主要决定于两个因素，第一是人的大脑，第二是市场的需求。人的智力开发，是无穷无尽的。我希望学软件的学生，一定要把基础打好，必须要有创造思维。如果学软件没有创造思维，就没有出路。不能仅仅满足于书本，软件关键在于开发，学习这个专业，是很有前途的。”

（2008年12月20日，北航图书馆）

使用

研究应用

软件专业的学生须有坚实的基础

Program model (machine, assembler, ... model language, OO

Complexity of computing ((Non)-Computable actually)

Computing model (Computable, Non-computable)

John Von Nouma Knuth

## 1.2.2 Algorithms and other technologies

- Algorithms are at the core of most technologies used in contemporary computers
- Having a solid base of algorithmic knowledge and technique is one characteristic that separates the truly skilled programmers from the novices (初学者)
- With modern computing technology, you can accomplish some tasks without knowing much about algorithms
- With a good background in algorithms, you can do much, much more !!!

## Exercises and problems

All

## 2 Getting Started

Goals:

- Start using framework for describing and analyzing algorithms （描述和分析算法的框架）
- Examine two algorithms for sorting: insertion sort and merge sort
- See how to describe algorithms in pseudocode, C/C++ and argue the correctness of that （如何描述算法）
- Begin using asymptotic notation to express running-time analysis （使用一致性符号来分析算法的运算时间）
- Learn the technique of “divide and conquer” in the context of merge sort （通过merge sort来学习分而治之方法）

## 2 Getting Started

- 2.1 Insertion sort: framework for describing algorithms
- 2.2 Insertion sort: Analyzing algorithms
- 2.3 Merge sort: Designing algorithms

## 2.1 Insertion sort

Problem: to sort a sequence of numbers into nondecreasing order

Input: A sequence of n numbers <a₁,a₂,…,aₙ>

Output: A permutation (reordering) <a₁',a₂',…,aₙ'> of the input sequence such that a₁' ≤ a₂' ≤ … ≤ aₙ'

![](img/09c68ab421cfce4995ddad1430ef2637_35_0.png)

## 2.1 Insertion sort

- **Pseudocode**
  - That is similar in many respects to C, Pascal, or Java
- **Differences between pseudocode and real code**
  - pseudocode is clear and concise to specify a given algorithm (清晰、准确)
  - Pseudocode is not typically concerned with issues of software engineering (data abstraction, modularity(模块化), error handling) (不用考虑太多技术细节)
  - 用伪代码可以体现算法的本质
  - 永远不会过时

![](img/09c68ab421cfce4995ddad1430ef2637_37_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_37_1.png)

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

Is the algorithm correct?

![](img/09c68ab421cfce4995ddad1430ef2637_37_2.png)

![](img/09c68ab421cfce4995ddad1430ef2637_37_3.png)

## 2.1.1 Loop invariants and the correctness of insertion sort

- **Loop invariants**

**Loop invariant:** At the start of each iteration of **for** loop, the subarray *A[1 .. j-1]* consists of the elements originally in *A[1 .. j-1]* but in sorted order.

It can help us to understand why an algorithm is correct.

- **three properties about a loop invariant**
  - （初值、维持、终值） （初始化、保存、终止）

- **Initialization:** it is true prior to the first iteration of the loop.(base case)

- **Maintenance:** if it is true before an iteration of the loop, it remains true before the next iteration. (inductive step) ( [i-1] true => [i] true )

- **Termination:** When the loop terminates, the invariant show that the algorithms is correct. (stopping the “induction” when the loop terminates; the inductive step of mathematical induction is used infinitely. 类似于数学归纳法，但数学归纳法能用于无限情况)

When the first two properties hold, the loop invariant is true prior to every iteration of the loop. It is similar to mathematical induction.
