# C++编程概念 IN2377：第10讲：表达式模板与CRTP模式 🚀

![](img/76562bafaa214f560f4acc675a8dc6fe_1.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_3.png)

在本节课中，我们将要学习两种强大的C++编译时编程技术：**表达式模板** 和 **奇异递归模板模式**。我们将探讨如何利用这些技术编写出既优雅又高效的代码，特别是在数值线性代数等高性能计算领域。

---

![](img/76562bafaa214f560f4acc675a8dc6fe_5.png)

## 概述 📋

![](img/76562bafaa214f560f4acc675a8dc6fe_7.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_8.png)

上一讲我们探讨了编译时编程的基础。本节中，我们来看看两个具体的、强大的应用实例：**表达式模板** 和 **奇异递归模板模式**。表达式模板允许我们以数学公式般优雅的语法编写代码，同时获得与底层C风格循环相媲美甚至更优的性能。CRTP模式则是一种实现静态多态性的技术，可以在没有虚函数开销的情况下实现多态行为。

---

![](img/76562bafaa214f560f4acc675a8dc6fe_10.png)

## 表达式模板：优雅与性能兼得 ✨

![](img/76562bafaa214f560f4acc675a8dc6fe_12.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_14.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_15.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_17.png)

数值线性代数（例如向量和矩阵运算）是科学计算、深度学习等领域的核心。一个典型的操作是计算两个缩放后向量的和：
`z = c1 * x + c2 * y`

![](img/76562bafaa214f560f4acc675a8dc6fe_19.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_21.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_23.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_24.png)

### 传统C++方式的性能问题

![](img/76562bafaa214f560f4acc675a8dc6fe_26.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_28.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_29.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_30.png)

在C++中，我们可以通过运算符重载让代码像数学公式一样优雅：

![](img/76562bafaa214f560f4acc675a8dc6fe_32.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_33.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_35.png)

```cpp
Vector z = c1 * x + c2 * y;
```

![](img/76562bafaa214f560f4acc675a8dc6fe_37.png)

然而，这种直观写法的朴素实现（每个运算符都返回一个新的临时`Vector`对象）会导致严重的性能问题：
1.  **额外的内存分配**：`c1*x`和`c2*y`会创建两个临时向量，`+`操作可能再创建一个。对于大型向量（例如数十GB），这会耗尽GPU内存或显著增加内存压力。
2.  **缓存不友好**：多次遍历数据，效率低下。
3.  **性能损失**：与手写的、融合了所有操作的C风格循环相比，性能可能相差一个数量级（例如10倍）。

![](img/76562bafaa214f560f4acc675a8dc6fe_39.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_41.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_43.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_44.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_46.png)

### 解决方案：惰性求值与表达式模板

![](img/76562bafaa214f560f4acc675a8dc6fe_48.png)

核心思想是**惰性求值**。我们不立即执行每个运算符，而是将它们组合成一个**表达式树**，仅在最终需要结果（例如赋值给`z`）时，才一次性遍历数据并执行所有计算。

![](img/76562bafaa214f560f4acc675a8dc6fe_50.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_52.png)

表达式模板是一种在编译时构建此表达式树的技术。它通过模板元编程，将用户写的`c1 * x + c2 * y`这样的表达式，在编译期转换为一个代表整个计算过程的类型。

![](img/76562bafaa214f560f4acc675a8dc6fe_54.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_56.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_58.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_60.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_62.png)

以下是实现表达式模板的关键组件：

![](img/76562bafaa214f560f4acc675a8dc6fe_64.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_66.png)

1.  **通用的`Expression`类模板**：它存储一个代表元素级运算的可调用对象（如lambda）和对其操作数的引用（打包在`std::tuple`中）。

    ```cpp
    template <typename Callable, typename... Operands>
    class Expression {
    private:
        Callable callable_;
        std::tuple<const Operands&...> operands_;
    public:
        Expression(Callable callable, const Operands&... ops)
            : callable_(std::move(callable)), operands_(ops...) {}
        // ... 下标运算符稍后定义
    };
    ```

![](img/76562bafaa214f560f4acc675a8dc6fe_68.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_70.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_72.png)

