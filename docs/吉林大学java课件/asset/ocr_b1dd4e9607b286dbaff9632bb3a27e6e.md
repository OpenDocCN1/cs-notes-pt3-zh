# 键盘事件及监听处理

在Swing的事件处理中也可以对键盘的操作进行监听，直接使用 KeyListener接口即可。此接口定义了如下的方法。

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | void keyTyped(KeyEvent e) | 普通 | 键入某个键时调用 |
| 2 | void keyPressed(KeyEvent e) | 普通 | 键盘按下时调用 |
| 3 | void keyReleased(KeyEvent e) | 普通 | 键盘松开时调用 |

如果要想取得键盘键入的内容，则可以通过KeyEvent取得，此类的常用方法如下所示。

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public char getKeyChar() | 普通 | 返回键入的字符，只针对keyTyped有意义 |
| 2 | public int getKeyCode() | 普通 | 返回键入字符的键码 |
| 3 | public static String getKeyText(int keyCode) | 普通 | 返回此键的信息，如：“HOME”、“F1”或“A”等 |