# # Array and Multiset Types in SQL

+   - Example of array and multiset declaration:

```
```sql
create type Publisher as
(name varchar(20),
branch varchar(20));

create type Book as
(title varchar(20),
author_array varchar(20) array [10],
pub_date date,
publisher Publisher,
keyword-set varchar(20) multiset);

create table books of Book;
```
```