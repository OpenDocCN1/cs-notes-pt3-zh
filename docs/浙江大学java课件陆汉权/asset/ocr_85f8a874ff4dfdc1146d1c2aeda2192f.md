Swing组合框举例：窗口中有一个组合框和一个标签，当选择组合框中某项时，在标签中显示所选的信息。

```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.event.*;
public class T1 extends JFrame{
    private JComboBox jcb;
    private JLabel jlb;
    public T1(){
        super("组合框举例");              //构造方法
        setSize(200,150);
        Object obj[]={"杭州","宁波","温州","金华","绍兴","嘉兴","湖州"};
        jcb=new JComboBox(obj);
        jcb.setMaximumRowCount(4);    //设置下拉列表框显示的最大行数
        jlb=new JLabel("");
        Container c=getContentPane();       //获得默认的内容窗格
        c.setLayout(new FlowLayout());
        c.add(jcb);
        c.add(jlb);
        jcb.addItemListener(new ItListener());   //构造方法中添加监听组合框事件
        setVisible(true);
    }
}
```

![](bbox=[0.664, 0.089, 0.972, 0.396])