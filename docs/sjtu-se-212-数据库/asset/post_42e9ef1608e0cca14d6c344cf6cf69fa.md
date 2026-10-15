
## Cardinality Constraints

- We express cardinality constraints by drawing either a directed line (→), signifying “one,” or an undirected line (–), signifying “many,” between the relationship set and the entity set.
- One-to-one relationship:
  - A student is associated with at most one instructor via the relationship advisor
  - A student is associated with at most one department via stud_dept

## One-to-One Relationship

- one-to-one relationship between an instructor and a student
  - an instructor is associated with at most one student via advisor
  - and a student is associated with at most one instructor via advisor

![](img/5285b20d8f5a79969a3f150d38beebfc_158_0.png)

## One-to-Many Relationship

one-to-many relationship between an instructor and a student

- an instructor is associated with several (including 0) students via advisor
- a student is associated with at most one instructor via advisor.

![](img/5285b20d8f5a79969a3f150d38beebfc_159_0.png)

## Many-to-One Relationships

In a many-to-one relationship between an instructor and a student,

- an instructor is associated with at most one student via advisor.
- and a student is associated with several (including 0) instructors via advisor

![](img/5285b20d8f5a79969a3f150d38beebfc_160_0.png)

## Many-to-Many Relationship

- An instructor is associated with several (possibly 0) students via advisor
- A student is associated with several (possibly 0) instructors via advisor

![](img/5285b20d8f5a79969a3f150d38beebfc_161_0.png)

## Participation of an Entity Set in a Relationship Set

- Total participation (indicated by double line): every entity in the entity set participates in at least one relationship in the relationship set
  - E.g., participation of section in sec_course is total
    - every section must have an associated course
- Partial participation: some entities may not participate in any relationship in the relationship set
  - Example: participation of instructor in advisor is partial

![](img/5285b20d8f5a79969a3f150d38beebfc_162_0.png)

## Alternative Notation for Cardinality Limits

- Cardinality limits can also express participation constraints

![](img/5285b20d8f5a79969a3f150d38beebfc_163_0.png)

## ER Diagram with a Ternary Relationship

![](img/5285b20d8f5a79969a3f150d38beebfc_164_0.png)

Entity: `instructor`

- **ID**
- name
- salary

Entity: `project`

- ...

Entity: `student`

- **ID**
- name
- tot_cred

![](img/5285b20d8f5a79969a3f150d38beebfc_164_1.png)

## Cardinality Constraints on Ternary Relationship

- We allow at most one arrow out of a ternary (or greater degree) relationship to indicate a cardinality constraint
- E.g., an arrow from proj_guide to instructor indicates each student has at most one guide for a project
- If there is more than one arrow, there are two ways of defining the meaning.
  - E.g., a ternary relationship R between A, B and C with arrows to B and C could mean
    1. each A entity is associated with a unique entity from B and C or
    2. each pair of entities from (A, B) is associated with a unique C entity, and each pair (A, C) is associated with a unique B
  - Each alternative has been used in different formalisms
  - To avoid confusion we outlaw more than one arrow

![](img/5285b20d8f5a79969a3f150d38beebfc_166_0.png)

How about doing an ER design interactively on the board?
Suggest an application to be modeled.

## Weak Entity Sets

- An entity set that does not have a primary key is referred to as a **weak entity set**.
- The existence of a weak entity set depends on the existence of an **identifying entity set**
  - It must relate to the identifying entity set via a total, one-to-many relationship set from the identifying to the weak entity set
  - **Identifying relationship** depicted using a double diamond
- The **discriminator** (or partial key) of a weak entity set is the set of attributes that distinguishes among all the entities of a weak entity set.
- The primary key of a weak entity set is formed by the primary key of the strong entity set on which the weak entity set is existence-dependent, plus the weak entity set’s discriminator.
