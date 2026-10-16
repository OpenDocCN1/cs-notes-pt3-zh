# 依赖倒转原则

# 依赖倒转原则分析

+   ✓ 依赖注入

Home Blog Articles Books About Me Contact Me ThoughtWorks

# Inversion of Control Containers and the Dependency Injection pattern

Martin Fowler

In the Java community there's been a rush of lightweight containers that help to assemble components from different projects into a cohesive application. Underlying these containers is a common pattern to how they perform the wiring, a concept they refer under the very generic name of "Inversion of Control". In this article I dig into how this pattern works, under the more specific name of "Dependency Injection", and contrast it with the Service Locator alternative. The choice between them is less important than the principle of separating configuration from use.

Last significant update: 23 Jan 04

| Chinese | Portuguese | French | Italian |