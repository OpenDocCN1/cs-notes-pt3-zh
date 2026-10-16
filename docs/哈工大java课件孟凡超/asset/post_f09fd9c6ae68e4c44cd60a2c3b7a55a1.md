
## 7.4 事件处理

产生并传递 ActionEvent事件对象e

接收事件对象e，激活事件处理器，实现关闭窗口功能。

单击关闭按钮

事件对象 e

事件源 按钮对象b

监听器对象 （含关闭窗口事件处理器）

注册

实例化

ActionEvent监听器类 ButtonHandler （含关闭窗口事件处理器）

含有

图形界面程序 （ActionEventDemo）

## 7.4 事件处理

```
package example.charpter_7;
import java.awt.*;

public class ActionEventDemo {
    public static void main(String[] args) {
        JFrame frame=new JFrame("ActionEvent Demo");
        MyButton b=new MyButton("Press me");//事件源
        //注册事件监听器（ActionEvent型事件）
        //b.addActionListener(new ButtonHandler());
        frame.getContentPane().add(b,BorderLayout.CENTER);
        frame.setSize(200,100);
        frame.setVisible(true);
    }
}
//MyButton类定义
class MyButton extends JButton implements ActionListener{
    public MyButton(String text){
        super(text);//继承父类的构造函数
        addActionListener(this);//注册事件监听程序
    }
    //出现ActionEvent事件时，输出"Action occurred",结束程序运行
    public void actionPerformed(ActionEvent e){
        System.out.println("Action occurred");
        System.exit(0);
    }
}
```

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_265_0.png)

## 7.4 事件处理

### 事件的种类

- 每一类事件有一个相应的事件监听器接口，该接口定义了接收和处理事件的抽象方法。实现该接口的类，就是监听器类。其对象可作为监听器对象向相应的组件注册。
- 事件的类名通常为： XxxEvent。
- 对应的事件监听器接口名通常为： XxxListener。
- 一个监听器接口定义了一种以上的抽象事件处理方法（事件处理器）。
- 事件监听器类实现事件监听器接口，其类名可以由我们自己取。事件监听器类需要我们自己编写。

## 7.4 事件处理

### ■一个事件处理例子

| 事件类别 | interface名称 | 方法 |
|---|---|---|
| Mouse Motion | MouseMotionListener | mouseDragged(MouseEvent)<br>mouseMoved(MouseEvent) |
| Mouse Button | MouseListener | mousePressed(MouseEvent)<br>mouseReleased(MouseEvent)<br>mouseEntered(MouseEvent)<br>mouseExited(MouseEvent)<br>mouseClicked(MouseEvent) |

## 7.4 事件处理

```
public class TwoListener implements MouseMotionListener, MouseListener{
    private JFrame frame;
    private JTextField tf;

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        TwoListener that=new TwoListener();
        that.go();
    }

    public void go(){
        frame=new JFrame("Two listeners example");
        Container contentPane=frame.getContentPane();
        contentPane.add(new Label("Click and drag the mouse"),BorderLayout.NORTH);
        tf=new JTextField(30);
        contentPane.add(tf,BorderLayout.SOUTH);
        //注册监听程序
        frame.addMouseMotionListener(this);
        frame.addMouseListener(this);
        frame.setSize(300*300);
        frame.setVisible(true);
    }
}
```

同时实现两个接口

监听多类事件

## 7.4 事件处理

```
//实现MouseMotionListener接口中的方法
public void mouseDragged(MouseEvent e){
    System.out.println("mouseDragged");
}
public void mouseMoved(MouseEvent e){
    String s="Mouse dragging: X="+e.getX()+"Y="+e.getY();
    tf.setText(s);
}

//实现MouseListener接口中的方法
public void mouseClicked(MouseEvent e){
}
public void mouseEntered(MouseEvent e){
    String s="The Mouse entered";
    tf.setText(s);
}
public void mouseExited(MouseEvent e){
    String s="The Mouse has left the building";
    tf.setText(s);
}
public void mousePressed(MouseEvent e){
}
public void mouseReleased(MouseEvent e){
}
```

## 7.4 事件处理

### 监听适配器

单击鼠标事件监听器类(实现监听器类)

```
public class MouseClickHandler implements MouseListener{
    //我们只关心对单击鼠标事件的处理，因此改写mouseClicked()方法
    public void mouseClicked(MouseEvent e){
        //处理代码
    }
    //对于其他方法，仍需要给出实现
    public void mousePressed(MouseEvent e){}
    public void mouseReleased(MouseEvent e){}
    public void mouseEntered(MouseEvent e){}
    public void mouseExited(MouseEvent e){ }
}
```

## 7.4 事件处理

### mouseListener接口

```
public interface mouseListener extends EventListener{
    public void mouseClicked(MouseEvent e);
    public void mousePressed(MouseEvent e);
    public void mouseReleased(MouseEvent e);
    public void mouseEntered(MouseEvent e);
    public void mouseExited(MouseEvent e);
}
```

### 对应的适配器mouseAdapter

```
public abstract class mouseAdapter implements mouseListener {
    public void mouseClicked(MouseEvent e){}
    public void mousePressed(MouseEvent e){}
    public void mouseReleased(MouseEvent e){}
    public void mouseEntered(MouseEvent e){}
    public void mouseExited(MouseEvent e){}
}
```
