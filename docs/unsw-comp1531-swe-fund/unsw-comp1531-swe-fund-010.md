# 010：静态验证 🛡️

在本节课中，我们将要学习静态验证，这是继上周关于动态测试（Jest）讲座之后的逻辑延续。我们将探讨什么是类型安全，并介绍TypeScript语言，通过一系列示例来展示如何利用静态类型检查在代码运行前提升软件的安全性。

## 概述

![](img/71bbe526b35bef4d46131c32b0431a03_1.png)

![](img/71bbe526b35bef4d46131c32b0431a03_3.png)

![](img/71bbe526b35bef4d46131c32b0431a03_5.png)

上一节我们介绍了通过动态测试（如Jest）来验证软件正确性。本节中，我们来看看静态验证，它旨在在代码运行前（编译时）就发现潜在问题。我们将重点关注**类型安全**，并学习如何使用**TypeScript**来实现它。

![](img/71bbe526b35bef4d46131c32b0431a03_7.png)

## 静态验证与类型安全

![](img/71bbe526b35bef4d46131c32b0431a03_9.png)

静态验证的核心思想是在代码运行前进行检查。**类型安全**是其主要关注点，它旨在防止变量、常量和函数的实际类型与预期类型不匹配。

例如，在JavaScript中，你可以比较一个数字和一个字符串，代码会运行但可能产生错误结果。而在C语言中，类似的代码会在编译时产生错误，阻止程序运行。这就是类型安全检查的作用。

**公式/代码示例：**
```javascript
// JavaScript (非类型安全)
const a = 4;
const b = "hi";
if (a == b) { // 会运行，但逻辑可能错误
    // ...
}

// C (类型安全)
int a = 4;
char* b = "hi";
if (a == b) { // 编译错误：指针与整数比较
    // ...
}
```

## 为什么需要TypeScript？

![](img/71bbe526b35bef4d46131c32b0431a03_11.png)

![](img/71bbe526b35bef4d46131c32b0431a03_13.png)

![](img/71bbe526b35bef4d46131c32b0431a03_14.png)

JavaScript本身是动态、弱类型的语言，不提供编译时的类型安全检查。为了弥补这一点，我们引入了**TypeScript**。

![](img/71bbe526b35bef4d46131c32b0431a03_16.png)

TypeScript是构建在JavaScript之上的语言，语法极其相似，但增加了静态类型检查功能。你可以将其视为JavaScript的“保镖”，在运行前对类型进行额外检查。

![](img/71bbe526b35bef4d46131c32b0431a03_18.png)

**代码示例：**
```typescript
// TypeScript 函数定义
function sum(a: number, b: number): number {
    return a + b;
}
console.log(sum(1, 2)); // 正确
console.log(sum(1, "2")); // 编译错误：类型不匹配
```

![](img/71bbe526b35bef4d46131c32b0431a03_20.png)

![](img/71bbe526b35bef4d46131c32b0431a03_22.png)

![](img/71bbe526b35bef4d46131c32b0431a03_23.png)

## 运行TypeScript代码

![](img/71bbe526b35bef4d46131c32b0431a03_25.png)

![](img/71bbe526b35bef4d46131c32b0431a03_27.png)

由于Node.js无法直接运行`.ts`文件，我们需要安装相关工具。

以下是运行TypeScript所需的步骤：

![](img/71bbe526b35bef4d46131c32b0431a03_29.png)

![](img/71bbe526b35bef4d46131c32b0431a03_30.png)

![](img/71bbe526b35bef4d46131c32b0431a03_32.png)

![](img/71bbe526b35bef4d46131c32b0431a03_34.png)

![](img/71bbe526b35bef4d46131c32b0431a03_36.png)

1.  **安装依赖库**：`typescript` 和 `ts-node`。
    ```bash
    npm install --save-dev typescript ts-node
    ```
2.  **运行代码**：使用`ts-node`命令。
    ```bash
    ./node_modules/.bin/ts-node yourfile.ts
    ```
    为了方便，可以在`package.json`中配置脚本：
    ```json
    {
      "scripts": {
        "ts-node": "ts-node",
        "tsc": "tsc"
      }
    }
    ```
    然后通过 `npm run ts-node yourfile.ts` 运行。

