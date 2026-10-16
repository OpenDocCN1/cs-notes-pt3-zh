# Creation of Collection Values

+   - Array construction
+   
+   array ['Silberschatz','Korth','Sudarshan']

+   - Multisets
+   
+   multiset ['computer', 'database', 'SQL']

To create a tuple of the type defined by the books relation:

('Compilers', array['Smith','Jones'],
 new Publisher ('McGraw-Hill','New York'),
 multiset ['parsing', 'analysis' ])

To insert the preceding tuple into the relation books

insert into books
values
('Compilers', array['Smith','Jones'],
 new Publisher ('McGraw-Hill','New York'),
 multiset ['parsing', 'analysis' ]);