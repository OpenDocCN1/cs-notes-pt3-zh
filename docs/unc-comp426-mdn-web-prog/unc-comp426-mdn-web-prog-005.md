# 005：函数式编程 🧠



在本节课中，我们将学习函数式编程的核心概念，特别是高阶函数和闭包。我们将通过分析内存图来理解这些概念在JavaScript/TypeScript中是如何工作的，并探索如何仅使用函数来模拟面向对象编程中的类和行为。

## 课程概述与公告 📢

欢迎回到现代Web编程的第5讲。课程现在开始。

首先是一些课程公告。关于个人作品集作业a01，大家完成得非常出色。评分工作预计在下周晚些时候完成。

此外，网站上发布了一个新的补充页面s02，标题为“从a01到真实网页”。这个页面将指导你如何将使用Vercel部署的网站（网址类似 `a01-personal-portfolio-你的名字.vercel.app`）连接到一个自定义域名（例如 `yourname.com`）。虽然这不是课程要求，但如果你想拥有一个展示个人技能的真实网站，这是一个很好的资源。

阅读作业R03“高阶函数”已于昨晚截止。如果尚未提交，你还有额外一天时间。如有任何问题，请随时联系我们。

新的作业a02“像素艺术生成器”今天发布，下周二截止。这是你的第一个TypeScript作业，你将构建一个绘画工具。你可以选择单独完成，或者与**最多一名**伙伴组队完成。作业说明中包含演示，展示了最终产品的样子。

本周没有新的阅读作业，大家可以专注于完成a02。

## 内存图回顾 🧱

在深入新内容之前，我们先来回顾上节课介绍的内存图。内存图是解释Web编程和TypeScript中核心概念的主要工具。

内存图通常分为两列：**栈**和**堆**。
*   **栈**负责跟踪变量定义以及当前正在调用的函数。每次调用新函数时，都会在栈上添加一个新的帧。
*   **堆**负责存储我们创建的对象或函数定义。如果需要引用堆中的某个项目，可以从栈指向它。

让我们通过一个例子来复习。考虑以下脚本：

```typescript
1: const num = 426;
2:
3: const half = (x: number): number => {
4:   // 函数体
5:   return x / 2;
6: };
7:
8: const result = half(num);
```

其执行过程的内存图演变如下：
1.  程序启动，栈上创建**全局帧**（F0）。执行第1行，在全局帧中添加变量 `num`，值为 `426`。
2.  执行第3行，在**堆**上创建一个函数定义（ID0），其父帧是定义它时的活动帧，即F0。在全局帧中，变量 `half` 的值被设置为指向堆中的这个函数（ID0）。
3.  执行第8行，调用 `half` 函数。这会在栈上添加一个新的帧 `half`（F1）。其父帧是函数定义所在的帧（来自堆上ID0的父帧信息），即F0。同时记录返回地址（第8行）和参数 `x`（值为 `426`）。
4.  执行跳转到函数内部（第5行），计算 `426 / 2 = 213`，并将其设置为F1帧的返回值。
5.  函数返回，回到第8行。返回值 `213` 被赋给变量 `result`。`half` 函数帧（F1）从栈中弹出。

## 热身练习：绘制内存图 ✏️

为了巩固理解，我们一起来分析一个稍复杂的例子：

```typescript
1: const x = 12;
2:
3: const multiply = (a: number, b: number): number => {
4:   return a * b;
5: };
6:
7: const square = (a: number): number => {
8:   return multiply(a, a);
9: };
10:
11: const result = square(x);
```

其内存图的构建步骤如下：
1.  **全局帧 (F0)**：包含 `x = 12`。
2.  **定义 `multiply` 函数**：在堆上创建函数定义（ID0），父帧为F0。全局变量 `multiply` 指向 ID0。
3.  **定义 `square` 函数**：在堆上创建函数定义（ID1），父帧为F0。全局变量 `square` 指向 ID1。
4.  **调用 `square(12)`**：创建新栈帧 `square` (F1)。其父帧是 `square` 函数定义时的父帧（来自ID1），即F0。参数 `a = 12`，返回地址为第11行。
5.  **在 `square` 内调用 `multiply(a, a)`**：创建新栈帧 `multiply` (F2)。**关键点**：其父帧是 `multiply` 函数定义时的父帧（来自ID0），即F0，而不是调用它的F1帧。参数 `a = 12`, `b = 12`，返回地址为第8行。
6.  **执行 `multiply`**：计算 `12 * 12 = 144`，作为F2的返回值。
7.  **返回至 `square`**：F2帧弹出。`square` 帧（F1）获得返回值 `144`。
8.  **返回至全局**：F1帧弹出。全局变量 `result` 被赋值为 `144`。

这个练习强调了重要的一点：**函数调用帧的父帧，取决于该函数定义在堆上时所记录的父帧，而不是调用它时的栈帧**。这一点对理解闭包至关重要。

## 高阶函数深入 🔄

上一节我们通过内存图复习了函数执行的基础。本节中，我们来看看一个更强大的概念：高阶函数。

高阶函数是指那些**接收函数作为参数**，和/或**返回一个函数作为结果**的函数。在TypeScript中，函数可以像数字、字符串一样被赋值给变量、传递和返回。

考虑以下代码，它包含高阶函数：

```typescript
// 一个接收函数作为参数的高阶函数
const mystery = (nums: number[], fn: (x: number) => number): number[] => {
  const result: number[] = [];
  for (const num of nums) {
    result.push(fn(num)); // 对每个数字应用传入的函数fn
  }
  return result;
};

// 一个返回函数的高阶函数
const operationFactory = (factor: number): ((x: number) => number) => {
  return (x: number): number => {
    return x * factor;
  };
};

// 使用它们
const operation = operationFactory(3); // operation 现在是一个函数：x => x * 3
const result = mystery([1, 2, 3], operation); // 对 [1,2,3] 每个元素应用 x*3
console.log(result); // 输出: [3, 6, 9]
```

