# # Nesting

+   Nesting is the opposite of unnesting, creating a collection-valued attribute

+   NOTE: SQL:1999 does not support nesting

+   Nesting can be done in a manner similar to aggregation, but using the function collect() in place of an aggregation operation, to create a multiset

+   To nest the flat-books relation on the attribute keyword:

+   select title, author, Publisher (pub_name, pub_branch ) as publisher, collect (keyword) as keyword_set from flat-books groupby title, author, publisher

+   To nest on both authors and keywords: select title, collect (author ) as author_set, Publisher (pub_name, pub_branch) as publisher, collect (keyword ) as keyword_set from flat-books group by title, publisher