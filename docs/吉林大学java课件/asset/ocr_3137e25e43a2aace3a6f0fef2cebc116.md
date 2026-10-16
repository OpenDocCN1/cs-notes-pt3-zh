# 为文本域加入滚动条

```
package org.lxh.demo18.jtextdemo;
import java.awt.GridLayout;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JScrollPane;
import javax.swing.JTextArea;
public class JTextAreaDemo02 {
    public static void main(String args[]) {
        JFrame frame = new JFrame("Welcome To MLDN");          // 实例化窗体对象
        JTextArea jta = new JTextArea(3,20);                    // 构造一个文本域
        jta.setLineWrap(true);                                  // 如果内容过长, 自动换行
        // 在文本域上加入滚动条, 水平和垂直滚动条始终出现
        JScrollPane scr = new JScrollPane(jta,
                JScrollPane.VERTICAL_SCROLLBAR_ALWAYS,
                JScrollPane.HORIZONTAL_SCROLLBAR_ALWAYS);
        JLabel lab = new JLabel("多行文本域:");                // 定义标签
        frame.setLayout(new GridLayout(2,1));                   // 设置布局管理器
        frame.add(lab);                                         // 向容器中增加组件
        frame.add(scr);                                         // 向容器中增加组件
        frame.setSize(300, 150);                                // 设置窗体大小
        frame.setLocation(300,200);                             // 设置窗体的显示位置
        frame.setVisible(true);                                 // 让组件显示
    }
}
```

![](bbox=[0.62, 0.26, 0.98, 0.48])