
## Figure 11.15

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_572_0.png)

## Partitioned Hashing

- Hash values are split into segments that depend on each attribute of the search-key: $(A_1, A_2, \ldots, A_n)$ for $n$-attribute search-key.
- Example: $n = 2$, for customer, search-key being (customer-street, customer-city)

  | search-key value | hash value |
  | --- | --- |
  | (Main, Harrison) | 101 111 |
  | (Main, Brooklyn) | 101 001 |
  | (Park, Palo Alto) | 010 010 |
  | (Spring, Brooklyn) | 001 001 |
  | (Alma, Palo Alto) | 110 010 |

- To answer equality query on single attribute, need to look up multiple buckets. Similar in effect to grid files.

## Grid Files

- Structure used to speed the processing of general multiple search-key queries involving one or more comparison operators.
- The grid file has a single grid array and one linear scale for each search-key attribute. The grid array has a number of dimensions equal to the number of search-key attributes.
- Multiple cells of the grid array can point to the same bucket.
- To find the bucket for a search-key value, locate the row and column of its cell using the linear scales and follow the pointer.

### Example Grid File for account

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_575_0.png)

### Queries on a Grid File

A grid file on two attributes A and B can handle queries of all following forms with reasonable efficiency:

- $(a_1 \le A \le a_2)$
- $(b_1 \le B \le b_2)$
- $(a_1 \le A \le a_2 \land b_1 \le B \le b_2)$.

E.g., to answer $(a_1 \le A \le a_2 \land b_1 \le B \le b_2)$, use linear scales to find corresponding candidate grid array cells, and look up all the buckets pointed to from those cells.

### Grid Files (Cont.)

- During insertion, if a bucket becomes full, a new bucket can be created if more than one cell points to it.
  - The idea is similar to extendable hashing, but on multiple dimensions.
  - If only one cell points to it, either an overflow bucket must be created or the grid size must be increased.
- Linear scales must be chosen to uniformly distribute records across cells.
  - Otherwise there will be too many overflow buckets.
- Periodic re-organization to increase grid size will help.
  - But reorganization can be very expensive.
- Space overhead of the grid array can be high.
- R-trees (Chapter 23) are an alternative.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_578_0.png)

## Chapter 12: Query Processing

Database System Concepts, 6th Ed.
©Silberschatz, Korth and Sudarshan
See www.db-book.com for conditions on re-use

- Overview
- Measures of Query Cost
- Selection Operation
- Sorting
- Join Operation
- Other Operations
- Evaluation of Expressions

### Basic Steps in Query Processing

1. Parsing and translation
2. Optimization
3. Evaluation

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_580_0.png)

### Basic Steps in Query Processing (Cont.)

- Parsing and translation
  - Translate the query into its internal form. This is then translated into relational algebra.
  - Parser checks syntax, verifies relations.
- Evaluation
  - The query-execution engine takes a query-evaluation plan, executes that plan, and returns the answers to the query.

### Basic Steps in Query Processing: Optimization

A relational algebra expression may have many equivalent expressions.

- E.g., $\sigma_{salary<75000}(\Pi_{salary}(instructor))$ is equivalent to  
  $\Pi_{salary}(\sigma_{salary<75000}(instructor))$

Each relational algebra operation can be evaluated using one of several different algorithms.

- Correspondingly, a relational-algebra expression can be evaluated in many ways.

An annotated expression specifying a detailed evaluation strategy is called an evaluation-plan.

- E.g., can use an index on salary to find instructors with salary < 75000,
- or can perform a complete relation scan and discard instructors with salary ≥ 75000.