2.  **重载运算符，返回表达式对象**：运算符（如`+`, `*`）不再进行计算，而是返回一个包装了相应运算和操作数的`Expression`对象。

    ```cpp
    // 向量加法运算符
    template <typename L, typename R>
    auto operator+(const L& lhs, const R& rhs) {
        auto callable = [](auto a, auto b) { return a + b; };
        return Expression<decltype(callable), L, R>(callable, lhs, rhs);
    }

    // 标量乘法运算符
    template <typename L, typename R>
    auto operator*(const L& lhs, const R& rhs) {
        auto callable = [](auto a, auto b) { return a * b; };
        return Expression<decltype(callable), L, R>(callable, lhs, rhs);
    }
    ```

    当用户写下`c1 * x`时，编译器会实例化并返回一个`Expression<Lambda, double, Vector>`类型的对象。

![](img/76562bafaa214f560f4acc675a8dc6fe_74.png)

3.  **`Vector`类的赋值运算符**：这是触发实际计算的“求值”点。它接受任何`Expression`类型，并遍历向量索引，对每个索引`i`调用表达式的下标运算符来获取结果。

    ```cpp
    class Vector {
        std::vector<double> data_;
    public:
        template <typename Expr>
        Vector& operator=(const Expr& expr) {
            for (size_t i = 0; i < data_.size(); ++i) {
                data_[i] = expr[i]; // 触发表达式求值
            }
            return *this;
        }
    };
    ```

![](img/76562bafaa214f560f4acc675a8dc6fe_76.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_78.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_80.png)

4.  **`Expression`的下标运算符**：这是魔法发生的地方。当`expr[i]`被调用时，它需要解包操作数元组，对每个操作数获取其第`i`个元素（如果是向量或表达式）或直接返回值（如果是标量），然后将这些值传递给存储的`callable_`（如乘法lambda）进行计算。

    这里需要一个辅助函数`subscript_at`，利用`if constexpr`和类型特征在编译时决定如何获取操作数的值：

    ```cpp
    // 类型特征，判断是否为向量或表达式
    template <typename T> struct is_vector_or_expr : std::false_type {};
    template <> struct is_vector_or_expr<Vector> : std::true_type {};
    template <typename Callable, typename... Ops>
    struct is_vector_or_expr<Expression<Callable, Ops...>> : std::true_type {};

    // 辅助函数：获取操作数在索引i处的值
    template <typename Operand>
    auto subscript_at(const Operand& op, size_t i) {
        if constexpr (is_vector_or_expr<Operand>::value) {
            return op[i]; // 向量或表达式：使用下标
        } else {
            return op;    // 标量：直接返回值
        }
    }

    // Expression类的下标运算符
    auto operator[](size_t i) const {
        auto call_at_index = [this, i](const auto&... ops) {
            // 对每个操作数调用subscript_at，然后传递给callable_
            return callable_(subscript_at(ops, i)...);
        };
        return std::apply(call_at_index, operands_);
    }
    ```

![](img/76562bafaa214f560f4acc675a8dc6fe_82.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_83.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_85.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_87.png)

### 优势与总结

![](img/76562bafaa214f560f4acc675a8dc6fe_89.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_91.png)

通过表达式模板，`Vector z = c1 * x + c2 * y;` 这行代码在编译期被转换为一个高效的、融合的循环，等价于：
```cpp
for (size_t i = 0; i < n; ++i) {
    z[i] = c1 * x[i] + c2 * y[i];
}
```

**优势**：
*   **零额外临时对象**：只存储标量和引用，内存效率与C风格代码相同。
*   **单次遍历**：数据只遍历一次，缓存友好。
*   **性能提升点**：在`Vector::operator=`的循环中，可以方便地引入**SIMD向量化**、**多线程并行**甚至**GPU内核调用**，而用户代码无需任何更改。
*   **语法优雅**：保持了数学公式般的可读性。

![](img/76562bafaa214f560f4acc675a8dc6fe_93.png)

**注意事项**：使用`auto`关键字接收表达式模板结果时需要小心，因为`auto expr = c1 * x + c2 * y;`只会存储表达式树，而不会进行计算。只有赋值给具体的`Vector`对象时才会求值。

