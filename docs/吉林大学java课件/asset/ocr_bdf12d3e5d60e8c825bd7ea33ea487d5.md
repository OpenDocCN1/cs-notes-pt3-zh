# 使用JTextArea

```
package org.lxh.demo18.jtextdemo;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextArea;
public class JTextAreaDemo01 {
    public static void main(String args[]) {
        JFrame frame = new JFrame("Welcome To MLDN");    // 实例化窗体对象
        JTextArea jta = new JTextArea(3,10);             // 构造一个文本域
        JLabel lab = new JLabel("多行文本域：");         // 定义标签
        lab.setBounds(10,10,120,20);                     // 设置组件位置及大小
        jta.setBounds(130, 10, 150, 100);                // 设置组件位置及大小
        frame.setLayout(null);                           // 使用绝对定位
        frame.add(lab);                                  // 向容器中增加组件
        frame.add(jta);                                  // 向容器中增加组件
        frame.setSize(300, 150);                         // 设置窗体大小
        frame.setLocation(300,200);                      // 设置窗体的显示位置
        frame.setVisible(true);
    }
}
```

![](bbox=[0.65, 0.64, 0.97, 0.89])