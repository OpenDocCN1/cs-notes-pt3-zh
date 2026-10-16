
## Transformation Example: Pushing Selections

- Query: Find the names of all instructors in the Music department, along with the titles of the courses that they teach
- Π_name, title(σ_dept_name= "Music" (instructor ⋈ (teaches ⋈ Π_course_id, title (course))))

- Transformation using rule 7a.
- Π_name, title((σ_dept_name= "Music"(instructor)) ⋈ (teaches ⋈ Π_course_id, title (course)))

- Performing the selection as early as possible reduces the size of the relation to be joined.

## Transformation Example: Pushing Projections

- Consider: Π_name, title(σ_dept_name= “Music” (instructor) ⋈ teaches ⋈ Π_course_id, title (course)))
- When we compute
  (σ_dept_name = “Music” (instructor) ⋈ teaches)
  we obtain a relation whose schema is:
  (ID, name, dept_name, salary, course_id, sec_id, semester, year)
- Push projections using equivalence rules 8a and 8b; eliminate unneeded attributes from intermediate results to get:
  Π_name, title(Π_name, course_id (
    σ_dept_name= “Music” (instructor) ⋈ teaches)
    ⋈ Π_course_id, title (course)))
- Performing the projection as early as possible reduces the size of the relation to be joined.

## Join Ordering Example

- For all relations $r_1, r_2,$ and $r_3,$
  $(r_1 \bowtie r_2)\bowtie r_3 = r_1 \bowtie (r_2 \bowtie r_3)$
  (Join Associativity)

- If $r_2 \bowtie r_3$ is quite large and $r_1 \bowtie r_2$ is small, we choose
  $(r_1 \bowtie r_2)\bowtie r_3$
  so that we compute and store a smaller temporary relation.

## Join Ordering Example (Cont.)

- Consider the expression
  
  \(\Pi_{name,\ title}(\sigma_{dept\_name = \text{“Music”}}(instructor) \bowtie teaches \bowtie \Pi_{course\_id,\ title}(course))\)

- Could compute \(teaches \bowtie \Pi_{course\_id,\ title}(course)\) first, and join result with
  
  \(\sigma_{dept\_name = \text{“Music”}}(instructor)\)
  
  but the result of the first join is likely to be a large relation.

- Only a small fraction of the university’s instructors are likely to be from the Music department
  - it is better to compute
  
    \(\sigma_{dept\_name = \text{“Music”}}(instructor) \bowtie teaches\)
  
    first.

## Enumeration of Equivalent Expressions

- Query optimizers use equivalence rules to **systematically** generate expressions equivalent to the given expression
- Can generate all equivalent expressions as follows:
  - Repeat
    - apply all applicable equivalence rules on every subexpression of every equivalent expression found so far
    - add newly generated expressions to the set of equivalent expressions
  - Until no new equivalent expressions are generated above
- The above approach is very expensive in space and time
  - Two approaches
    - Optimized plan generation based on transformation rules
    - Special case approach for queries with only selections, projections and joins

## Implementing Transformation Based Optimization

- Space requirements reduced by sharing common sub-expressions:
  - when E1 is generated from E2 by an equivalence rule, usually only the top level of the two are different, subtrees below are the same and can be shared using pointers
    - E.g. when applying join commutativity
  - Same sub-expression may get generated multiple times
    - Detect duplicate sub-expressions and share one copy
- Time requirements are reduced by not generating all expressions
  - Dynamic programming
    - We will study only the special case of dynamic programming for join order optimization

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_656_0.png)

## Cost Estimation

- Cost of each operator computed as described in Chapter 12

- Need statistics of input relations

  - E.g. number of tuples, sizes of tuples

- Inputs can be results of sub-expressions

  - Need to estimate statistics of expression results

    - To do so, we require additional statistics

      - E.g. number of distinct values for an attribute

- More on cost estimation later
