# A small catalog of architecture styles

| 体系结构风格 | 进一步细分 |
| --- | --- |
| 数据流系统 (Data flow) | 顺序批处理 (Batch Sequential) |
|  | 管道和过滤器 (Pipes and Filters) |
| 调用-返回系统 (call and return) | 主程序和子程序 (Main program and subroutine) |
|  | OO 系统 |
|  | 分层结构 (Layered) |
| 独立组件 (Independent components) | 通信进程 (Communicating Process) |
|  | 事件系统 | Implicit Invocation |
|  |  | Explicit Invocation |
| 虚拟机 (Virtual machine) | 解释器 (Interpreter) |
|  | 基于规则的系统 (Rule-Based System) |
| 数据为中心系统 (Data-centered) | 数据仓库 (Repository) |
|  | 超文本系统 ( Hypertext) |
|  | 黑板 ( Blackboard) |

# 虚拟机结构/解释器风格

基本结构

![](bbox=[0.22, 0.7, 0.78, 0.88])

Interpreters/Virtual Machine

+   - 作用：常被用于建立一种虚拟机以弥合程序的语义合作为计算引擎的硬件之间的间隙。
+   - 构件：四个构件——作为执行引擎的状态机和三个存储器
+   - 连接件：过程调用和直接存储访问。