我们来分解一下：
1.  `mystery` 函数接收一个数字数组 `nums` 和一个函数 `fn`。它遍历数组，将 `fn` 应用于每个元素，并将结果收集到新数组中返回。这里 `fn` 的类型 `(x: number) => number` 明确表示它接收一个数字并返回一个数字。
2.  `operationFactory` 函数接收一个数字 `factor`，并**返回一个新的函数**。这个返回的函数接收一个数字 `x`，并返回 `x * factor`。
3.  当调用 `operationFactory(3)` 时，它返回函数 `(x) => x * 3`，我们将其赋值给变量 `operation`。
4.  调用 `mystery([1,2,3], operation)`，意味着对数组中的每个数字 `1`, `2`, `3` 分别调用 `operation`（即乘以3），得到结果 `[3, 6, 9]`。

这类似于数学中的函数复合。高阶函数极大地增强了代码的表达力和复用性。

## 闭包：函数的“记忆”能力 🎯

理解了高阶函数后，我们来看一个更神奇的现象——闭包。闭包允许一个函数“记住”并访问其定义时的词法作用域，即使该函数在其定义的作用域之外被执行。

请看这个令人惊讶的例子：

```typescript
const createUpdater = (): (() => void) => {
  let counter = 0; // 这个变量在 createUpdater 的函数作用域内
  return (): void => {
    counter += 1;
    console.log(counter);
  };
};

const updater = createUpdater(); // updater 现在是一个函数
updater(); // 输出: 1
updater(); // 输出: 2
updater(); // 输出: 3
```

为什么 `counter` 变量在 `createUpdater` 函数执行结束后似乎依然“存活”并被修改？内存图揭示了秘密：

1.  调用 `createUpdater()` 时，创建栈帧F1，其中定义了局部变量 `counter = 0`。
2.  它返回一个箭头函数 `() => { counter += 1; console.log(counter); }`。这个函数被放在堆上（ID1），其**父帧被记录为F1**（它被定义时所在的帧）。
3.  变量 `updater` 被赋值为指向这个堆上的函数（ID1）。`createUpdater` 的栈帧F1按理说应该弹出。
4.  当我们调用 `updater()` 时，创建新的栈帧（例如F2）。**关键点**：这个新帧的父帧不是调用它的全局帧F0，而是其函数定义记录的父帧——F1。因此，它仍然能访问到F1帧中的 `counter` 变量。
5.  每次调用 `updater()`，都通过这个闭包访问并修改同一个F1帧中的 `counter` 变量，从而实现状态的保持。

**闭包**就是指这个返回的函数以及它所能访问的父作用域（变量 `counter`）的组合。它“关闭 over”了其定义时的环境。

## 函数式编程范式：用函数模拟对象 🏗️

闭包的概念为我们打开了一扇新的大门：**函数式编程范式**。在COMP110、210、301中，你们主要学习的是**面向对象编程**，通过类来建模数据和行为。

然而，在JavaScript/TypeScript这类支持高阶函数和闭包的语言中，我们可以使用纯函数来模拟面向对象编程的许多特性。事实上，在早期JavaScript中，根本没有 `class` 关键字，对象都是通过函数和闭包来创建的。

以下是一个对比示例：

**面向对象风格（使用类）**：
```typescript
class Person {
  name: string;
  constructor(firstName: string, lastName: string) {
    this.name = `${firstName} ${lastName}`;
  }
  greet(): string {
    return `Hi, ${this.name}!`;
  }
}
const aj = new Person('A', 'J');
console.log(aj.greet()); // 输出: Hi, A J!
```

**函数式风格（使用闭包）**：
```typescript
type Person = {
  name: string;
  greet: () => string;
};
const createPerson = (firstName: string, lastName: string): Person => {
  const name = `${firstName} ${lastName}`; // “私有”变量，类似于类的字段
  return {
    name: name,
    greet: (): string => {
      return `Hi, ${name}!`; // 闭包：内部函数可以访问外部函数的变量 `name`
    }
  };
};
const aj = createPerson('A', 'J');
console.log(aj.greet()); // 输出: Hi, A J!
```

在函数式版本中：
*   `createPerson` 函数类似于构造函数。
*   内部变量 `name` 类似于类的私有字段。
*   返回的对象中的 `greet` 方法是一个闭包，它永久地捕获并可以访问创建时的 `name` 变量，就像类方法访问 `this.name` 一样。

这两种方式在功能上是完全等价的。通过闭包，我们无需类语法也能实现数据封装和行为绑定。


## 总结与展望 📚

本节课中我们一起学习了：
1.  **内存图**：回顾了栈、堆、函数调用帧和父帧的概念，这是理解高级语言特性的基础。
2.  **高阶函数**：学习了接收函数为参数或返回函数的函数，它们增强了代码的抽象和组合能力。
3.  **闭包**：理解了函数如何“记住”其定义时的作用域，这是实现状态封装和函数式编程的基石。
4.  **函数式编程范式**：探索了如何仅使用函数和闭包来模拟面向对象编程中的类和对象，这是Web编程中广泛使用的模式。


函数式编程思想，尤其是高阶函数和闭包，在现代Web开发中无处不在，例如事件处理、状态管理库（如Redux）、React Hooks等。掌握这些概念将为你后续的学习打下坚实的基础。


![](img/2448d019eef57d191f04ec5a90f3c9bc_10.png)

下节课我们将继续探索更多Web编程的核心概念。