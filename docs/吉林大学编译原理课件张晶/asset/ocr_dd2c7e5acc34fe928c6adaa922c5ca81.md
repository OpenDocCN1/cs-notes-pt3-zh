# 4. 类型的语义表示

结构体和联合体

| Size | Kind | RecBody |

+   - Kind=structTy 表示结构体类型
+   - Kind=unionTy表示联合体类型

RecBody的内部表示如下

| Name | Type | Off | Link |

Name表示域名
Type指向域的类型
Off表示纪录域相对于结构体类型分配的内存块起始地址的偏移量，对于联合类型而言，所有的域名标识符的起始偏移都是相同的，所以可以省略；
Link指向下一个域名标识符内部表示的指针