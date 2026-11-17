# 001：JavaScript入门教程 🚀

在本节课中，我们将要学习JavaScript编程语言。我们将从它与C语言的区别开始，逐步介绍其核心语法、数据结构以及一些独特的语言特性。课程旨在帮助已有C语言基础的同学快速上手JavaScript。

![](img/8745e98bc46b158cc24032f59bc347ef_1.png)

---

## 概述 📋

JavaScript是一种高级、多范式、解释型的脚本语言，广泛应用于Web开发。与C语言不同，JavaScript不直接处理内存和指针，没有显式的类型声明，并且拥有丰富的内置功能。本节课我们将通过对比C语言，学习JavaScript的基本语法和核心概念。

---

## 为什么学习JavaScript？🤔

JavaScript是构建现代Web应用的核心语言。它拥有庞大的生态系统和开源库，能帮助开发者快速构建应用。学习JavaScript不仅是为了掌握一门新语言，更是为了理解如何高效地学习第二门编程语言。

---

## JavaScript与C语言对比 🆚

上一节我们介绍了学习JavaScript的原因，本节中我们来看看它与C语言的主要区别。

以下是两种语言的关键差异：

| 特性 | C语言 | JavaScript |
| :--- | :--- | :--- |
| **范式** | 过程式 | 多范式（过程式、函数式、面向对象） |
| **类型系统** | 静态类型（如 `int`, `double`） | 动态类型（无显式类型声明） |
| **内存管理** | 手动（`malloc`/`free`） | 自动垃圾回收 |
| **编译/解释** | 编译型语言 | 解释型语言（通过Node.js运行） |
| **指针** | 支持指针运算 | 不支持指针 |

![](img/8745e98bc46b158cc24032f59bc347ef_3.png)

![](img/8745e98bc46b158cc24032f59bc347ef_4.png)

![](img/8745e98bc46b158cc24032f59bc347ef_5.png)

![](img/8745e98bc46b158cc24032f59bc347ef_7.png)

**核心区别公式化描述**：
*   **C语言函数定义**: `int min(int a, int b) { ... }`
*   **JavaScript函数定义**: `function min(a, b) { ... }`

主要区别在于JavaScript函数没有返回类型和参数类型的声明。

![](img/8745e98bc46b158cc24032f59bc347ef_9.png)

---

![](img/8745e98bc46b158cc24032f59bc347ef_11.png)

## 运行JavaScript代码 ▶️

在C语言中，我们需要先编译(`gcc`)，再运行可执行文件。JavaScript则通过Node.js直接解释执行。

![](img/8745e98bc46b158cc24032f59bc347ef_13.png)

**C语言运行步骤**:
```bash
gcc -o program program.c
./program
```

![](img/8745e98bc46b158cc24032f59bc347ef_15.png)

**JavaScript运行步骤**:
```bash
node program.js
```

`node` 是一个命令行工具，它读取`.js`文件中的代码并立即执行。这种“边解释边执行”的方式使得JavaScript开发流程更快捷。

![](img/8745e98bc46b158cc24032f59bc347ef_17.png)

![](img/8745e98bc46b158cc24032f59bc347ef_19.png)

---

![](img/8745e98bc46b158cc24032f59bc347ef_21.png)

## 变量与常量 📦

![](img/8745e98bc46b158cc24032f59bc347ef_23.png)

在JavaScript中，我们使用 `let` 和 `const` 来声明变量，而不是指定类型（如 `int`）。

*   `let`: 用于声明可重新赋值的变量。
*   `const`: 用于声明常量，其值不可改变。

**代码示例**:

![](img/8745e98bc46b158cc24032f59bc347ef_25.png)

```javascript
let changeable = 10; // 这个值可以改变
changeable = 20;     // 正确
const constant = 5;  // 这个值不可改变
constant = 8;        // 错误！TypeError
```

![](img/8745e98bc46b158cc24032f59bc347ef_27.png)

JavaScript的变量可以持有任何类型的数据，包括数字、字符串、布尔值，以及特殊的 `undefined` 和 `null`。

---

![](img/8745e98bc46b158cc24032f59bc347ef_29.png)

## 字符串操作 🔤

![](img/8745e98bc46b158cc24032f59bc347ef_31.png)

![](img/8745e98bc46b158cc24032f59bc347ef_32.png)

![](img/8745e98bc46b158cc24032f59bc347ef_33.png)

字符串处理在JavaScript中比在C语言中简单得多。你可以使用加号(`+`)来连接字符串。

**代码示例**:
```javascript
let greeting = "Hello";
greeting = greeting + " " + "World!"; // greeting 现在为 "Hello World!"
greeting += " How are you?";          // 等同于 greeting = greeting + " How are you?"
```

