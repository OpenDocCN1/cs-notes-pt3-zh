+   - RowSet
+     - FilteredRowSet
+       ```
+       RowSetFactory rowSetFactory = 
+           RowSetProvider.newFactory();
+       rowset = rowSetFactory.createFilteredRowSet();
+       Range range = new Range();
+       rowset.setFilter(range);
+       ```