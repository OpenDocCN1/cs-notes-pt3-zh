
## Partitioned Parallel Hash-Join

Parallelizing partitioned hash join:

- Assume s is smaller than r and therefore s is chosen as the build relation.
- A hash function h₁ takes the join attribute value of each tuple in s and maps this tuple to one of the n processors.
- Each processor Pᵢ reads the tuples of s that are on its disk Dᵢ, and sends each tuple to the appropriate processor based on hash function h₁. Let sᵢ denote the tuples of relation s that are sent to processor Pᵢ.
- As tuples of relation s are received at the destination processors, they are partitioned further using another hash function, h₂, which is used to compute the hash-join locally. (Cont.)

## Partitioned Parallel Hash-Join (Cont.)

- Once the tuples of s have been distributed, the larger relation r is redistributed across the m processors using the hash function h₁
  - Let rᵢ denote the tuples of relation r that are sent to processor Pᵢ.
- As the r tuples are received at the destination processors, they are repartitioned using the function h₂
  - (just as the probe relation is partitioned in the sequential hash-join algorithm).
- Each processor Pᵢ executes the build and probe phases of the hash-join algorithm on the local partitions rᵢ and s of r and s to produce a partition of the final result of the hash-join.
- Note: Hash-join optimizations can be applied to the parallel case
  - e.g., the hybrid hash-join algorithm can be used to cache some of the incoming tuples in memory and avoid the cost of writing them and reading them back in.

## Parallel Nested-Loop Join

- Assume that
  - relation *s* is much smaller than relation *r* and that *r* is stored by partitioning.
  - there is an index on a join attribute of relation *r* at each of the partitions of relation *r*.
- Use asymmetric fragment-and-replicate, with relation *s* being replicated, and using the existing partitioning of relation *r*.
- Each processor *P<sub>j</sub>* where a partition of relation *s* is stored reads the tuples of relation *s* stored in *D<sub>j</sub>*, and replicates the tuples to every other processor *P<sub>i</sub>*.
  - At the end of this phase, relation *s* is replicated at all sites that store tuples of relation *r*.
- Each processor *P<sub>i</sub>* performs an indexed nested-loop join of relation *s* with the i<sup>th</sup> partition of relation *r*.

## Other Relational Operations

Selection σ_θ(r)

- If θ is of the form aᵢ = v, where aᵢ is an attribute and v a value.
  - If r is partitioned on aᵢ, the selection is performed at a single processor.
- If θ is of the form l <= aᵢ <= u (i.e., θ is a range selection) and the relation has been range-partitioned on aᵢ
  - Selection is performed at each processor whose partition overlaps with the specified range of values.
- In all other cases: the selection is performed in parallel at all the processors.

## Other Relational Operations (Cont.)

- Duplicate elimination
  - Perform by using either of the parallel sort techniques
    - eliminate duplicates as soon as they are found during sorting.
  - Can also partition the tuples (using either range- or hash-partitioning) and perform duplicate elimination locally at each processor.
- Projection
  - Projection without duplicate elimination can be performed as tuples are read in from disk in parallel.
  - If duplicate elimination is required, any of the above duplicate elimination techniques can be used.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_991_0.png)

## Grouping/Aggregation

- Partition the relation on the grouping attributes and then compute the aggregate values locally at each processor.
- Can reduce cost of transferring tuples during partitioning by partly computing aggregate values before partitioning.
- Consider the **sum** aggregation operation:
  - Perform aggregation operation at each processor Pᵢ on those tuples stored on disk Dᵢ
    - results in tuples with partial sums at each processor.
  - Result of the local aggregation is partitioned on the grouping attributes, and the aggregation performed again at each processor Pᵢ to get the final result.
- Fewer tuples need to be sent to other processors during partitioning.
