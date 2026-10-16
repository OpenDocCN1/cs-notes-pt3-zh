# Theory of the Strategy Pattern

# Structure

Client

传入策略子类对象

Context
ContextInterface()

为调用准备环境

Strategy
+operation()

提供了一个
共同的接口
operation()

Strategy

ConcreteStrategyA
+operation()

ConcreteStrategyB
+operation()

ConcreteStrategyC
+operation()

Diagram of Strategy pattern