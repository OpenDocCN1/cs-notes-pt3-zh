

## 递归函数

- 直接或间接调用自己的函数被称为递归函数
- 递归函数必须定义一个停止条件（基本情况）

```
int rgcd( int v1, int v2 )
{
    if ( v2 != 0 )
        return rgcd( v2, v1%v2 );
    return v1;
}
```

## 递归函数

- 例如，考虑阶乘函数
- C++（以及绝大多数别的编程语言中）没有阶乘操作符
- 必须以编写函数的方式来实现

- 首先，考察阶乘的数学定义：

$$factorial(n)=\prod_{i=1,n}i\quad(for\ n>0)$$

- 例如，factorial(3) 的计算如下：

$$factorial(3)=\prod_{i=1,n}i=(1\times2\times3)$$

## 递归函数

- 阶乘还有另外一种定义形式：
$$factorial(n) = \begin{cases} 1 & n = 0 \\ n \times factorial(n-1) & n > 0 \end{cases}$$

- 这是阶乘的递归定义
- 阶乘函数是使用阶乘自身来定义的

## 递归函数

- 这个定义有两个特性：
- 首先，它有一个无需计算的终止情况

$factorial(0)=1$

- 其次，其他情况可以按照如下方式解决：
- 先解决更小的问题，它更接近终止情况
- 再在这个更小问题的处理结果上执行简单的附加操作，得到“更大”的结果
- 这就是递归步骤（recursive step），或称为归纳步骤

## 递归解决方案

- 阶乘函数

```
int factorial(int n)
// REQUIRES: n >= 0 // EFFECTS: computes n!
1 {
2   if (n==0) {
3     return 1; // This is the base case---trivial!
4   } else {
5     return n*factorial(n-1); // This is the recursive step
6   }
7 }
```

## 递归的执行

- 假设我们以如下方式调用阶乘函数

```
int main()
1 {
2   int x;
3   x = factorial(3);
4 }
```

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_341_0.png)

## 递归的执行

- 主函数用参数 3 调用阶乘函数，调用时：
- 计算实参的值
- 创建一条活动记录
- 将实参的值复制给形参
- 赋值发生在主函数的第三行

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_342_0.png)

- 在阶乘函数体中：
- n 不等于 0
- 于是执行 if 语句的另一条分支
- `return 3*factorial(2)`

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_342_1.png)

因此，阶乘函数必须调用它自身

## 递归的执行

- 在阶乘函数调用阶乘函数时：
- 对新的阶乘函数实例创建一条新的活动记录

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_343_0.png)

发生在阶乘函数的第5行

- n 仍就 不等于 0:
- 所以再次计算执行的 if 分支
return 2*factorial(1)

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_344_0.png)

- n 再次调用时为 0:
- 执行 if 分支
return 1

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_345_0.png)

- 从栈中弹出最近的活动记录：

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_346_0.png)

## 递归的执行

- 弹出的活动记录对应的调用是：
return 1*factorial(0)
- 现在已经知道 factorial(0) 的值为1，因此直接可知
return 1*1 ➔ return 1;
- 然后依次再弹出栈一个活动记录：

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_347_0.png)

- 同理，执行：
return 2*factorial(1) ➔ return 2*1 ➔ return 2
- 再弹出栈一个活动记录：
- 接着，解决最后一个未完成的乘法
return 3*factorial(2) ➔ return 3*2 ➔ return 6
- 至此，执行完毕

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_348_0.png)

## 递归的问题

- 递归程序中每一次递归调用都需要占用栈中的一帧
- 这种方式代价有可能会很大
- 可能需要很多内存空间
- 这潜在地会导致栈溢出
- 递归版本的函数在内存空间使用上显得效率很低
- 是否存在一种方案可以降低对内存空间的要求呢？

- 我们来跟踪计算2的阶乘的调用情况：
- 对比两个版本

新版本

旧版本

```
factorial(2)
→ fact_helper(2, 1)
→ fact_helper(1, 2)
→ fact_helper(0, 2)
← 2
← 2
← 2
```

```
factorial(2)
→ 2 * factorial(1)
→ 1 * factorial(0)
← 1
← 1*1 (==1)
← 2*1 (==2)
← 2
```

## 尾递归

- 两个递归过程看起来是相同的
- 但是，它们存在本质区别：
- 新版本做的工作更少
- 它从最深层调用直接返回最终结果到最顶层
- 而旧版本在每一层都需要拿到返回结果后再做处理
- 这到底有什么不同呢？

## 尾递归

- 新版本中我们优化了对栈的使用
- 函数的活动记录只有在计算未处理完的情况下才需要
- 只要函数返回值已知，那么活动记录就可以丢弃
- 这就意味着对内存空间的使用更有效率

- 在新版本中，具体的返回值是未知的
- 在每次递归调用时未知

- 但是，每个调用都知道，无论它产生的递归调用返回什么：
- 该返回值也就是这个调用要返回的值

- 这意味着再也不需要为调用者在栈中分配帧
- 我们可以将其丢弃

- 这就是“尾递归（tail-recursion）”

- 由于在每个递归步骤中都不再执行未完成的计算
- 我们可以重用活动记录而不是创建新的活动记录

- 新版本按如下方式工作：

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_356_0.png)

## 尾递归

- n 不等于0，因此执行：
return fact_helper(2,3)

- 这是一个尾递归调用
- fact_helper调用了它自己
- 并且在递归调用返回时，
不需要再做额外的工作

- 因此，我们可以重用栈中的帧
- 并返回其地址

| factorial | |
| 参数 | 3 |
| 返回地址：foo | |
| fact_helper | |
| n | 2 |
| 结果 | 3 |
| 返回地址：factorial，第1行 | |

