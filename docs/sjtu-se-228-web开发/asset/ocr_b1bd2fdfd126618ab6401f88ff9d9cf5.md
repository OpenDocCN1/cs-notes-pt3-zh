# CallableStatement

```
CallableStatement cstmt =
    con.prepareCall("{CALL insert_user(?, ?, ?, ?)}");
cstmt.registerOutParameter(2, java.sql.Types.INTEGER);
cstmt.setInt(1, 4);
cstmt.setString(2, "Host");
cstmt.setString(3, "Host");
cstmt.setString(4, "Host@sjtu.edu.cn");

cstmt.execute();

// Retrieve OUT parameters
String username = cstmt.getNString(2);
System.out.println(username);
```