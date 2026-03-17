# 003：堆内存 🧠

![](img/36947c91fbde9e9ddb3e92988d111608_1.png)

![](img/36947c91fbde9e9ddb3e92988d111608_2.png)

![](img/36947c91fbde9e9ddb3e92988d111608_4.png)

![](img/36947c91fbde9e9ddb3e92988d111608_5.png)

![](img/36947c91fbde9e9ddb3e92988d111608_7.png)

![](img/36947c91fbde9e9ddb3e92988d111608_8.png)

![](img/36947c91fbde9e9ddb3e92988d111608_10.png)

![](img/36947c91fbde9e9ddb3e92988d111608_12.png)

![](img/36947c91fbde9e9ddb3e92988d111608_13.png)

![](img/36947c91fbde9e9ddb3e92988d111608_14.png)

![](img/36947c91fbde9e9ddb3e92988d111608_15.png)

![](img/36947c91fbde9e9ddb3e92988d111608_16.png)

在本节课中，我们将要学习C++中两种主要的内存管理方式之一：堆内存。我们将从回顾栈内存开始，然后深入探讨堆内存的工作原理、如何分配与释放，以及它们之间的核心区别。

![](img/36947c91fbde9e9ddb3e92988d111608_18.png)

![](img/36947c91fbde9e9ddb3e92988d111608_20.png)

![](img/36947c91fbde9e9ddb3e92988d111608_22.png)

![](img/36947c91fbde9e9ddb3e92988d111608_24.png)

![](img/36947c91fbde9e9ddb3e92988d111608_26.png)

![](img/36947c91fbde9e9ddb3e92988d111608_27.png)

![](img/36947c91fbde9e9ddb3e92988d111608_29.png)

![](img/36947c91fbde9e9ddb3e92988d111608_31.png)

上一节我们介绍了栈内存，它是一种自动管理、高效但生命周期有限的内存区域。本节中我们来看看另一种内存管理方式——堆内存，它允许我们手动控制内存的分配与释放，从而创建生命周期更长的对象。

![](img/36947c91fbde9e9ddb3e92988d111608_33.png)

![](img/36947c91fbde9e9ddb3e92988d111608_35.png)

![](img/36947c91fbde9e9ddb3e92988d111608_36.png)

![](img/36947c91fbde9e9ddb3e92988d111608_38.png)

![](img/36947c91fbde9e9ddb3e92988d111608_40.png)

![](img/36947c91fbde9e9ddb3e92988d111608_42.png)

![](img/36947c91fbde9e9ddb3e92988d111608_44.png)

## 栈内存回顾 📚

![](img/36947c91fbde9e9ddb3e92988d111608_46.png)

![](img/36947c91fbde9e9ddb3e92988d111608_47.png)

![](img/36947c91fbde9e9ddb3e92988d111608_49.png)

![](img/36947c91fbde9e9ddb3e92988d111608_51.png)

![](img/36947c91fbde9e9ddb3e92988d111608_53.png)

![](img/36947c91fbde9e9ddb3e92988d111608_55.png)

![](img/36947c91fbde9e9ddb3e92988d111608_57.png)

![](img/36947c91fbde9e9ddb3e92988d111608_59.png)

栈内存用于存储函数调用时的局部变量。每次调用函数时，系统会创建一个栈帧，其中包含该函数的变量。当函数返回时，这个栈帧及其包含的变量会被自动清理。

![](img/36947c91fbde9e9ddb3e92988d111608_61.png)

![](img/36947c91fbde9e9ddb3e92988d111608_63.png)

![](img/36947c91fbde9e9ddb3e92988d111608_65.png)

![](img/36947c91fbde9e9ddb3e92988d111608_66.png)

![](img/36947c91fbde9e9ddb3e92988d111608_67.png)

![](img/36947c91fbde9e9ddb3e92988d111608_68.png)

![](img/36947c91fbde9e9ddb3e92988d111608_70.png)

![](img/36947c91fbde9e9ddb3e92988d111608_72.png)

栈内存的地址空间从高地址向低地址增长。我们不需要手动管理栈内存，它的分配和释放是自动的。

![](img/36947c91fbde9e9ddb3e92988d111608_74.png)

![](img/36947c91fbde9e9ddb3e92988d111608_76.png)

![](img/36947c91fbde9e9ddb3e92988d111608_78.png)

![](img/36947c91fbde9e9ddb3e92988d111608_80.png)

