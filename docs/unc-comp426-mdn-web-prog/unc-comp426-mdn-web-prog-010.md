# 010：处理副作用 🎯

在本节课中，我们将要学习React中一个核心概念：副作用。我们将了解什么是副作用，为什么它们很重要，以及如何使用React的`useEffect`钩子来管理它们。这对于构建需要与外部数据源（如API）交互的现代Web应用至关重要。

---

## 课程概述

上一节我们介绍了React中状态（State）与UI的自动同步机制。本节中我们来看看当我们的组件需要执行一些“额外”操作时，例如从API获取数据，会发生什么。这些操作被称为“副作用”，我们需要一种特殊的方式来处理它们，以避免不必要的重复执行或无限循环。

---

## 什么是副作用？


在React的渲染循环中，我们主要关注状态改变如何触发UI更新。然而，许多应用需要执行一些超出这个循环的操作，例如：
*   从服务器获取数据。
*   设置全局事件监听器（如键盘事件）。
*   与浏览器本地存储（localStorage）交互。
*   设置定时器。



这些操作被称为**副作用**。它们不是直接由状态改变驱动UI更新的一部分，但又是应用功能所必需的。


**核心问题**：如果我们在组件函数体内直接执行这些操作（如`fetch`），那么**每次组件渲染（包括状态更新引起的渲染）都会执行这些操作**，这通常不是我们想要的。

---

## `useEffect` 钩子简介


React提供了`useEffect`这个钩子函数来专门处理副作用。它允许我们指定一段代码，并控制这段代码在何时运行。


`useEffect`的基本语法是一个接受两个参数的函数：
```javascript
useEffect(() => {
    // 这里放置要执行的副作用代码
}, [dependencyArray]); // 依赖数组
```
第二个参数**依赖数组**决定了副作用代码的执行时机。

---

## `useEffect` 的三种常见使用场景

以下是`useEffect`最主要的三种使用模式：

### 1. 仅在组件首次渲染时执行一次
如果你希望副作用代码（如初始化数据获取）只在组件挂载时运行一次，而在后续渲染中不再运行，可以使用空数组`[]`作为依赖。
```javascript
useEffect(() => {
    fetch(‘/api/data‘)
        .then(response => response.json())
        .then(data => console.log(data));
}, []); // 空依赖数组
```



### 2. 在特定状态改变时执行
如果你希望副作用代码仅在某个或某些特定状态变量改变时才重新执行，可以将这些状态变量放入依赖数组。
```javascript
const [filter, setFilter] = useState(‘‘);
useEffect(() => {
    // 仅当 filter 改变时，才重新获取数据
    fetch(`/api/items?filter=${filter}`)
        .then(response => response.json())
        .then(data => setItems(data));
}, [filter]); // 依赖数组中包含 filter
```



### 3. 在每次渲染后都执行（谨慎使用）
如果你省略依赖数组参数，副作用代码将在**每次**组件渲染后都执行。这很少是需要的，容易导致性能问题。
```javascript
useEffect(() => {
    // 这段代码在每次渲染后都会运行
    console.log(‘组件渲染了！‘);
}); // 没有依赖数组
```

---



## 清理副作用

有些副作用需要清理，例如事件监听器或定时器，以防止组件卸载后它们继续运行导致内存泄漏。

`useEffect`可以返回一个**清理函数**。这个函数会在组件卸载时，或者在依赖项改变、下一次副作用执行**之前**被调用。
```javascript
useEffect(() => {
    const handleKeyPress = (e) => {
        console.log(`按下了: ${e.key}`);
    };
    window.addEventListener(‘keydown‘, handleKeyPress);
    // 返回清理函数
    return () => {
        window.removeEventListener(‘keydown‘, handleKeyPress);
    };
}, []); // 空依赖数组表示只在挂载和卸载时执行
```

---

## 何时不需要使用 `useEffect`

`useEffect`功能强大，但不应滥用。一个常见的误区是使用`useEffect`来同步计算派生状态。

**不推荐的做法**：使用`useEffect`和额外状态来同步计算值。
```javascript
const [firstName, setFirstName] = useState(‘‘);
const [lastName, setLastName] = useState(‘‘);
const [fullName, setFullName] = useState(‘‘);
// 不必要的 useEffect
useEffect(() => {
    setFullName(`${firstName} ${lastName}`);
}, [firstName, lastName]);
```

**推荐的做法**：直接在渲染过程中计算。因为状态改变会触发重新渲染，所以每次渲染都会得到最新的计算值。
```javascript
const [firstName, setFirstName] = useState(‘‘);
const [lastName, setLastName] = useState(‘‘);
// 直接计算
const fullName = `${firstName} ${lastName}`;
```
这种方法更简单，且避免了由`setFullName`触发的额外、不必要的渲染。

---

## 性能优化：使用 `useMemo` 记忆化昂贵计算

当组件内有一个计算量很大的函数，并且这个计算依赖于某些状态或属性时，我们不希望每次渲染都重新计算，尤其是当依赖项没有改变时。

**问题场景**：一个过滤和排序歌曲列表的函数非常耗时，但只有当歌曲列表本身改变时才需要重新计算。用户选择某首歌曲（触发状态更新）时不应重新计算。
```javascript
function SongList({ songs }) {
    const [selectedSongId, setSelectedSongId] = useState(null);
    // 每次渲染（包括选择歌曲时）都会执行这个昂贵操作，这很糟糕！
    const curatedSongs = expensiveFilterAndSort(songs);
    // ... 渲染逻辑
}
```

**解决方案**：使用`useMemo`钩子来“记忆化”计算结果。它接收一个计算函数和一个依赖数组，只有当依赖项改变时，才会重新执行计算函数。
```javascript
import { useMemo, useState } from ‘react‘;
function SongList({ songs }) {
    const [selectedSongId, setSelectedSongId] = useState(null);
    // 仅当 `songs` 改变时，才会重新计算 curatedSongs
    const curatedSongs = useMemo(() => {
        return expensiveFilterAndSort(songs);
    }, [songs]); // 依赖项是 songs
    // ... 渲染逻辑
}
```
这样，即使用户频繁点击选择不同的歌曲（`selectedSongId`改变），只要`songs`列表没变，`curatedSongs`就会直接返回之前缓存的结果，极大提升性能。

---

## 本节课总结

本节课中我们一起学习了React中处理副作用的核心知识：
1.  **副作用**是指那些不直接参与UI渲染但必要的操作，如数据获取、订阅事件等。
2.  **`useEffect`钩子**是管理副作用的工具，通过**依赖数组**可以精确控制副作用代码的执行时机（首次渲染、特定状态变化时）。
3.  对于需要清理的副作用（如事件监听），`useEffect`可以通过**返回一个清理函数**来实现。
4.  应避免滥用`useEffect**。对于派生状态，应优先选择在渲染过程中直接计算，而不是用`useEffect`去同步状态。
5.  对于性能敏感的**昂贵计算**，可以使用`useMemo`钩子进行记忆化，避免不必要的重复计算。

![](img/c428a28c3278f1e53710d28db478088c_24.png)

掌握这些概念将使你能够构建出功能正确、性能高效且可维护的React应用程序。