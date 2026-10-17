# (4) Null values

+   - It is possible for tuples to have a null value, denoted by *null*, for some of their attributes
+   - *null* signifies **an unknown** value or that a value does **NOT exist**.
+   - The result of **any arithmetic expression involving *null* is *null*.**
+   - **Aggregate functions simply ignore null values**
+     - Is an arbitrary decision. Could have returned null as result instead.
+     - We follow the semantics of SQL in its handling of null values
+   - For duplicate elimination and grouping, null is treated like any other value, and two nulls are assumed to be the same
+     - Alternative: assume each null is different from each other
+     - Both are arbitrary decisions, so we simply follow SQL