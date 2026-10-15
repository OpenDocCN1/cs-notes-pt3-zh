# Debugging

+   - Debugging = Find + Fix + *Experience*
+     - example#1: "*Segmentation fault*"
+     - example#2:
+       test.c:6: error: expected `,` or `;` before `struct`
+       test.c:9: warning: data definition has no type or storage class
+       test.c:9: warning: type defaults to `int` in
+       ...
+       test.c:16: warning: (near initialization for `s`)
+       test.c:16: error: storage size of `s` isn't known
+       test.c:21: error: request for member `a` in something not a structure or union
+       test.c:16: warning: unused variable `s`