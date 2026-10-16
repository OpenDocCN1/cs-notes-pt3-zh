
# UML2面向对象分析与设计

# Object-Oriented Analysis & Design with UML2

谭火彬

## 第01章 上升到面向对象

## An Approach to the Object Orientation

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_1_0.png)

## 内容安排

- ☑ 第一个案例
- ☑ 课程介绍
- ☑ 对象技术
- ☑ 对象和类
- ☑ 对象技术相关原则
- ☑ 上升到面向对象

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_2_0.png)

## 内容安排

- ☑ 第一个案例
- ☑ 课程介绍
- ☑ 对象技术
- ☑ 对象和类
- ☑ 对象技术相关原则
- ☑ 上升到面向对象

## 素数问题

**素数的定义**：除了1与本身之外，不能被其他正整数除的数，叫作素数，也叫质数

按照习惯规定，1 不算素数，最小的素数是 2，其余的是 3、5、7、11、13、17、19……等等

## 由定义判断素数

对于数 n，从 i=2, 3, 4, 5...到 n−1 判断 n 能否被 i 整除，如果全部不能整除，则 n 是素数，只要有一个能除尽，则 n 不是素数，为了压缩循环次数，可将判断范围从 2 ~ n−1 改为 2 ~ sqrt(n)

## 筛选法求素数序列

筛选法：生成 2< i <n 的素数序列，设n=50

筛掉2的倍数： 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 ...

筛掉3的倍数： 2 3 5 7 9 11 13 15 17 19 21 23 25 27 29 ...

筛掉5的倍数： 2 3 5 7 11 13 17 19 23 25 29 31 35 37 41 ...

筛掉7的倍数： 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 49

留下素数序列： 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47

## 思考？

- ☑ 用结构化思维解决上述问题
- ☑ 用对象思维解决上述问题
- ☑ 将解决思路用合适的方式记录下来
- ☑ 思考：
  - ◆ 结构化思维与对象化思维有什么本质的不同？体现了怎样的思维差异？对象思想有何优势？
  - ◆ 如何表达设计思想：代码？图形？

## 结构化实现

```
//PrimerNumber.c
main(){
int *sieve,n;
int iCounter=2, iMax, i;
printf("Please input max number:");
scanf("%d", &n);
sieve=malloc((n-1)*sizeof(int));
for(i=0;i<n-1;i++) { sieve[i]=i+2; }
iMax = sqrt(n);
while (iCounter<=iMax) {
for (i=2*iCounter-2; i<n-1; i+=iCounter)
sieve[i] = 0;
iCounter++; }
for(i=0; i<n-1; i++)
if (sieve[i]!=0) printf("%d ",sieve[i]);
}
```

## 结构化小结

- ☑ 通过流程图（结构化建模）可以更清楚表达设计思想

- ☑ 针对过程的抽象
  - ◆ 过程（函数）是系统的核心，通过过程实现系统功能
  - ◆ 数据是静态的，由过程来控制对数据的访问

- ☑ 面向对象的方法如何解决呢？

## Java实现-是对象思维吗？

```
import java.lang.Math;
public class PrimerNumber{
    public static void main(String args[]) {
        int n=50;
        int sieve[]=new int[n-1];
        int iCounter=2, iMax, i;
        for(i=0;i<n-1;i++) {sieve[i]=i+2;}
        iMax=(int)Math.sqrt(n);
        while(iCounter<=iMax){
            for (i=2*iCounter-2; i<n-1; i+=iCounter)
                sieve[i]=0;
            iCounter++;
        }
        for(i=0; i<n-1; i++)
            if (sieve[i]!=0) System.out.println(sieve[i]);
    }
}
```

## 用对象思维解决问题？

筛选法：生成 2< i <n 的整数序列，设n=50

筛掉2的倍数：2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 ...

筛掉3的倍数：2 3 5 7 9 11 13 15 17 19 21 23 25 27 29 ...

筛掉5的倍数：2 3 5 7 11 13 17 19 23 ...

筛掉7的倍数：2 3 5 7 11 13 17 19 23 ...

留下素数序列：2 3 5 7 11 13 17 19 23 ...

筛子：存储源数据

过滤器：表明当前过滤因子

什么是对象？对象过滤器？记录当前正在筛选的数据

## 这才是对象思维！

象基类，为程序提供多态

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_12_0.png)

## 面向对象的编程—C++语法

```
class Item{
public:
        Item* source;
        Item (Item* src) {source=src;}
        virtual int out() {return 0;}
};

class Counter: public Item{
        int value;
public:
        int out() {return value++;}
        Counter(int v):Item(0){value=v;}
};
```

## 面向对象的编程-过滤器

```
class Filter:public Item{
    int factor;
public:
    int out(){
        while(1){
            int n=source->out();
            if (n%factor) return n;
        }
    }
    Filter(Item *src, int f):Item(src) {factor=f;}
};
```

## 面向对象的编程-筛子

```
class Sieve: public Item{
public:
    int out(){
        int n=source->out();
        source= new Filter(source, n);
        return n;
    }
    Sieve(Item *src):Item(src){}
};
```

## 验证设计方案

```
void main(){
    Counter c(2);
    Sieve s(&c);
    int next, n;
    cin>>n;
    while(1){
        next=s.out();
        if(next>n) break;
        cout<<next<<" ";
    }
    cout<<endl;
}
```

> 关键代码只有一行，筛子自己知道如何找出素数

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_16_0.png)

## 对象方法小结

- 通过UML类图（面向对象建模）可以更清楚表达设计思想，并为代码实现提供框架

- 针对数据的抽象：类

- 类拥有自己的数据和行为，能够完成自身的工作职责

- 过程是类的组成部分，为类提供行为

- 通过类的对象之间的协作完成系统功能

## 对象技术的思考

- ☑ 对象思维具有更大的灵活性，更好的模块化，可以进行更大规模的设计

- ☑ 面向对象设计和开发的难度更大，面临着**对象识别**、**职责分配**、**多态抽象**等一系列问题

- ◆ 学习更多知识和技术，并掌握一系列面向对象的设计原则和模式

- ◆ 图形化工具（UML）有助于表达和交流设计思想，并简化实现的过程

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_18_0.png)
