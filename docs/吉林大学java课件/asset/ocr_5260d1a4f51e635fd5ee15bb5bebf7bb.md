# 使用匿名内部类

```
package org.lxh.demo18.windoweventdemo;
import java.awt.Color;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import javax.swing.JFrame;
public class MyWindowEventJFrame03 {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Welcome To MLDN");        // 实例化窗体对象
        // 此时直接使用WindowAdapter的子类完成监听的处理
        frame.addWindowListener(new WindowAdapter() {        // 覆盖窗口关闭的方法
            public void windowClosing(WindowEvent arg0) {
                System.exit(1);                         // 系统退出
            }
        });
        frame.setSize(300, 160);                        // 设置组件大小
        frame.setBackground(Color.WHITE);               // 设置窗体的背景颜色
        frame.setLocation(300,200);                     // 设置窗体的显示位置
        frame.setVisible(true);                         // 让组件显示
    }
}
```