
## Authorization Specification in SQL

- The **grant** statement is used to confer authorization:

  ```text
  grant <privilege list>
  on <relation name or view name> to <user list>
  ```

- <user list> is:
  - a user-id
  - **public**, which allows all valid users the privilege granted
  - a role (more on this later)

- Granting a privilege on a view does not imply granting any privileges on the underlying relations.

- The grantor of the privilege must already hold the privilege on the specified item (or be the database administrator).

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_157_0.png)

## Privileges in SQL

- **select**: allows read access to relation, or the ability to query using the view

- Example: grant users U₁, U₂, and U₃ select authorization on the `instructor` relation:

  ```text
  grant select on instructor to U₁, U₂, U₃
  ```

- **insert**: the ability to insert tuples

- **update**: the ability to update using the SQL update statement

- **delete**: the ability to delete tuples

- **all privileges**: used as a short form for all the allowable privileges

## Revoking Authorization in SQL

- The **revoke** statement is used to revoke authorization.

  ```text
  revoke <privilege list>
  on <relation name or view name> from <user list>
  ```

- Example:

  ```text
  revoke select on branch from U₁, U₂, U₃
  ```

- `<privilege-list>` may be **all** to revoke all privileges the revokee may hold.

- If `<revokee-list>` includes **public**, all users lose the privilege except those granted it explicitly.

- If the same privilege was granted twice to the same user by different grantees, the user may retain the privilege after the revocation.

- All privileges that depend on the privilege being revoked are also revoked.

## Roles

- `create role instructor;`
- `grant instructor to Amit;`

Privileges can be granted to roles:

- `grant select on takes to instructor;`

Roles can be granted to users, as well as to other roles:

- `create role teaching_assistant;`
- `grant teaching_assistant to instructor;`

Instructor inherits all privileges of teaching_assistant.

Chain of roles:

- `create role dean;`
- `grant instructor to dean;`
- `grant dean to Satoshi;`

## Authorization on Views

- **create view** `geo_instructor` **as**

  ```text
  select *
  from instructor
  where dept_name = 'Geology';
  ```

- **grant select on** `geo_instructor` **to** `geo_staff`

- Suppose that a `geo_staff` member issues:

  ```text
  select *
  from geo_instructor
  ```

- What if:
  - `geo_staff` does not have permissions on `instructor`?
  - creator of view did not have some permissions on `instructor`?

## Other Authorization Features

- **references** privilege to create foreign key
  - `grant references (dept_name) on department to Mariano;`
  - why is this required?
- transfer of privileges
  - `grant select on department to Amit with grant option;`
  - `revoke select on department from Amit, Satoshi cascade;`
  - `revoke select on department from Amit, Satoshi restrict;`
- Etc. Read Section 4.6 for more details we have omitted here.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_162_0.png)

## End of Chapter 4

## Figure 4.01

| ID | name | dept_name | tot_cred |
|---|---|---|---|
| 00128 | Zhang | Comp. Sci. | 102 |
| 12345 | Shankar | Comp. Sci. | 32 |
| 19991 | Brandt | History | 80 |
| 23121 | Chavez | Finance | 110 |
| 44553 | Peltier | Physics | 56 |
| 45678 | Levy | Physics | 46 |
| 54321 | Williams | Comp. Sci. | 54 |
| 55739 | Sanchez | Music | 38 |
| 70557 | Snow | Physics | 0 |
| 76543 | Brown | Comp. Sci. | 58 |
| 76653 | Aoi | Elec. Eng. | 60 |
| 98765 | Bourikas | Elec. Eng. | 98 |
| 98988 | Tanaka | Biology | 120 |

## Figure 4.02

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_164_0.png)

| ID | course_id | sec_id | semester | year | grade |
| --- | --- | --- | --- | --- | --- |
| 00128 | CS-101 | 1 | Fall | 2009 | A |
| 00128 | CS-347 | 1 | Fall | 2009 | A- |
| 12345 | CS-101 | 1 | Fall | 2009 | C |
| 12345 | CS-190 | 2 | Spring | 2009 | A |
| 12345 | CS-315 | 1 | Spring | 2010 | A |
| 12345 | CS-347 | 1 | Fall | 2009 | A |
| 19991 | HIS-351 | 1 | Spring | 2010 | B |
| 23121 | FIN-201 | 1 | Spring | 2010 | B+ |
| 44553 | PHY-101 | 1 | Fall | 2009 | C- |
| 45678 | CS-101 | 1 | Fall | 2009 | F |
| 45678 | CS-101 | 1 | Spring | 2010 | B+ |
| 45678 | CS-319 | 1 | Spring | 2010 | B |
| 54321 | CS-101 | 1 | Fall | 2009 | A- |
| 54321 | CS-190 | 2 | Spring | 2009 | B+ |
| 55739 | MU-199 | 1 | Spring | 2010 | A- |
| 76543 | CS-101 | 1 | Fall | 2009 | A |
| 76543 | CS-319 | 2 | Spring | 2010 | A |
| 76653 | EE-181 | 1 | Spring | 2009 | C |
| 98765 | CS-101 | 1 | Fall | 2009 | C- |
| 98765 | CS-315 | 1 | Spring | 2010 | B |
| 98988 | BIO-101 | 1 | Summer | 2009 | A |
| 98988 | BIO-301 | 1 | Summer | 2010 | null |
