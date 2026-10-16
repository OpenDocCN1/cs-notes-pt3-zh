# Embedded SQL

![](bbox=[0.05, 0.02, 0.18, 0.18])

+   - The SQL standard defines embeddings of SQL in a variety of programming languages such as C, C++, Java, Fortran, and PL/1,

+   - A language to which SQL queries are embedded is referred to as a host language, and the SQL structures permitted in the host language comprise embedded SQL.

+   - The basic form of these languages follows that of the System R embedding of SQL into PL/1.

+   - EXEC SQL statement is used to identify embedded SQL request to the preprocessor

```
EXEC SQL <embedded SQL statement> ;
```

Note: this varies by language:

+   - In some languages, like COBOL, the semicolon is replaced with END-EXEC

+   - In Java embedding uses # SQL { .... };