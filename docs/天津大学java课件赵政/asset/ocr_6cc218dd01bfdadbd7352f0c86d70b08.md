# 8.1.3 超类变量可以引用子类对象

+   超类的一个引用变量可以被任何从该超类派生的子类的引用赋值。

+   继承的这个方面在很多条件下是很有用的。

+   Weightbox 是 BoxWeight 对象的一个引用，plainbox 是 Box 对象的一个引用。

+   BoxWeight 是 Box 的一个子类，允许用一个 weightbox 对象的引用给 plainbox 赋值。