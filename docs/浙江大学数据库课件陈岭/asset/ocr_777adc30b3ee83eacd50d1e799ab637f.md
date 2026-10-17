# Prepared Statement

+   - Prepared statement allows queries to be compiled and executed multiple times with different arguments

```
PreparedStatement pStmt = conn.prepareStatement(
    “insert into account values(?,?,?)”);
pStmt.setString(1, "A_9732");
pStmt.setString(2, "Perryridge");
pStmt.setInt(3, 1200);
pStmt.executeUpdate();

pStmt.setString(1, "A_9733");
pStmt.executeUpdate();
```

+   - Beware: If value to be stored in database contains a **single quote** or **other special character**, prepared statements work fine, but creating a query string and executing it directly would result in a syntax error!