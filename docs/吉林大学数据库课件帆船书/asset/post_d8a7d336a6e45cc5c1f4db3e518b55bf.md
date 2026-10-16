
![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_25_0.png)

## Database Users and Administrators

Database

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_26_0.png)

## Database System Internals

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_28_0.png)

## Database Architecture

The architecture of a database systems is greatly influenced by the underlying computer system on which the database is running:

- Centralized
- Client-server
- Parallel (multi-processor)
- Distributed

## History of Database Systems

- 1950s and early 1960s:
  - Data processing using magnetic tapes for storage
    - Tapes provided only sequential access
  - Punched cards for input
- Late 1960s and 1970s:
  - Hard disks allowed direct access to data
  - Network and hierarchical data models in widespread use
  - Ted Codd defines the relational data model
    - Would win the ACM Turing Award for this work
    - IBM Research begins System R prototype
    - UC Berkeley begins Ingres prototype
  - High-performance (for the era) transaction processing

## History (cont.)

- 1980s:
  - Research relational prototypes evolve into commercial systems
    - SQL becomes industrial standard
  - Parallel and distributed database systems
  - Object-oriented database systems
- 1990s:
  - Large decision support and data-mining applications
  - Large multi-terabyte data warehouses
  - Emergence of Web commerce
- Early 2000s:
  - XML and XQuery standards
  - Automated database administration
- Later 2000s:
  - Giant data storage systems
    - Google BigTable, Yahoo PNuts, Amazon, ..

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_29_0.png)

## End of Chapter 1

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_31_0.png)

## Chapter 2: Intro to Relational Model

## Example of a Relation

| ID | name | dept_name | salary |
|---|---|---|---|
| 10101 | Srinivasan | Comp. Sci. | 65000 |
| 12121 | Wu | Finance | 90000 |
| 15151 | Mozart | Music | 40000 |
| 22222 | Einstein | Physics | 95000 |
| 32343 | El Said | History | 60000 |
| 33456 | Gold | Physics | 87000 |
| 45565 | Katz | Comp. Sci. | 75000 |
| 58583 | Califeri | History | 62000 |
| 76543 | Singh | Finance | 80000 |
| 76766 | Crick | Biology | 72000 |
| 83821 | Brandt | Comp. Sci. | 92000 |
| 98345 | Kim | Elec. Eng. | 80000 |

attributes (or columns)

tuples (or rows)

## Attribute Types

- The set of allowed values for each attribute is called the **domain** of the attribute
- Attribute values are (normally) required to be **atomic**; that is, indivisible
- The special value *null* is a member of every domain. Indicated that the value is “unknown”
- The null value causes complications in the definition of many operations

## Relation Schema and Instance

- *A₁, A₂, ..., Aₙ are attributes*
- *R = (A₁, A₂, ..., Aₙ) is a relation schema*
  Example:
  *instructor = (ID, name, dept_name, salary)*
- Formally, given sets *D₁, D₂, .... Dₙ* a **relation r** is a subset of *D₁ x D₂ x ... x Dₙ*
  Thus, a relation is a set of *n-tuples (a₁, a₂, ..., aₙ)* where each *aᵢ ∈ Dᵢ*
- The current values (**relation instance**) of a relation are specified by a table
- An element *t* of *r* is a *tuple*, represented by a *row* in a table

## Relations are Unordered

- Order of tuples is irrelevant (tuples may be stored in an arbitrary order)
- Example: *instructor* relation with unordered tuples

| ID | name | dept_name | salary |
|---|---|---|---|
| 22222 | Einstein | Physics | 95000 |
| 12121 | Wu | Finance | 90000 |
| 32343 | El Said | History | 60000 |
| 45565 | Katz | Comp. Sci. | 75000 |
| 98345 | Kim | Elec. Eng. | 80000 |
| 76766 | Crick | Biology | 72000 |
| 10101 | Srinivasan | Comp. Sci. | 65000 |
| 58583 | Califieri | History | 62000 |
| 83821 | Brandt | Comp. Sci. | 92000 |
| 15151 | Mozart | Music | 40000 |
| 33456 | Gold | Physics | 87000 |
| 76543 | Singh | Finance | 80000 |
