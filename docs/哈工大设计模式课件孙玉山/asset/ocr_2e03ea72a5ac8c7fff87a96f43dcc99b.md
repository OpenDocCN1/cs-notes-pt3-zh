# TrafficLightGUI

# Context

| Context |
|---|
| -light: LightState |
| +Context(LightState lt) |
| +getColor(): Color |
| +doAction(): void |
| +setState(String st): void |
| +setupStateObj(): LightState |

+   1) `rs = new Red();`
+   2) `cxt = new Context(rs);`
+   3) `rs.setupContext(cxt);`
+   4) `cxt.setState(TrafficLight.RED);`
+   5) `color = cxt.getColor();`
+   6) `cxt.doAction();`

调用 `performTask()`

# LightState

| LightState |
|---|
| +getCurrentState(): String |
| +setupContext(Context cxt): void |
| +performTask(): void |
| +setColor(): Color |
| +changeState(): void |

doAction() 被反复调用

light

获得状态对象

# Red

+   - `performTask()`
+   - `changeState()`
+   - `setColor()`

# Green

+   - `performTask()`
+   - `changeState()`
+   - `setColor()`

# Yellow

+   - `performTask()`
+   - `changeState()`
+   - `setColor()`