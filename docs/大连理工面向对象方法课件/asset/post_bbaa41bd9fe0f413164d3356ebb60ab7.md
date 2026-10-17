
```
}

CNetGameFactory::~CNetGameFactory()
{
}
```

```
CEasyGame * CNetGameFactory::createEasyGame()
{
    return new CNetEasyGame;
}
```

```
CDifficultGame* CNetGameFactory::createDifficultGame()
{
    return new CNetDifficultGame;
}
```

上面两个方法返回两个产品的2个产品，而不论用户选择什么游戏类型。

```
void playGame(int i,int j)//必须用
{
    CLocalGameFactory cLocalGameFactory;//具体工厂对象
    CNetGameFactory cNetGameFactory; //具体工厂对象
    if(1==i)
    {
        if(4==j)
        {
            cLocalGameFactory.createEasyGame()->play();
        }
        else
        {
            cLocalGameFactory.createDifficultGame()->play();
        }
    }
    else if(2==i)
    {
        if(4==j)
        {
            cNetGameFactory.createEasyGame()->play();
        }
        else
        {
            cNetGameFactory.createDifficultGame()->play();
        }
    }
}
```

```
int main(int argc, char* argv[])
{
    int i,j;
    for(;;)
    {
        cout<<"Welcome to play Games."<<endl;
        cout<<"1 for local Game ;2 for Net Game ;others for quit : ";
        cin>>i;
        if(i != 1 && i != 2)
            break;
        cout<<"4 for easy Game ; 5 for Difficult Game ;others for quit : ";
        cin>>j;
        if(j != 4 && j != 5)
            break;
        playGame(i,j);
    }
    return 0;
}
```

### 问题：必须讲：

开闭原则<sup>108</sup>

- 1. 增加产品族？ 答案：支持开闭原则
- 2. 增加产品等级结构？ 答案：不支持开闭原则
- 3. 课后练习 p107

## 第一讲 引言

### 2009 级研究生用

内容：任意个整数排序（三种实现方法举例）

#### 1. 用静态数组实现任意整数排序 Static.cpp

```c
//////////////////////////////////
/*静态数组排序*/
#include "stdio.h"
#define DataNum 65534
void input(int *data,int n);
void sort (int *data,int n);
void display(int *data,int n);

main()
{
    int DataCounter;
    int data[DataNum+1];

    printf("Please input the number of integers to be sorted:\n");
    scanf("%d",&DataCounter);
    if(DataCounter >= DataNum)
    DataCounter = DataNum;
    printf("Please input the integers to be sorted:\n ");
    input(data, DataCounter);   //输入函数
    sort(data, DataCounter);    //排序函数
    display(data, DataCounter); //显示函数
    return true;
}
////////////////////////////////////
/*函数——输入数组*/
void input(int *data,int n)
{
    int i;
    for(i=0;i<n;i++)
        scanf("%d",&data[i]);
}
//////////////////////////////
/*函数——数组排序*/
void sort (int *data,int n)
{
    int i,j,temp;
    for (i = n;i > 0;i--)
    {
        for (j = 0;j < i - 1;j++)
        {
            if (data[j] > data[j+1])
            {
                temp = data[j];
                data[j] = data[j+1];
                data[j+1] = temp;
            }
        }
    }
}
//////////////////////////////
/*函数——输出数组*/
void display(int *data,int n)
{
    int i;
    for(i=0;i<n;i++)
        printf("%d ",data[i]);
    printf("\n");
}
```

##### 运行结果：

![](img/3b4669cf00b2833fe526284506f3f342_69_0.png)

#### 2. 用动态数组实现任意整数排序（activesort.cpp）

```c
/*动态数组排序*/

#include "stdio.h"

void input(int *data,int n);
void sort (int *data,int n);
void display(int *data,int n);

main()
{
    int DataCounter;
    int *data;
    string str = "Please input the number of integers to be sorted:\n";
    cout <<str ;
    scanf("%d",&DataCounter);
    printf("Please input the number of integers: \n");
    data = new int[DataCounter];
    input(data,DataCounter);
    sort(data,DataCounter);
    printf("The sorted integers are:\n");
    display(data,DataCounter);

    delete data;
    return true;
}
/*函数 -- 输入数组*/
void input(int *data,int n)
{
    int i;
    for(i=0;i<n;i++)
        scanf("%d",&data[i]);
}
/*函数 -- 数组排序*/
void sort (int *data,int n)
{
    int i,j,temp;
    for (i = n;i > 0;i--)
    {
        for (j = 0;j < i - 1;j++)
            if (data[j] > data[j+1])
            {
                temp = data[j];
                data[j] = data[j+1];
                data[j+1] = temp;
            }
    }
}
/*函数——输出数组*/
void display(int *data,int n)
{
    int i;
    for(i=0;i<n;++i)
        printf("%d ",data[i]);
    printf("\n");
}
```

##### 运行结果：

![](img/3b4669cf00b2833fe526284506f3f342_71_0.png)

#### 3. 用面向对象的基本方法实现任意整数排序（ClassSort.cpp）

##### （1）C++方法

```c
/*用类、动态数组实现排序*/
#include "stdio.h"
class DataSort
{
private:
    int DataNum;
    int *data;
public:
    DataSort();
    void inputcounter();
    void apply();
    void inputnum();
    void sort();
    void display();
    ~DataSort();
};
//////////////
DataSort::DataSort()
{
    DataNum = 0;
}
```
