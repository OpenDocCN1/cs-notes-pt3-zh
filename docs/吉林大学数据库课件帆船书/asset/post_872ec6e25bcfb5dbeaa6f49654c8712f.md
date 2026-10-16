
## BCNF Decomposition (Cont.)

- *course* is in BCNF
  - How do we know this?
- *building, room_number* → *capacity* holds on *class-1*
  - but {*building, room_number*} is not a superkey for *class-1*.
  - We replace *class-1* by:
    - *classroom* (*building, room_number, capacity*)
    - *section* (*course_id, sec_id, semester, year, building, room_number, time_slot_id*)
- *classroom* and *section* are in BCNF.

## Third Normal Form: Motivation

- There are some situations where
  - BCNF is not dependency preserving, and
  - efficient checking for FD violation on updates is important
- Solution: define a weaker normal form, called Third Normal Form (3NF)
  - Allows some redundancy (with resultant problems; we will see examples later)
  - But functional dependencies can be checked on individual relations without computing a join.
  - There is always a lossless-join, dependency-preserving decomposition into 3NF.

## 3NF Example

Relation dept_advisor.

- dept_advisor (s_ID, i_ID, dept_name)
  - F = {s_ID, dept_name → i_ID, i_ID → dept_name}
- Two candidate keys: s_ID, dept_name, and i_ID, s_ID
- R is in 3NF
  - s_ID, dept_name → i_ID
    - s_ID, dept_name is a superkey
  - i_ID → dept_name
    - dept_name is contained in a candidate key

## Redundancy in 3NF

- There is some redundancy in this schema
- Example of problems due to redundancy in 3NF:
  - R = (J, K, L)
  - F = {JK → L, L → K}

| J | L | K |
| j₁ | l₁ | k₁ |
| j₂ | l₁ | k₁ |
| j₃ | l₁ | k₁ |
| null | l₂ | k₂ |

- repetition of information (e.g., the relationship l₁, k₁)
  - (i_ID, dept_name)
- need to use null values (e.g., to represent the relationship l₂, k₂ where there is no corresponding value for J)
  - (i_ID, dept_name) if there is no separate relation mapping instructors to departments

## Testing for 3NF

- Optimization: Need to check only FDs in F, need not check all FDs in F⁺.
- Use attribute closure to check for each dependency α → β, if α is a superkey.
- If α is not a superkey, we have to verify if each attribute in β is contained in a candidate key of R.
  - This test is rather more expensive, since it involves finding candidate keys.
  - Testing for 3NF has been shown to be NP-hard.
  - Interestingly, decomposition into third normal form (described shortly) can be done in polynomial time.

## 3NF Decomposition Algorithm

```
Let F_c be a canonical cover for F;
 i := 0;
 for each functional dependency α → β in F_c do
  if none of the schemas R_j, 1 ≤ j ≤ i contains αβ
   then begin
    i := i + 1;
    R_i := αβ;
   end
 if none of the schemas R_j, 1 ≤ j ≤ i contains a candidate key for R
 then begin
  i := i + 1;
  R_i := any candidate key for R;
 end;
 /* Optionally, remove redundant relations */
 repeat
  if any schema R_j is contained in another schema R_k
   then /* delete R_j */
    R_j := R_i;
    i := i - 1;
 until no more R_j's can be deleted;
 return (R_1, R_2, ..., R_i);
```

## 3NF Decomposition Algorithm (Cont.)

Above algorithm ensures:
- Each relation schema R_i is in 3NF.
- Decomposition is dependency preserving and lossless-join.
- Proof of correctness is at end of this presentation (click here).

## 3NF Decomposition: An Example

- Relation schema: *cust_banker_branch = (customer_id, employee_id, branch_name, type)*
- The functional dependencies for this relation schema are:
  1. *customer_id, employee_id → branch_name, type*
  2. *employee_id → branch_name*
  3. *customer_id, branch_name → employee_id*
- We first compute a canonical cover:
  - *branch_name* is extraneous in the r.h.s. of the 1st dependency.
  - No other attribute is extraneous, so we get F_C =
    - *customer_id, employee_id → type*
    - *employee_id → branch_name*
    - *customer_id, branch_name → employee_id*

## 3NF Decomposition Example (Cont.)

- The **for** loop generates the following 3NF schemas:
  - (customer_id, employee_id, type)
  - (employee_id, branch_name)
  - (customer_id, branch_name, employee_id)
  - Observe that (customer_id, employee_id, type) contains a candidate key of the original schema, so no further relation schema needs to be added.
- At the end of the for loop, detect and delete schemas, such as (employee_id, branch_name), which are subsets of other schemas.
  - The result will not depend on the order in which FDs are considered.
- The resultant simplified 3NF schema is:
  - (customer_id, employee_id, type)
  - (customer_id, branch_name, employee_id)
