
## Solution

## 15.5-1

```
A(r, i, j)
1  if i=1 && j=n
2      r[i,j] is the root
3  if i=j
4      print "d"i-1" is the left child of k"i
5      print "d"i" is the right child of k"i
6  else if r[i,j]=i
7      print "d"i-1" is the left child of k"i
8      print "k"r[i+1,j]" is the right child of k"r[i,j]
9      A(r, i+1, j)
10 else if r[i,j]=j
11     print "k"r[i,j-1]" is the left child of k"r[i,j]
12     A(r, i, j-1)
13     print "d"j" is the right child of k"j
14 else // i<r[i,j]<j
15     print "k"r[i,r[i,j]-1]" is the left child of k"r[i,j]
16     A(r, i, r[i,j]-1)
17     print "k"r[r[i,j]+1,j]" is the right child of k"r[i,j]
18     A(r, r[i,j]+1, j)
```

## Amortized Analysis

- In an amortized analysis, we average the time required to perform a sequence of data-structure operations over all the operations performed.（在多个操作中，求一个操作的平均时间）
- With amortized analysis, we can show that the average cost of an operation is small, if we average over a sequence of operations, even though a single operation within the sequence might be expensive.
- Amortized analysis differs from average-case analysis in that probability is not involved; an amortized analysis guarantees the average performance of each operation in the worst case.

## 17.1 Aggregate analysis

- In aggregate analysis, we show that for all *n*, a sequence of *n* operations takes worst-case time T(*n*) in total.
- In the worst case, the average cost, or amortized cost, per operation is therefore T(*n*)/*n*.

## Stack operations

- **PUSH(S, x)**: pushes object x onto stack S. O(1)
- **POP(S)**: pops the top of stack S and returns the popped object. Calling POP on an empty stack generates an error. O(1)
- **MULTIPOP(S, x)**: removes the k top objects of stack S, popping the entire stack if the stack contains fewer than k objects. (The stack has s objects.) O(min(s, k))?

## Stack operations

- **MULTIPOP(S, x)**: removes the k top objects of stack S, popping the entire stack if the stack contains fewer than k objects. (The stack has s objects.)

```
MULTIPOP(S, k)
1   while not STACK-EMPTY(S) and k > 0
2       POP(S)
3       k = k - 1
```

O(min(s, k))

![](img/09c68ab421cfce4995ddad1430ef2637_333_0.png)

## Stack operations

- Let us analyze a sequence of n PUSH, POP, and MULTIPOP operations on an initially empty stack.

```
STACK(S, n)
    S = NULL
    for i←1 to n
        One of ( PUSH(S, i), POP(S), MULTIPOP(S, k) )
```

- Running time tightly. O(n)
- The number of times that POP can be called on a nonempty stack, including calls within MULTIPOP, is at most the number of PUSH operations, which is at most n. (push一个对象后，至多能被pop一次。至多n次push.)
- The average cost of an operation is O(n)/n = O(1)
- In aggregate analysis, we assign the amortized cost of each operation to be the average cost.
- For STACK operations, the average cost (the running time) of a stack operation is O(1), we did not use probabilistic reasoning.
- Dividing this total cost by n yielded the average cost per operation, or the amortized cost.

## Incrementing a binary counter

- Consider the problem of implementing a k-bit binary counter that counts upward from 0.
- We use an array A[0 .. k-1] of bits as the counter. (使用位数组作为计数器)
- A number x that is stored in the counter has its lowest-order bit in A[0] and its highest-order bit in A[k-1], so that
  $$x = \sum_{i=0}^{k-1} A[i] \cdot 2^{i}$$
- Initially, x = 0, and thus A[i] = 0 for i = 0, 1, ..., k-1.
- To add 1 (modulo 2^k) to the value in the counter, we use the following procedure.

```
INCREMENT(A)
1  i = 0      // index of A
2  while i < A.length and A[i] == 1
3      A[i] = 0
4      i = i + 1
5  if i < A.length
6      A[i] = 1
```

| Counter value | A[7] | A[6] | A[5] | A[4] | A[3] | A[2] | A[1] | A[0] | Total cost |
|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| 2 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 3 |
| 3 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 4 |
| 4 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 7 |
| 5 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 8 |
| 6 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 10 |
| 7 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 11 |
| 8 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 15 |
| 9 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 16 |
| 10 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 18 |
| 11 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 19 |
| 12 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 22 |
| 13 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 23 |
| 14 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 25 |
| 15 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 26 |
| 16 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 31 |
