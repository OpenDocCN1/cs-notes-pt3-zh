
## Embedded SQL (Cont.)

- Example:
  - From within a host language, find the ID and name of students who have completed more than the number of credits stored in variable credit_amount in the host language

- Specify the query in SQL as follows:

```
EXEC SQL
declare c cursor for
select ID, name
from student
where tot_cred > :credit_amount
END_EXEC
```

- The variable c (used in the cursor declaration) is used to identify the query

## Embedded SQL (Cont.)

The open statement for our example is as follows:

```
EXEC SQL open c ;
```

This statement causes the database system to execute the query and to save the results within a temporary relation. The query uses the value of the host-language variable credit-amount at the time the open statement is executed.

The fetch statement causes the values of one tuple in the query result to be placed on host language variables.

```
EXEC SQL fetch c into :si, :sn END_EXEC
```

Repeated calls to fetch get successive tuples in the query result

## Embedded SQL (Cont.)

- A variable called SQLSTATE in the SQL communication area (SQLCA) gets set to ‘02000’ to indicate no more data is available
- The close statement causes the database system to delete the temporary relation that holds the result of the query.

```
EXEC SQL close c ;
```

Note: above details vary with language. For example, the Java embedding defines Java iterators to step through result tuples.

## Updates Through Embedded SQL

- Embedded SQL expressions for database modification (**update**, **insert**, and **delete**)
- Can update tuples fetched by cursor by declaring that the cursor is for update
    
    EXEC SQL
    
    declare c cursor for
    select *
    from instructor
    where dept_name = ‘Music’
    for update
- We then iterate through the tuples by performing **fetch** operations on the cursor (as illustrated earlier), and after fetching each tuple we execute the following code:
    
    update instructor
    set salary = salary + 1000
    where current of c

## Extensions to SQL

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_198_0.png)

## Functions and Procedures

- SQL:1999 supports functions and procedures
  - Functions/procedures can be written in SQL itself, or in an external programming language (e.g., C, Java).
  - Functions written in an external languages are particularly useful with specialized data types such as images and geometric objects.
    - Example: functions to check if polygons overlap, or to compare images for similarity.
  - Some database systems support **table-valued functions**, which can return a relation as a result.
- SQL:1999 also supports a rich set of imperative constructs, including
  - Loops, if-then-else, assignment
- Many databases have proprietary procedural extensions to SQL that differ from SQL:1999.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_199_0.png)

## SQL functions (Cont.)

- **Compound statement: begin ... end**
  - May contain multiple SQL statements between **begin** and **end**.
- **returns** -- indicates the variable-type that is returned (e.g., integer)
- **return** -- specifies the values that are to be returned as result of invoking the function
- SQL function are in fact **parameterized views** that generalize the regular notion of views by allowing parameters.

## Table Functions

- SQL:2003 added functions that return a relation as a result

- Example: Return all instructors in a given department
**create function** *instructor_of* (*dept_name* **char**(20))
**returns table** (
*ID* **varchar**(5),
*name* **varchar**(20),
*dept_name* **varchar**(20),
*salary* **numeric**(8,2))
**return table**
(*select ID, name, dept_name, salary*
**from** *instructor*
**where** *instructor.dept_name = instructor_of.dept_name*)

- Usage
**select ***
**from table** (*instructor_of* ( ‘Music’ ))
