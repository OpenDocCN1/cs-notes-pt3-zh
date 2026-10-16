# 顺序表（SeqList）的类型定义

```
#define List_init_Size 100   //初始分配量
#define Listincrement 10   //分配增量
typedef struct
{
    Elemtype * elem;    //存储空间基址
    int length;         //当前元素个数
    int listszie ;      //当前分配的存储容量
} sqlist;
```

```
L.length = 0;
L.listsize= List_init_Size;
return OK;
}
```