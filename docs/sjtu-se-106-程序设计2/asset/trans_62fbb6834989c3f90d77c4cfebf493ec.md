

## 对前例的修复

- 重写类 C 以显式调用 A::f

```cpp
class C : public A, public B {
    public:
        void virtual f() {
            A::f();  // Call A::f(), not B::f();
        }
};
```

- 合理的解决方案
  - 这消除了歧义
  - 保留了对 A 的依赖
    - 对 A::f 的更改会改变 C::f

## 多重继承的 vtable

```cpp
class A {
    public:
        int x;
        virtual void f();
};
class B {
    public:
        int y;
        virtual void g();
        virtual void f();
};

class C: public A, public B {
    public:
        int z;
        virtual void f();
};
C *pc = new C;
B *pb = pc;
A *pa = pc;
```

三个指针指向同一对象，但静态类型不同。

## 对象和类

![](img/af430dff16b82a0fe61ce7dee05dcf9c_64_0.png)

- 在调用 pb->f 时使用 vtbl 中的偏移量 δ，因为 C::f 可能引用位于指针 pb 之上的 A 数据
- 对 pc->g 的调用可以通过 C-as-B vtbl 进行

## 多重继承“菱形”

![](img/af430dff16b82a0fe61ce7dee05dcf9c_65_0.png)

- 接口或实现是否被继承两次？
- 如果定义冲突怎么办？

## C++ 中的菱形继承

- 标准基类
  - D 的成员在 C 中出现两次
- 虚基类
  - `class A : public virtual D { ... }`
  - 避免基类成员的重复
  - 需要额外的指针，以便 D 部分的 A、B 部分的对象可以共享

C++ 多重继承之所以复杂，部分原因是希望保持高效的查找

![](img/af430dff16b82a0fe61ce7dee05dcf9c_66_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_66_1.png)

## C++ 总结

- 对象
  - 由类创建
  - 包含成员数据和指向类的指针
- 类：虚函数表
- 继承
  - 公有和私有基类，多重继承
- 子类型化：仅在使用公有基类时发生
- 封装
  - 成员可以声明为 public、private、protected
  - 对象初始化部分强制执行

## C++ vs. Java：偶然差异

- 布尔变量的类型是 `bool` 而不是 `boolean`。
- 类型 `char` 表示 8 位 ASCII 字符而不是 16 位 Unicode 字符。
- C++ 程序通过调用名为 `main` 的函数开始，该函数返回一个整数状态，成功完成时为 0。
- C++ 程序中使用的所有函数都必须先于一个 *prototype*，该原型定义了其参数结构。
- `string` 类导出的许多方法存在偶然差异。例如，C++ `substr` 方法的第二个参数是 *length* 而不是 *ending position*。
- 用于控制台 I/O 的学科有显著不同，但本质上并非如此。

## C++ vs. Java：本质差异

- C++ 允许你非常接近机器的内部工作。Java 保护你免受这些细节的影响。
- C++ 支持 *call by reference*。
- C++ 允许程序员以比 Java 更多的方式修改语言。特别是，C++ 类可以重新定义 + 或 << 等运算符的含义。
- C++ 没有 Java 那样的垃圾回收器。因此，*你* 有责任释放在堆上分配的任何内存。
- Java 中的对象始终在堆上分配。在 C++ 中，对象通常存储在栈上以简化内存管理任务。
- C++ 支持 *multiple inheritance*，这意味着类可以从多个超类继承行为。

## 应用

- 主页
- 联系人
- 电话
- 浏览器
- ...

## 应用框架

- Activity 管理器
- Window 管理器
- 内容提供者
- 视图系统
- 通知管理器
- 包管理器
- 电话管理器
- 资源管理器
- 位置管理器
- GTalk 服务

## 库

- Surface 管理器
- 媒体框架
- SQLite
- OpenGL ES
- FreeType
- WebKit
- SGL
- SSL
- libc

## Android 运行时

- 核心库
- Dalvik 虚拟机

## Linux 内核

- 显示驱动
- 相机驱动
- 蓝牙驱动
- 闪存驱动
- Binder（IPC）驱动
- USB 驱动
- 按键驱动
- WiFi 驱动
- 音频驱动
- 电源管理

