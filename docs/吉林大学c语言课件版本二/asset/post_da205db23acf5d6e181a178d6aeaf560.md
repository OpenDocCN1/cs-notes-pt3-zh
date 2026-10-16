
/* p 多项式尾 */
while (p!=NULL) {
    adds( p->exp , p->coef , r );
    p = p->next;
    r=r->next;
}
/* q 多项式尾 */
while (q!=NULL) {
    adds( q->exp , q->coef , r );
    q = q->next;
    r=r->next;
}
/* 释放哨兵变量 */
r = s;
s = s->next;
free(r);
return s ;
}

## 本章小结

- 本章讲述十分重要的动态数据结构
  - 动态数据结构概念
  - 各种简单的动态数据结构
    - 栈
    - 队列
    - 链表
    - 树
    - 图

重点掌握动态数据结构的操作

## 作业

- ① 12.1
- ② 12.2
- ③ 12.3
- ④ 12.9
- ⑤ 12.45

## 第一章 基本知识

- 程序设计语言分类
- 程序执行
- 巴克斯范式(BNF)
  - 写出具体文法的BNF
  - 写出BNF确定的语言
- PAD图
  - 流程图到PAD的转换

## 第二章 数据信息

- 基本符号
  - 标识符
- 数据
  - 浮点类型
  - 整数类型
  - 字符类型
  - 布尔类型
  - 枚举类型

## 第三章 简单程序

- 变量的基本概念
  - 声明、形态、地址、初始化
- 表达式
- 语句
  - 赋值语句
  - 类型转换
  - 格式输入输出

## 第四章 函数

- 函数
  - 函数声明
    - 返回类型
    - 函数名
    - 参数列表
    - 函数体
      - return 语句
  - 函数执行的过程
  - 函数原型
  - 逐步求精的程序设计思想

## 第五章 流程控制

- 顺序结构
- 分支结构
  - if
  - if else
  - switch
- 循环语句
  - while
  - do-while
  - for

## 打印100以内素数

开始

for (i=2;i<=100;i++)

prime(i)?

打印 i

结束

prime(i)

flag = true

for (j=i/2;j>=2;j--)

i%j == 0

flag = false

return flag

用实数数组存储多项式，数组的i个元素存储多项式的i次幂的系数，如多项式

5.7x⁵+10.8x³+0.49x²+2.7表示为

| 0 | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| 2.7 | 0 | 0.49 | 10.8 | 0 | 5.7 |

编一个函数, 计算上述存储方式的多项式的值。

Cal(float[] [])

读入x

rs=0

for (i=0; i<=MAXexp; i++)

return rs

结束

tmp=a[1][i]

for (j=1; j<=a[0][i]; j++)

tmp=tmp*x

rs=rs+tmp

## 第八章 再论函数

- C中参数的传递规则
- 指针作参数——swap函数
- 数组作参数
- 返回指针的函数
- 递归程序设计
  - 递归出口
  - 递归程序分类：间接、直接
  - 递归执行过程

## 第九章 程序开发和结构化程序设计

- 自顶向下逐步求精算法
- 受限排列组合
  - 穷举法
  - 试探法
  - 八皇后问题
  - Debuijn环

## 9.1

```
do{
    a=c;
    if(x<y){
        a=b;
        x=x+1;
    }else{
        if(x>y){
            a=d;
            y=y-1;
        }else
            break;
    }
}while(1);
```

## 9.20

- 5=4+1
- 5=3+2
- 5=3+1+1
- 5=2+2+1
- 5=2+1+1+1
- 5=1+1+1+1+1

## 函数F

- #define L 21
- int a[L];
- void F(int sum, int upbound, int pos)

## F(int sum, int upbound, int pos)

打印分解结果,即数组a

sum
==0

```
for (i=sum;
i>=8;
i++ )
```

i<=
upbound

```
a[pos]=i
```

```
F(sum-i,i,pos+1)
```

结束

```
void F(int sum,int upbound,int pos){
    if(sum==0){            //print the expression
        printf("%d=",a[0]);
        for(int j=1;j<pos-1;j++)
            printf("%d+",a[j]);
        printf("%d",a[pos-1]);
        printf("\n");
        return;
    }
    for(int i=upbound;i>=1;i--){
        if(i<=upbound){
            a[pos]=i;
            F(sum-i,i,pos+1);
        }
    }
}
```

```
void main(){
    int m;
    printf("please input an integer(<20):");
    scanf("%d",&m);
    for(int j=0;j<L;j++)
        a[j]=0;
    a[0]=m;
    F(m,m-1,1);
    printf("\n");
}
```

## 第十章 文件

- 文件的基本概念
- C中对文件的操作
  - 文件打开、关闭
  - 字符读写
  - 字符串读写
  - 数据块读写
  - 格式块读写
  - 定位文件读写指针

## 第十一章 结构体与共用体

- 结构体类型
- 结构体指针
- 结构体在函数中的应用
  - 指针
  - 参数
  - 返回值

## 第十二章 动态数据结构

- 动态变量
  - 申请、释放
- 动态数据结构
  - 栈、队列
  - 链表
  - 树
    - 二叉检索树
  - 图

## 12.2

| 循环 | 递归 |
|---|---|
| ```c
int len(struct tr *x){
    int L=0;
    struct tr *tp=x;
    while(tp!=NULL){
        L++;
        tp=tp->n;
    }
    return L;
}
``` | ```c
int len(struct tr *x){
    if(x==NULL)
        return 0;
    else
        return len(x->n)+1;
}
``` |
