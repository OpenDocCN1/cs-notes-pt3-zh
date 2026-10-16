# Metadata (Cont)

+   Database metadata

```
DatabaseMetaData dbmd = conn.getMetaData();
// Arguments to getColumns: Catalog, Schema-pattern, Table-pattern,
// and Column-Pattern
// Returns: One row for each column; row has a number of attributes
// such as COLUMN_NAME, TYPE_NAME
// The value null indicates all Catalogs/Schemas.
// The value "" indicates current catalog/schema
// The value "%" has the same meaning as SQL like clause
```

```
ResultSet rs = dbmd.getColumns(null, "univdb", "department", "%");
while (rs.next()) {
  System.out.println(rs.getString("COLUMN_NAME"),
  rs.getString("TYPE_NAME"));
}
```

+   And where is this useful?

![](bbox=[0.05, 0.02, 0.25, 0.15])