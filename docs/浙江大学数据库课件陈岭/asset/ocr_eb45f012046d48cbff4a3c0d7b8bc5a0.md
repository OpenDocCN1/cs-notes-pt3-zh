# # (11) Assignment Operation

The assignment operation (←) provides a convenient way to express complex queries.

+   Write query as a sequential program consisting of
+   a series of assignments
+   followed by an expression whose value is displayed as a result
+   of the query.

+   Assignment must always be made to a **temporary** relation variable.

+   Example: Write \( r \div s \) as
+   \( temp1 \leftarrow \Pi_{R-S}(r) \)
+   \( temp2 \leftarrow \Pi_{R-S}((temp1 \times s) - \Pi_{R-S,S}(r)) \)
+   \( result = temp1 - temp2 \)

+   The result to the **right** of the ← is **assigned** to the relation variable
+   on the **left** of the ←.

+   May use variable in subsequent expressions.