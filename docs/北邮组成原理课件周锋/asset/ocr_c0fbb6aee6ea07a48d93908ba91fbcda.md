# 块读写函数测试程序

```
#include<stdio.h>
#include<stdlib.h>
typedef struct node
{
    char name[20];
    double score;
    int age;
}Student;
int main(void)
{ FILE *fp;
int i;
Student s1[3]={{"liudehua",85.5,45}, {"zhangxueyou",79.3,47},
{"guofucheng",83.4,43}};
Student s2[3];
```