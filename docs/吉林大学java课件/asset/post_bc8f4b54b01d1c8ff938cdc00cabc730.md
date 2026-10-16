
## 使用匿名内部类

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

## 动作事件及监听处理

一个按钮要想让其变得有意义，就必须使用事件处理，在Swing的事件处理中，可以使用ActionListener接口处理按钮的动作事件，ActionListener接口只定义了一个方法。

| No. | 方法 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | void actionPerformed(ActionEvent e) | 普通 | 发生操作时调用 |

## 使用ActionListener监听

```
class ActionHandle{
    private JFrame frame = new JFrame("Welcome To MLDN");    // 声明
    private JButton but = new JButton("显示");    // 声明
    private JLabel lab = new JLabel();    // 声明
    private JTextField text = new JTextField(10);    // 定义
    private JPanel pan = new JPanel();    // 定义
    public ActionHandle(){
        Font fnt = new Font(...);    // 设置标签的显示字体
        lab.setFont(fnt);    // 设置默认显示文字
        but.addActionListener(new Action...){    // 采用匿名内部类
            public void actionPerformed(ActionEvent arg0){
                if (arg0.getSource() == but){    // 判断触发源是否是按钮
                    lab.setText(text.getText()); // 将文本文字设置到标签
                }
            }
        });    // 此处加入动作监听
        frame.addWindowListener(new WindowAdapter(){    // 加入窗口监听, 覆写窗口关闭的方法
            public void windowClosing(WindowEvent arg0){
                System.exit(1);    // 系统退出
            }
        });
        ...
    }
}
```

![](img/b706331eacf49a62651c2c9b2de81ca5_779_0.png)

![](img/b706331eacf49a62651c2c9b2de81ca5_779_1.png)

## 键盘事件及监听处理

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

## 实现键盘监听

```
class MyKeyHandle extends JFrame implements KeyListener {
    private JTextArea text = new JTextArea();
    public MyKeyHandle() {
        super.setTitle("Welcome To MLDN");
        JScrollPane scr = new JScrollPane(text);
        scr.setBounds(5,5, 300, 200);
        super.add(scr);
        text.addKeyListener(this);
        super.setSize(310,210);
        super.setVisible(true);
        super.addWindowListener(new WindowAdapter(){
            public void windowClosing(WindowEvent arg0) {
                System.exit(1);    // 系统退出
            }
        });
    }
    public void keyPressed(KeyEvent e) {    // 键盘按下
        text.append("键盘 \"" + KeyEvent.getKeyText(e.getKeyCode()) + "\"键按下\n");
    }
    public void keyReleased(KeyEvent e) {    // 键盘松开
        text.append("键盘 \"" + KeyEvent.getKeyText(e.getKeyCode()) + "\"键松开\n");
    }
    public void keyTyped(KeyEvent e) {    // 键入内容
        text.append("输入的内容是: " + e.getKeyChar() + "\n");
    }
}
```

![](img/b706331eacf49a62651c2c9b2de81ca5_781_0.png)

## 鼠标事件及监听处理

如果想对一个鼠标的操作进行监听，例如，鼠标按下、松开等，则可以实现MouseListener接口

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | void mouseClicked(MouseEvent e) | 普通 | 鼠标单击时调用（按下并释放） |
| 2 | void mousePressed(MouseEvent e) | 普通 | 鼠标按下时调用 |
| 3 | void mouseReleased(MouseEvent e) | 普通 | 鼠标松开时调用 |
| 4 | void mouseEntered(MouseEvent e) | 普通 | 鼠标进入到组件时调用 |
| 5 | void mouseExited(MouseEvent e) | 普通 | 鼠标离开组件时调用 |
