# # Consistency Requirements for Subtables

+   - Consistency requirements on subtables and supertables.
+     - Each tuple of the supertable (e.g. _people_) can correspond to at most one tuple in each of the subtables (e.g. _students_ and _teachers_)
+     - Additional constraint in SQL: 1999:
+       All tuples corresponding to each other (that is, with the same values for inherited attributes) must be derived from one tuple (inserted into one table).
+       - That is, each entity must have a most specific type
+       - We cannot have a tuple in _people_ corresponding to a tuple each in _students_ and _teachers_