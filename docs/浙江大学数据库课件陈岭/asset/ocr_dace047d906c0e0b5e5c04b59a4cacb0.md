# （5） String Operations

+   - SQL includes a **string-matching operator** for comparisons on character strings. Patterns are described using two special characters（通配符）:
+     - `%` - matches any substring. (like `*` in file system)
+     - `_` - matches any character. (like `?` in file system)

> 可实现模糊匹配
> 
> （置于where中，且必须与LIKE连用）