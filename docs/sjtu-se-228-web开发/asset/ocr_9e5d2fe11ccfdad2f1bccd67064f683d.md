# Scriptlets

+   - A similar variable is "response".
+     - This can be used to affect the response being sent to the browser.
+     - For instance, you can call response.sendRedirect( anotherUrl ); to send a response to the browser that it should load a different URL.
+     - This response will actualy go all the way to the browser.
+     - The browser will then send a different request, to "anotherUrl".

```
<HTML>
<BODY>
<%
// This scriptlet declares and initializes "date"
response.sendRedirect("index3.jsp");
%>
</BODY>
</HTML>
```