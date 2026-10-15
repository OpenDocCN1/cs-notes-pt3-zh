

## 练习：三堆 Nim

- 作为今天的最后练习，我想通过使用书中简单的 Nim 程序作为起点，来演示如何实现一个更复杂的 Nim 版本。
- 在这个版本中，有三行硬币，通常的初始配置如下：
- 一次行动包括拿走任意数量的硬币，但它们必须全部来自同一行。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_247_0.png)

## 递归回溯

- 将问题表述为决策点
  - 识别需要做出的决策
  - 识别每个决策可用的选项
  - 递归调用做出一个决策，并对剩余决策进行递归
- 回溯方法
  - 设计递归函数返回成功/失败
  - 在每次调用时，选择一个选项并执行
  - 递归继续并观察结果
  - 如果成功，很好，否则撤销选择并重试
  - 如果没有选项可行，返回失败从而触发回溯
- 启发式方法可能提高效率
  - 通过剪枝尽早消除死路
  - 优先尝试最可能的选项

## 回溯伪代码

```
bool Solve(configuration conf)
{
    if (no more choices) // BASE CASE
        return (conf is goal state);

    for (all available choices) {
        try one choice c;
        // solve from here, if works out, you're done
        if (Solve(conf with choice c made)) return true;
        unmake choice c;
    }

    return false; // tried all choices, no solution found
}
```

## 第四部分：递归 VS 迭代

Jingyu Zhou

## 递归 vs 迭代

- 迭代：
  - 将问题分解为*序列*的典型情况
  - 识别典型情况（主体）
  - 识别到下一个情况的*增量*步骤
  - 识别继续或停止的*条件*
  - 识别*初始化*

- 递归：(简单)
  - 将问题分解为*第一*部分和*剩余*部分
  - 识别第一种情况
  - 识别对剩余部分的递归调用
  - 识别何时应进行递归调用。
    - 确保有停止情况（*基本情况*）
  - 可能需要包装方法进行*初始化*

## 递归示例：幂运算

- 回顾预定义函数 pow()：
  result = pow(2.0,3.0);
  - 返回 2 的 3 次方（8.0）
  - 接受两个 double 参数
  - 返回 double 值
- 我们来递归地编写
  - 对于简单示例

## power() 函数定义

```
int power(int x, int n)
{
    if (n<0)
    {
        cout << "Illegal argument";
        exit(1);
    }
    if (n>0)
        return power(x, n-1)*x;
    else
        return 1;
}
```

## 调用 power() 函数

- 更大的示例：
  power(2,3);
  → power(2,2)*2
  → power(2,1)*2
  → power(2,0)*2
  → 1

- 到达基本情况

- 递归停止

- 值“返回”回栈中

## 递归思考

- 忽略细节
  - 忘记栈如何工作
  - 忘记挂起的计算
  - 是的，这是一个“抽象”原则！
  - 也是封装原则！
- 让计算机做“记账”
  - 程序员只需思考“大局”

## 递归思考：power

- 再次考虑 power()
- power() 的递归定义：

`power(x, n)`

返回：

`power(x, n - 1) * x`

- 只需确保“公式”正确
- 并确保基本情况会被满足

## 递归设计技术

- 不要追踪整个递归序列！
- 只检查 3 个属性：
  - 无无限递归
  - 停止情况返回正确值
  - 递归情况返回正确值

## 递归设计检查：power()

检查 power() 是否符合 3 个属性：

- 1. 无无限递归：
  - 第二个参数每次调用减少 1
  - 最终必须到达 1 的基本情况

- 2. 停止情况返回正确值：
  - power(x,0) 是基本情况
  - 返回 1，这对 x0 是正确的

- 3. 递归调用正确：
  - 对于 n>1，power(x,n) 返回 power(x,n-1)*x
  - 代入值 → 正确

