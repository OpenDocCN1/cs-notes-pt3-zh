
```c
void main(void) {
    printf("please input xa,ya,xb,yb,\n    xc,yc,xd,yd:\n");
    scanf("%f%f%f%f%f%f %f%f ",&xa,&ya,
    &xb,&yb,&xc,&yc,&xd,&yd);

    s1 = areauvw (xa, ya, xb, yb, xd, yd );
    s2 = areauvw (xb, yb, xc, yc, xd, yd );

    ss=s1+s2;
    ss=ss/1000;    // 折合成亩
    m=ss*950;    // 计算总产量
    printf("m=%10.3f\n",m); // 打印输出
}
```

## 程序执行的主要步骤

- 从第18行主函数开始，执行
  printf("please input xa,ya,xb,yb,xc,yc,xd,yd:\n");
  输出一行提示信息：
  please input xa,ya,xb,yb,xc,yc,xd,yd :
- 执行第19行函数调用
  scanf("%f%f%f%f%f%f%f%f", &xa, &ya, &xb, &yb, &xc, &yc, &xd, &yd);
  等待操作员键入数值。设操作员键入
  547 411 804 77 39 208 116 332
  当操作员键入并回车之后，变量xa、ya、xb、yb、xc、yc、xd、yd分别取得相应值。

### 第20行以xa、ya、xb、yb、xd、yd为实参调用函数areauvw

- 分别计算xa，ya，xb，yb，xd，yd的值，得547、411、804、77、116、332
- 将547、411、804、77、116、332分别送入areauvw的形参xu、yu、xv、yv、xw、yw中
- 进入函数areauvw，执行areauvw的操作部分
- 第11行，以xu，yu，xv，yv为实在参数调用函数liners，计算边uv长
- 分别计算xu，yu，xv，yv得547、411、804、77；
- 将547、411、804、77顺序送入liners形参xr，yr，xs，ys中
- 第6行返回语句

  ```c
  return sqrt( (xr-xs)* (xr-xs)+(yr-ys)* (yr-ys) );
  ```

- 计算出表达式的值为 421.432
- 带着函数值421.432返回调用处
- areauvw中第11行，给uv赋值。uv的值为421.432
- 第12行，以xu，yu，xw，yw为实参调用函数liners，计算边uw长uw。uw值为： 438.18
- 第13行，以xv，yv，xw，yw为实参调用函数liners，计算边vw长vw。vw值为： 733.736
- 第14行，计算出s=796.674
- 15行返回语句。计算表达式的值为82128.5，也就是函数areauvw的值。
- 带着函数值82128.5返回调用处主程序第20行
- 第21行，计算三角形BCD的面积，s2=52473.5
- 第22行，计算总面积，ss=134602
- 第23行，折合成亩，ss=134.602
- 第24行，计算总产量，m=127871.9
- 第25行，输出函数printf在屏幕显示：
  m=127871.90

![](img/2c9b154d61523ac3dc02daf316966b8e_185_0.png)

### 使用子程序技术分离了“做什么”与“怎么做”

- 程序逻辑结构清晰，易写，易读，易懂。
- 程序的设计，调试，维护变得容易。

## 函数

### 数学中函数

\( f(x, y) = x^y \)

### 函数概念的组成

- 函数定义
- 函数调用

### 使用函数注意事项

- 先定义该函数（标准库函数除外）
  ——类似于数学中的函数定义。
- 再在表达式中调用该函数
  ——数学中计算某函数的一个特定值。

## 函数调用(function-designator)

### 调用过程
- 形参实参结合
- 进入函数执行复合语句

### 一般形式
- F (e, e, ..., e)
- F ( )

### 例子
- p (x+5)
- f (u*0.3,x+u)

## 函数定义(function-declaration)

- 除标准库函数外，程序中使用函数必须**先定义**，然后再用“函数调用”调用它。
- 标准函数是系统已经定义好的函数，不必定义即可直接调用。
- 在程序example401A中：

```c
float f(float v,float w ){
    return (w+v)/(7*v);
}
float p(float u){
    return ( f(u*0.3,x+u)+(u/2))/(2*x) );
}
```

由上述语法可知，一个函数定义的形式是：

类型说明符 标识符 （ 参数列表 ）
复合语句

```c
float f (float u)
{
    return (f(u*0.3,x+u)+(u/2))/(2*x);
}
```

## 函数定义说明符

上述形式的第一行称“函数定义说明符”，形式如下

### TT F（参数列表）

具体指明以下点：

- 函数的结果类型  ——由“类型说明符”（TT）标明；
- 函数的名字  ——由类型说明符后的“标识符”（F）标明；
- 函数的形式参数个数和每个形式参数的特性  ——由“参数列表”标明。

## 函数类型（返回值的类型）

- 不能是数组或函数
- 没有返回值的函数类型是void

## 函数返回

- 返回方式：
- return ;
- return 表达式；
- 函数运行到复合语句末尾（最后那个闭花括号“}”）后。

```c
int f(int x){
    return x*x;
}

int y=9;
void f(int x){
    if (x<0)
        return;
    y=y+x;
}
```

## 参数列表(parameter-list)

- 组成：
  - 每个参数声明具体说明形式：
    类型说明符 标识符
  - 参数列表形式
    T id , T id , ... , T id
- C允许使用无参函数，无参函数的参数列表为空，或使用“空类型”的类型说明符“void”
  TT F()
  TT F(void)

```c
int f(int x, int y, float z)
```

```c
int f(int x,y , float z)
```

```c
int f(int x,y , float z)
```

### 根据参数出现的位置

- 形式参数——函数声明(局部于函数的变量)

```c
int f(int x,int y){
    return x+y;
}
```

- 实际参数——函数调用

```c
void main(){
    int a=2,b=3;
    f(a+b, b);
    f(2+b,3);
}
```

### 根据参数值的传递规则

- 值参：当调用函数时，把**实参的值**传入形参变量
- 变参：当调用函数时，把**实参的地址值**传入形参变量

**C语言中的参数都是**<span style="color:red">值参</span>

```c
int f (int x, int y){
return x*y;
}
void main(){
int a=3, b=2,x=9;
int c;
c=f(a+b,a+x);
printf("%d\n", c);
printf("%d\n", x);
}
```

程序输出为：

- 60
- 9

![](img/2c9b154d61523ac3dc02daf316966b8e_198_0.png)

- 复合语句（compound-statement）由声明和语句列表组成
- 声明部分具体的说明本函数内使用的其它量；
- 语句部分规定在本函数中要执行的操作。
- 函数定义的形式：

```c
TT F ( T id，T id，…，T id ){
    …
}
```
