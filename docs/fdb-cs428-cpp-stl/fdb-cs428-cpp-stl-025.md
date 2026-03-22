# 025：算法、容器和适配器的应用

![](img/d0a7ff755611e40bbce27dc51146699e_1.png)

![](img/d0a7ff755611e40bbce27dc51146699e_3.png)

在本节课中，我们将学习如何综合运用C++标准模板库（STL）中的算法、容器和迭代器适配器来解决一个实际问题：检测会议日程中的冲突并输出排序后的日程表。

![](img/d0a7ff755611e40bbce27dc51146699e_5.png)

![](img/d0a7ff755611e40bbce27dc51146699e_6.png)

我们将通过一个具体的程序示例来展示如何将STL的各个组件无缝地组合在一起，实现强大而简洁的功能。

---

## 程序概述与演示

上一节我们介绍了STL的各个组件。本节中，我们来看看如何将它们应用于一个实际的日程管理程序。

![](img/d0a7ff755611e40bbce27dc51146699e_8.png)

![](img/d0a7ff755611e40bbce27dc51146699e_9.png)

该程序从命令行参数读取一系列会议信息，包括会议名称、星期几以及开始和结束时间。程序的核心任务是：
1.  检测并打印出存在时间重叠的会议冲突。
2.  按日期和时间顺序打印出完整的日程表。

![](img/d0a7ff755611e40bbce27dc51146699e_11.png)

以下是程序运行的示例。假设我们有一个包含多个课程会议信息的输入文件，程序会分析这些会议并输出冲突信息及排序后的日程。

![](img/d0a7ff755611e40bbce27dc51146699e_1.png)

![](img/d0a7ff755611e40bbce27dc51146699e_3.png)

![](img/d0a7ff755611e40bbce27dc51146699e_5.png)

![](img/d0a7ff755611e40bbce27dc51146699e_6.png)

![](img/d0a7ff755611e40bbce27dc51146699e_8.png)

![](img/d0a7ff755611e40bbce27dc51146699e_9.png)

![](img/d0a7ff755611e40bbce27dc51146699e_13.png)

![](img/d0a7ff755611e40bbce27dc51146699e_14.png)

程序成功检测到了CS251与CS242、以及CS242与CS281在周二的时间冲突，并输出了按时间排序的周一到周四的日程。

![](img/d0a7ff755611e40bbce27dc51146699e_16.png)

---

![](img/d0a7ff755611e40bbce27dc51146699e_18.png)

![](img/d0a7ff755611e40bbce27dc51146699e_20.png)

## 代码结构总览

![](img/d0a7ff755611e40bbce27dc51146699e_22.png)

现在让我们回到代码，从高层次理解程序是如何工作的。

![](img/d0a7ff755611e40bbce27dc51146699e_24.png)

程序的主函数 `main` 主要执行三个步骤：
1.  从命令行参数读取会议列表。
2.  检测并打印任何时间重叠的冲突。
3.  将排序后的日程写入输出。

![](img/d0a7ff755611e40bbce27dc51146699e_26.png)

以下是实现这些步骤的核心思路：

```cpp
int main(int argc, char* argv[]) {
    // 1. 使用自定义迭代器适配器从argv读取数据并存入vector
    // 2. 使用sort算法对vector排序
    // 3. 调用check_for_conflicts函数检测冲突
    // 4. 使用ostream_iterator输出排序后的日程
}
```

![](img/d0a7ff755611e40bbce27dc51146699e_28.png)

![](img/d0a7ff755611e40bbce27dc51146699e_29.png)

![](img/d0a7ff755611e40bbce27dc51146699e_30.png)

![](img/d0a7ff755611e40bbce27dc51146699e_31.png)

我们首先将会议日程存储在一个 `vector` 中，`vector` 的元素是 `Meeting` 结构体，它记录了会议的名称、星期几、开始和结束时间。

---

![](img/d0a7ff755611e40bbce27dc51146699e_33.png)

![](img/d0a7ff755611e40bbce27dc51146699e_34.png)

![](img/d0a7ff755611e40bbce27dc51146699e_35.png)

![](img/d0a7ff755611e40bbce27dc51146699e_36.png)

## 核心组件详解

### 自定义迭代器适配器：ArgvIterator

![](img/d0a7ff755611e40bbce27dc51146699e_38.png)

