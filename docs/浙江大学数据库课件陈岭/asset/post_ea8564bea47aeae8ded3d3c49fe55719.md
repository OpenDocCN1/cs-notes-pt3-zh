
## (1) E-R Diagram With Composite, Multivalued, and Derived Attributes

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_362_0.png)

## (3) Roles

- Entity sets of a relationship need NOT be distinct.
  E.g. **Recursive relationship set** (自环联系集)

- **Role:** the function that an entity plays in a relationship.

  The labels “manager” and “worker” are called **roles**; they specify how employee entities interact via the works-for relationship set.

- Role labels are optional, and are used to clarify semantics of the relationship.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_364_0.png)

## (4) Express the Cardinality Constraints (基数约束)

We express cardinality constraints by drawing either a directed line (→), signifying “one,” or an undirected line (—), signifying “many,” between the relationship set and the entity set.

### (a) One-to-one relationship:

- E.g. A customer is associated with at most one loan via the relationship _borrower_. A loan is associated with at most one customer via _borrower_. (一个客户最多只能借一笔贷款，一笔贷款只能由一个客户借)

- 注：一个联系集的类型取决于被表达对象的语义约束及设计者的意图

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_365_0.png)

### (b) One-To-Many Relationship

In the one-to-many relationship, a loan is associated with at most one customer via borrower, a customer is associated with several (including 0) loans via borrower. (一个客户可借多笔贷款，一笔贷款只能由一个客户借)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_366_0.png)

### (c) Many-To-One Relationships

In a many-to-one relationship, a loan is associated with several (including 0) customers via borrower, a customer is associated with at most one loan via borrower.

(一个客户最多只能借一笔贷款，一笔贷款可由多个客户共借)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_367_0.png)

## (5) Participation of an Entity Set in a Relationship Set（参与约束）

- **Total participation (全参与) (indicated by double line):**
- **Partial participation (部分参与):** some entities may not participate in any relationship in the relationship set.

- 映射基数约束（**Mapping cardinality constraints**）限定了一个实体与发生关联的另一端实体可能关联的数目上限。
- 全参与和部分参与约束，则反映了一个实体参与关联的数目下限：**0**次，还是至少**1**次。

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_369_0.png)

## (8) Binary Vs. Non-Binary Relationships

### (a) Some relationships that appear to be non-binary may be better represented using binary relationships

- E.g. A ternary relationship *parents*, relating a child to his/her father and mother, is best replaced by two binary relationships, *father* and *mother*.

  `parents(he, she, child) => father(he, child), mother(she, child)`

- Using two binary relationships allows partial information (e.g. only the mother being known).

- But there are **some relationships** that are naturally non-binary.

  E.g. **works-on(employee, branch, job)**

### (b) Converting Non-Binary Relationships to Binary Form

In general, any non-binary relationship can be represented using binary relationships by creating an **artificial entity set**.

- Replace non-binary relationship _R_ between entity sets A, B and C by an entity set _E_, and three new relationship sets:
- Create a special identifying attribute for _E_
- Add any attributes of _R_ to _E_
- For each relationship (_aᵢ_, _bᵢ_, _cᵢ_) in _R_, create _R<sub>A</sub>_, _R<sub>B</sub>_, _R<sub>C</sub>_

E.g.:

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_373_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_373_1.png)

## 6.5 Weak Entity Sets (弱实体集)

An entity set that does not have a primary key is referred to as a weak entity set.

**Vs strong entity set (强实体集)**

E.g.: 还贷登记表 payment(pay-num, pay-date, pay-amount). 假设为了清楚起见，pay-num 按对应的每项贷款分别编号（都从 1, 2, 3... 开始），这样，pay-num 就不是码，并且该实体集没有码。故 payment 是弱实体集。pay-num is a discriminator or partial key (分辨符或部分码).

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_374_0.png)