`tsc`是TypeScript编译器，仅进行类型检查而不运行代码，类似于C语言中的`gcc -c`。

![](img/71bbe526b35bef4d46131c32b0431a03_38.png)

![](img/71bbe526b35bef4d46131c32b0431a03_40.png)

![](img/71bbe526b35bef4d46131c32b0431a03_42.png)

## TypeScript核心概念示例

![](img/71bbe526b35bef4d46131c32b0431a03_44.png)

现在，我们通过一些示例来了解TypeScript的核心特性。

### 1. 基础类型注解

为变量和函数参数添加类型是最常见的用法。

![](img/71bbe526b35bef4d46131c32b0431a03_46.png)

![](img/71bbe526b35bef4d46131c32b0431a03_48.png)

![](img/71bbe526b35bef4d46131c32b0431a03_50.png)

![](img/71bbe526b35bef4d46131c32b0431a03_51.png)

**代码示例：**
```typescript
function greet(name: string): string {
    return `Hello, ${name}`;
}
const firstName: string = "Hayden";
```

![](img/71bbe526b35bef4d46131c32b0431a03_53.png)

![](img/71bbe526b35bef4d46131c32b0431a03_55.png)

TypeScript具有强大的**类型推断**能力，在许多情况下可以自动推导出类型，无需显式注解。
```typescript
const firstName = "Hayden"; // TypeScript 推断出类型为 string
```

### 2. 联合类型

当一个值可以是多种类型之一时，使用联合类型。

**代码示例：**
```typescript
function printIfReady(ready: boolean | number) {
    if (ready === true || ready !== 0) {
        console.log(ready);
    }
}
printIfReady(true);  // 通过
printIfReady(1);     // 通过
printIfReady("now"); // 编译错误：类型不匹配
```

### 3. 数组类型

![](img/71bbe526b35bef4d46131c32b0431a03_57.png)

![](img/71bbe526b35bef4d46131c32b0431a03_59.png)

定义数组包含的元素类型。

![](img/71bbe526b35bef4d46131c32b0431a03_61.png)

![](img/71bbe526b35bef4d46131c32b0431a03_62.png)

![](img/71bbe526b35bef4d46131c32b0431a03_64.png)

**代码示例：**
```typescript
function createList(item: string | number): (string | number)[] {
    const arr: (string | number)[] = [];
    for (let i = 0; i < 10; i++) {
        arr.push(item);
    }
    return arr;
}
// 或使用 Array<type> 语法
const numArray: Array<number> = [1, 2, 3];
```

![](img/71bbe526b35bef4d46131c32b0431a03_66.png)

![](img/71bbe526b35bef4d46131c32b0431a03_68.png)

### 4. 类型别名

使用`type`关键字创建类型别名，提高代码可读性和复用性。

![](img/71bbe526b35bef4d46131c32b0431a03_70.png)

![](img/71bbe526b35bef4d46131c32b0431a03_71.png)

![](img/71bbe526b35bef4d46131c32b0431a03_73.png)

![](img/71bbe526b35bef4d46131c32b0431a03_75.png)

**代码示例：**

![](img/71bbe526b35bef4d46131c32b0431a03_77.png)

![](img/71bbe526b35bef4d46131c32b0431a03_79.png)

![](img/71bbe526b35bef4d46131c32b0431a03_81.png)

```typescript
type ListItem = string | number;
type StringArray = Array<string>;
function processItems(items: ListItem[]): StringArray {
    // ...
}
```

![](img/71bbe526b35bef4d46131c32b0431a03_83.png)

### 5. 可选参数与属性

使用`?`标记函数参数或对象属性为可选。

**代码示例：**

![](img/71bbe526b35bef4d46131c32b0431a03_85.png)

```typescript
// 可选函数参数
function substring(str: string, start: number, end?: number): string {
    const actualEnd = end ?? str.length;
    let result = "";
    for (let i = start; i < actualEnd; i++) {
        result += str[i];
    }
    return result;
}
console.log(substring("Hayden", 0, 3)); // "Hay"
console.log(substring("Hayden", 2));    // "yden"
// 可选对象属性
type Person = {
    name: string;
    age?: number; // age 可能不存在
};
const person1: Person = { name: "Hayden" }; // 正确
const person2: Person = { name: "Alex", age: 25 }; // 正确
```