![](img/76562bafaa214f560f4acc675a8dc6fe_95.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_97.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_99.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_101.png)

Eigen和Boost.uBLAS等库都使用了表达式模板技术。C++26标准也将引入基础的线性代数支持。

![](img/76562bafaa214f560f4acc675a8dc6fe_103.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_105.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_107.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_108.png)

---

![](img/76562bafaa214f560f4acc675a8dc6fe_110.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_112.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_114.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_116.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_118.png)

## 奇异递归模板模式：静态多态 🔄

![](img/76562bafaa214f560f4acc675a8dc6fe_120.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_122.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_124.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_125.png)

上一节我们介绍了如何利用编译时技术优化数值运算。本节中，我们来看看另一种模式——CRTP，它用于实现**静态多态**，以规避虚函数调用的运行时开销。

![](img/76562bafaa214f560f4acc675a8dc6fe_127.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_129.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_131.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_133.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_135.png)

### 动态多态的开销

![](img/76562bafaa214f560f4acc675a8dc6fe_137.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_139.png)

传统的多态通过虚函数和虚表实现。虽然灵活，但每次虚函数调用都涉及间接寻址，阻止了内联优化，在极端性能敏感的场景下可能成为瓶颈。

![](img/76562bafaa214f560f4acc675a8dc6fe_141.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_143.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_144.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_146.png)

### CRTP模式简介

![](img/76562bafaa214f560f4acc675a8dc6fe_148.png)

奇异递归模板模式的核心形式是：一个类`Derived`公开继承自一个以`Derived`自身作为模板参数的基类模板`Base<Derived>`。

![](img/76562bafaa214f560f4acc675a8dc6fe_150.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_152.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_154.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_155.png)

```cpp
template <typename Derived>
class Base {
    // ... 基类可以利用`Derived`类型
};

![](img/76562bafaa214f560f4acc675a8dc6fe_157.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_159.png)

class Derived : public Base<Derived> {
    // ...
};
```

![](img/76562bafaa214f560f4acc675a8dc6fe_161.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_163.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_165.png)

这种“循环”引用让基类在编译时就知道派生类的类型。

### 实现静态多态

![](img/76562bafaa214f560f4acc675a8dc6fe_167.png)

基类可以定义非虚方法，这些方法通过`static_cast`将`this`指针转换为派生类类型，然后调用派生类的方法。

![](img/76562bafaa214f560f4acc675a8dc6fe_169.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_171.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_173.png)

```cpp
template <typename Derived>
class Amount {
public:
    double getValue() const {
        // 在编译时向下转型为Derived并调用其getValue
        return static_cast<const Derived&>(*this).getValue();
    }
};

![](img/76562bafaa214f560f4acc675a8dc6fe_175.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_176.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_178.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_180.png)

class Constant42 : public Amount<Constant42> {
public:
    double getValue() const { return 42.0; }
};

![](img/76562bafaa214f560f4acc675a8dc6fe_182.png)

class Variable : public Amount<Variable> {
    double value_;
public:
    Variable(double v) : value_(v) {}
    double getValue() const { return value_; }
};

![](img/76562bafaa214f560f4acc675a8dc6fe_184.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_185.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_187.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_189.png)

// 使用模板函数实现“多态”调用
template <typename T> // T 被约束为继承自Amount<T>
void printValue(const Amount<T>& amount) {
    std::cout << amount.getValue() << std::endl;
}
// 调用 printValue(Constant42{}) 或 printValue(Variable{43})
```

![](img/76562bafaa214f560f4acc675a8dc6fe_191.png)

当`amount.getValue()`被调用时，它内联了`Derived::getValue()`的调用，没有虚函数开销。

![](img/76562bafaa214f560f4acc675a8dc6fe_193.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_195.png)

### C++20概念的简化

使用C++20的概念，可以更清晰地表达约束，而无需使用继承链：

![](img/76562bafaa214f560f4acc675a8dc6fe_197.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_199.png)

