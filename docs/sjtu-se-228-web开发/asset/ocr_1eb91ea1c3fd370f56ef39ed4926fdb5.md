+   - The target of the form is "SaveName.jsp", which saves the user's name in the session.

```
<%
    String name = request.getParameter( "username" );
    session.setAttribute( "theName", name );
%>
<HTML>
    <BODY>
        <A HREF="NextPage.jsp">Continue</A>
    </BODY>
</HTML>
```

+   - The SaveName.jsp saves the user's name in the session, and puts a link to another page, NextPage.jsp.