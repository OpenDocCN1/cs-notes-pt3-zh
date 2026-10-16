
## Choice of Evaluation Plans

- Must consider the interaction of evaluation techniques when choosing evaluation plans
  - choosing the cheapest algorithm for each operation independently may not yield best overall algorithm. E.g.
    - merge-join may be costlier than hash-join, but may provide a sorted output which reduces the cost for an outer level aggregation.
    - nested-loop join may provide opportunity for pipelining
- Practical query optimizers incorporate elements of the following two broad approaches:
  1. Search all the plans and choose the best plan in a cost-based fashion.
  2. Uses heuristics to choose a plan.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_658_0.png)

## Cost-Based Optimization

- Consider finding the best join-order for $r_1 \bowtie r_2 \bowtie \ldots \bowtie r_n$.
- There are $(2(n-1))!/(n-1)!$ different join orders for above expression. With $n=7$, the number is 665280, with $n=10$, the number is greater than 176 billion!
- No need to generate all the join orders. Using dynamic programming, the least-cost join order for any subset of $\{r_1, r_2, \ldots r_n\}$ is computed only once and stored for future use.

## Dynamic Programming in Optimization

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_660_0.png)

- To find best join tree for a set of n relations:
- To find best plan for a set S of n relations, consider all possible plans of the form: S₁ ⋈ (S – S₁) where S₁ is any non-empty subset of S.
- Recursively compute costs for joining subsets of S to find the cost of each plan. Choose the cheapest of the 2^n – 2 alternatives.
- Base case for recursion: single relation access plan
  - Apply all selections on R_i using best choice of indices on R_i
- When plan for any subset is computed, store it and reuse it when it is required again, instead of recomputing it
  - Dynamic programming

## Join Order Optimization Algorithm

```pseudocode
procedure findbestplan(S)
if (bestplan[S].cost ≠ ∞)
    return bestplan[S]

// else bestplan[S] has not been computed earlier, compute it now
if (S contains only 1 relation)
    set bestplan[S].plan and bestplan[S].cost based on the best way of accessing S /* Using selections on S and indices on S */
else
    for each non-empty subset S1 of S such that S1 ≠ S
        P1 = findbestplan(S1)
        P2 = findbestplan(S - S1)
        A = best algorithm for joining results of P1 and P2
        cost = P1.cost + P2.cost + cost of A
        if cost < bestplan[S].cost
            bestplan[S].cost = cost
            bestplan[S].plan = "execute P1.plan; execute P2.plan; join results of P1 and P2 using A"
    return bestplan[S]
```

- Some modifications to allow indexed nested loops joins on relations that have selections (see book)

## Left Deep Join Trees

In left-deep join trees, the right-hand-side input for each join is a relation, not the result of an intermediate join.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_662_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_662_1.png)

## Interesting Sort Orders

- Consider the expression ($r_1 \bowtie r_2$) $\bowtie r_3$  (with A as common attribute)
- An **interesting sort order** is a particular sort order of tuples that could be useful for a later operation
  - Using merge-join to compute $r_1 \bowtie r_2$ may be costlier than hash join but generates result sorted on A
  - Which in turn may make merge-join with $r_3$ cheaper, which may reduce cost of join with $r_3$ and minimizing overall cost
  - Sort order may also be useful for order by and for grouping
- Not sufficient to find the best join order for each subset of the set of $n$ given relations
  - must find the best join order for each subset, **for each interesting sort order**
  - Simple extension of earlier dynamic programming algorithms
  - Usually, number of interesting orders is quite small and doesn’t affect time/space complexity significantly
