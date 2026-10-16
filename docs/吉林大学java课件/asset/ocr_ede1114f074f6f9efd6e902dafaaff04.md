# 窗体事件

WindowListener是专门处理窗体的事件监听接口，一个窗体的所有变化，例如：窗口打开、关闭等都可以使用这个接口进行监听。

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | void windowActivated(WindowEvent e) | 普通 | 将窗口变为活动窗口时触发 |
| 2 | void windowDeactivated(WindowEvent e) | 普通 | 将窗口变为不活动窗口时触发 |
| 3 | void windowClosed(WindowEvent e) | 普通 | 当窗口被关闭时触发 |
| 4 | void windowClosing(WindowEvent e) | 普通 | 当窗口正在关闭时触发 |
| 5 | void windowIconified(WindowEvent e) | 普通 | 窗口最小化时触发 |
| 6 | void windowDeiconified(WindowEvent e) | 普通 | 窗口从最小化恢复到正常状态时触发 |
| 7 | void windowOpened(WindowEvent e) | 普通 | 窗口打开时触发 |