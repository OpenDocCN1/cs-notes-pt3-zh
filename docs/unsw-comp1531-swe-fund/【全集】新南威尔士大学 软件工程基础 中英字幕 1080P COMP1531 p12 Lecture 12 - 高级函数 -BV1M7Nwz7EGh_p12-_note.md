# 软件工程基础：12：高级函数 🚀

![](img/2a025dce3cfb679d25c2c4c37cada74f_1.png)

在本节课中，我们将要学习JavaScript中的高级函数概念。我们将探讨函数的不同定义方式、一等函数、高阶函数以及数组的`map`、`filter`、`reduce`方法。这些概念是理解现代JavaScript编程的关键，能帮助我们编写更简洁、更易维护的代码。

## 函数定义方法 📝

在JavaScript中，有三种主要的方式来定义函数。上一节我们介绍了课程背景，本节中我们来看看这些具体的语法。

![](img/2a025dce3cfb679d25c2c4c37cada74f_3.png)

**方法一：传统函数声明**
这是最经典的方式，类似于C语言风格，但不需要指定返回类型。
```javascript
function sum(a, b) {
    return a + b;
}
```

![](img/2a025dce3cfb679d25c2c4c37cada74f_5.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_7.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_9.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_11.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_13.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_14.png)

**方法二：函数表达式**
这种方式将函数赋值给一个变量。
```javascript
const sum = function(a, b) {
    return a + b;
};
```

![](img/2a025dce3cfb679d25c2c4c37cada74f_16.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_17.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_18.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_19.png)

**方法三：箭头函数（现代语法）**
这是方法二的简写形式，使用`=>`符号，语法更紧凑。
```javascript
const sum = (a, b) => {
    return a + b;
};
```
箭头函数还有一个便利特性：如果函数体只有单行返回语句，可以省略大括号和`return`关键字。
```javascript
const sum = (a, b) => a + b;
```

## 一等函数 🥇

一等函数是JavaScript的核心特性之一，它意味着函数可以像其他变量（如字符串、数字）一样被对待。具体来说，函数可以被赋值给变量、作为参数传递给其他函数，或者作为其他函数的返回值。

![](img/2a025dce3cfb679d25c2c4c37cada74f_21.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_23.png)

以下是一个简单的例子，展示了如何将函数作为参数传递：

![](img/2a025dce3cfb679d25c2c4c37cada74f_25.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_27.png)

```javascript
// 定义两个格式化函数
const brackets = (str) => `(${str})`;
const fullStop = (str) => `${str}.`;

![](img/2a025dce3cfb679d25c2c4c37cada74f_29.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_31.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_33.png)

// 定义一个接受函数作为参数的函数
const sayHi = (name, format) => {
    console.log(`Hello ${format(name)}`);
};

![](img/2a025dce3cfb679d25c2c4c37cada74f_35.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_37.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_38.png)

// 调用sayHi，并传入不同的格式化函数
sayHi('Hayden', brackets); // 输出: Hello (Hayden)
sayHi('Hayden', fullStop); // 输出: Hello Hayden.
```

![](img/2a025dce3cfb679d25c2c4c37cada74f_40.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_42.png)

在TypeScript中，我们需要为作为参数的函数定义类型：
```typescript
type Formatter = (str: string) => string;
const sayHi = (name: string, format: Formatter) => {
    console.log(`Hello ${format(name)}`);
};
```

![](img/2a025dce3cfb679d25c2c4c37cada74f_44.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_46.png)

## 匿名函数与数组方法 🛠️

![](img/2a025dce3cfb679d25c2c4c37cada74f_48.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_50.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_52.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_54.png)

匿名函数是指没有名称的函数，通常用于只需要使用一次的场合。它们在与`map`、`filter`、`reduce`等数组方法结合时特别有用。

![](img/2a025dce3cfb679d25c2c4c37cada74f_56.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_58.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_60.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_62.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_64.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_65.png)

以下是`map`、`filter`、`reduce`的核心概念：

![](img/2a025dce3cfb679d25c2c4c37cada74f_67.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_69.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_71.png)

