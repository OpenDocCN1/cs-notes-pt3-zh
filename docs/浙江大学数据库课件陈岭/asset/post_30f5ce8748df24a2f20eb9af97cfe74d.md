
## Embedded SQL (Cont.)

Step2: The open statement causes the query to be evaluated:

```sql
EXEC SQL OPEN c END_EXEC
```

Step3: The fetch statement causes the values of one tuple in the result of the query to be placed on host language variables.

```sql
EXEC SQL FETCH c INTO :cn, :ccity END_EXEC
```

Repeated calls to fetch of successive tuples in the query result.

A variable called SQLSTATE in the SQLCA (SQL communication area) gets set to '02000' to indicate no more data is available.

Step4: The close statement causes the database system to delete the temporary relation that holds the result of the query.

```sql
EXEC SQL CLOSE c END_EXEC
```

Note: above details vary with language. E.g. the Java embedding defines Java iterators (迭代器) to step through result tuples.

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_315_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_315_1.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_315_2.png)

### Example for embedded SQL (For Oracle Pro*C)

```c
Exec SQL include SQLCA;
//SQL通讯区，是存放语句的执行状态的数据结构，其中
// 有一个变量sqlcode指示每次执行SQL语句的返回代码（success, not_success）
Exec SQL BEGIN DECLARE SECTION;
char bn[20], bc[30];
Exec SQL END DECLARE SECTION;
Exec SQL DECLARE branch_cur CURSOR FOR
select branch_name, branch_city from branch;
......
Exec SQL OPEN branch_cur;
while (1) { Exec SQL FETCH branch_cur INTO :bn, :bc ;
if (sqlca.sqlcode<> SUCCESS) BREAK;
...... // 由宿主语句对bn, bc中的数据进行相关处理
}
Exec SQL CLOSE branch_cur;
......
```

( Pro*C程序→预编译pcc →compiler cc → linker →.exe)

### (2) Updates

#### （1）单行的修改

```c
Exec SQL BEGIN DECLARE SECTION;
char an[20];
float bal;
Exec SQL END DECLARE SECTION;
......
scanf("%s,%f", an, &bal); //读入账号及要增加的存款额
EXEC SQL update account set balance=balance + :bal
where account_number = :an;
......
```

### (2) Updates (cont.)

(2) 多行的修改: Can update tuples fetched by cursor by declaring that the cursor is for update.

```sql
Exec SQL BEGIN DECLARE SECTION;
    char an[20];
    float bal;
Exec SQL END DECLARE SECTION;
EXEC SQL DECLARE csr CURSOR FOR
    SELECT *
    FROM account
    WHERE branch_name = 'Perryridge'
    FOR UPDATE OF balance;
.......
```

#### To update tuple at the current location of cursor

```sql
EXEC SQL OPEN csr ;

while(1) {
    EXEC SQL FETCH csr INTO :an, :bn, :bal ;
    if (sqlca.sqlcode<> SUCCESS) BREAK;
    ...... // 由宿主语句对an, bn, bal中的数据进行相关处理(如打印)
    EXEC SQL update account
    set balance = balance + 100
    where CURRENT OF csr ;
}
......
EXEC SQL CLOSE csr;
......
```

Or:

```sql
EXEC SQL delete from account
where current of csr ;
```

## 3.12 ODBC

- Open Database Connectivity (ODBC)
- A standard for application program to communicate with a database server.
- application program interface (API) to
  - (1) open a connection with a database,
  - (2) send queries and updates,
  - (3) get back results.
- Applications such as GUI, spreadsheets, etc. can use ODBC

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_321_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_321_1.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_321_2.png)

## 3.12 ODBC (cont.)

### Embedded SQL vs. ODBC

- Embedded SQL: The precompiler is DBMS-specific.
- ODBC provides a standardized way for connection of database to the application programmers through API (Application Programming Interface).
- Not DBMS-specific.
- Need not precompiling.

ODBC提供了一个公共的、与具体数据库无关的应用程序设计接口API (Application Programming Interface)。所谓公共的接口API就是为开发者提供单一的编程接口，这样同一个应用程序就可以访问不同的数据库服务器。

### 使用ODBC访问数据库的方法：

- ODBC API访问数据库
- Visual C++的MFC提供了丰富的ODBC类，它们封装了大量的函数用以完成数据库的大部分应用

### 访问数据库的其他方法

- OLE DB (Object Linking and Embedding Database)，是一套通过COM (Component Object Model，组件对象模型)接口访问数据库的ActiveX底层接口技术，速度快，支持关系型和非关系型数据库，编程量大。
- ADO (ActiveX Data Objects)，基于COM，建立在OLE DB 之上，更易于使用。
- DAO (Data Access Objects)，基于Microsoft Jet引擎，访问Access数据库(即*.MDB文件)时具有很好的性能，DAO类与ODBC类相比具有很多相似之处。
