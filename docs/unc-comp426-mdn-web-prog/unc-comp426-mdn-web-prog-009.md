# 009：React状态管理 🧠

在本节课中，我们将要学习React的核心概念之一：状态管理。我们将探讨什么是状态，为什么它在Web应用中至关重要，以及React如何通过其独特的机制来简化状态与UI之间的同步过程。

## 课程概述

上一讲我们介绍了React库，并了解了如何使用React组件来构建可组合的用户界面。本节中，我们将重点探讨React的另一个强大功能：状态管理。我们将学习如何定义和更新应用的状态，以及React如何自动响应状态变化来更新用户界面。

## 什么是状态？

在计算机科学中，“状态”一词有多种含义。例如，在有限状态机中，状态代表系统的一种特定配置；在Git版本控制中，状态代表项目在某个时间点的快照。

在Web编程的上下文中，**状态**指的是我们应用程序数据和呈现方式的当前配置。它包含了驱动UI的数据，以及基于这些数据所呈现出的UI外观。

回顾我们之前的像素艺术制作器项目，其底层架构可以对应到经典的MVC（模型-视图-控制器）模式：
*   **视图**：由`index-start.html`文件指定，定义了应用程序的UI（如256个网格单元格、工具栏）。
*   **模型**：由`engine.ts`文件实现，存储应用程序的功能和数据（如代表画布的二维数组）。
*   **控制器**：由`main.ts`文件实现，连接视图和模型，处理事件并更新两者。

在这个架构中，**状态**主要存在于模型中（存储数据），但也体现在视图里（基于数据呈现的UI）。状态的变化会导致UI的更新。

## React的状态管理模型

React采用了一种更简化的架构模型，它主要关注两个部分：**状态**和**UI**。中间的控制器层被React自身抽象和处理了。

其核心思想是：UI可以改变底层状态，而当状态改变时，UI会自动更新以反映新的状态。我们不再需要手动编写代码来同步数据和DOM。

这是通过React的 **`useState` Hook** 来实现的。

### 使用 `useState` Hook

`useState` 是一个函数，它允许我们在React组件内部定义和管理状态。

其基本语法如下：
```javascript
const [stateVariable, setStateFunction] = useState(initialValue);
```



例如，要存储一个计数器：
```javascript
const [counter, setCounter] = useState(0);
```

以下是代码各部分的作用：
*   `useState(0)`：创建状态，并设置其初始值为 `0`。
*   `counter`：这是一个**不可变**的变量，是对当前状态值的引用。我们可以在UI中使用它。
*   `setCounter`：这是一个**函数**，专门用于更新`counter`状态的值。**必须使用这个函数来更新状态**，直接修改变量`counter`不会触发UI更新。





### 一个简单的计数器示例

让我们通过一个计数器组件来看状态管理是如何工作的。

```jsx
function App() {
  // 1. 创建状态来存储计数器
  const [counter, setCounter] = useState(0);

  // 2. 定义一个函数来增加计数器
  function plus() {
    setCounter(counter + 1); // 使用setCounter更新状态
  }

  // 3. UI渲染，使用当前状态值
  return (
    <div>
      <p>当前计数：{counter}</p>
      <button onClick={plus}>增加计数</button>
    </div>
  );
}
```

在这个例子中：
1.  我们创建了一个名为`counter`的状态，初始值为0。
2.  我们定义了一个`plus`函数，它调用`setCounter`将`counter`的值加1。
3.  UI中有一个段落显示`counter`的当前值，以及一个按钮，点击时触发`plus`函数。

当你点击按钮时，`setCounter`被调用，`counter`状态从0变为1。随后，React会自动检测到状态变化，并**重新渲染**依赖于`counter`的UI部分（即段落），将显示内容更新为“当前计数：1”。整个过程无需我们手动操作DOM。

### 关键注意事项



