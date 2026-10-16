# 4.10.3 Reference Counts,Shared and Recursive Lists

Sharing of sublists:

+   - saving storage.
+   - consistency.

To facilitate specification, extend the definition of a list to allow for naming of sublist. E.g.: A=(a, (b,c)), Z=(b,c) ➔ A=(a, Z(b, c)) and to be consistent, A is written as A(a, Z(b, c)).