![](img/36947c91fbde9e9ddb3e92988d111608_81.png)

![](img/36947c91fbde9e9ddb3e92988d111608_83.png)

![](img/36947c91fbde9e9ddb3e92988d111608_85.png)

![](img/36947c91fbde9e9ddb3e92988d111608_86.png)

## 一个栈内存的“陷阱” ⚠️

![](img/36947c91fbde9e9ddb3e92988d111608_88.png)

![](img/36947c91fbde9e9ddb3e92988d111608_90.png)

![](img/36947c91fbde9e9ddb3e92988d111608_92.png)

![](img/36947c91fbde9e9ddb3e92988d111608_94.png)

![](img/36947c91fbde9e9ddb3e92988d111608_96.png)

![](img/36947c91fbde9e9ddb3e92988d111608_98.png)

![](img/36947c91fbde9e9ddb3e92988d111608_100.png)

![](img/36947c91fbde9e9ddb3e92988d111608_102.png)

为了理解为什么需要堆内存，我们先看一个使用栈内存时可能遇到的问题。

![](img/36947c91fbde9e9ddb3e92988d111608_104.png)

![](img/36947c91fbde9e9ddb3e92988d111608_106.png)

![](img/36947c91fbde9e9ddb3e92988d111608_108.png)

![](img/36947c91fbde9e9ddb3e92988d111608_109.png)

![](img/36947c91fbde9e9ddb3e92988d111608_111.png)

![](img/36947c91fbde9e9ddb3e92988d111608_113.png)

![](img/36947c91fbde9e9ddb3e92988d111608_114.png)

以下是一段有问题的代码，它试图返回一个指向栈内存的指针：

![](img/36947c91fbde9e9ddb3e92988d111608_116.png)

![](img/36947c91fbde9e9ddb3e92988d111608_118.png)

![](img/36947c91fbde9e9ddb3e92988d111608_120.png)

![](img/36947c91fbde9e9ddb3e92988d111608_122.png)

![](img/36947c91fbde9e9ddb3e92988d111608_123.png)

![](img/36947c91fbde9e9ddb3e92988d111608_125.png)

![](img/36947c91fbde9e9ddb3e92988d111608_127.png)

```cpp
Cube* createCube() {
    Cube c(20);
    return &c; // 返回局部变量c的地址
}

![](img/36947c91fbde9e9ddb3e92988d111608_129.png)

![](img/36947c91fbde9e9ddb3e92988d111608_131.png)

![](img/36947c91fbde9e9ddb3e92988d111608_133.png)

![](img/36947c91fbde9e9ddb3e92988d111608_135.png)

![](img/36947c91fbde9e9ddb3e92988d111608_137.png)

![](img/36947c91fbde9e9ddb3e92988d111608_139.png)

![](img/36947c91fbde9e9ddb3e92988d111608_140.png)

int main() {
    Cube* c = createCube();
    someOtherFunction();
    double vol = c->getVolume(); // 潜在问题！
}
```

![](img/36947c91fbde9e9ddb3e92988d111608_142.png)

![](img/36947c91fbde9e9ddb3e92988d111608_144.png)

![](img/36947c91fbde9e9ddb3e92988d111608_146.png)

![](img/36947c91fbde9e9ddb3e92988d111608_148.png)

![](img/36947c91fbde9e9ddb3e92988d111608_150.png)

![](img/36947c91fbde9e9ddb3e92988d111608_152.png)

![](img/36947c91fbde9e9ddb3e92988d111608_154.png)

让我们逐步分析这段代码：
1.  `main`函数调用`createCube`。
2.  `createCube`函数在其栈帧中创建了一个局部`Cube`对象`c`。
3.  `createCube`返回了局部变量`c`的地址。
4.  函数返回后，其栈帧被释放，`c`所占用的内存不再属于该程序。
5.  `main`函数调用`someOtherFunction`，该函数可能会使用刚才被释放的内存区域。
6.  当`main`函数试图通过指针`c`访问`getVolume()`时，它实际上是在访问一块可能已被覆盖或不再有效的内存。这会导致未定义行为，程序可能崩溃或返回垃圾数据。

![](img/36947c91fbde9e9ddb3e92988d111608_156.png)

![](img/36947c91fbde9e9ddb3e92988d111608_158.png)

![](img/36947c91fbde9e9ddb3e92988d111608_160.png)

![](img/36947c91fbde9e9ddb3e92988d111608_161.png)

