```
```java
public static void main(String []args){
    T1 frm=new T1();
    frm.addWindowListener(new winListen());    //在main中添加监听窗口事件
}
class ItListen implements ItemListener{    //内部类,监听是否发生ItemEvent事件
    public void itemStateChanged(ItemEvent e){    //选择项目时执行
        jlb.setText("你选中了"+jcb.getSelectedItem());    //getSelectedItem():获得选项
    }
}
static class winListen extends WindowAdapter{    //内部类,监听是否发生WindowEvent事件
    public void windowClosing(WindowEvent e){    //关闭窗口时执行
        System.exit(0);    //终止程序执行
    }
}
```

```

![](bbox=[0.357, 0.711, 0.626, 0.978])