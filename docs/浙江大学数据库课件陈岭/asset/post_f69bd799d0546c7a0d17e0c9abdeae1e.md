

## (a) Privileges in SQL

- **select**: allows read access to relation, or the ability to query using the view
- **Example:** To grant users U₁, U₂, and U₃ select and insert authorization on the *branch* relation:
  - SQL: `grant select, insert on branch to U₁, U₂, U₃;`
- **insert**: the ability to insert tuples
- **update**: the ability to update using the SQL update statement
- **delete**: the ability to delete tuples.
- **references**: ability to declare foreign keys when creating relations.
- **all privileges**: used as a short form for all the allowable privileges
- **all**

## (b) Roles (角色)

Roles permit **common privileges** for a class of users can be specified just once by creating a corresponding “role”.

Privileges can be granted to or revoked from roles, just like user; roles can be assigned to users, and even to other roles.

SQL:1999 supports roles

```
create role teller (出纳);
create role manager ;
grant select on branch to teller ;
grant update (balance) on account to teller ;
grant all privileges on account to manager ;
grant teller to manager ;
grant teller to alice, bob ;
grant manager to avi ;
```

## (5) Revoking Authorization in SQL

- The revoke statement is used to revoke authorization.

REVOKE<privilege list> ON <relation name or view name> FROM <user list> [ restrict | cascade ]

- Example:

revoke select on branch from U₁, U₃ cascade;

- Revocation of a privilege from a user may cause other users also to lose that privilege; referred to as cascading of the revoke.

- We can prevent cascading by specifying restrict:

revoke select on branch from U₁, U₃ restrict;

With restrict, the revoke command fails if cascading revokes are required.

## Revoking Authorization in SQL (Cont.)

- `<privilege-list>` may be **ALL**, to revoke all privileges the revokee may hold.
- If `<revokee-list>` includes **PUBLIC**, all users lose the privilege except those granted it explicitly.
- If the same privilege was granted twice to the same user by different grantees, the user may retain the privilege after the revocation.
- All privileges that depend on the privilege being revoked are also revoked.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_300_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_300_1.png)

## (6) Limitations of SQL Authorization

- SQL does not support authorization at a tuple level
  - E.g. we cannot restrict students to see only (the tuples storing) their own grades by grant.

- With the growth in Web access to databases, database accesses come primarily from application servers.
  - End users don't have database user ids, they are all mapped to the same database user id;

- All end-users of an application (such as a web application) may be mapped to a single database user.

## Limitations of SQL Authorization (cont.)

- The task of authorization in above cases **falls on the application program**, with no support from SQL
  - **Benefit:** fine grained authorizations, such as to individual tuples, can be implemented by the application.
  - **Drawback:** Authorization must be done in application code, and may be dispersed all over an application.
  - **Checking for absence of authorization loopholes becomes very difficult** since it requires reading large amounts of application code.

## 4.4 Audit Trails

- An audit trail (审计跟踪) is **a log of all changes (inserts/deletes/updates)** to the database along with information such as **which user** performed the change, and **when** the change was performed.
- Used to **track erroneous/fraudulent updates**.
- Can be implemented using triggers, but **many database systems provide direct support**.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_303_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_303_1.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_303_2.png)