![](img/36947c91fbde9e9ddb3e92988d111608_162.png)

![](img/36947c91fbde9e9ddb3e92988d111608_164.png)

![](img/36947c91fbde9e9ddb3e92988d111608_166.png)

这个问题的核心在于：**栈内存中的变量在其所属函数返回后，生命周期就结束了**。我们无法安全地保留指向它的指针。

![](img/36947c91fbde9e9ddb3e92988d111608_168.png)

![](img/36947c91fbde9e9ddb3e92988d111608_169.png)

![](img/36947c91fbde9e9ddb3e92988d111608_170.png)

![](img/36947c91fbde9e9ddb3e92988d111608_172.png)

![](img/36947c91fbde9e9ddb3e92988d111608_174.png)

## 引入堆内存 🆕

![](img/36947c91fbde9e9ddb3e92988d111608_176.png)

![](img/36947c91fbde9e9ddb3e92988d111608_177.png)

![](img/36947c91fbde9e9ddb3e92988d111608_178.png)

![](img/36947c91fbde9e9ddb3e92988d111608_180.png)

![](img/36947c91fbde9e9ddb3e92988d111608_181.png)

![](img/36947c91fbde9e9ddb3e92988d111608_183.png)

为了解决上述问题，并允许我们创建生命周期超越单个函数调用的对象，C++提供了堆内存。

![](img/36947c91fbde9e9ddb3e92988d111608_185.png)

![](img/36947c91fbde9e9ddb3e92988d111608_187.png)

![](img/36947c91fbde9e9ddb3e92988d111608_189.png)

![](img/36947c91fbde9e9ddb3e92988d111608_191.png)

![](img/36947c91fbde9e9ddb3e92988d111608_193.png)

![](img/36947c91fbde9e9ddb3e92988d111608_195.png)

![](img/36947c91fbde9e9ddb3e92988d111608_197.png)

![](img/36947c91fbde9e9ddb3e92988d111608_198.png)

堆内存是程序中另一块可用的内存区域。与栈内存从高地址向低地址增长不同，堆内存从低地址向高地址增长。堆内存的分配和释放需要程序员**显式地**进行管理。

![](img/36947c91fbde9e9ddb3e92988d111608_200.png)

![](img/36947c91fbde9e9ddb3e92988d111608_201.png)

![](img/36947c91fbde9e9ddb3e92988d111608_203.png)

![](img/36947c91fbde9e9ddb3e92988d111608_205.png)

## 使用 `new` 分配堆内存 🔧

![](img/36947c91fbde9e9ddb3e92988d111608_207.png)

![](img/36947c91fbde9e9ddb3e92988d111608_208.png)

![](img/36947c91fbde9e9ddb3e92988d111608_210.png)

![](img/36947c91fbde9e9ddb3e92988d111608_211.png)

![](img/36947c91fbde9e9ddb3e92988d111608_212.png)

![](img/36947c91fbde9e9ddb3e92988d111608_214.png)

![](img/36947c91fbde9e9ddb3e92988d111608_216.png)

![](img/36947c91fbde9e9ddb3e92988d111608_217.png)

![](img/36947c91fbde9e9ddb3e92988d111608_219.png)

在C++中，我们使用关键字 **`new`** 在堆上分配内存。

![](img/36947c91fbde9e9ddb3e92988d111608_221.png)

![](img/36947c91fbde9e9ddb3e92988d111608_223.png)

![](img/36947c91fbde9e9ddb3e92988d111608_225.png)

![](img/36947c91fbde9e9ddb3e92988d111608_227.png)

![](img/36947c91fbde9e9ddb3e92988d111608_229.png)

![](img/36947c91fbde9e9ddb3e92988d111608_230.png)

![](img/36947c91fbde9e9ddb3e92988d111608_232.png)

![](img/36947c91fbde9e9ddb3e92988d111608_234.png)

`new` 操作符主要完成三件事：
1.  **分配内存**：在堆上分配足够大小的内存块。
2.  **调用构造函数**：对于类类型，调用其构造函数来初始化对象；对于基本类型（如`int`, `double`），进行值初始化（例如，`new int` 会初始化为0）。
3.  **返回地址**：返回指向新分配内存的指针。

![](img/36947c91fbde9e9ddb3e92988d111608_236.png)

![](img/36947c91fbde9e9ddb3e92988d111608_238.png)

