
## Querying Collection-Valued Attributes

- To find all books that have the word “database” as a keyword,

  ```sql
  select title
  from books
  where 'database' in (unnest(keyword_set))
  ```

- We can access individual elements of an array by using indices
  E.g.: If we know that a particular book has three authors, we could write:

  ```sql
  select author_array[1], author_array[2], author_array[3]
  from books
  where title = 'Database System Concepts'
  ```

- To get a relation containing pairs of the form “title, author-name”
  for each book and each author of the book

  ```sql
  select B.title, A.author
  from books as B, unnest(B.author_array) as A(author)
  ```

- To retain ordering information we add a with ordinality clause

  ```sql
  select B.title, A.author, A.position
  from books as B, unnest(B.author_array) with ordinality
  as A(author, position)
  ```

## Unnesting

The transformation of a nested relation into a form with fewer (or no) relation-valued attributes is called **unnesting**.

- E.g.

  ```sql
  select title, A as author, publisher.name as pub_name, publisher.branch as pub_branch, K.keyword
  from books as B, unnest(B.author_array) as A(author),
  unnest(B.keyword_set) as K(keyword)
  ```

## Nesting

- Nesting is the opposite of unnesting, creating a collection-valued attribute

- NOTE: SQL:1999 does not support nesting

- Nesting can be done in a manner similar to aggregation, but using the function collect() in place of an aggregation operation, to create a multiset

- To nest the flat-books relation on the attribute keyword:

  ```sql
  select title, author, Publisher(pub_name, pub_branch) as publisher, collect(keyword) as keyword_set
  from flat-books
  group by title, author, publisher
  ```

- To nest on both authors and keywords:

  ```sql
  select title, collect(author) as author_set, Publisher(pub_name, pub_branch) as publisher, collect(keyword) as keyword_set
  from flat-books
  group by title, publisher
  ```

## 1NF Version of Nested Relation

1NF version of books

| title | author | pub_name | pub_branch | keyword |
|---|---|---|---|---|
| Compilers | Smith | McGraw-Hill | New York | parsing |
| Compilers | Jones | McGraw-Hill | New York | parsing |
| Compilers | Smith | McGraw-Hill | New York | analysis |
| Compilers | Jones | McGraw-Hill | New York | analysis |
| Networks | Jones | Oxford | London | Internet |
| Networks | Frick | Oxford | London | Internet |
| Networks | Jones | Oxford | London | Web |
| Networks | Frick | Oxford | London | Web |

flat-books

## Nesting (Cont.)

Another approach to creating nested relations is to use subqueries in the **select** clause.

```sql
select title,
       array(select author
             from authors as A
             where A.title = B.title
             order by A.position) as author_array,
       Publisher(pub_name, pub_branch) as publisher,
       multiset(select keyword
                from keywords as K
                where K.title = B.title) as keyword_set
from books as B
```

## Object-Identity and Reference Types

Define a type _Department_ with a field _name_ and a field _head_ which is a reference to the type _Person_, with table _people_ as scope:

```sql
create type Department (
    name varchar(20),
    head ref(Person) scope people)
```

We can then create a table _departments_ as follows

```sql
create table departments of Department
```

We can omit the declaration **scope** _people_ from the type declaration and instead make an addition to the **create table** statement:

```sql
create table departments of Department
    (head with options scope people)
```

## User Generated Identifiers

- The type of the object-identifier must be specified as part of the type definition of the referenced table, and
- The table definition must specify that the reference is user generated

```sql
create type Person
    (name varchar(20),
     address varchar(20))
     ref using varchar(20)
create table people of Person
     ref is person_id user generated
```

- When creating a tuple, we must provide a unique value for the identifier:

  ```sql
  insert into people (person_id, name, address) values
      ('01284567', 'John', '23 Coyote Run')
  ```

- We can then use the identifier value when inserting a tuple into *departments*
  - Avoids need for a separate query to retrieve the identifier:

    ```sql
    insert into departments
        values ('CS', '01284567')
    ```
