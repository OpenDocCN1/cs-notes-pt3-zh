# TrafficLightGUI

# Context

-light: LightState
+Context(LightState lt)
+getColor(): Color
+doAction(): void 调用performTask()
+setState(String st): void
+setupStateObj(): LightState

创建一个具体的状态对象，并且传递给Context

具体的子类负责改变状态

light

决定状态对象

# LightState

+getCurrentState(): String
+setupContext(Context cxt): void
+performTask(): void
+setColor(): Color
+changeState(): void

# Red

+performTask(): void
+setColor(): Color
+changeState(): void

# Yellow

+performTask(): void
+setColor(): Color
+changeState(): void

# Green

+performTask(): void
+setColor(): Color
+changeState(): void

交通信号灯控制软件-设计1