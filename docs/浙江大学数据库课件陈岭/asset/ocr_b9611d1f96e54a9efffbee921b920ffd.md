# Array and Multiset Types in SQL

+   - Example of array and multiset declaration:
+   
+     ```sql
+     create type Publisher as
+         (name          varchar(20),
+          branch        varchar(20))
+   
+     create type Book as
+         (title         varchar(20),
+          author-array  varchar(20) array [10],
+          pub-date      date,
+          publisher     Publisher,
+          keyword-set   varchar(20) multiset )
+   
+     create table books of Book
+     ```

+   - Similar to the nested relation books, but with array of authors instead of set