![](img/36947c91fbde9e9ddb3e92988d111608_239.png)

![](img/36947c91fbde9e9ddb3e92988d111608_241.png)

![](img/36947c91fbde9e9ddb3e92988d111608_242.png)

![](img/36947c91fbde9e9ddb3e92988d111608_244.png)

![](img/36947c91fbde9e9ddb3e92988d111608_246.png)

![](img/36947c91fbde9e9ddb3e92988d111608_247.png)

![](img/36947c91fbde9e9ddb3e92988d111608_249.png)

其基本语法如下：
```cpp
Cube* c = new Cube(20); // 分配一个Cube对象，并用参数20调用其构造函数
int* p = new int;       // 分配一个int，值初始化为0
```
**注意**：`new` 的返回值总是一个指针，因此必须用一个相应类型的指针变量来接收它。

![](img/36947c91fbde9e9ddb3e92988d111608_251.png)

![](img/36947c91fbde9e9ddb3e92988d111608_253.png)

![](img/36947c91fbde9e9ddb3e92988d111608_255.png)

![](img/36947c91fbde9e9ddb3e92988d111608_256.png)

![](img/36947c91fbde9e9ddb3e92988d111608_258.png)

![](img/36947c91fbde9e9ddb3e92988d111608_260.png)

![](img/36947c91fbde9e9ddb3e92988d111608_262.png)

![](img/36947c91fbde9e9ddb3e92988d111608_263.png)

![](img/36947c91fbde9e9ddb3e92988d111608_264.png)

![](img/36947c91fbde9e9ddb3e92988d111608_265.png)

## 使用 `delete` 释放堆内存 🗑️

![](img/36947c91fbde9e9ddb3e92988d111608_267.png)

![](img/36947c91fbde9e9ddb3e92988d111608_269.png)

![](img/36947c91fbde9e9ddb3e92988d111608_271.png)

![](img/36947c91fbde9e9ddb3e92988d111608_273.png)

![](img/36947c91fbde9e9ddb3e92988d111608_275.png)

![](img/36947c91fbde9e9ddb3e92988d111608_277.png)

与 `new` 相对应，我们使用关键字 **`delete`** 来释放堆内存。

![](img/36947c91fbde9e9ddb3e92988d111608_279.png)

![](img/36947c91fbde9e9ddb3e92988d111608_281.png)

![](img/36947c91fbde9e9ddb3e92988d111608_282.png)

![](img/36947c91fbde9e9ddb3e92988d111608_284.png)

![](img/36947c91fbde9e9ddb3e92988d111608_286.png)

![](img/36947c91fbde9e9ddb3e92988d111608_288.png)

![](img/36947c91fbde9e9ddb3e92988d111608_290.png)

![](img/36947c91fbde9e9ddb3e92988d111608_292.png)

![](img/36947c91fbde9e9ddb3e92988d111608_294.png)

![](img/36947c91fbde9e9ddb3e92988d111608_296.png)

`delete` 操作符主要完成两件事：
1.  **调用析构函数**：对于类类型，调用其析构函数来执行必要的清理工作（例如关闭文件、释放其他资源）。
2.  **释放内存**：将内存归还给系统，以便后续重用。

![](img/36947c91fbde9e9ddb3e92988d111608_298.png)

![](img/36947c91fbde9e9ddb3e92988d111608_300.png)

![](img/36947c91fbde9e9ddb3e92988d111608_302.png)

![](img/36947c91fbde9e9ddb3e92988d111608_304.png)

![](img/36947c91fbde9e9ddb3e92988d111608_306.png)

![](img/36947c91fbde9e9ddb3e92988d111608_308.png)

![](img/36947c91fbde9e9ddb3e92988d111608_309.png)

![](img/36947c91fbde9e9ddb3e92988d111608_310.png)

其基本语法如下：
```cpp
delete c; // 释放c指向的堆内存
delete p; // 释放p指向的堆内存
```
**重要原则**：每一个通过 `new` 分配的内存，最终都必须通过 `delete` 来释放，否则会导致内存泄漏。

![](img/36947c91fbde9e9ddb3e92988d111608_312.png)

![](img/36947c91fbde9e9ddb3e92988d111608_314.png)

![](img/36947c91fbde9e9ddb3e92988d111608_316.png)

![](img/36947c91fbde9e9ddb3e92988d111608_317.png)

![](img/36947c91fbde9e9ddb3e92988d111608_319.png)

