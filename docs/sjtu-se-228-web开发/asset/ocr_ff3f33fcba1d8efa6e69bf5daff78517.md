+   - A JSP tag is somewhat like an HTML tag.
+     - JSP tags can have a "start tag", a "tag body" and an "end tag".
+     - JSP tags do not use `<%`, but just the `<` character.

```
<some:tag>
  body
</some:tag>
```

```
<some:tag/>
```

```
<HTML>
  <BODY> Going to include index.jsp...<BR>
    <jsp:include page="index.jsp"/>
  </BODY>
</HTML>
```