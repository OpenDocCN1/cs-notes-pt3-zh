# 文件开启+模式注意-死循环

```
//测试程序，当读/写模式开启文件时，常出现死循环的问题。
//更新一个文本文件，将其中所有出现的字符'c'变为'd'。
#include"stdio.h"
int main()
{ FILE *fp;
    char ch;
    if((fp=fopen("file.txt","r+")) ==NULL)
        printf("Check File Path!\n");
    else {
        ch=fgetc(fp);
        while(!feof(fp))
        {
            if(ch == 'c') {
                printf("c");//跟踪
                ch='d';
                fseek(fp,-1L,1);//回上一位
                fputc(ch,fp);
            }
        }
    }
}
```

第一个参数file指针
第二个参数移动的偏移量
第三个参数移动到哪里
分别用3个宏
SEEK_SET 既0 文件开头
SEEK_CUR 既1 文件当前位置
SEEK_END 既2 文件结尾