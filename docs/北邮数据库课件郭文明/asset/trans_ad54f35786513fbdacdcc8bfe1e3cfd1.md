

## 3.1 嵌入式 SQL

使用 SQL 嵌入主语言时，必须解决以下三个问题：

- 1. 区分 SQL 语句与主语言语句，以 `EXEC SQL` 开始。
- 2. 数据库工作单元和程序工作单元之间的通信。  
  SQL 语句可以使用主语言中的程序变量（简称主变量）。这些变量名前加冒号（`:`）作为标志，以区别于字段名。这些变量需要在 `BEGIN DECLARE SECTION` 和 `END DECLARE SECTION` 语句之间声明。  
  主语言中不能引用数据库中的字段变量。  
  SQL 语句执行后，系统需要向应用程序反馈若干信息，这些信息会被送到 SQL 通信区 SQLCA。SQLCA 使用 `EXEC SQL INCLUDE` 语句进行定义。
- 3. 一个 SQL 语句原则上可以生成或处理一组记录，而主语言一次只能处理一条记录，因此必须协调这两种处理方式。这通过游标来解决。

### 嵌入式 SQL 的执行

预处理器将嵌入的 SQL 语句从主程序命令中分离出来，并将其转换为相应的主语言语句。例如：

- 1. 在 UNIX 环境下，程序员创建包含 SQL 的 `main.pc` 源程序。
- 2. Oracle 程序员调用预编译器：
  `proc iname=main.pc`  
  生成 `main.c`，其中的 SQL 语句会被纯 C 语句（Oracle 运行时库函数）替换。
- 3. 编译主语言程序：  
  `cc -c main.c`，生成 `main.o` 目标文件。
- 4. 连编生成可执行文件。

![](img/ffd1e1f008d7fcbd0b52f1e6bcb7a952_224_0.png)

### 3.1.1 C 语言中的嵌入式 SQL

```
#include <stdio.h>
#include "prompt.h"
exec sql include sqlca;  /*声明通讯区*/
char cid_prompt[]="请输入顾客号:";
int main()
{
    exec sql begin declare section;
        char cust_id[5],cust_name[14];
        float cust_discnt;
        char user_name[20],user_pwd[20];
    exec sql end declare section;
    /*声明变量*/
    exec sql whenever sqlerror goto report_error;
    exec sql whenever not found goto notfound;
    /*出错处理*/
    strcpy(user_name,"mytest");
    strcpy(user_pwd,"test");
    exec sql connect :user_name
        identified by :user_pwd; /*连接*/
    while((prompt(cid_prompt,1,cust_id,4))>=0)
    {
        exec sql select cname,discnt
            into :cust_name,:cust_discnt
            from customers where cid=:cust_id;
        exec sql commit work;
        printf("顾客名: %s 折扣率: %5.1f\n",
            cust_name,cust_discnt);
        continue;
    notfound: printf("没找到 %s,继续\n",cust_id);
    }  /*根据输入的顾客ID查询顾客信息*/
    exec sql commit release; /*正常释放连接*/
    return 0;

    report_error:
        print_dberror(); /*出错信息*/
        exec sql rollback release; /*释放连接*/
        return 1;
}
```

- 区分 SQL 语句与 C 语言语句  
  嵌入的 SQL 语句以 **EXEC SQL** 开始，以分号（`;`）结束。  
  例：

  `exec sql select cname,discnt`  
  `into :cust_name,:cust_discnt`  
  `from customers where cid=:cust_id;`

- 嵌入式 SQL 语句与 C 语言之间的数据传递  
  宿主变量（宿主变量出现在 SQL 语句中时，前面加 `:` 以区别于列名）  
  C 变量既可以用在 C 语句中，也可以用在 SQL 语句中，用来在两者之间传递数据。

- 宿主变量的声明

在嵌入式 SQL 语句中使用宿主变量时，必须先声明它们；按照通常的方式将其声明为 C 变量，并将其放在以下标识语句之间：

```
EXEC SQL BEGIN DECLARE SECTION
EXEC SQL END DECLARE SECTION
```

例：`exec sql begin declare section;`

```
char cust_id[5]='c001';
char cust_name[14];
float cust_discnt;
exec sql end declare section;
```

- 在 SQL 中建立连接和释放连接

在嵌入式 SQL 程序开始运行时，程序面临着与交互式用户相同的问题：如何与数据库建立连接。

```
例: exec sql begin declare section; /*声明变量*/
char user_name[10],user_pwd[10];
exec sql end declare section;
strcpy(user_name,'mytest');    /*变量赋值*/
strcpy(user_pwd,'test');
exec sql connect :user_name
    identified by :user_pwd;  /*Oracle连接*/
```

例：`exec sql commit release;/*Oracle断开连接*/`  
`exec sql rollback release;/*Oracle断开连接*/`

### 3.1.2 游标

- SQL 与主语言之间操作方式的协调  
  SQL：一次处理一个集合。  
  C 语言：一次处理一条记录。
  - 游标：在查询结果的记录集合中移动的指针。  
  如果一个 SQL 语句返回单个元组，则不需要游标。  
  如果一个 SQL 语句返回多个元组，则需要使用游标。
  - 不需要游标的数据操作
- 结果是一个元组的 `select` 语句

```
exec sql select cname,discnt
into :cust_name,:cust_discnt
from customers where cid=:cust_id;
```

- 需要游标的数据操作

当 `select` 语句的结果中包含多个元组时，可以使用游标逐个访问这些元组。

活动集：`select` 语句返回的元组集合。

当前行：活动集中当前正在处理的行。游标就是指向当前行的指针。

游标分类：

- 滚动游标：游标的位置可以前后移动，可以在活动集中获取任意元组。
- 非滚动游标：只能按顺序在活动集中获取下一个元组。
- 更新游标：数据库会锁定游标指向的当前行；当程序读取下一行数据时，解锁当前行并锁定下一行数据。

- 定义一个游标，使其对应一个 `select` 语句

**DECLARE** 游标名 [**SCROLL**] **CURSOR**  
**FOR** select 语句 [**for update [of 列表名]**]

`for update` 可选项表示该游标可用于修改和删除当前行。

- 打开一个游标，执行游标对应的查询，查询结果集即为该游标的活动集。

**OPEN** 游标名

游标声明之后仍然不是活动状态。在程序开始检索信息之前，需要执行 SQL 的 `OPEN` 语句打开游标。游标打开后，可以使用提取（`fetch`）操作从游标中每次检索一行。程序完成检索后，应关闭游标。

- 在活动集中将游标移动到特定行，并将该行数据取出，存放到相应的宿主变量中。  
  `FETCH [NEXT | PRIOR | FIRST | LAST | CURRENT | RELETIVE n | ABSOLUTE n]` 游标名 `INTO [宿主变量表]`
- 关闭游标，释放活动集及其占用的资源。需要再次使用该游标时，执行 `open` 语句。  
  `CLOSE` 游标名
- 删除游标，之后便不能再对该游标执行 `open` 语句。  
  `FREE` 游标名

