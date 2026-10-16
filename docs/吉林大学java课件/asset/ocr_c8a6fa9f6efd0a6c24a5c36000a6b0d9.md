# 实现WindowListener

```
public class MyWindowEventHandle implements WindowListener { // 实现窗口监听
    public void windowActivated(WindowEvent arg0) {      // 设置为活动窗口时触发
        System.out.println("windowActivated --> 窗口被选中。");
    }
    public void windowClosed(WindowEvent arg0) {      // 窗口被关闭窗口时触发
        System.out.println("windowClosed --> 窗口被关闭。");
    }
    public void windowClosing(WindowEvent arg0) {      // 窗口关闭时触发，按下关闭按钮
        System.out.println("windowClosing --> 窗口关闭。");
        System.exit(1) ;                         // 系统退出
    }
    public void windowDeactivated(WindowEvent arg0) {      // 设置为非活动窗口时触发
        System.out.println("windowDeactivated --> 取消窗口选中。");
    }
    public void windowDeiconified(WindowEvent arg0) {      // 窗口从最小化还原时触发
        System.out.println("windowDeiconified --> 窗口从最小化恢复。");
    }
    public void windowIconified(WindowEvent arg0) {      // 窗口最小化时触发
        System.out.println("windowIconified --> 窗口最小化。");
    }
    public void windowOpened(WindowEvent arg0) {      // 窗口打开时触发
        System.out.println("windowOpened --> 窗口被打开。");
    }
}
```