![](img/71bbe526b35bef4d46131c32b0431a03_87.png)

### 6. 对象类型

显式定义对象的结构。

![](img/71bbe526b35bef4d46131c32b0431a03_89.png)

![](img/71bbe526b35bef4d46131c32b0431a03_91.png)

![](img/71bbe526b35bef4d46131c32b0431a03_92.png)

![](img/71bbe526b35bef4d46131c32b0431a03_93.png)

**代码示例：**

![](img/71bbe526b35bef4d46131c32b0431a03_95.png)

![](img/71bbe526b35bef4d46131c32b0431a03_97.png)

```typescript
type Person = {
    name: string;
    age?: number;
    height?: number;
};
const person: Person = {
    name: "Hayden"
};
person.age = 5; // 正确，因为 age 是可选属性
```

![](img/71bbe526b35bef4d46131c32b0431a03_99.png)

![](img/71bbe526b35bef4d46131c32b0431a03_101.png)

### 7. 字面量类型

将类型限制为特定的值。

![](img/71bbe526b35bef4d46131c32b0431a03_103.png)

![](img/71bbe526b35bef4d46131c32b0431a03_105.png)

**代码示例：**
```typescript
type Visibility = "public" | "private";
function setVisibility(vis: Visibility) {
    // ...
}
setVisibility("public");  // 正确
setVisibility("hidden");  // 编译错误

// 数字字面量类型 (较少用，仅作演示)
type SmallNumber = 1 | 2 | 3 | 4 | 5;
function addSmall(a: SmallNumber, b: SmallNumber) {
    return a + b;
}
addSmall(3, 4); // 正确
addSmall(3, 10); // 编译错误
```

![](img/71bbe526b35bef4d46131c32b0431a03_107.png)

![](img/71bbe526b35bef4d46131c32b0431a03_109.png)

### 8. `any` 类型

`any`类型是“逃生舱口”，它禁用类型检查，应谨慎使用。

![](img/71bbe526b35bef4d46131c32b0431a03_111.png)

![](img/71bbe526b35bef4d46131c32b0431a03_113.png)

![](img/71bbe526b35bef4d46131c32b0431a03_115.png)

**代码示例：**
```typescript
let uncertainValue: any = "could be anything";
uncertainValue = 42;        // 正确
uncertainValue = true;      // 正确
// 使用 any 会失去类型安全保护
```

![](img/71bbe526b35bef4d46131c32b0431a03_117.png)

![](img/71bbe526b35bef4d46131c32b0431a03_119.png)

## 类型安全语言分类

![](img/71bbe526b35bef4d46131c32b0431a03_121.png)

![](img/71bbe526b35bef4d46131c32b0431a03_123.png)

*   **内置强制静态类型检查**：如 C、Haskell、Java。类型必须声明，编译器严格检查。
*   **内置可选类型检查**：如 TypeScript、Objective-C。类型系统存在，但可以部分忽略或宽松处理。
*   **外部可选类型检查器**：如 Python (MyPy)、Ruby。类型检查通过第三方工具实现。

![](img/71bbe526b35bef4d46131c32b0431a03_125.png)

![](img/71bbe526b35bef4d46131c32b0431a03_127.png)

## 课程中的TypeScript

在本课程中，我们将以渐进的方式引入TypeScript：
*   **迭代2开始**：项目代码库将迁移到TypeScript。
*   **轻量级集成**：初始设置会较为宽松，避免类型错误阻碍开发进度。
*   **持续集成**：TypeScript检查 (`tsc`) 将被添加到GitLab CI流水线中，在每次代码推送时自动运行。
*   **奖励机制**：为了鼓励使用，在项目后期，确保代码完全通过类型检查可能会与奖励分数关联。

## 总结

![](img/71bbe526b35bef4d46131c32b0431a03_129.png)

本节课中我们一起学习了静态验证的核心概念——**类型安全**。我们探讨了JavaScript在类型安全上的不足，并引入了**TypeScript**作为解决方案。通过一系列示例，我们了解了如何为变量、函数、数组、对象等添加类型注解，以及如何使用联合类型、可选属性、字面量类型等高级特性来构建更健壮、更易维护的代码。记住，静态类型检查的目标是将错误发现阶段从运行时提前到编译时，从而提升软件的安全性和开发效率。