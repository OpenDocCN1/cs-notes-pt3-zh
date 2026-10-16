# 4.1 数组

# 创建数组

定义一个数组只是对数组的说明，系统并没有为数组分配任何内容，因此我们还不能访问它的任何元素。数组必须经过初始化后才能应用数组的元素，这个过程就是数组的创建的过程。

+   数组的初始化分为：静态初始化和动态初始化。

+   静态初始化：定义数组的同时对数组元素进行初始化。

```
int intArray[]={1,2,3,4}; //定义了一个含有4个元素的int型数组
int[] ages={34,12,45}; //定义了一个含有3个元素的int型数组
double[] heights={4.5,23.6,84.124,78.2,61.5}; //定义了一个含有5个元素的double型数组
boolean[] tired={true,false,false,true}; //定义了一个含有4个元素的boolean型数组
String[] names={"Zhang","Li","Wang"}; //定义了一个含有3个元素的String型数组
char vowels[]={'a','b','c','d'}; //定义一个含有4个元素的char型数组
Customer[] customers={new Customer("Zhang"),
    new Customer("Li"),
    new Customer("Wang")}; //定义一个含有3个元素的Customer型数组
```