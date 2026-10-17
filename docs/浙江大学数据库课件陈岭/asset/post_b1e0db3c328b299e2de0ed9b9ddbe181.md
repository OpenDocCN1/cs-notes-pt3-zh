

## Checking Referential Integrity on Database Modification (cont.)

**Delete.** If a tuple, $t_1$, is deleted from $r_1$, the system must compute the set of tuples in $r_2$ that reference $t_1$:

$$\sigma_\alpha = \{t[r_2]\}$$

> 如果r2中存在与r1中被删记录匹配的元组

If this set is **NOT** empty, then

- either the delete command is rejected as an error, or
- the tuples in $t_2$ that references $t_1$ **must themselves be deleted** (*cascading* (多级) deletions are possible).

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_259_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_259_1.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_259_2.png)

## Database Modification (Cont.)

Update. There are two cases:

- If a tuple $t_2$ is updated in relation $r_2$ and the update modifies values for foreign key \(\alpha\), then a test similar to the insert case is made:
  - Let \(t_2'\) denote the new value of tuple \(t_2\). The system must ensure that
    
    $$t_2'[\alpha] \in \Pi_\kappa(r_1)$$

## Referential Integrity in SQL

Primary and candidate keys and foreign keys can be specified as part of the SQL create table statement:

- The **primary key** clause lists attributes that comprise the primary key.
- The **unique key** clause lists attributes that comprise a **candidate key**.
- The **foreign key** clause lists the attributes that comprise the foreign key and the name of the relation referenced by the foreign key.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_261_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_261_1.png)

## Referential Integrity in SQL(cont.)

- **By default**, a foreign key references **the primary key attributes of the referenced table:**
  - *foreign key (account-number) references account*

- **Short form** for specifying a single column as foreign key:
  - *account-number char (10) references account*

- Reference columns in the referenced table can be **explicitly specified**
  - but must be declared as primary/candidate keys:
  - ... foreign key *(account-number)* references *account (account-number)*

名字可以不同

## Integrity constraint in SQL – Example

```
create table customer
(customer-name	char(20),
customer-street	varchar(30),
customer-city varchar(30),
primary key (customer-name));
create table branch
(branch-name varchar(15),
branch-city	varchar(30),
assets		integer,
primary key (branch-name));
```

## Referential Integrity in SQL – Example

```
create table *account*
    (*account-number* char(10),
     *branch-name* char(15),
     *balance* integer,
     primary key (*account-number*),
     **foreign key** (*branch-name*) **references** *branch*);
```

```
create table *depositor*
    (*customer-name* char(20),
     *account-number* char(10),
     primary key (*customer-name*, *account-number*),
     **foreign key** (*account-number*) **references** *account*,
     **foreign key** (*customer-name*) **references** *customer*);
```

## Cascading Actions in SQL

```
create table *account*(
    ...
    foreign key(*branch-name*) references *branch*
        [ *on delete cascade* ]
        [ *on update cascade* ]
    ... );
```

- Due to the on delete cascade clauses, if a delete of a tuple in *branch* results in referential-integrity constraint violation, the delete “cascades” to the *account* relation, deleting the tuple in *account* that refers to the *branch* which was deleted.
- Cascading updates are similar.

## Cascading Actions in SQL (Cont.)

- If there is a chain of foreign-key dependencies across multiple relations, with on delete cascade specified for each dependency, a deletion or update at one end of the chain can propagate across the entire chain.
- But, if a cascading update or delete causes a constraint violation that cannot be handled by a further cascading operation, the system aborts the transaction.
- As a result, all the changes caused by the transaction and its cascading actions are undone.