![](img/36947c91fbde9e9ddb3e92988d111608_321.png)

![](img/36947c91fbde9e9ddb3e92988d111608_323.png)

## 堆内存与栈内存的对比 📊

![](img/36947c91fbde9e9ddb3e92988d111608_325.png)

![](img/36947c91fbde9e9ddb3e92988d111608_327.png)

![](img/36947c91fbde9e9ddb3e92988d111608_329.png)

![](img/36947c91fbde9e9ddb3e92988d111608_331.png)

![](img/36947c91fbde9e9ddb3e92988d111608_333.png)

![](img/36947c91fbde9e9ddb3e92988d111608_335.png)

![](img/36947c91fbde9e9ddb3e92988d111608_337.png)

![](img/36947c91fbde9e9ddb3e92988d111608_338.png)

以下是堆内存和栈内存的核心区别总结：

![](img/36947c91fbde9e9ddb3e92988d111608_340.png)

![](img/36947c91fbde9e9ddb3e92988d111608_341.png)

![](img/36947c91fbde9e9ddb3e92988d111608_343.png)

![](img/36947c91fbde9e9ddb3e92988d111608_345.png)

![](img/36947c91fbde9e9ddb3e92988d111608_347.png)

![](img/36947c91fbde9e9ddb3e92988d111608_349.png)

![](img/36947c91fbde9e9ddb3e92988d111608_350.png)

![](img/36947c91fbde9e9ddb3e92988d111608_352.png)

| 特性 | 栈内存 (Stack) | 堆内存 (Heap) |
| :--- | :--- | :--- |
| **管理方式** | 自动（由编译器/系统管理） | 手动（由程序员管理） |
| **生命周期** | 与函数调用周期一致 | 从 `new` 到 `delete` |
| **分配速度** | 快（移动栈指针即可） | 相对较慢（需寻找合适内存块） |
| **大小限制** | 通常较小（取决于系统设置） | 理论上可达系统可用内存上限 |
| **主要用途** | 局部变量、函数参数、返回地址 | 生命周期长的对象、大型数据结构、需要在函数间共享的数据 |
| **增长方向** | 从高地址向低地址增长 | 从低地址向高地址增长 |

![](img/36947c91fbde9e9ddb3e92988d111608_354.png)

![](img/36947c91fbde9e9ddb3e92988d111608_355.png)

![](img/36947c91fbde9e9ddb3e92988d111608_357.png)

![](img/36947c91fbde9e9ddb3e92988d111608_358.png)

![](img/36947c91fbde9e9ddb3e92988d111608_360.png)

![](img/36947c91fbde9e9ddb3e92988d111608_362.png)

## 一个堆内存的示例与陷阱 🧪

![](img/36947c91fbde9e9ddb3e92988d111608_364.png)

![](img/36947c91fbde9e9ddb3e92988d111608_366.png)

![](img/36947c91fbde9e9ddb3e92988d111608_368.png)

![](img/36947c91fbde9e9ddb3e92988d111608_370.png)

![](img/36947c91fbde9e9ddb3e92988d111608_372.png)

让我们通过一个例子来理解堆内存的使用和另一个常见陷阱——重复释放。

![](img/36947c91fbde9e9ddb3e92988d111608_374.png)

![](img/36947c91fbde9e9ddb3e92988d111608_375.png)

![](img/36947c91fbde9e9ddb3e92988d111608_376.png)

![](img/36947c91fbde9e9ddb3e92988d111608_378.png)

![](img/36947c91fbde9e9ddb3e92988d111608_380.png)

![](img/36947c91fbde9e9ddb3e92988d111608_382.png)

```cpp
int main() {
    Cube* c1 = new Cube(); // 在堆上分配Cube1
    Cube* c2 = c1;         // c2指向与c1相同的堆内存

    c2->setLength(10);     // 通过c2修改对象

    delete c2;             // 释放堆内存
    delete c1;             // 错误！重复释放同一块内存
    double vol = c1->getVolume(); // 错误！访问已释放的内存
}
```

![](img/36947c91fbde9e9ddb3e92988d111608_384.png)

![](img/36947c91fbde9e9ddb3e92988d111608_386.png)

![](img/36947c91fbde9e9ddb3e92988d111608_387.png)

![](img/36947c91fbde9e9ddb3e92988d111608_389.png)

![](img/36947c91fbde9e9ddb3e92988d111608_390.png)

