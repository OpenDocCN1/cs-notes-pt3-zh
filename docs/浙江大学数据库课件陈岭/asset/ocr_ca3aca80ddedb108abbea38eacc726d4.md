# 4.5 Embedded SQL（嵌入式SQL）

+   - SQL的功能不完备性。（计算，资源……）
+   - The SQL standard defines embeddings of SQL in a variety of programming languages such as Pascal, PL/I, Fortran, C, and Cobol.
+   - A language in which SQL queries are embedded is referred to as a **Host language（宿主语言）**, and the SQL structures permitted in the host language comprise *embedded SQL*.
+   - **EXEC SQL** statement is used to identify embedded SQL request to the preprocessor:
+   
+     **EXEC SQL** `<embedded SQL statement>` **END_EXEC**
+   
+     Note: this varies by language. E.g. the Java embedding use:
+   
+     **# SQL { ... } ;**