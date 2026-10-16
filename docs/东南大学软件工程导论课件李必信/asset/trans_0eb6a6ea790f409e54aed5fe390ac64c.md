

## 可替换性
- 子类应当可以替换其基类

![](img/fcdc64f47992afbcce2e20fafbbb0375_281_0.png)

## 依赖倒置
- 依赖于抽象。
- 不要依赖于具体实现。

![](img/fcdc64f47992afbcce2e20fafbbb0375_282_0.png)

## 接口隔离
- 多个特定于客户的接口要好于一个通用目的的接口。

![](img/fcdc64f47992afbcce2e20fafbbb0375_283_0.png)

## 内聚
- 模块的“专一性”
- 内聚意味着单个组件或类只封装那些彼此紧密相关、并且与该类或组件本身紧密相关的属性和操作。
- 内聚的示例
  - 功能性
  - 层
  - 通信性

## 功能内聚
- 通常适用于操作。当一个模块只执行一个且仅一个计算，然后返回结果时，发生功能内聚。

![](img/fcdc64f47992afbcce2e20fafbbb0375_285_0.png)

## 层内聚
- 适用于包、组件和类。当高层可以访问低层，但低层不能访问高层时，发生层内聚。

![](img/fcdc64f47992afbcce2e20fafbbb0375_286_0.png)

## 耦合
- 对类或组件之间相互连接程度的一种定性度量。
- **应避免**
  - 内容耦合
- **需谨慎**
  - 公共耦合
- **需注意**
  - 常规调用耦合
  - 类型使用耦合
  - 包含或导入耦合

## 内容耦合
- 当一个组件“偷偷修改另一个组件内部的数据”时发生。
- 违反信息隐藏
- 这里有什么问题？ →

```
public class StudentRecord {
    private String name;
    private int[] quizScores;

    public String getName() {
        return name;
    }
    public int getQuizScore(int n) {
        return quizScores[n];
    }
    public int[] getAllQuizScores() {
        return quizScores;
    }
    ....
```

## 公共耦合
- 当多个组件都使用一个全局变量时发生。

![](img/fcdc64f47992afbcce2e20fafbbb0375_290_0.png)

## 常规耦合
- 在面向对象编程中，某些类型的耦合经常出现。

```
package myPackage;
import java.util.Collection.*;

public class MyClass {
    private Stack s;
    public void doSomething() {
        s.push(x);
        // do something
    }
    ...
```

![](img/fcdc64f47992afbcce2e20fafbbb0375_291_0.png)

## 组件级设计
- 1. 识别问题领域中的设计类
- 2. 识别基础设施设计类
- 3. 详细描述设计类
- 4. 描述持久化数据源
- 5. 详细描述行为表示
- 6. 详细描述部署图
- 7. 重构设计并考虑替代方案

## 步骤 1 和 2 – 识别类
- 1. 问题领域中的大多数类是作为分析模型的一部分而创建的分析类。
- 2. 基础设施设计类在架构设计期间作为组件被引入。

## 第 3 步 – 类的细化
- a) 当类或组件协作时，指定消息的详细信息。
- b) 为每个组件识别合适的接口。
- c) 细化属性并定义实现它们所需的数据结构。
- d) 详细描述每个操作内的处理流程。

### 3a. 协作细节
- 可以通过以下方式扩展消息的语法来对其进行细化：
  - `[guard condition] sequence expression (return value) := message name (argument list)`

![](img/fcdc64f47992afbcce2e20fafbbb0375_295_0.png)

### 3b. 合适的接口
- Pressman 认为，幻灯片 5 中 PrintJob 接口的“initiateJob”没有表现出足够的内聚性，因为它执行了三个不同的子功能。他建议进行这种重构。

![](img/fcdc64f47992afbcce2e20fafbbb0375_296_0.png)