以下是代码分析：
1.  `c1` 指向堆上新创建的 `Cube` 对象。
2.  `c2` 被赋值为 `c1`，因此 `c1` 和 `c2` 指向**同一个**堆对象。
3.  通过 `c2` 修改长度，实际上修改了 `c1` 也指向的那个对象。
4.  `delete c2;` 释放了堆上的 `Cube` 对象。
5.  `delete c1;` 试图再次释放**同一块已经释放的内存**，这会导致未定义行为（通常是程序崩溃）。
6.  后续通过 `c1` 访问对象也是非法的。

![](img/36947c91fbde9e9ddb3e92988d111608_392.png)

![](img/36947c91fbde9e9ddb3e92988d111608_394.png)

![](img/36947c91fbde9e9ddb3e92988d111608_396.png)

![](img/36947c91fbde9e9ddb3e92988d111608_398.png)

![](img/36947c91fbde9e9ddb3e92988d111608_400.png)

![](img/36947c91fbde9e9ddb3e92988d111608_401.png)

这个例子强调了两个要点：
*   **多个指针可以指向同一块堆内存**。
*   **同一块堆内存只能被 `delete` 一次**。重复释放或访问已释放的内存是严重错误。

![](img/36947c91fbde9e9ddb3e92988d111608_402.png)

![](img/36947c91fbde9e9ddb3e92988d111608_404.png)

![](img/36947c91fbde9e9ddb3e92988d111608_405.png)

![](img/36947c91fbde9e9ddb3e92988d111608_407.png)

![](img/36947c91fbde9e9ddb3e92988d111608_409.png)

![](img/36947c91fbde9e9ddb3e92988d111608_411.png)

![](img/36947c91fbde9e9ddb3e92988d111608_413.png)

![](img/36947c91fbde9e9ddb3e92988d111608_415.png)

![](img/36947c91fbde9e9ddb3e92988d111608_417.png)

## 总结 🎯

![](img/36947c91fbde9e9ddb3e92988d111608_419.png)

![](img/36947c91fbde9e9ddb3e92988d111608_421.png)

![](img/36947c91fbde9e9ddb3e92988d111608_422.png)

![](img/36947c91fbde9e9ddb3e92988d111608_423.png)

![](img/36947c91fbde9e9ddb3e92988d111608_425.png)

![](img/36947c91fbde9e9ddb3e92988d111608_427.png)

本节课中我们一起学习了C++中堆内存的核心概念。

![](img/36947c91fbde9e9ddb3e92988d111608_429.png)

![](img/36947c91fbde9e9ddb3e92988d111608_431.png)

![](img/36947c91fbde9e9ddb3e92988d111608_433.png)

我们首先回顾了栈内存的自动管理特性及其局限性，特别是无法安全返回指向局部变量的指针。接着，我们引入了堆内存作为解决方案，它允许我们手动控制内存的生命周期。

![](img/36947c91fbde9e9ddb3e92988d111608_435.png)

![](img/36947c91fbde9e9ddb3e92988d111608_437.png)

![](img/36947c91fbde9e9ddb3e92988d111608_439.png)

![](img/36947c91fbde9e9ddb3e92988d111608_441.png)

![](img/36947c91fbde9e9ddb3e92988d111608_443.png)

![](img/36947c91fbde9e9ddb3e92988d111608_445.png)

![](img/36947c91fbde9e9ddb3e92988d111608_447.png)

我们详细探讨了如何使用 `new` 操作符在堆上分配内存并初始化对象，以及如何使用 `delete` 操作符释放内存并调用析构函数。我们比较了堆内存和栈内存的关键区别，包括管理方式、生命周期、性能和用途。

![](img/36947c91fbde9e9ddb3e92988d111608_449.png)

![](img/36947c91fbde9e9ddb3e92988d111608_450.png)

![](img/36947c91fbde9e9ddb3e92988d111608_452.png)

![](img/36947c91fbde9e9ddb3e92988d111608_454.png)

![](img/36947c91fbde9e9ddb3e92988d111608_456.png)

![](img/36947c91fbde9e9ddb3e92988d111608_458.png)

![](img/36947c91fbde9e9ddb3e92988d111608_460.png)

最后，我们通过实例分析了堆内存的使用，并指出了诸如“重复释放”和“访问已释放内存”等常见陷阱。理解并正确管理堆内存是编写健壮、高效C++程序的基础，在后续构建复杂数据结构时至关重要。