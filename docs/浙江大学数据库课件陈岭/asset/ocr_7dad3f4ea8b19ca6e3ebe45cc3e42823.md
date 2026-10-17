# # Unnesting

The transformation of a nested relation into a form with fewer (or no) relation-valued attributes us called **unnesting**.

+   E.g.
+   select title, A as author, publisher.name as pub_name, publisher.branch as pub_branch, K.keyword
+   from books as B, unnest(B.author_array ) as A (author ),
+   unnest (B.keyword_set ) as K (keyword )