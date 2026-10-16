# 建立一个普通的按钮

```
package org.lxh.demo18.jbuttondemo;
import java.awt.Color;
import java.awt.Font;
import javax.swing.JButton;
import javax.swing.JFrame;
public class JButtonDemo01 {
    public static void main(String args[]) {
        JFrame frame = new JFrame("Welcome To MLDN"); // 实例化窗口对象
        JButton but = new JButton("按我");                 // 定义按钮对象
        Font fnt = new Font("Serif", Font.BOLD, 28);
        but.setFont(fnt);                                   // 设置按钮的显示字体
        frame.add(but);                                     // 向容器中加入组件
        frame.setSize(200, 70);                             // 设置窗口大小
        frame.setLocation(300,200);                         // 设置窗口的显示位置
        frame.setVisible(true);                             // 让组件显示
    }
}
```

![](bbox=[0.72, 0.71, 0.95, 0.85])