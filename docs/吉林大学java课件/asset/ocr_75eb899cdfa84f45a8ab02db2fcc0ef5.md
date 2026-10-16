# 设置FlowLayout

```
package org.lxh.demo18.layoutdemo;
import java.awt.FlowLayout;
import javax.swing.JButton;
import javax.swing.JFrame;
public class FlowLayoutDemo01 {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Welcome To MLDN");        // 实例化窗体对象
        // 设置窗体中的布局管理器为FlowLayout，所有的组件居中对齐，水平和垂直间距为3
        frame.setLayout(new FlowLayout(FlowLayout.CENTER, 3, 3));
        JButton but = null;
        for (int i = 0; i < 9; i++) {
            but = new JButton("按钮 - " + i);
            frame.add(but);                         // 加入按钮
        }
        frame.setSize(280,123);                     // 设置窗体大小
        frame.setVisible(true);                     // 设置窗体可见
    }
}
```

![](bbox=[0.68, 0.27, 0.97, 0.43])