*   **`map`**: 遍历数组，对每个元素应用一个函数，并返回一个由结果组成的**新数组**。新数组长度与原数组相同。
    ```javascript
    const tutors = ['Simon', 'Theresa', 'Kai', 'Michelle'];
    const shoutedTutors = tutors.map(name => name.toUpperCase() + '!');
    // 结果: ['SIMON!', 'THERESA!', 'KAI!', 'MICHELLE!']
    ```
*   **`filter`**: 遍历数组，用一个函数测试每个元素，返回一个由所有通过测试的元素组成的**新数组**。新数组长度可能小于原数组。
    ```javascript
    const marks = [39, 43, 48, 24, 33];
    const passingMarks = marks.filter(mark => mark >= 50);
    // 结果: [55, 65] (假设有55和65)
    ```
*   **`reduce`**: 遍历数组，通过一个“归约”函数将数组元素累积计算为**单个值**（如求和、求积）。
    ```javascript
    const marks = [55, 43, 34, 23];
    const total = marks.reduce((prev, current) => prev + current, 0);
    // 结果: 155
    ```

![](img/2a025dce3cfb679d25c2c4c37cada74f_73.png)

一个结合使用的例子：
```javascript
const marks = [39, 43, 48, 24, 33];
// 1. 标准化分数（假设满分60）
const normalized = marks.map(mark => (mark / 60) * 100);
// 2. 筛选出及格分数
const passing = normalized.filter(mark => mark >= 50);
// 3. 计算及格分数的总和
const totalPassing = passing.reduce((sum, mark) => sum + mark, 0);
// 4. 计算平均及格分
const averagePassing = totalPassing / passing.length;
```

![](img/2a025dce3cfb679d25c2c4c37cada74f_75.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_77.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_79.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_81.png)

## 高阶函数 🏭

![](img/2a025dce3cfb679d25c2c4c37cada74f_83.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_85.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_87.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_89.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_91.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_93.png)

高阶函数是指**返回另一个函数**的函数。你可以把它们想象成“函数工厂”，用于生成特定行为的函数。

![](img/2a025dce3cfb679d25c2c4c37cada74f_95.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_97.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_99.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_101.png)

假设我们需要多个函数来祝贺不同成绩等级的学生：

![](img/2a025dce3cfb679d25c2c4c37cada74f_103.png)

```javascript
// 传统方式：定义多个相似函数
const congratulateMarkPass = (name) => `Congratulations ${name} on your pass.`;
const congratulateMarkCredit = (name) => `Congratulations ${name} on your credit.`;
// ... 更多等级
```

![](img/2a025dce3cfb679d25c2c4c37cada74f_105.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_107.png)

使用高阶函数可以更优雅地解决：

```javascript
// 高阶函数：生成祝贺函数的工厂
const generateCongratulateMark = (mark: string) => {
    // 返回一个新的函数
    return (name: string) => `Congratulations ${name} on your ${mark}.`;
};

// 使用工厂创建特定函数
const congratulateMarkPass = generateCongratulateMark('pass');
const congratulateMarkCredit = generateCongratulateMark('credit');

![](img/2a025dce3cfb679d25c2c4c37cada74f_109.png)

// 使用它们
console.log(congratulateMarkPass('Hayden')); // Congratulations Hayden on your pass.
console.log(congratulateMarkCredit('Juliana')); // Congratulations Juliana on your credit.
```
这种方式减少了重复代码，使逻辑更集中，便于维护和扩展。

## 总结 📚

本节课中我们一起学习了JavaScript中的高级函数概念。
我们首先了解了三种定义函数的方法，特别是现代箭头函数的简洁语法。
接着，我们探讨了一等函数的概念，即函数可以像变量一样被传递和使用，这是`map`、`filter`、`reduce`等方法的基础。
然后，我们深入学习了`map`（映射）、`filter`（过滤）、`reduce`（归约）这三个强大的数组方法，它们能让我们以声明式、简洁的方式处理数据集合。
最后，我们介绍了高阶函数，即返回函数的函数，它像工厂一样能生成特定行为的函数，有助于减少代码重复并提高抽象层次。

![](img/2a025dce3cfb679d25c2c4c37cada74f_111.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_113.png)

![](img/2a025dce3cfb679d25c2c4c37cada74f_115.png)

掌握这些概念将极大地提升你编写简洁、高效且易维护的JavaScript代码的能力。