**模板字符串**是一种更强大的字符串创建方式，允许嵌入变量或表达式。

![](img/8745e98bc46b158cc24032f59bc347ef_35.png)

**代码示例**:
```javascript
const name = "Hayden";
const age = 7;
const message = `Hello, my name is ${name} and I am ${age} years old.`;
console.log(message); // 输出: Hello, my name is Hayden and I am 7 years old.
```
**注意**：模板字符串使用反引号（`` ` ``）而非单引号或双引号。

![](img/8745e98bc46b158cc24032f59bc347ef_37.png)

![](img/8745e98bc46b158cc24032f59bc347ef_39.png)

---

![](img/8745e98bc46b158cc24032f59bc347ef_41.png)

## 控制结构 🎛️

如果你熟悉C语言，那么JavaScript的 `if`、`else`、`while` 和 `for` 循环看起来会非常亲切。语法几乎一致，只是去掉了类型声明。

![](img/8745e98bc46b158cc24032f59bc347ef_43.png)

**代码示例**:
```javascript
// if-else 语句
if (score > 90) {
    grade = 'A';
} else if (score > 80) {
    grade = 'B';
} else {
    grade = 'C';
}

// while 循环
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}

// for 循环
for (let j = 0; j < 5; j++) {
    console.log(j);
}
```

---

![](img/8745e98bc46b158cc24032f59bc347ef_45.png)

## 函数 📞

![](img/8745e98bc46b158cc24032f59bc347ef_47.png)

JavaScript使用 `function` 关键字定义函数。由于是动态类型，我们不需要指定参数和返回值的类型。

**代码示例**:
```javascript
function add(a, b) {
    return a + b;
}

