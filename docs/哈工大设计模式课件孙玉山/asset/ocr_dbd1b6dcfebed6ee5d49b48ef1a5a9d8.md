# Visitor Pattern-when to use?

# 何时使用访问者模式？

# Use the Visitor pattern when

+   1) 对象结构包含很多个子类，而这些类有不同的接口。你需要针对不同的类进行不同的操作。An object structure contains many classes of objects with differing interfaces, and you want to perform operations on these objects that depend on their concrete classes.

注：这就是为什么访问者类要针对每个被访问的类都设计一个不同的接口的原因。事实上，如果每个子类都有相同的接口，包括构造函数、其它方法、参数都一致，则访问者类则只需要设计一个访问方法，在该方法中，含有一个用于区别不同的被访问的子类的参数即可，例如，可以使用被访问者基类作为参数类型。