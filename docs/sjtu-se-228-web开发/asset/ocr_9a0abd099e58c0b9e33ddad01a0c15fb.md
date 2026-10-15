+   - NextPage.jsp shows how to retrieve the saved name.
+     ```html
+     <HTML>
+     <BODY> Hello, <%= session.getAttribute( "theName" ) %>
+     </BODY>
+     </HTML>
+     ```
+   - If you bring up two different browsers (not different windows of the same browser),
+     - or run two browsers from two different machines, you can put one name in one browser and another name in another browser, and both names will be kept track of.
+   - The session is kept around until a timeout period.
+     - Then it is assumed the user is no longer visiting the site, and the session is discarded.