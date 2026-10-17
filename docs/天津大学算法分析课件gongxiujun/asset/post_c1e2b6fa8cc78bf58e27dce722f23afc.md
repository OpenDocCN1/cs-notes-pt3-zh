

## Outline

## Are problems easy or hard?

- Problem stacks
- tractable problems
- intractable problems
- unsolvable problems
- Decision vs Optimization problems

## What makes a problem hard ?

## Hardness equivalence of problems

## Are problems easy or hard?

### Problem stacks

Linear Sorting

Matrix Multiplying

Path Finding

Graph Searching

Item Loading

Job Scheduling

Quick Sort

Merge Sort

Select number

Matrix Blocks

Matrix Chain

One pair shortest path

All pairs shortest path

Traveling salesman problem

Max Clique

Non crossing subset

LCS problem

Container Loading

Subset Sum

0/1 Knapsack

Bin Processor

Nuns Processors

Dense Puzzles

Algorithms

Greedy algorithm

Divide & conquer

Dynamic programming

Backtracking algorithm

Branch & bound

T(n) = O(n^2)

T(n) = O(2^n)

GONG Xiu-Jun

Algorithms

NPC Problems

We have seen many problems that can be solved in polynomial time, for instances,

- Sorting n numbers
- Finding the shortest path between a pair vertices in a graph
- Calculating the square root of an integer
- ...

These problems are computationally tractable, means that

- A tractable problem can be solved by a polynomial-time algorithm.
- Its upper bound is polynomial, such as bounded by \(log(n)\), \(nlog(n)\), \(n^2\), etc.
- This complexity holds for reasonable input size other than for Internet-size.

We have seen many problems that cannot be solved in polynomial time.

# intractable problem

a problem that cannot be solved by a polynomial-time algorithm. The lower bound is exponential.

Examples include:

- Some of them require a non-polynomial amount of output, so they clearly will take a non-polynomial amount of time
- Towers of Hanoi: we can prove that any algorithm that solves this problem must have a worst-case running time that is at least 2^n − 1.

