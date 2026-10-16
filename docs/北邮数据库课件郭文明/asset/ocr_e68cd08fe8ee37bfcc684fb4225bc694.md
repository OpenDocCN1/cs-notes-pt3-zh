# 3.1.1 C语言中嵌入式SQL

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