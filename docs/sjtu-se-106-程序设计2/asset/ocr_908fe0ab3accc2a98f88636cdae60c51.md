# Some problem areas

+   - **Casts**
+     - Sometimes no-op, sometimes not (e.g., multiple inheritance)
+   - **Lack of garbage collection**
+     - Memory management is error prone
+       - Constructors, destructors are helpful though
+   - **Objects allocated on stack**
+     - Better efficiency, interaction with exceptions
+     - BUT assignment works badly, possible dangling ptrs
+   - **Overloading**
+     - Too many code selection mechanisms?
+   - **Multiple inheritance**
+     - Efforts at efficiency lead to complicated behavior