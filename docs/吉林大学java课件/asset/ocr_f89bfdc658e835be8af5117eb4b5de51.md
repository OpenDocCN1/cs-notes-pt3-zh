# 在标签上设置图象 —— 另一种ImageIcon的使用

```
package org.lxh.demo18.jlabeldemo;
import java.awt.Color;
import java.io.File;
import javax.swing.Icon;
import javax.swing.ImageIcon;
import javax.swing.JFrame;
import javax.swing.JLabel;
public class JLabelDemo04 {
    public static void main(String args[]) {
        JFrame frame = new JFrame("Welcome To MLDN");    // 实例化窗体对象
        String picPath = "f:" + File.separator + "mldn.gif";    // 实例化Icon对象
        Icon icon = new ImageIcon(picPath) ;
        JLabel lab = null ;
        lab = new JLabel(icon, JLabel.CENTER);    // 实例化对象，使用居中对齐
        lab.setBackground(Color.YELLOW) ;    // 设置标签的背景颜色
        lab.setForeground(Color.RED) ;    // 设置标签的文字颜色
        frame.add(lab) ;    // 向容器中加入组件
        frame.setSize(300, 160) ;    // 设置组件大小
        frame.setBackground(Color.WHITE) ;    // 设置窗体的背景颜色
        frame.setLocation(300,200) ;    // 设置窗体的显示位置
        frame.setVisible(true) ;    // 让组件显示
    }
}
```

![](bbox=[0.65, 0.24, 0.98, 0.46])