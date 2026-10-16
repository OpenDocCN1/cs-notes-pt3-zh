在主程序中，将使用函数readcard带回的card值。例如主程序中具有功能：输入所有职工卡片、填加一张职工卡片等，这些功能的实现都将调用该函数。如果用数组保存所有卡片并且设不超过100个职工，并有声明：

```
#define n 100
int v,flag;
typecardperson card_arr[n];
```