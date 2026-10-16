
```c
fread( &v1 , sizeof(int) , 1 , f1 );
fread( &v2 , sizeof(int) , 1 , f2 );
while( !feof(f1) && !feof(f2) ) {
    if (v1 < v2) {          /* 取较小元素存入f3文件 */
        fwrite( &v1 , sizeof(int) , 1 , f3 );
        fread( &v1 , sizeof(int) , 1 , f1 );
    }else {
        fwrite( &v2 , sizeof(int) , 1 , f3 );
        fread( &v2 , sizeof(int) , 1 , f2 );
    }
}
while( !feof(f1) ) {          /* 处理f1文件尾部 */
    fwrite( &v1 , sizeof(int) , 1 , f3 );
    fread( &v1 , sizeof(int) , 1 , f1 );
}
while( !feof(f2) ) {          /* 处理f2文件尾部 */
    fwrite( &v2 , sizeof(int) , 1 , f3 );
    fread( &v2 , sizeof(int) , 1 , f2 );
}
```

### 例 10-4

在磁盘中建立一个正弦函数表文件 “sin.tab” 格式如下：

```
# THE LIST OF SIN(X)
a   SIN(a)   a   SIN(a)   a   SIN(a)   a   SIN(a)   a   SIN(a)
0  0.0000  1  0.0175  2  0.0349  3  0.0523  4  0.0698
5  0.0872  6  0.1045  7  0.1219  8  0.1392  9  0.1564
... ...
```

到 359° 为止

```c
void main(){
    int u,v;
    FILE *f;
    if (( f=fopen("sin.tab","w"))==NULL){  /*打开文件*/
        printf("can not open file \"sin.tab\"\n");
        exit(0);
    }
    fprintf( f , "%40c THE LIST OF SIN(X)\n" , ',' ); /* 表头 */
    fprintf( f , "a   SIN(a)   a   SIN(a)   a   SIN(a)" );
    fprintf( f , "  a   SIN(a)   a   SIN(a)\n" );
    for ( v=0; v<=71; v++ ) {                  /* 表体 */
        for ( u=0; u<=4; u++ )
            fprintf(f,"%5d %.4f",v*5+u,sin((v*5+u)*PAI/180));
        fprintf(f,"\n");
    }
    fclose(f);
}
```

### 例10-5

设磁盘上有两个 text 文件，

- NAME.DAT 上为一个人员名单；
- ADDRESS.DAT 上是对应 NAME.DAT 文件上每个人的家庭地址。
- 编一个程序，在磁盘上生成一个姓名、地址、电话号码表文件 NAMEADDR.TAB，其中每个人的电话号码在终端上随机录入。

该程序总体上一个人一个人的处理。对每个人来讲：

- 1. 先从NAME.DAT上读入一个姓名；然后从 ADDRESS.DAT上读入相应家庭地址；
- 2. 然后在终端屏幕上显示正处理的人员姓名，要求操作员键入其电话号码，并读入该电话号码；
- 3. 最后把姓名、地址、电话号码作为一行送入文件 NAMEADDR.TAB上。

```
开始

初始化文件

NAME未结束

结束

读 NAME => name0 ; ADDRESS => addr

显示 name0

读入电话号码>tel

name0、addr、tel写入文件 NAMEADDR.TAB
```

```c
void main(){
    FILE *name;    /*名字源文件指针*/
    FILE *address; /*地址源文件指针*/
    FILE *nameaddr;  /*目标文件指针 */
    char name0[8],addr[30],tel[10];
    if ((name=fopen("NAME.DAT","r"))==NULL){
        printf("can not open source file 'NAME.DAT'\n");
        exit(0);
    }
    if ((address=fopen("ADDRESS.DAT","r"))==NULL){
        printf("can not open source file 'ADDRESS.DAT'\n");
        exit(0);
    }
}
```

### 本章小结

- 本章主要介绍了文件的概念及其操作。
- 重点掌握文件打开、关闭、读写等操作。

### 作业

① 10.8

## 第十一章 结构体

- 结构体
- 结构体与函数
- 本章小结
- 作业

| 名字 | 年龄 | 出生时间 | 年 | 月 | 日 | 性别 |
|---|---|---|---|---|---|---|

| 名字 | 发射时间 | 年 | 月 | 日 |
| 重量 | 直径 | 轨道半径 | 与赤道夹角 |  |

- 数组可描述由同类型子数据项组成的数据。
- 结构体可描述由不同类型子数据项组成的数据

### 结构体

- 结构体类型
  - 结构体类型是分量的集合
  - 分量也称成员、成分、域

| 结构体类型定义形式A | 结构体类型定义形式B |
|---|---|
| `struct {`<br>`  t id, ...,id;`<br>`  ...`<br>`  t id, ...,id;`<br>`}` | `struct sid {`<br>`  t id, ...,id;`<br>`  ...`<br>`  t id, ...,id;`<br>`}` |

### 例11-1 一个人的自然情况表
卫星数据类型

```c
enum sex { male , female };
struct date {
    int year ,  month ,  day ;
};
struct person {
    char name[10] ;
    int  age ;
    enum sex sex ;
    struct date birthdate ;
};
```

```c
struct mansatellite {
    char name[10] ;
    struct date
        launchdate ;
    float weight,
        diameter,
        orbitrad,
        angle ;
};
```

- date是一个结构体类型，包含三个成分
  - 成分year为int类型
  - 成分month为int类型
  - 成分day为int类型

![](img/2c9b154d61523ac3dc02daf316966b8e_1152_0.png)

person是一个结构体类型，包含四个成分

- 成分name为数组类型
- 成分age为int类型
- 成分sex为枚举类型
- 成分birthdate仍为一个结构体类型

| name: |  |  |
|---|---|---|
| age: |  |  |
| sex: |  |  |
| birthdate: | year: |  |
|  | month: |  |
|  | day: |  |

### mansatellite是一个结构体类型，包含六个成分

| name: |  |  |
|---|---|---|
| launchdate: | year: |  |
|  | month: |  |
|  | day: |  |
| weight: |  |  |
| diameter: |  |  |
| orbitrad: |  |  |
| angle: |  |  |

### 结构体类型引用

在struct后跟以结构体标签，称为“结构体类型引用”。在例11-1的结构体类型定义的意义下：

```c
struct date
struct person
struct mansatellite
```

都是结构体类型引用，使用它们将分别标记相应结构体定义。