*   **必须使用Setter函数**：更新状态时，必须使用`useState`提供的setter函数（如`setCounter`）。直接修改变量（如`counter = counter + 1`）**不会**触发重新渲染，会导致UI与状态不同步。
*   **组件可以拥有多个状态**：一个组件可以多次调用`useState`来管理多个独立的状态变量。
*   **状态在重新渲染间持久化**：当状态改变触发组件重新渲染时，React函数会从头到尾再次执行。然而，状态值会被保留，不会被重置为初始值。而函数内普通的变量声明会在每次渲染时重新计算。
*   **重新渲染是高效的**：React使用一种称为“协调”的智能算法。当状态改变时，React只会更新DOM中真正发生变化的部分，而不是整个页面，这保证了性能。



## 状态与重新渲染的深入理解

在React中，**视图是状态的函数**。这意味着UI输出是由输入的状态值决定的。

每次状态更新，都会触发一个“重新渲染”周期，包含三步：
1.  **触发**：状态发生改变（例如调用了`setCounter`）。
2.  **渲染**：React调用组件函数，计算新的UI应该是什么样子。
3.  **提交**：React将计算出的变化高效地更新到实际的DOM中。

由于组件函数在每次渲染时都会运行，我们需要理解其影响。





### 计算值与状态

考虑以下组件：
```jsx
function SampleComponent() {
  const [firstName, setFirstName] = useState('John');
  const [lastName, setLastName] = useState('Doe');

  // 这是一个根据状态计算出的普通变量
  const fullName = firstName + ' ' + lastName;

  function changeName() {
    setFirstName('Jane');
  }

  return (
    <div>
      <p>全名：{fullName}</p>
      <button onClick={changeName}>更改名字</button>
    </div>
  );
}
```

**问题**：点击按钮后，屏幕上显示什么？
*   A. John Doe
*   B. Jane Doe
*   C. 出错

**答案是 B. Jane Doe**。

**解析**：
1.  **初始渲染**：`firstName` 为 ‘John’，`lastName` 为 ‘Doe’。`fullName` 被计算为 ‘John Doe’。UI显示 ‘John Doe’。
2.  **点击按钮**：调用 `setFirstName(‘Jane’)`，触发重新渲染。
3.  **第二次渲染**：React函数再次运行。此时状态 `firstName` 已更新为 ‘Jane’，`lastName` 仍为 ‘Doe’。**`fullName` 变量被重新计算**，得到 ‘Jane Doe’。UI更新显示 ‘Jane Doe’。

这个例子说明：**只有通过 `useState` 定义的状态会在重新渲染间保留。组件内的普通变量和表达式会在每次渲染时重新计算。** 因此，我们不需要为 `fullName` 单独创建一个状态，它可以直接作为一个派生值。

### 状态更新的批处理

如果在一个事件处理函数中连续更新多个状态，React会将它们**批量处理**，只触发一次重新渲染，以提高性能。

```jsx
function handleClick() {
  setCounterA(counterA + 1);
  setCounterB(counterB + 1);
  // 这只会导致一次重新渲染，而不是两次
}
```

## 总结

本节课中我们一起学习了React状态管理的核心概念。

我们首先回顾了状态在Web应用中的定义，并将其与MVC架构联系起来。接着，我们探讨了React如何通过简化模型（状态 + UI）和 `useState` Hook 来优雅地管理状态。


我们深入了解了：
*   如何使用 `const [state, setState] = useState(initialValue)` 语法创建和更新状态。
*   **必须使用setter函数**来更新状态以触发UI重新渲染。
*   React组件在状态变化时会重新执行，但状态值会得以保留。
*   视图可以看作是状态的函数，我们可以基于状态派生出其他值。
*   React会智能地批量处理状态更新并高效地更新DOM。






![](img/3706eb233fe7fdd62f323570d4e3a93a_38.png)

理解这些原理是掌握React开发的基础。在接下来的课程和作业中，你将有机会实际应用这些概念来构建动态的交互式Web应用。