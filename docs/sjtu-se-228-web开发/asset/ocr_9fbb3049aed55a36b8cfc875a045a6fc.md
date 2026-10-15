+   - RowSet
+     - JdbcRowSet – online

```
public class AccessDB {
    private JdbcRowSet rowset;
    public AccessDB(String url, String user, String pwd)
        throws SQLException {
        RowSetFactory rowSetFactory =
            RowSetProvider.newFactory();
        JdbcRowSet rowset =
            rowSetFactory.createJdbcRowSet();
        rowset.setUrl(
            "jdbc:mysql://localhost:3306/sample_one");
        rowset.setUsername("root");
        rowset.setPassword("12345678");
        rowset.setCommand("SELECT * FROM tbl_user");
        rowset.execute();
    }
}
```