![](img/d0a7ff755611e40bbce27dc51146699e_40.png)

为了将命令行参数（`argc`, `argv`）方便地用于STL算法，我们创建了一个自定义的迭代器适配器 `ArgvIterator`。这体现了STL适配器的强大之处：它能将原本不兼容的接口（如命令行参数）转换成可与STL算法协同工作的迭代器。

![](img/d0a7ff755611e40bbce27dc51146699e_42.png)

`ArgvIterator` 继承自 `std::iterator`，是一个前向迭代器。它的核心构造函数接收调整后的 `argc` 和 `argv`（跳过了程序名本身）。迭代器每次递增会跳过指定数量的参数（本例中为4，对应会议信息的4个字段），其解引用操作会将当前 `argv` 指向的字符串转换为 `Meeting` 对象。

![](img/d0a7ff755611e40bbce27dc51146699e_44.png)

![](img/d0a7ff755611e40bbce27dc51146699e_45.png)

![](img/d0a7ff755611e40bbce27dc51146699e_47.png)

```cpp
template <typename T>
class ArgvIterator : public std::iterator<std::forward_iterator_tag, T> {
public:
    ArgvIterator(int argc, char** argv, int increment = 1)
        : argc_(argc), argv_(argv), base_argv_(argv), increment_(increment) {}
    // ... 其他成员函数，如 operator++, operator*, operator!=
private:
    int argc_;
    char** argv_;
    char** base_argv_;
    int increment_;
};
```

![](img/d0a7ff755611e40bbce27dc51146699e_49.png)

![](img/d0a7ff755611e40bbce27dc51146699e_51.png)

在主函数中，我们这样使用它和 `std::copy` 算法来填充 `vector`：

```cpp
std::vector<Meeting> schedule;
std::copy(ArgvIterator<Meeting>(argc - 1, argv + 1, 4),
          ArgvIterator<Meeting>(),
          std::back_inserter(schedule));
```

![](img/d0a7ff755611e40bbce27dc51146699e_53.png)

![](img/d0a7ff755611e40bbce27dc51146699e_54.png)

![](img/d0a7ff755611e40bbce27dc51146699e_55.png)

![](img/d0a7ff755611e40bbce27dc51146699e_56.png)

![](img/d0a7ff755611e40bbce27dc51146699e_57.png)

![](img/d0a7ff755611e40bbce27dc51146699e_58.png)

![](img/d0a7ff755611e40bbce27dc51146699e_59.png)

### 数据结构：Meeting 类

![](img/d0a7ff755611e40bbce27dc51146699e_61.png)

![](img/d0a7ff755611e40bbce27dc51146699e_63.png)

`Meeting` 类（实际是结构体）是程序的核心数据结构，用于表示单个会议。

它包含以下成员：
*   `title`：会议名称（如 “CS101”）。
*   `day`：星期几，使用枚举类型 `DayOfWeek` 表示。
*   `start_time` 和 `finish_time`：会议的开始和结束时间（24小时制）。

![](img/d0a7ff755611e40bbce27dc51146699e_65.png)

关键成员函数包括：
1.  **构造函数 `Meeting(const char* str)`**：接受一个字符串（来自 `argv`），按格式解析出会议名称、日期和时间，并初始化对象。它使用 `std::stringstream` 来安全地将时间字符串转换为整数。
2.  **相等运算符 `operator==`**：用于判断两个会议是否时间冲突。冲突的定义是：两个会议在同一天，且一个会议的开始时间早于另一个会议的结束时间，同时另一个会议的开始时间也早于前一个会议的结束时间。这个定义被 `adjacent_find` 和 `transform` 算法用于检测冲突。
3.  **小于运算符 `operator<`**：用于 `std::sort` 算法。首先按星期几排序（周一、周二…），然后在同一天内按开始时间排序。
4.  **流插入运算符 `operator<<`**：用于格式化输出会议信息。

![](img/d0a7ff755611e40bbce27dc51146699e_67.png)

![](img/d0a7ff755611e40bbce27dc51146699e_69.png)

