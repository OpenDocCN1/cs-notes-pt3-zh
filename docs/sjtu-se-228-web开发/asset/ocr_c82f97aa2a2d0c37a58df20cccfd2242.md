# Manipulate result

+   - **RowSet**
+     - CachedRowSet
+       ```java
+       RowSetFactory rowSetFactory =
+           RowSetProvider.newFactory();
+       rowset = rowSetFactory.createCachedRowSet();
+       ```
+     - WebRowSet
+       ```java
+       RowSetFactory rowSetFactory =
+           RowSetProvider.newFactory();
+       rowset = rowSetFactory.createWebRowSet();
+       rowset.execute();
+       rowset.writeXml(System.out);
+       ```