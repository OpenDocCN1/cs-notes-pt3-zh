

# 第4章 运算符重载

## 4.4.2 重载自增运算符

设 A Aobject ;
++Aobject; // A对象自增

成员函数重载

友元函数重载

![](img/f89aaa55889bdc91174ae4576e90c3f2_181_0.png)

## 友元函数重载++

```cpp
class Increase
{
int value ;
public :
Increase ( ) { value=0; }
void display() const { cout<<value<<'\n'; } ;
friend Increase& operator ++ ( Increase & ) ; // 前置
friend Increase& operator ++ ( Increase &, int ) ;
};
Increase& operator ++ ( Increase & a )
{ a.value ++ ; return a ; }
Increase& operator ++ ( Increase & a, int )
{ Increase temp(a); a.value ++ ; return temp; }
```

![](img/f89aaa55889bdc91174ae4576e90c3f2_182_0.png)

## 4.4.3 特殊运算符的重载

```cpp
class IntArray
{
public:
    IntArray(int s=0);
    ~IntArray();
    //其他成员函数
private:
    int * pArr; //数组首地址
    int size;   //数组大小
};
```

使用数组的局限性
int i=3, a[3], b[i];
cout << b ;
a = b ;
a[3] = b[3];

## 重载下标运算符[]

运算符 [] 是二元运算符，下标运算符“[ ]”通常用于在数组中标识数组元素的位置，下标运算符重载可以实现数组数据的赋值和取值。

只能用成员函数重载，不能用友元函数重载

下标运算符函数重载的一般形式为：
返回类型 类名 :: operator[ ]( int index ) ;

![](img/f89aaa55889bdc91174ae4576e90c3f2_184_0.png)

![](img/f89aaa55889bdc91174ae4576e90c3f2_184_1.png)

![](img/f89aaa55889bdc91174ae4576e90c3f2_184_2.png)

## 重载下标运算符[]

```cpp
class IntArray
{
public:
    IntArray(int s=0);
    ~IntArray();
    int& operator[](int i);
private:
    int * pArr;
    int size;
};
```

```cpp
int& IntArray::operator[](int i)
{
    if(i<1||i>size)
    {
        cout<<" Out of range!"<<endl;
        return pArr[0]; }
    return pArr[i];
}
```

```cpp
IntArray a(3),b(5);
for( int i = 1 ; i<=5;i++ )  b[i] = i;
for( i = 1 ; i<=5; i++)  cout<< a[i] <<' ';
cout<< a<< b<<endl;
```

## 重载运算符<<

```cpp
class IntArray
{
public:
	IntArray(int s=0);
	~IntArray();
	int& operator[](int i);
	friend ostream& operator<< ( ostream& out, IntArray&a );
private:
	int * pArr;
	int size;
};
```

```cpp
ostream& operator<<
(ostream& out, IntArray& a)
{	for(int i = 1 ; i<=a.size ; i++)
		out<< a.pArr[i]<<' ' ;
	return out;
}
```

cout 的别名

```cpp
IntArray a(3),b(5);
for( int i = 1 ; i<=5;i++) b[i] = i;
for( i = 1 ; i<=5; i++) cout<< a[i] <<' ';
cout<< a<< b<<endl;
```

```cpp
class IntArray
{
    int * pArr;
    int size;
public:
    IntArray(int s=0);
    ~IntArray();
    int& operator[](int i);
    friend ostream& operator<< ( ostream&, IntArray& ) ;
};
```

![](img/f89aaa55889bdc91174ae4576e90c3f2_189_0.png)

```cpp
IntArray a(3),b(5);
for( int i = 1 ; i<=5;i++)  b[i] = i;
a = b;
cout<< a<< b<<endl;
```

=可以不必重载
运行错误

## 复制构造

## 赋值运算

IntArray a(5), b(a);
IntArray a(5),b(3);
b = a;

![](img/f89aaa55889bdc91174ae4576e90c3f2_190_0.png)

![](img/f89aaa55889bdc91174ae4576e90c3f2_190_1.png)

![](img/f89aaa55889bdc91174ae4576e90c3f2_190_2.png)

![](img/f89aaa55889bdc91174ae4576e90c3f2_190_3.png)

(a) 赋值操作前

(b) 赋值操作后

# 第4章 运算符重载

```cpp
IntArray::IntArray(int s){
	size = s;
	if(size == 0) //空数组
	pArr = NULL;
	else //分配空间，0号元素不用
	pArr = new int[size+1];
	for(int i = 1; i<= size;i++)
		pArr[i] = 0; // 数组元素置0
}
IntArray::~IntArray(){
	if(pArr!=NULL)
		delete []pArr ; //释放数组空间
}
```

> IntArray a(5);
> IntArray b = a;
> 
> 深复制与浅复制

## 复制构造- 深复制与浅复制

## 赋值运算

IntArray a(5), b(a);
IntArray a(5),b(3);
b = a;

![](img/f89aaa55889bdc91174ae4576e90c3f2_192_0.png)

![](img/f89aaa55889bdc91174ae4576e90c3f2_192_1.png)

(a) 析构对象b

(b) 析构对象a

## 赋值运算

IntArray a(5), b(a);
IntArray a(5),b(3);
b = a;

![](img/f89aaa55889bdc91174ae4576e90c3f2_193_0.png)

## 重载赋值运算符

- 何时重载=

赋值运算符重载用于对已有对象数据的深度复制

- 如何重载=

operator=() 必须重载为成员函数，函数原型：

类类型& 类名 :: operator= ( const 类类型 & ) ;

```
类类型& 类名 :: operator= ( const 类类型 & ) ;
```

> 必须是类类型的引用？

![](img/f89aaa55889bdc91174ae4576e90c3f2_194_0.png)

