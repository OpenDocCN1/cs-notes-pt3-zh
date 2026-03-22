# 016：异常处理 🚨

![](img/26c5d7975cd77b4ac458eb3afb3519a5_1.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_2.png)

在本节课中，我们将学习一种处理程序中错误的更优雅、更健壮的方法——异常处理。到目前为止，我们主要通过返回错误对象等方式来处理错误，这是一种较为传统的方式。而异常是存在于大多数现代编程语言中的强大概念，它允许我们更优雅地从错误中恢复，使程序更加健壮。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_4.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_5.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_7.png)

## 为什么需要异常？

上一节我们介绍了传统的错误处理方式。本节中，我们来看看一个简单的程序示例，并分析其局限性。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_9.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_11.png)

我们有一个名为 `justCrash` 的程序，它提示用户输入一个数字并计算其平方根。如果输入的数字小于0，程序会打印错误信息并退出。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_13.png)

```javascript
import promptSync from 'prompt-sync';
const prompt = promptSync({});

![](img/26c5d7975cd77b4ac458eb3afb3519a5_15.png)

function sqrt(x: number): number {
    if (x < 0) {
        console.error('Error: Input less than 0');
        process.exit(1);
    }
    return Math.pow(x, 0.5);
}

![](img/26c5d7975cd77b4ac458eb3afb3519a5_17.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_18.png)

const input = prompt('Please enter a number: ');
console.log(sqrt(parseInt(input)));
```

![](img/26c5d7975cd77b4ac458eb3afb3519a5_20.png)

这种方法的问题是，它直接导致程序崩溃，这不是良好的程序设计。我们可能会想，可以返回 `null` 或其他特殊值来代替崩溃。

```javascript
function sqrt(x: number): number | null {
    if (x < 0) {
        return null;
    }
    return Math.pow(x, 0.5);
}
```

![](img/26c5d7975cd77b4ac458eb3afb3519a5_22.png)

但这种方法存在局限性：从类型角度看可能变得复杂；如果 `null` 本身是一个有意义的返回值，就会产生混淆。

## 抛出异常

为了解决上述问题，我们引入“抛出异常”的概念。以下是修改后的 `sqrt` 函数：

```javascript
function sqrt(x: number): number {
    if (x < 0) {
        throw new Error('Error: Input less than 0');
    }
    return Math.pow(x, 0.5);
}
```

关键字 `throw` 用于“抛出”一个异常。`new Error(‘...’)` 创建了一个包含错误信息的异常对象。当这行代码执行时，程序的正常流程会被中断。

运行这个程序，当输入负数时，程序会崩溃，并在控制台输出详细的错误堆栈信息。这与直接退出相比，提供了更丰富的调试信息。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_24.png)

## 捕获和处理异常

![](img/26c5d7975cd77b4ac458eb3afb3519a5_26.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_28.png)

仅仅抛出异常还不够，我们还需要能够“捕获”并处理它们，这才是异常机制价值所在。为此，我们使用 `try...catch` 语句块。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_30.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_32.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_34.png)

```javascript
try {
    // 尝试执行可能会抛出异常的代码
    const input = prompt('Please enter a number: ');
    console.log(sqrt(parseInt(input)));
    console.log(‘Third line’); // 如果上一行抛出异常，这行不会执行
} catch (error) {
    // 当try块中的代码抛出异常时，跳转到这里执行
    console.error(‘There was an error:’, error.message);
}
console.log(‘Done’);
```

![](img/26c5d7975cd77b4ac458eb3afb3519a5_36.png)

以下是 `try...catch` 的工作流程：
*   `try` 块中的代码会正常执行。
*   如果 `try` 块中的任何代码抛出了异常，程序会立即停止执行 `try` 块中剩余的代码，并跳转到对应的 `catch` 块。
*   `catch` 块接收被抛出的异常对象（通常命名为 `error`），并处理这个错误。
*   无论是否发生异常，`catch` 块之后的代码（‘Done’）都会继续执行。

这种“中断-跳转”的机制，避免了使用返回值时需要在每一步进行错误检查的繁琐。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_38.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_40.png)

## 在循环中使用异常

![](img/26c5d7975cd77b4ac458eb3afb3519a5_42.png)

我们可以结合循环，实现更友好的用户交互，例如持续要求用户输入，直到输入有效。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_44.png)

```javascript
let success = false;
while (!success) {
    try {
        const input = prompt(‘Please enter a number: ‘);
        console.log(sqrt(parseInt(input)));
        success = true; // 只有未抛出异常时才会执行到这里
    } catch (error) {
        console.error(‘Invalid input, try again.’);
    }
}
```

![](img/26c5d7975cd77b4ac458eb3afb3519a5_46.png)

## 异常对象与测试

被捕获的 `error` 对象包含了异常的详细信息。通常，我们可以通过 `error.message` 属性获取创建异常时传入的描述字符串。

在编写单元测试时，我们也需要测试函数是否会按预期抛出异常。以下是使用 Jest 测试框架的示例：

```javascript
import { sqrt } from ‘./sqrt’;

![](img/26c5d7975cd77b4ac458eb3afb3519a5_48.png)

describe(‘sqrt function‘, () => {
    test(‘sqrt of positive number‘, () => {
        expect(sqrt(4)).toBe(2);
    });

    test(‘sqrt throws error for negative input‘, () => {
        // 注意：我们需要传递一个函数，而不是函数调用的结果
        expect(() => sqrt(-2)).toThrow(‘Error: Input less than 0‘);
    });
});
```

![](img/26c5d7975cd77b4ac458eb3afb3519a5_50.png)

测试异常的关键是：`expect` 接受一个**函数**（例如 `() => sqrt(-2)`），然后检查执行该函数时是否抛出了特定信息的异常。如果直接传递 `sqrt(-2)` 的结果，异常会在测试设置前就被抛出，导致测试失败。

![](img/26c5d7975cd77b4ac458eb3afb3519a5_52.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_54.png)

## 总结

![](img/26c5d7975cd77b4ac458eb3afb3519a5_56.png)

![](img/26c5d7975cd77b4ac458eb3afb3519a5_58.png)

本节课中我们一起学习了异常处理的核心概念。我们了解到，异常是一种中断程序正常流程的机制，用于优雅地处理运行时错误。通过 `throw` 关键字可以主动抛出异常，而 `try...catch` 语句块则用于捕获和处理这些异常，防止程序崩溃。异常机制避免了通过返回值传播错误的繁琐，并通过异常对象携带详细的错误信息。最后，我们还学习了如何在单元测试中验证函数是否正确地抛出了异常。掌握异常处理将使你编写的软件更健壮、更易于维护。