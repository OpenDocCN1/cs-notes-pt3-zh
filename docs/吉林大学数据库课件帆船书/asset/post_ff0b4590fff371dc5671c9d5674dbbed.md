
## Keys

- Let K ⊆ R
- *K* is a **superkey** of *R* if values for *K* are sufficient to identify a unique tuple of each possible relation *r(R)*
  - Example: {ID} and {ID,name} are both superkeys of *instructor*.
- Superkey *K* is a **candidate key** if *K* is minimal
  Example: {ID} is a candidate key for *Instructor*
- One of the candidate keys is selected to be the **primary key**.
  - which one?
- **Foreign key** constraint: Value in one relation must appear in another
  - **Referencing** relation
  - **Referenced** relation
  - Example – *dept_name* in *instructor* is a foreign key from *instructor* referencing *department*

## Schema Diagram for University Database

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_37_0.png)

## Relational Query Languages

- Procedural vs. non-procedural, or declarative
- “Pure” languages:
  - Relational algebra
  - Tuple relational calculus
  - Domain relational calculus
- The above 3 pure languages are equivalent in computing power
- We will concentrate in this chapter on relational algebra
  - Not Turing-machine equivalent
  - consists of 6 basic operations

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_38_0.png)

## Select Operation – selection of rows (tuples)

- Relation r

| A | B | C | D |
|---|---|---|---|
| α | α | 1 | 7 |
| α | β | 5 | 7 |
| β | β | 12 | 3 |
| β | β | 23 | 10 |

σ_A=B ∧ D > 5 (r)

| A | B | C | D |
|---|---|---|---|
| α | α | 1 | 7 |
| β | β | 23 | 10 |

## Project Operation – selection of columns (Attributes)

- Relation r:

| A | B | C |
|---|---|---|
| α | 10 | 1 |
| α | 20 | 1 |
| β | 30 | 1 |
| β | 40 | 2 |

- Π_A,C (r)

| A | C |
|---|---|
| α | 1 |
| α | 1 |
| β | 1 |
| β | 2 |

=

| A | C |
|---|---|
| α | 1 |
| β | 1 |
| β | 2 |

## Union of two relations

- Relations r, s:

| A | B |
|---|---|
| α | 1 |
| α | 2 |
| β | 1 |

*r*

| A | B |
|---|---|
| α | 2 |
| β | 3 |

*s*

- r ∪ s:

| A | B |
|---|---|
| α | 1 |
| α | 2 |
| β | 1 |
| β | 3 |

## Set difference of two relations

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_42_0.png)

- Relations r, s:

| A | B |
|---|---|
| α | 1 |
| α | 2 |
| β | 1 |

| A | B |
|---|---|
| α | 2 |
| β | 3 |

- r - s:

| A | B |
|---|---|
| α | 1 |
| β | 1 |

## Set intersection of two relations

- Relation r, s:

| A | B |
|---|---|
| α | 1 |
| α | 2 |
| β | 1 |

*r*

| A | B |
|---|---|
| α | 2 |
| β | 3 |

*s*

- r ∩ s

| A | B |
|---|---|
| α | 2 |

Note: r ∩ s = r − (r − s)

## joining two relations -- Cartesian-product

- Relations r, s:

| A | B |
|---|---|
| α | 1 |
| β | 2 |

*r*

| C | D | E |
|---|---|---|
| α | 10 | a |
| β | 10 | a |
| β | 20 | b |
| γ | 10 | b |

*s*

- r x s:

| A | B | C | D | E |
|---|---|---|---|---|
| α | 1 | α | 10 | a |
| α | 1 | β | 10 | a |
| α | 1 | β | 20 | b |
| α | 1 | γ | 10 | b |
| β | 2 | α | 10 | a |
| β | 2 | β | 10 | a |
| β | 2 | β | 20 | b |
| β | 2 | γ | 10 | b |

## Cartesian-product – naming issue

- Relations r, s:

| A | B |
|---|---|
| α | 1 |
| β | 2 |

*r*

| B | D | E |
|---|---|---|
| α | 10 | a |
| β | 10 | a |
| β | 20 | b |
| γ | 10 | b |

*s*

- r x s:

| A | r.B | s.B | D | E |
|---|---|---|---|---|
| α | 1 | α | 10 | a |
| α | 1 | β | 10 | a |
| α | 1 | β | 20 | b |
| α | 1 | γ | 10 | b |
| β | 2 | α | 10 | a |
| β | 2 | β | 10 | a |
| β | 2 | β | 20 | b |
| β | 2 | γ | 10 | b |

## Renaming a Table

- Allows us to refer to a relation, (say E) by more than one name.
- ρ_X(E)
- returns the expression E under the name X

- Relations r

| A | B |
| --- | --- |
| α | 1 |
| β | 2 |

*r*

- r × ρ_s(r)

| r.A | r.B | s.A | s.B |
| --- | --- | --- | --- |
| α | 1 | α | 1 |
| α | 1 | β | 2 |
| β | 2 | α | 1 |
| β | 2 | β | 2 |

## Composition of Operations

- Can build expressions using multiple operations

- Example: σ_{A=C} (r × s)

- r x s

| A | B | C | D | E |
| --- | --- | --- | --- | --- |
| α | 1 | α | 10 | a |
| α | 1 | β | 10 | a |
| α | 1 | β | 20 | b |
| α | 1 | γ | 10 | b |
| β | 2 | α | 10 | a |
| β | 2 | β | 10 | a |
| β | 2 | β | 20 | b |
| β | 2 | γ | 10 | b |

- σ_{A=C} (r × s)

| A | B | C | D | E |
| --- | --- | --- | --- | --- |
| α | 1 | α | 10 | a |
| β | 2 | β | 10 | a |
| β | 2 | β | 20 | b |
