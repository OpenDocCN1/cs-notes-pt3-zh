
## 在标签上设置图像 —— 使用InputStream

```
public class JLabelDemo03 {
    public static void main(String args[]) {
        JFrame frame = new JFrame("Welcome To MLDN");       // 实例化窗体对象
        String picPath = ":f:" + File.separator + "mldn.gif";
        File file = new File(picPath);                       // 实例化File对象
        InputStream input = null;                            // 输入流对象
        byte b[] = new byte[(int)file.length()];             // 根据图片大小开辟byte数组
        try {
            input = new FileInputStream(file);               // 实例化输入流对象
            input.read(b);                                    // 读取文件信息
            input.close();                                   // 关闭输入流
        } catch (Exception e) {
            e.printStackTrace();
        }
        Icon icon = new ImageIcon(b);                        // 实例化Icon对象
        JLabel lab = null;
        lab = new JLabel("MLDN", icon, JLabel.CENTER);      // 实例化对象，使用居中对齐
        Font fnt = new Font("Serief", Font.ITALIC + Font.BOLD, 28);
        lab.setFont(fnt);                                     // 设置标签的字体
        lab.setBackground(Color.YELLOW);                     // 设置标签的背景颜色
        lab.setForeground(Color.RED);                        // 设置标签的文字颜色
        frame.add(lab);                                       // 向容器中加入组件
        frame.setSize(300, 160);                             // 设置组件大小
        frame.setBackground(Color.WHITE);                    // 设置窗体的背景颜色
        frame.setLocation(300, 200);                         // 设置窗体的位置
        frame.setVisible(true);                              // 让组件显示
    }
}
```

![](img/b706331eacf49a62651c2c9b2de81ca5_729_0.png)

## 在标签上设置图象 —— 另一种ImageIcon的使用

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

![](img/b706331eacf49a62651c2c9b2de81ca5_730_0.png)

## 下一章内容

## 按钮组件： JButton

![](img/b706331eacf49a62651c2c9b2de81ca5_731_0.png)

## 图形界面
—— 按钮组件：JButton

## 本章目标

- □ 了解JButton的作用
- □ 可以向JButton中设置图片显示

## JButton组件

JButton组件表示一个普通的按钮，直接使用此类就可以直接在窗体中增加一个按钮。

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public JButton() throws HeadlessException | 构造 | 创建一个Button对象 |
| 2 | public JButton(String label) throws HeadlessException | 构造 | 创建一个Button对象，同时指定其显示内容 |
| 3 | public JButton(Icon icon) | 构造 | 创建一个带图片的按钮 |
| 4 | public JButton(String text,Icon icon) | 构造 | 创建一个带图片和文字的按钮 |
| 5 | public void setLabel(String label) | 普通 | 设置Button的显示内容 |
| 6 | public String getLabel() | 普通 | 得到Button的显示内容 |
| 7 | public void setBounds(int x,int y,int width,int height) | 普通 | 设置组件的大小及显示方式 |
| 8 | public void setMnemonic(int mnemonic) | 普通 | 设置按钮的快捷键 |

## 建立一个普通的按钮

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

![](img/b706331eacf49a62651c2c9b2de81ca5_735_0.png)