```cpp
template <typename T>
concept HasValue = requires(const T& t) {
    { t.getValue() } -> std::convertible_to<double>;
};

![](img/76562bafaa214f560f4acc675a8dc6fe_201.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_203.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_205.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_207.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_209.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_211.png)

template <HasValue T>
void printValue(const T& obj) {
    std::cout << obj.getValue() << std::endl;
}
// Constant42和Variable只需实现getValue，无需继承自特定基类。
```

![](img/76562bafaa214f560f4acc675a8dc6fe_213.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_215.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_217.png)

### 应用：多态克隆

![](img/76562bafaa214f560f4acc675a8dc6fe_219.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_221.png)

CRTP一个经典应用是实现“多态克隆”。在多态继承体系中，由于对象可能通过基类指针引用，直接拷贝会导致切片问题。常见的做法是禁止拷贝，并提供一个虚的`clone`方法。但使用`std::unique_ptr`等智能指针时，协变返回类型不再适用。

![](img/76562bafaa214f560f4acc675a8dc6fe_223.png)

以下是利用CRTP实现多态克隆的框架：

![](img/76562bafaa214f560f4acc675a8dc6fe_225.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_227.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_229.png)

1.  **定义可克隆接口**：
    ```cpp
    class Cloneable {
    public:
        virtual ~Cloneable() = default;
        virtual std::unique_ptr<Cloneable> cloneImpl() const = 0;
        std::unique_ptr<Cloneable> clone() const {
            return cloneImpl();
        }
    };
    ```

![](img/76562bafaa214f560f4acc675a8dc6fe_231.png)

2.  **使用CRTP的辅助类**：
    ```cpp
    template <typename Derived, typename Base = Cloneable>
    class CloneInherit : public Base {
    public:
        std::unique_ptr<Derived> clone() const {
            // 调用派生类的cloneImpl（来自基类接口）
            return std::unique_ptr<Derived>(
                static_cast<Derived*>(this->cloneImpl().release())
            );
        }
    private:
        // 实现基类的纯虚函数，利用协变返回类型（返回原始指针）
        Cloneable* cloneImpl() const override {
            return new Derived(static_cast<const Derived&>(*this));
        }
    };
    ```

![](img/76562bafaa214f560f4acc675a8dc6fe_233.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_234.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_236.png)

3.  **派生类的定义**：
    ```cpp
    class Concrete : public CloneInherit<Concrete> {
        // ... 私有拷贝构造函数
    public:
        // 现在Concrete对象拥有一个返回unique_ptr<Concrete>的clone方法
    };
    ```

![](img/76562bafaa214f560f4acc675a8dc6fe_238.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_240.png)

这样，我们通过CRTP在编译时为每个派生类注入了正确的克隆实现，避免了手动重复编写克隆逻辑，同时安全地使用了智能指针管理内存。

![](img/76562bafaa214f560f4acc675a8dc6fe_242.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_244.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_246.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_248.png)

---

![](img/76562bafaa214f560f4acc675a8dc6fe_250.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_252.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_254.png)

## 总结 🎯

![](img/76562bafaa214f560f4acc675a8dc6fe_256.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_258.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_260.png)

本节课中我们一起学习了两种高级的C++编译时编程范式：

![](img/76562bafaa214f560f4acc675a8dc6fe_262.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_264.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_266.png)

1.  **表达式模板**：通过编译期表达式树和惰性求值，将优雅的运算符重载语法转换为高效、融合的循环。这是高性能线性代数库的基石，允许无缝集成向量化、并行化和GPU计算。

![](img/76562bafaa214f560f4acc675a8dc6fe_268.png)

2.  **奇异递归模板模式**：通过让基类以派生类为模板参数，实现编译时多态，消除虚函数开销。我们看到了它在静态多态接口和多态克隆等场景下的应用。

![](img/76562bafaa214f560f4acc675a8dc6fe_270.png)

![](img/76562bafaa214f560f4acc675a8dc6fe_272.png)

这些技术体现了C++“零开销抽象”哲学的强大之处：你可以构建高级、易用的接口，同时不牺牲底层性能。虽然实现细节可能复杂，但它们通常被封装在库中，最终用户能享受到简洁和高效的双重好处。理解这些模式有助于你阅读高级库的源码，并在需要时自己构建高性能的抽象。