```cpp
struct Meeting {
    std::string title;
    DayOfWeek day;
    int start_time = 0;
    int finish_time = 0;

    Meeting(const char* str);
    bool operator==(const Meeting& other) const; // 检测时间重叠
    bool operator<(const Meeting& other) const;  // 用于排序
};

![](img/d0a7ff755611e40bbce27dc51146699e_71.png)

![](img/d0a7ff755611e40bbce27dc51146699e_73.png)

![](img/d0a7ff755611e40bbce27dc51146699e_74.png)

std::ostream& operator<<(std::ostream& os, const Meeting& m);
```

### 冲突检测的两种算法实现

![](img/d0a7ff755611e40bbce27dc51146699e_76.png)

程序最有趣的部分是 `check_for_conflicts` 函数，它展示了使用不同STL算法解决同一问题的两种方式。

#### 方法一：使用 `adjacent_find` 算法

`std::adjacent_find` 算法在给定范围内查找第一对相邻且“相等”的元素。这里我们利用重载的 `Meeting::operator==` 来检测相邻会议是否时间冲突。

![](img/d0a7ff755611e40bbce27dc51146699e_78.png)

这种方法需要一个显式的循环来查找所有冲突，因为每次找到一对冲突后，需要从下一个位置继续查找。

![](img/d0a7ff755611e40bbce27dc51146699e_80.png)

![](img/d0a7ff755611e40bbce27dc51146699e_81.png)

```cpp
template <typename InputIterator>
void check_for_conflicts(InputIterator begin, InputIterator end) {
    auto iter = begin;
    while (iter != end) {
        iter = std::adjacent_find(iter, end);
        if (iter != end) {
            std::cout << "CONFLICT: " << *iter << " and " << *(iter + 1) << std::endl;
            ++iter; // 跳过当前冲突项，继续查找
        }
    }
}
```

#### 方法二：使用 `transform` 算法

`std::transform` 算法通常用于转换一个序列的元素。这里我们巧妙地用它来遍历并检测冲突，而无需显式循环。

思路是创建两个偏移的迭代器范围，使用一个二元Lambda函数对每对相邻元素进行检查。如果发现冲突（`lhs == rhs` 为真），则打印冲突信息。虽然 `transform` 会“写回”结果，但我们只是返回原始值，并不实际修改容器。

![](img/d0a7ff755611e40bbce27dc51146699e_83.png)

```cpp
template <typename InputIterator>
void check_for_conflicts(InputIterator begin, InputIterator end) {
    std::transform(begin, std::prev(end), std::next(begin), begin,
        [](decltype(*begin)& lhs, decltype(*begin)& rhs) {
            if (lhs == rhs) { // 使用 Meeting::operator== 检测重叠
                std::cout << "CONFLICT: " << lhs << " and " << rhs << std::endl;
            }
            return lhs; // 原样返回，不实际修改数据
        });
}
```

**两种方法的比较**：
*   `adjacent_find` 方法更直观，目的明确，但需要外部循环。
*   `transform` 方法更函数式，无需显式循环，但语义上稍显“过度”（本意是转换，我们却用于检测），且可能产生不必要的赋值操作。
STL提供了多种工具，我们可以根据代码清晰度、性能需求和个人偏好来选择最合适的一种。

![](img/d0a7ff755611e40bbce27dc51146699e_85.png)

---

## 总结与核心思想

![](img/d0a7ff755611e40bbce27dc51146699e_87.png)

本节课中我们一起学习了如何构建一个综合运用C++ STL组件的实际应用程序。

我们回顾一下关键步骤和组件：
1.  **数据读取**：通过自定义的 `ArgvIterator` 适配器，将命令行参数无缝接入 `std::copy` 算法，优雅地填充 `std::vector<Meeting>`。
2.  **数据排序**：利用 `std::sort` 算法和 `Meeting::operator<`，轻松将会议按日期和时间排序。
3.  **冲突检测**：探索了使用 `std::adjacent_find` 和 `std::transform` 两种算法来实现核心的冲突检测逻辑，并比较了其优缺点。
4.  **结果输出**：使用 `std::ostream_iterator` 适配器，简洁地将整个排序后的日程表输出到标准输出。

这个程序的核心价值在于展示了STL的“组合式”威力。通过编写少量、可复用的组件（如 `ArgvIterator`, `Meeting`），并大量使用STL内置的算法、容器和适配器，我们以极少的、清晰的代码完成了一个功能完整的任务。这完美体现了“零开销抽象”和“写更少，做更多”的C++哲学。一旦你熟悉了STL的模式，就能快速构建出高效、可维护的解决方案。