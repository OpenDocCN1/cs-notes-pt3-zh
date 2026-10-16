
- Unicon以枚举的方式预定义了多种构件和连接件类型。
  - 预定义的构件类型包括Module，Computation，SharedData，SeqFile，Filter，Process，SharedProcess，General。
  - 预定义的连接类型包括Pipe，FileIO，ProcedureCall，DataAccess，PLBundler，RemoteProcCall，RTScheduler。Unicon还定义了每个构件类型的演员和每个连接件类型的角色，以及约束演员和角色匹配关系的内部规则。
- Unicon提供了图形和文本两种描述方式，可以在这两种方式之间进行转换，提供了编译器支持文本形式编译。
- Unicon将各种连接件的实现机制都内嵌到了工具的实现当中，编译器对实现构件功能的源文件或对象文件的位置进行跟踪。
  - 当模型经过解析并将所有连接关系都建立起来之后，Unicon可以产生一个类似Make文件的描述文件，然后触发目标语言的编译和链接工具来生成可执行系统。
  - Unicon提供了与外部开发工具进行集成的机制，通过集成RMA。
  - Unicon可以对实时处理过程中进程的调度情况进行分析。

## 构件的定义：

```
〈Component〉::= COMPONENT <identifier>
                         <interface>
                         <component_implementation>
                   END <identifier>
〈interface〉::= INTERFACE IS
                         TYPE <component_type>
                         <property_list>
                         <player_list>
                   END INTERFACE
〈component_type〉::= Module|Computation|SharedData|SeqFile|
                     Filter|Process|SchedProcess|General
〈component_implementation〉::= <primitive_implementation>|
                               <composite_implementation>
....................
```

![](img/da691714eec1b93795825838a75ee408_208_0.png)

![](img/da691714eec1b93795825838a75ee408_208_1.png)

- 连接件的定义：
  
  ```text
  <Connector> ::= CONNECTOR <identifier>
                  <protocol>
                  <connector_implementation>
                END <identifier>

  <protocol> ::= PROTOCOL IS
                  TYPE <connector_type>
                  <property_list>
                  <role_list>
                END PROTOCOL

  <connector_type> ::= DataAccess|FileIO|Pipe|PLBundler|
                       ProcedureCall|RemoteProcCall|RTScheduler

  <connector_implementation> ::= IMPLEMENTATION IS
                                  BUILTIN
                                  END IMPLEMENTATION
  ```

- 连接件的实现方式是UniCon语言内建的，不支持用户定义的连接件。

## Darwin

- Darwin主要用来对**基于消息传递的分布式系统**进行描述，通过π-calculus来描述结构元素的语义，对系统行为建模，利用其强类型系统进行静态检查。
- Darwin没有对连接件提供显式的描述，构件之间的交互关系通过绑定关系来表示。
  - 提供了惰性实例化（Lazy Instantiation）和显式动态构建（Explicit Dynamic Construction）两种机制来支持系统的动态配置，支持软件体系结构执行时期的演化。
- Darwin对软件体系结构风格的支持通过参数配置实现。Darwin具备**编译器**，这使得它们可以根据软件体系结构描述**生成可执行系统**。

## Rapide

- Rapide是美国Standford大学的David C. Luckham等人定义的一种可执行的软件体系结构描述语言，主要适用于对基于事件的、复杂、并发、分布式系统的软件体系结构进行描述。
- Rapide是一种基于事件的、并发的面向对象语言，为系统的体系结构建立快速原型。
- Rapide中构件的计算和交互语言通过偏序事件集（称为posets）定义。构件计算由构件接受到事件触发，并进一步产生事件传送到其他构件，由此触发其他计算。
- Rapide构件类型（称为Interfaces）的定义包括动作、服务、行为和约束，其中对动作和服务的执行和调度表现为事件的接收和发送。构件间的连接通过监视和产生事件的匹配来实现，并不能对连接件提供显示的支持。

## Rapide特点

- 与Unicon、Darwin等直接通过实现来定义构件行为的方式不同，Rapide通过抽象状态和状态转移规则来定义该类构件的行为约束。
  - 利用这种机制Rapide可以对软件体系结构进行模拟执行，模拟执行过程中可以进行模型的一致性检查和分析，模型的执行结果被表示为一系列具有因果（Causal）和时序（Timing）关系事件集合。
- Rapide具备编译器，可以根据软件体系结构描述生成可执行系统。

## Rapide

- **Rapide由5种子语言组成：**
  - **类型语言：** 定义接口类型和函数类型，支持通过继承已有的接口来构造新的接口类型。
  - **模式语言：** 定义具有因果、独立、时序等关系的事件所构成的事件模式。
  - **可执行语言：** 包含描述构件行为的控制结构。
  - **体系结构语言：** 通过定义同步和通信连接来描述构件之间的事件流。
  - **约束语言：** 定义构件行为和体系结构所满足的形式化约束，其中约束为需要的或禁止的偏序集模式。

## 对构件的描述

```
type Application is interface
    in action Request ( p: params);
    out action Request (p : params);
    behavior
       (?M in string) Receive(?M=>Results(?M);
end Application;
```

## MetaH

- MetaH是由Honeywell定义的，支持对可靠性和安全性要求较高的多处理器实时嵌入式系统的创建、分析和验证，主要适用于航空电子控制软件系统。
- MetaH的语义主要基于形式化调度和数据流模型。
  - 预定义了一些构件类型，包括事件（Event）、端口（Port）、子程序（SubProgram）、包（Package）、监视器（Monitor）和进程（Process）；
  - 预定义连接类型包括事件连接、端口连接、等价连接和存取连接等。在构件连接件的定义中嵌入了很多与领域相关的信息。
- MetaH支持实时调度、可靠性和安全性分析，以及代码的自动生成、编译和连接功能，可以根据软件体系结构描述生成可执行系统。

## AADL（Architecture Analysis and Design Language）

- AADL是一种体系结构描述语言，主要是用于对嵌入式实时系统进行建模。
- AADL的背景：
  - 在设计关键任务和实时系统时，设计师必须满足功能需求和非功能需求，如性能（吞吐量和服务质量）、保护、可靠性、时间间歇性、安全和容错等。随着嵌入式软件系统的硬件多样性和复杂性的不断提高，可以采用模型驱动的开发方法来满足开发早期阶段出现的系统集成问题。基于模型的设计方法的要点之一是要选择合适的设计语言来描述具体平台架构。
