
## Cost of Parallel Evaluation of Operations

- If there is no skew in the partitioning, and there is no overhead due to the parallel evaluation, expected speed-up will be 1/n
- If skew and overheads are also to be taken into account, the time taken by a parallel operation can be estimated as

$T_{part} + T_{asm} + \max(T_0, T_1, ..., T_{n-1})$

- T_part is the time for partitioning the relations
- T_asm is the time for assembling the results
- T_i is the time taken for the operation at processor P_i

this needs to be estimated taking into account the skew, and the time wasted in contentions.

## Interoperator Parallelism

### Pipelined parallelism

- Consider a join of four relations
  - r1 ⋈ r2 ⋈ r3 ⋈ r4
- Set up a pipeline that computes the three joins in parallel
  - Let P1 be assigned the computation of
    temp1 = r1 ⋈ r2
  - And P2 be assigned the computation of temp2 = temp1 ⋈ r3
  - And P3 be assigned the computation of temp2 ⋈ r4
- Each of these operations can execute in parallel, sending result tuples it computes to the next operation even as it is computing further results
  - Provided a pipelineable join evaluation algorithm (e.g., indexed nested loops join) is used

## Factors Limiting Utility of Pipeline Parallelism

- Pipeline parallelism is useful since it avoids writing intermediate results to disk
- Useful with small number of processors, but does not scale up well with more processors. One reason is that pipeline chains do not attain sufficient length.
- Cannot pipeline operators which do not produce output until all inputs have been accessed (e.g., aggregate and sort)
- Little speedup is obtained for the frequent cases of skew in which one operator's execution cost is much higher than the others.

## Independent Parallelism

- **Independent parallelism**
  - Consider a join of four relations
    r₁ ⋈ r₂ ⋈ r₃ ⋈ r₄
    - Let P₁ be assigned the computation of temp1 = r₁ ⋈ r₂
    - And P₂ be assigned the computation of temp2 = r₃ ⋈ r₄
    - And P₃ be assigned the computation of temp1 ⋈ temp₂
    - P₁ and P₂ can work **independently in parallel**
    - P₃ has to wait for input from P₁ and P₂
      - Can pipeline output of P₁ and P₂ to P₃, combining independent parallelism and pipelined parallelism
    - Does not provide a high degree of parallelism
      - useful with a lower degree of parallelism.
      - less useful in a highly parallel system.

## Query Optimization

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_996_0.png)

Query optimization in parallel databases is significantly more complex than query optimization in sequential databases.

Cost models are more complicated, since we must take into account partitioning costs and issues such as skew and resource contention.

When scheduling execution tree in parallel system, must decide:

- How to parallelize each operation and how many processors to use for it.
- What operations to pipeline, what operations to execute independently in parallel, and what operations to execute sequentially, one after the other.

Determining the amount of resources to allocate for each operation is a problem.

- E.g., allocating more processors than optimal can result in high communication overhead.

Long pipelines should be avoided as the final operation may wait a lot for inputs, while holding precious resources

## Query Optimization (Cont.)

- The number of parallel evaluation plans from which to choose from is much larger than the number of sequential evaluation plans.
- Therefore heuristics are needed while optimization

- Two alternative heuristics for choosing parallel plans:
- No pipelining and inter-operation pipelining; just parallelize every operation across all processors.
  ▸ Finding best plan is now much easier --- use standard optimization technique, but with new cost model
  ▸ Volcano parallel database popularize the exchange-operator model
    – exchange operator is introduced into query plans to partition and distribute tuples
    – each operation works independently on local data on each processor, in parallel with other copies of the operation
- First choose most efficient sequential plan and then choose how best to parallelize the operations in that plan.
  ▸ Can explore pipelined parallelism as an option

- Choosing a good physical organization (partitioning technique) is important to speed up queries.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_997_0.png)
