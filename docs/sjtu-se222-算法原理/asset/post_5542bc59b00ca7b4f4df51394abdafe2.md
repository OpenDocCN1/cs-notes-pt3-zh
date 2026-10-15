
## Course goals

- To become proficient in the application of fundamental *algorithm design techniques*
- To gain familiarity with the main theoretical tools used in the *analysis of algorithms*
- To study and analyze different algorithms for many of “standard” *algorithmic problems*
- To introduce students to some of the *prominent subfields* of algorithmic study in which they may wish to pursue further study

## Where are we?

- Why study Algorithms
- Outline of the course
- Course Polices

## Grading Policy

- Homework 25%
  - Distributed on course website after every lecture
  - Submit every Tuesday
- Programming assignment 15%
  - LeetCode (http://leetcode.com)
- Final exam 60%

## TAs

- TAs
  - Bingbing Fang (方冰冰), fke_htj@sjtu.edu.cn
  - Wenbo Zhang (张文博), wbzhang@sjtu.edu.cn
- Homepage:
  http://basics.sjtu.edu.cn/~xiao juan/algo15/

## More on LeetCode

- Submission:

![](img/a8f1b433a70f1e5c410c8b43e41b650e_16_0.png)

- Due on every Saturday night: 23:59

- One student will be selected (randomly) to be report your solution (in 5 minutes) on Tuesday.

## Teaching techniques

- One minute paper

![](img/a8f1b433a70f1e5c410c8b43e41b650e_17_0.png)

## Voices from senior students

- 算法是用来娱乐身心、课余刷题、公司面试、学会使用编程思想来看待各种问题的课程
- 用心学算法，很有意思的，这是程序员的内力修为，别太在意考试面试
- 坚持到期末
- 算法无论从哪个次元来看都是程序员的基础。
- 好好听课，不然会对自己失去信心。
- 这是我在软院上过最有意思最有收获的一门课。
- 算法很重要，但更重要的是思想。或许将来我们不会用到今天学习的算法，但是某个算法的思想会帮我们解决很多实际问题。
- 大神们请低调，给学渣们活路啊！
- 冬天还是从被窝里爬起来吧，对找工作还是很重要滴
- ...

## Enjoy!

## Lecture I Introduction

- Problem: Dynamic Connectivity
- Solutions:
  correctness, complexity, improvements
- Applications

## The problem

Problem: DynamicConnectivity
Input: n sites, m operations (union or connected query)
Output: the answer of connected queries

```
union(4, 3)
union(3, 8)
union(6, 5)
union(9, 4)
union(2, 1)
connected(0, 7)  X
connected(8, 9)  ✓
union(5, 0)
union(7, 2)
union(6, 1)
connected(0, 7)  ✓
union(1, 0)
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_21_0.png)

## More difficult example

Q. Connected(p, q)

A. Yes.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_22_0.png)

## Where are we?

- Problem: Dynamic Connectivity
- Solutions:
  correctness, complexity, improvements
- Applications

## Your ideas

## Model the problem

![](img/a8f1b433a70f1e5c410c8b43e41b650e_25_0.png)

union(2, 5)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_25_1.png)

{ 0 } { 1 4 5 } { 2 3 6 7 }

3 connected components

{ 0 } { 1 2 3 4 5 6 7 }

2 connected components

Connected(2, 5): Are 2 and 5 in the same connected components?

## S1: Quick find

id[]
0 1 2 3 4 5 6 7 8 9
0 1 1 8 8 0 0 1 8 8

0, 5 and 6 are connected

1, 2, and 7 are connected

3, 4, 8, and 9 are connected

![](img/a8f1b433a70f1e5c410c8b43e41b650e_26_0.png)

Find(p,q). Check if p and q have the same id.

Union(p,q). To merge components containing p and q, change all entries whose id equals id[p] to id[q].

## Quiz

Assume there are N sites, then in the worst case,

- *quick-find* need () array access for *union*.
- *quick-find* need () array access for *find*.

A. N    B. 1    C. N²    D. logN

## S2: Quick union

![](img/a8f1b433a70f1e5c410c8b43e41b650e_28_0.png)

3's root is 9; 5's root is 6

3 and 5 are not connected

**Find(p,q).** Check if p and q have the same root.

**Union(p,q).** To merge components containing p and q, set the id of p's root to the id of q's root.

## Quiz

Assume there are N sites, then in the worst case,

- *quick-union* need () array access for *union*.
- *quick-union* need () array access for *find*.

A. N    B. 1    C. N²    D. logN

## Complexity

| algorithm | initialize | union | find |
|---|---|---|---|
| quick-find | N | N | 1 |
| quick-union | N | N | N |

Can we do better?
