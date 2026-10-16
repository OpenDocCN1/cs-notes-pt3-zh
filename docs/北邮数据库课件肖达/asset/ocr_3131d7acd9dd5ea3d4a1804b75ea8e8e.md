# Data model: a big map

+   - <Row, Column, Timestamp> triple for key - lookup, insert, and delete API
+   - Arbitrary “columns” on a row-by-row basis
+     - Column family:qualifier. Family is heavyweight, qualifier lightweight
+     - Column-oriented physical store- rows are sparse!
+   - Does not support a relational model
+     - No table-wide integrity constraints
+     - No multirow transactions

![](bbox=[0.002, 0.631, 0.978, 0.906])