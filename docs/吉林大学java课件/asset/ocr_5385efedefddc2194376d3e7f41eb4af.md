# 里氏代换原则

# 里氏代换原则定义

+   里氏代换原则(Liskov Substitution Principle, LSP)有两种定义方式，第一种定义方式相对严格，其定义如下：
+   - 如果对每一个类型为S的对象o1，都有类型为T的对象o2，使得以T定义的所有程序P在所有的对象o1都代替成o2时，程序P的行为没有变化，那么类型S是类型T的子类型。

+   其英文定义为：
+   - If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T.

+   第二种更容易理解的定义方式如下：
+   - 所有引用基类（父类）的地方必须能透明地使用其子类的对象。

+   其英文定义为：
+   - Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.