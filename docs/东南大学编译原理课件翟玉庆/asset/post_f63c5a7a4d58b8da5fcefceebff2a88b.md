
## Chapter 9 Code optimization

### Section 3 Loops in flow graphs

#### 1. Dominators

We say node d of a flow graph dominates node n, written d dom n, if every path from the initial node of the flow graph to n goes through d.

#### 2. Back edge

- The edges whose heads dominate their tails.

#### 3. Find all the loops in a flow graph

- Input. A flow graph G and a back edge n -> d.
- Output. The set loop consisting of all nodes in the natural loop of n -> d.

![](img/353f619caa6c5715591f2105bdfa2865_580_0.png)

#### 4. Pre-Headers

- Move statements before the header.
- Create a new block, preheader. It has only the header as successor, and all edges which formerly entered the header of L from outside L instead enter the preheader.

#### 5. Code optimization in a loop

- Code motion.
- Induction Variables and Reduction in Strength.

e.g.

```text
j := 1;
for i = 1 to 100 do
    A[i, j] := B[i, j] + 2
```

And the array is:

```text
A, B : array[1 : 100, 1 : 10]
m = 1
```

```text
(1) j := 1        (2) i := 1
(3) If i > 100 goto (15)
(4) T1 := i * 10  (5) T2 := T1 + j
(6) T3 := a - 11  (7) T4 := i * 10
(8) T5 := T4 + j  (9) T6 := b - 11
(10) T7 := T6[T5]
(11) T8 := T7 + 2
(12) T3[T2] := T8
(13) i := i + 1
(14) goto (3)
```

```text
(1) j := 1        (2) i := 1

(6) T3 := a - 11  (9) T6 := b - 11

(3) If i > 100 goto (15)

(4) T1 := i * 10  (5) T2 := T1 + j
(7) T4 := i * 10
(8) T5 := T4 + j
(10) T7 := T6[T5]
(11) T8 := T7 + 2
(12) T3[T2] := T8
(13) i := i + 1
(14) goto (3)
```

```text
(1) j := 1        (2) i := 1

(6) T3 := a - 11  (9) T6 := b - 11  (4) T1 := 0  (7) T4 := 0

(3) If i > 100 goto (15)

(4) T1 := T1 + 10  (5) T2 := T1 + j
(7) T4 := T4 + 10
(8) T5 := T4 + j
(10) T7 := T6[T5]
(11) T8 := T7 + 2
(12) T3[T2] := T8
(13) i := i + 1
(14) goto (3)
```

```text
(1) j := 1        (2) i := 1

(6) T3 := a - 11  (9) T6 := b - 11  (4) T1 := 0  (7) T4 := 0

(3) If T1 > 1000 goto (15)

(4) T1 := T1 + 10  (5) T2 := T1 + j
(7) T4 := T4 + 10
(8) T5 := T4 + j
(10) T7 := T6[T5]
(11) T8 := T7 + 2
(12) T3[T2] := T8
(14) goto (3)
```

### Section 4 Data-flow analysis

#### 1. Data-flow analysis

- Analyze global data-flow information to do code optimization and a good job of code generation.

Notes: Data-flow information can be collected by setting up and solving systems of equations that relate data-flow information at various points in a program flow.

#### 2. Definitions

1. Point

   The label of a statement in a program.

2. Path

   Path from p1 to pn is a sequence of points p1, p2, ..., pn such that for each i between 1 and n - 1, either:

   - (1) pi is the point immediately preceding a statement and pi+1 is the point immediately following that statement in the same block, or
   - (2) pi is the end of some block and pi+1 is the beginning of a successor block.

3. Reaching

   Notes: (1) Intuitively, if a definition d of some variable a reaches point p, then d might be the place at which the value of a used at p was last defined.

   (2) We kill a definition of a variable a if between two points along the path there is a definition of a.

#### 4. Reaching Algorithm

- Input. A flow graph for which kill[B] and gen[B] have been computed for each block B.
- Output. In[B] and out[B] for each block B.
- Method.
