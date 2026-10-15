# Tag Libraries

+   - JSP introduces a method of extending JSP tags, called "tag libraries".
+     - These libraries allow addition of tags similar to `jsp:include` or `jsp:forward`,
+     - but with different prefixes other than `jsp:` and with additional features.

```
```jsp
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/sql" prefix="sql" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<sql:query var="rs" dataSource="jdbc/sample">
    select id, username, password, email from tbl_user
</sql:query>
<head>
    <title>DB Test</title>
</head>
<body>
    <h2>Results</h2>
    <c:forEach var="row" items="${rs.rows}">
        ID ${row.id}<br/>
        Name ${row.username}<br/>
        Password ${row.password}<br/>
        email ${row.email}<br/>
    </c:forEach>
</body>
</html>
```
```