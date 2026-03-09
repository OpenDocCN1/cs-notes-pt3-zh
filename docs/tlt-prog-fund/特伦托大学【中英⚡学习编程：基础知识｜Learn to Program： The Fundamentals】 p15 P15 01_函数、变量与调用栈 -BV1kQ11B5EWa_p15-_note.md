# 学习编程：基础知识：P15：函数、变量与调用栈 🧠

![](img/4105a3d1442b5a29abef10dce5dfde43_0.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_2.png)

在本节课中，我们将要学习变量的创建时机、它们在计算机内存中的生命周期，以及当两个不同函数中存在同名变量时会发生什么。理解这些概念对于掌握程序执行流程至关重要。

---

![](img/4105a3d1442b5a29abef10dce5dfde43_4.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_5.png)

上一节我们介绍了函数的基本概念，本节中我们来看看函数调用时内存的具体变化。

![](img/4105a3d1442b5a29abef10dce5dfde43_7.png)

我们首先看到函数 `convert_to_minutes`，这是在函数可视化课程中探讨过的。我们新增了函数 `convert_to_seconds`，它用于将小时数转换为等效的秒数。

`convert_to_seconds` 函数通过调用 `convert_to_minutes` 来完成其工作，然后将结果乘以 60。其核心逻辑可以用以下公式表示：
**`seconds = convert_to_minutes(hours) * 60`**

---

![](img/4105a3d1442b5a29abef10dce5dfde43_9.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_10.png)

让我们使用可视化工具来探索这个过程。我们快速跳过函数定义部分。

两个函数对象被创建。`convert_to_minutes` 指向其中一个函数对象，`convert_to_seconds` 指向另一个。现在，我们即将执行一个赋值语句。

第一步是计算右侧表达式，这是一个函数调用。Python 首先计算参数并为其值创建一个对象。接着，Python 在调用栈上创建一个栈帧，并将值 `2` 的内存地址存储在参数 `num_hours` 中。

![](img/4105a3d1442b5a29abef10dce5dfde43_12.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_14.png)

作为提醒，这个区域被称为**调用栈**。它被显示为一个倒置的栈帧堆叠。在执行函数调用期间，会创建一个新的栈帧。每当一个函数退出时，当前的栈帧就会被擦除，并继续执行上一个函数。

`convert_to_seconds` 函数体中的第一行是另一个赋值语句。右侧是一个函数调用。我们遵循一贯的规则。

以下是执行步骤：
1.  计算参数 `num_hours`，它包含值 `2` 的内存地址。
2.  为 `convert_to_minutes` 的调用创建一个栈帧，其参数 `num_hours` 包含该值的内存地址。

![](img/4105a3d1442b5a29abef10dce5dfde43_16.png)

现在有两个名为 `num_hours` 的变量。一个在 `convert_to_minutes` 调用的栈帧中，另一个在 `convert_to_seconds` 调用的栈帧中。Python 将这两个正在运行的函数保存在内存的不同区域，因此不会混淆该使用哪个变量。

---

![](img/4105a3d1442b5a29abef10dce5dfde43_18.png)

继续跟踪执行过程。`convert_to_minutes` 函数体中的第一行是一个赋值语句。右侧是一个表达式 `num_hours * 60`。但我们应该使用哪个 `num_hours` 呢？

答案是 Python 会查看当前的栈帧。`num_hours` 指向 `2`，因此 `num_hours * 60` 的计算结果是 `120`。赋值语句的第二步是将 `120` 赋值给变量 `minutes`。

![](img/4105a3d1442b5a29abef10dce5dfde43_20.png)

如果变量 `minutes` 在当前栈帧中不存在，那么它将被创建。每个栈帧都包含自己的一组变量。在 `convert_to_minutes` 的栈帧中，变量是 `num_hours` 和 `minutes`。`convert_to_seconds` 的栈帧目前只有变量 `num_hours`，尽管在其执行结束时，它也将拥有 `minutes` 和 `seconds`。

![](img/4105a3d1442b5a29abef10dce5dfde43_21.png)

主程序的栈帧目前包含 `convert_to_minutes` 和 `convert_to_seconds`，尽管当第 20 行的赋值语句执行完毕时，变量 `seconds` 也会出现在那里。

![](img/4105a3d1442b5a29abef10dce5dfde43_23.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_24.png)

---

我们现在即将返回变量 `minutes` 的值并退出当前函数。但是我们要返回到哪里呢？答案总是返回到调用栈上的下一个栈帧。当前的栈帧是在这次 `convert_to_minutes` 调用期间创建的。当这次调用完成时，当前的栈帧被擦除，Python 将返回值作为这个函数调用表达式的值。

这次调用位于一个赋值语句的右侧。为了完成赋值，变量 `minutes` 将被创建，Python 将存储返回值的内存地址。

![](img/4105a3d1442b5a29abef10dce5dfde43_26.png)

让我们观察这个过程。注意，`convert_to_minutes` 的栈帧已被擦除，变量 `minutes` 已在 `convert_to_seconds` 的栈帧中被创建。

![](img/4105a3d1442b5a29abef10dce5dfde43_28.png)

这里我们有另一个赋值语句。右侧 `minutes * 60` 的计算结果是 `120 * 60` 的值。一个新的变量 `seconds` 将被创建，并包含这个新值的内存地址。

![](img/4105a3d1442b5a29abef10dce5dfde43_30.png)

接下来，我们返回 `seconds`。`seconds` 指向 `7200`。因此，这就是第 20 行对 `convert_to_seconds` 的调用所产生的值。

![](img/4105a3d1442b5a29abef10dce5dfde43_32.png)

---

![](img/4105a3d1442b5a29abef10dce5dfde43_34.png)

本节课中我们一起学习了变量的作用域和生命周期，以及调用栈如何管理函数调用和变量存储。我们看到了同名变量如何在不同函数的独立栈帧中共存而互不干扰，也观察了函数调用、返回和栈帧创建与销毁的完整流程。理解调用栈是理解程序执行顺序和内存管理的基础。