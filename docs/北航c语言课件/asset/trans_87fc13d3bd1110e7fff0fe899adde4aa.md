
- 按二进制格式读写文件（基本方式字符+“b”）:

  b 辅助说明，按二进制格式读写文件。

  ```
  例如：
  fp=fopen("mydata.txt","rb");
  ```

- 同时进行读写文件（基本方式字符+“b”+“+”）:

  辅助说明，可同时进行读和写文件。

  | 方式 | 说明 |
  | --- | --- |
  | r+ | 已存在的文件打开到开头，用于同时读和写。 |
  | w+ | 与w相同，但可同时读和写。 |
  | a+ | 与a相同，但可同时读和写。 |

  ```
  例如： fp=fopen("mydata.txt","r+");
  ```

例：

```c
#include <stdio.h>
main()
{ FILE *fp;
if((fp=fopen("mydata.txt","r"))==NULL)
{ printf("file not found.");
exit(0);
}
else
{ printf("file opened ok!");
fclose(fp); }
}
```

常使用此方法打开一个文件

exit函数的功能是关闭所有文件，终止程序运行。exit(0)为正常终止程序

说明：

```c
fp=fopen("mydata.txt","r");
if(fp == NULL)
```

程序运行结果：如果磁盘上存在文件 mydata.txt，屏幕上会显示 `file open ok`，否则屏幕上显示 `file not found`。

## 二、文件的关闭函数（fclose函数）

关闭文件

(1) 调用方式：

```
fclose(文件指针);

fclose(file_pointer)
```

(2) 功能：关闭由文件指针指定的文件，防止它被误用；同时把缓冲区中的数据（未装满缓冲区的数据）输出到磁盘上，释放文件指针。

文件上的所有操作一旦完成，就必须立即关闭文件。这可以确保与文件相关的所有未处理信息从缓冲区中冲洗出来，并断开与该文件的所有链接。

例如：

```c
FILE *fp;
fp=fopen("output.dat","r+");
...... /* 进行读写操作 */
fclose(fp);
```

注意： fopen函数和fclose函数总是成对出现的。无fclose函数时会导致部分数据丢失！

## § 13.4 文件的读写函数

文件上的输入/输出操作

### 一、fputc函数 和 fgetc函数

这两个函数是以字符为单位进行文件读写的函数。

这两个函数类似于**getchar**和**putchar**函数，每次处理一个字符。

**1. fputc函数**

一般调用形式：

```
fputc(字符常量或变量,文件指针);
fputc(character constant or variable,file_pointer)
```

功能：把指定字符存入文件指针所指的文件中。
如果输出失败，则返回一个EOF（-1）。
（EOF是在stdio.h文件中定义的符号常量，值为-1）

例如:`fputc(ch,fp);`（其中ch为字符变量，fp为文件指针）
含义：将ch的值输出到fp所指向的文件中去。
将字符变量ch中的字符写入与FILE指针fp关联的文件中。如果输出失败，fputc将返回一个EOF标记。

**2. fgetc函数**

一般调用形式：

```
字符变量=fgetc(文件指针);

ch=fgetc(fp);
```

功能：从文件指针所指文件中读一个字符赋给指定的字符变量。当遇文件结束符，返回一个文件结束标志EOF（-1）。

每次执行fgetc或fputc操作，文件指针都会移动一个字符位置。当到达文件末尾时，fgetc将返回一个文件结束标志EOF。

> 例如：`ch=fgetc(fp);`
>
> 其中ch为字符变量，fp为文件指针。
>
> 含义：从fp所指向的文件中读入1个字符赋给字符变量ch。

例：阅读程序。

```c
#include "stdio.h"
#define NULL 0
main()
{
    FILE *fp;
    int count=0; char c;
    if((fp=fopen("file.txt","r")) ==NULL)
        { printf("Can’t Open File \n"); exit(0); }
    do {c=fgetc(fp); count++;} while(c!=EOF);
    count--;
    printf("count=%d\n",count);
    fclose(fp);
}
```

这是读一个文本文件中字符，并判断文件是否结束的常用方法

若文件file.txt的内容是: abcd1234ABCD

输出结果： 12

## 关于文件读写状态的检测

输入/输出操作期间的错误处理

函数调用是否成功，可有两种手段来检测：

- 1. 由函数的返回值来确定
- 2. 用文件状态检测函数feof、ferror、fclearerr

feof(fp):测试fp所指向的文件的位置是否是文件尾。若已到达文件尾，函数返回非零值，若没有到达文件尾，则返回0。

当指针fp指向文件末尾后，feof(fp)将返回一个非零值，否则返回0。

常用程序段:

```c
while(!feof(fp))
{......}
```

```c
if(feof(fp))
printf("End of data.\n");
```

ferror(fp):测试对fp所指向的文件的操作是否出错。若出错，函数返回非零值，否则返回0。

```c
if(ferror(fp)!=0)
printf("An error has occurred.\n");
```

fclearerr(fp):使ferror和feof函数值置0。

### 二、 fread函数和fwrite函数

一般调用形式：

```
fread(buffer,size,count,fp);
```

```
fwrite(buffer,size,count,fp);
```

其中：

buffer:是一个指针(起始地址)。
对fread来说，它是读入数据的存放地址。
对fwrite来说，它是输出数据的地址。

size:要读写的字节数。

count:要进行读写多少个size字节的数据项。

功能：对fp所指的文件读写buffer所指的size*count个字节数据。

例如： `fread(f,4,2,fp);`（其中f是实型数组名）

**例1 把数组a写入文件fa.txt;再从fa读入数组b。**

```c
#include "stdio.h"
main()
{
    FILE* fp;
    int a[100]={1,5,6,78,21,34,67,87,23},b[100], i ;
    fp=fopen("fa.txt","wb");
    fwrite(a,sizeof(a),1,fp);
    /* fwrite(a,sizeof(int),100,fp);*/
    fclose(fp);
    fp=fopen("fa.txt","rb");
    fread(b,sizeof(a),1,fp);
    for(puts(""),i=0;i<10;i++) printf("%6d",b[i]);
    fclose(fp);
}
```

### 三、fprintf 函数和 fscanf 函数

这两个函数是进行格式读写文件的函数。

一般调用形式：

```
fprintf(文件指针,格式字符串,输出表列);
```

```
fscanf(文件指针,格式字符串,输入地址);
```

```
fprintf(fp, "control string", list);
```

*fp* 是一个与已打开用于写入的文件相关联的文件指针。
*控制字符串*包含列表中各项的输出规格。
*列表*可以包含变量、常量和字符串。