const result = add(3, 5); // 调用函数
console.log(result);      // 输出: 8
```
函数是JavaScript的一等公民，可以像变量一样被传递和使用。

![](img/8745e98bc46b158cc24032f59bc347ef_49.png)

![](img/8745e98bc46b158cc24032f59bc347ef_50.png)

![](img/8745e98bc46b158cc24032f59bc347ef_52.png)

---

![](img/8745e98bc46b158cc24032f59bc347ef_54.png)

![](img/8745e98bc46b158cc24032f59bc347ef_56.png)

![](img/8745e98bc46b158cc24032f59bc347ef_57.png)

![](img/8745e98bc46b158cc24032f59bc347ef_58.png)

## 数据结构：顺序集合 (数组) 🗃️

![](img/8745e98bc46b158cc24032f59bc347ef_60.png)

数组是JavaScript中最常用的顺序集合，用于存储有序的数据列表。与C语言的数组相比，JavaScript数组更加灵活和强大。

![](img/8745e98bc46b158cc24032f59bc347ef_62.png)

![](img/8745e98bc46b158cc24032f59bc347ef_64.png)

以下是创建和操作数组的基本方法：

![](img/8745e98bc46b158cc24032f59bc347ef_66.png)

1.  **创建数组**:
    ```javascript
    const fruits = ['apple', 'banana', 'orange'];
    ```

![](img/8745e98bc46b158cc24032f59bc347ef_68.png)

2.  **访问与修改元素**:
    ```javascript
    console.log(fruits[0]); // 输出: 'apple'
    fruits[1] = 'grape';    // 将第二个元素改为 'grape'
    ```

![](img/8745e98bc46b158cc24032f59bc347ef_70.png)

![](img/8745e98bc46b158cc24032f59bc347ef_72.png)

3.  **添加元素**:
    ```javascript
    fruits.push('mango');   // 在数组末尾添加 'mango'
    ```

![](img/8745e98bc46b158cc24032f59bc347ef_74.png)

4.  **获取数组长度**:
    ```javascript
    console.log(fruits.length); // 输出: 4
    ```

**遍历数组**有多种简洁的方法：

![](img/8745e98bc46b158cc24032f59bc347ef_76.png)


![](img/8745e98bc46b158cc24032f59bc347ef_78.png)

![](img/8745e98bc46b158cc24032f59bc347ef_80.png)

```javascript
// 方法1: 传统的 for 循环
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
// 方法2: for...of 循环 (获取值)
for (const fruit of fruits) {
    console.log(fruit);
}
// 方法3: for...in 循环 (获取索引)
for (const index in fruits) {
    console.log(index, fruits[index]);
}
```
数组是“对象”，内置了许多有用的方法，如 `.push()`, `.pop()`, `.includes()` 等。

---

![](img/8745e98bc46b158cc24032f59bc347ef_82.png)

![](img/8745e98bc46b158cc24032f59bc347ef_84.png)

![](img/8745e98bc46b158cc24032f59bc347ef_86.png)

## 数据结构：关联集合 (对象) 🗂️

对象是JavaScript的关联集合，类似于C语言中的结构体(`struct`)，但功能更强大。它用于存储键值对(`key-value pairs`)。

![](img/8745e98bc46b158cc24032f59bc347ef_88.png)

**代码示例**:

![](img/8745e98bc46b158cc24032f59bc347ef_90.png)

![](img/8745e98bc46b158cc24032f59bc347ef_92.png)

![](img/8745e98bc46b158cc24032f59bc347ef_94.png)

![](img/8745e98bc46b158cc24032f59bc347ef_96.png)

![](img/8745e98bc46b158cc24032f59bc347ef_98.png)


![](img/8745e98bc46b158cc24032f59bc347ef_100.png)

```javascript
// 创建一个对象
const student = {
    zid: 'z1234567',
    name: 'Alice',
    mark: 85
};
// 访问属性
console.log(student.name); // 输出: 'Alice'
console.log(student['zid']); // 输出: 'z1234567' (另一种访问方式)
// 修改或添加属性
student.mark = 90;       // 修改现有属性
student.grade = 'HD';    // 添加新属性
```
对象是动态的，可以随时添加或删除属性。

![](img/8745e98bc46b158cc24032f59bc347ef_102.png)

![](img/8745e98bc46b158cc24032f59bc347ef_104.png)

**遍历对象**:
```javascript
for (const key in student) {
    console.log(`${key}: ${student[key]}`);
}
// 输出:
// zid: z1234567
// name: Alice
// mark: 90
// grade: HD
```
你也可以使用 `Object.keys()`, `Object.values()`, `Object.entries()` 等内置方法来处理对象。

![](img/8745e98bc46b158cc24032f59bc347ef_106.png)

---

![](img/8745e98bc46b158cc24032f59bc347ef_108.png)

![](img/8745e98bc46b158cc24032f59bc347ef_110.png)

## 组合使用数组与对象 🤝

![](img/8745e98bc46b158cc24032f59bc347ef_112.png)

![](img/8745e98bc46b158cc24032f59bc347ef_114.png)

在实际开发中，我们经常组合使用数组和对象来建模复杂数据。

**代码示例**: 一个包含多个学生对象的数组。

![](img/8745e98bc46b158cc24032f59bc347ef_116.png)

![](img/8745e98bc46b158cc24032f59bc347ef_117.png)

```javascript
const students = [
    { name: 'Alice', score: 92 },
    { name: 'Bob', score: 78 },
    { name: 'Charlie', score: 88 }
];
// 找出成绩高于85分的学生
for (const student of students) {
    if (student.score > 85) {
        console.log(`${student.name} got an HD!`);
    }
}
```

![](img/8745e98bc46b158cc24032f59bc347ef_119.png)

![](img/8745e98bc46b158cc24032f59bc347ef_121.png)

---

![](img/8745e98bc46b158cc24032f59bc347ef_123.png)

![](img/8745e98bc46b158cc24032f59bc347ef_125.png)

## 重要注意事项与总结 🎯

本节课中我们一起学习了JavaScript的基础知识。最后，有几个关键点需要牢记：

1.  **相等性比较**：在JavaScript中，使用 `===`（严格相等）和 `!==`（严格不相等）来比较值和类型，避免使用 `==` 和 `!=`，因为它们会进行类型转换，可能导致意想不到的结果。
    ```javascript
    if (variable === 10) { /* 正确 */ }
    if (variable == 10) {  /* 避免使用 */ }
    ```

![](img/8745e98bc46b158cc24032f59bc347ef_127.png)

2.  **注释**：JavaScript的注释语法与C语言相同。
    ```javascript
    // 这是单行注释

    /*
    这是
    多行
    注释
    */
    ```

![](img/8745e98bc46b158cc24032f59bc347ef_129.png)

3.  **`null` 与 `undefined`**：两者都表示“无”的值，但含义略有不同。`undefined` 通常表示变量已声明但未赋值，而 `null` 表示一个空值或“空对象”的引用。在初学阶段，可以先按需使用其一并保持一致性。

![](img/8745e98bc46b158cc24032f59bc347ef_131.png)

JavaScript是一门强大而灵活的语言，初次接触可能会觉得它比C语言“大”得多，这是正常的。不要试图一次性掌握所有细节，通过实践和构建项目，你会逐渐熟悉它。核心在于理解其动态类型、灵活的数据结构以及基于原型的面向对象思想。