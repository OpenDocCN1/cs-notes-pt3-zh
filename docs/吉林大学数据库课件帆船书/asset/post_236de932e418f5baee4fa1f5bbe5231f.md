
![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1209_0.png)

## Querying Collection-Valued Attributes

To find all books that have the word “database” as a keyword,

```
select title
from books
where 'database' in (unnest(keyword-set ))
```

We can access individual elements of an array by using indices

E.g.: If we know that a particular book has three authors, we could write:

```
select author_array[1], author_array[2], author_array[3]
from books
where title = 'Database System Concepts'
```

To get a relation containing pairs of the form “title, author_name” for each book and each author of the book

```
select B.title, A.author
from books as B, unnest (B.author_array) as A (author)
```

To retain ordering information we add a with ordinality clause

```
select B.title, A.author, A.position
from books as B, unnest (B.author_array) with ordinality as A (author, position)
```

## Unnesting

- The transformation of a nested relation into a form with fewer (or no) relation-valued attributes is called unnesting.
- E.g.
- select title, A as author, publisher.name as pub_name, publisher.branch as pub_branch, K.keyword
- from books as B, unnest(B.author_array) as A (author), unnest(B.keyword_set) as K (keyword)
- Result relation flat_books

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

## Nesting

- **Nesting** is the opposite of unnesting, creating a collection-valued attribute
- Nesting can be done in a manner similar to aggregation, but using the function **collect()** in place of an aggregation operation, to create a multiset
- To nest the *flat_books* relation on the attribute *keyword*:
  **select** *title*, *author*, Publisher (*pub_name*, *pub_branch* ) **as** *publisher*, **collect** (*keyword*) **as** *keyword_set*
  **from** *flat_books*
  **group by** *title*, *author*, *publisher*
- To nest on both authors and keywords:
  **select** *title*, **collect** (*author* ) **as** *author_set*, Publisher (*pub_name*, *pub_branch*) **as** *publisher*, **collect** (*keyword* ) **as** *keyword_set*
  **from** *flat_books*
  **group by** *title*, *publisher*

## Nesting (Cont.)

Another approach to creating nested relations is to use subqueries in the select clause, starting from the 4NF relation *books4*

```
select title,
    array (select author
        from authors as A
        where A.title = B.title
        order by A.position) as author_array,
    Publisher (pub_name, pub_branch) as publisher,
    multiset (select keyword
        from keywords as K
        where K.title = B.title) as keyword_set
from books4 as B
```

## Object-Identity and Reference Types

- Define a type *Department* with a field *name* and a field *head* which is a reference to the type *Person*, with table *people* as scope:
  **create type** *Department* (
    *name* **varchar** (20),
    *head* **ref** (*Person*) **scope** *people*)
- We can then create a table *departments* as follows
  **create table** *departments* **of** *Department*
- We can omit the declaration **scope** *people* from the type declaration and instead make an addition to the **create table** statement:
  **create table** *departments* **of** *Department*
  (*head* **with options** **scope** *people*)
- Referenced table must have an attribute that stores the identifier, called the **self-referential attribute**
  **create table** *people* **of** *Person*
  **ref is** *person_id* **system generated**;
