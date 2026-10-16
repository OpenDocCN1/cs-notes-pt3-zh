# Structural Patterns -bridge

+   - 结构

# Structural Patterns

Composite: compose objects into tree structures. Composite lets clients treat objects uniformly.

# Structural Patterns (II)

Facade: provide a unified interface to a set of interface in subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.

# Behavior Patterns

+   - 行为模式涉及算法和对象间职责的分配。
+   - 行为模式不仅描述了对象和类的模式，还描述了它们之间的通讯模式
+   - 分为两类：
+     - 使用继承机制：如Template Method, Interpreter
+     - 使用对象组合：如Mediator, Chain of Responsibility 等

# Behavior Patterns—

+   - Chain of responsibility:
+   - Avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. Chain the receiving objects and pass the request along the chain until an object handles it.