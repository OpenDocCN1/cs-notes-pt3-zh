# Queue和QueueItem的友元声明

+   - Queue类的operator<<输出操作符依赖于item对象的operator<<实际输出每个元素：
+     os << p->item << " ";
+   - 绑定到Queue且使用Queue输出操作符的每种类型本身也必须有输出操作符
+   - 没有语言机制指定或强制Queue自身定义中的依赖性
+   - 为没有定义输出操作符的类创建Queue对象是合法的，但是输出保存这种类型的Queue对象会发生编译时或链接时错误