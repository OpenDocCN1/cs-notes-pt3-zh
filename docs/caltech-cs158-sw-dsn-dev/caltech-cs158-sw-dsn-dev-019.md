# 019：ArrayList 类 📚

![](img/0c57f9110cb1cec2cd3c17c9a429187f_0.png)

在本节课中，我们将要学习 Java 中的 `ArrayList` 类。`ArrayList` 是一个基于数组构建但功能更强大的类，它提供了动态调整大小、便捷的元素增删等能力，是处理数据集合的有力工具。我们将通过对比普通数组，来理解 `ArrayList` 的优势和基本用法。

## 概述

之前我们已经学习了数组的基础知识、多维数组、数组作为引用类型以及 `Arrays` 工具类。本节课程将作为数组主题的最后一讲，介绍 `ArrayList` 类。`ArrayList` 是 Java 集合框架的一部分，它封装了数组，并提供了更丰富、更易用的方法来管理数据集合，特别适合在程序运行时需要动态增减元素的场景。

## ArrayList 与标准数组的对比

上一节我们介绍了数组的各种特性，本节中我们来看看 `ArrayList` 与标准数组的主要区别。理解这些区别有助于我们在不同场景下做出合适的选择。

标准数组在创建时必须声明其固定长度。这在某些情况下可能带来不便，例如，当无法预知需要存储多少数据，或者数据量在程序运行期间会增长时。

`ArrayList` 则无需在创建时声明大小。它可以初始化为空，然后动态地添加元素，其内部容量会自动增长。此外，你还可以从中移除元素，从而减小其大小。以下是 `ArrayList` 的一些核心优势：
*   **动态扩容**：无需预先指定大小，随元素添加自动增长。
*   **灵活增删**：提供了 `add` 和 `remove` 等方法，可以方便地插入或删除元素，并自动调整后续元素的位置。
*   **丰富功能**：内置了搜索、比较、遍历等多种实用方法。

## 使用 ArrayList

要使用 `ArrayList`，首先需要导入它所在的包。与 `Scanner` 类似，`ArrayList` 属于 `java.util` 包。

```java
import java.util.ArrayList;
```

### 创建 ArrayList 实例

创建 `ArrayList` 实例需要使用 `new` 关键字，并指定其将要存储的元素类型。注意，`ArrayList` 只能存储**引用类型**。对于基本数据类型（如 `int`, `double`），需要使用其对应的包装类（如 `Integer`, `Double`）。

```java
// 创建一个存储字符串的 ArrayList
ArrayList<String> stringList = new ArrayList<>();
// 创建一个存储整数的 ArrayList
ArrayList<Integer> integerList = new ArrayList<>();
```

### 添加元素

我们可以使用 `add` 方法向 `ArrayList` 中添加元素。`add` 方法有两个重载版本：一个在列表末尾添加元素，另一个在指定索引处插入元素（原有元素会后移）。

以下是 `add` 方法的使用示例：
*   `list.add("Apple")`：在列表末尾添加 “Apple”。
*   `list.add(0, "Banana")`：在索引 0 处插入 “Banana”，原索引 0 及之后的元素依次后移。

### 访问与查询元素

与数组使用方括号 `[]` 访问元素不同，`ArrayList` 使用 `get` 方法根据索引获取元素。

```java
String fruit = list.get(1); // 获取索引为1的元素
```

`ArrayList` 还提供了便捷的查询方法：
*   `contains(Object)`：检查列表是否包含某个元素。
*   `indexOf(Object)`：返回指定元素首次出现的索引，未找到则返回 -1。
*   `lastIndexOf(Object)`：返回指定元素最后一次出现的索引。

### 移除元素

我们可以使用 `remove` 方法移除元素。它也有两个重载版本：按索引移除和按对象值移除。

```java
list.remove(1); // 移除索引为1的元素，并返回该元素
list.remove("Banana"); // 移除首次出现的 “Banana”，成功返回 true，否则返回 false
```

### 其他常用操作

`ArrayList` 包含许多其他实用方法，以下是其中一部分：
*   `set(int index, E element)`：替换指定索引处的元素。
*   `clear()`：清空列表中的所有元素。
*   `size()`：返回列表中当前元素的数量（相当于数组的 `length`，但是可变的）。
*   `isEmpty()`：检查列表是否为空。
*   `toArray()`：将 `ArrayList` 转换为一个标准数组。
*   `subList(int fromIndex, int toIndex)`：获取原列表的一个子列表视图。

### 遍历 ArrayList

除了使用标准的 `for` 循环或增强型 `for` 循环，`ArrayList` 还可以通过**迭代器**进行遍历。迭代器提供了顺序访问集合中每个元素的方法。

```java
// 获取一个迭代器
Iterator<String> it = list.iterator();
while (it.hasNext()) { // 检查是否还有下一个元素
    String item = it.next(); // 获取下一个元素
    System.out.println(item);
}
```

此外，`ListIterator` 提供了双向遍历的能力，可以向前或向后移动。

## 总结

![](img/0c57f9110cb1cec2cd3c17c9a429187f_2.png)

本节课中我们一起学习了 `ArrayList` 类。作为对标准数组的增强，`ArrayList` 通过封装动态数组的实现，提供了自动扩容、便捷的元素增删查改以及丰富的工具方法，极大地简化了集合数据的管理。虽然它在某些性能极端敏感的场景下可能不如原始数组高效，但对于大多数日常编程任务而言，`ArrayList` 因其灵活性和强大的功能而成为更受欢迎的选择。记住，当你的数据集合大小需要动态变化时，`ArrayList` 是一个非常得力的工具。