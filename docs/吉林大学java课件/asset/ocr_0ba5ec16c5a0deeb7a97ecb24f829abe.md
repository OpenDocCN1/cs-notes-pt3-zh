# 定义复选框

```
class MyCheckBox {
    private JFrame frame = new JFrame("Welcome To MLDN");        // 定义窗体
    private Container cont = frame.getContentPane();               // 得到窗体容器
    private JCheckBox jcb1 = new JCheckBox("MLDN");               // 定义一个复选框
    private JCheckBox jcb2 = new JCheckBox("MLDNJAVA");           // 定义一个复选框
    private JCheckBox jcb3 = new JCheckBox("智霖网");             // 定义一个复选框
    private JPanel pan = new JPanel();                              // 定义一个面板
    public MyCheckBox() {
        pan.setBorder(BorderFactory.createTitledBorder("请选择最喜爱的网站")); // 定义一个面板的边框显示条
        pan.setLayout(new GridLayout(1, 3));                        // 定义排版，1行3列
        pan.add(this.jcb1);                                         // 加入组件
        pan.add(this.jcb2);                                         // 加入组件
        pan.add(this.jcb3);                                         // 加入组件
        cont.add(pan);                                              // 加入面板
        this.frame.setSize(330,80);                                 // 定义窗体大小
        this.frame.setVisible(true);                                // 显示窗体
        this.frame.addWindowListener(new WindowAdapter(){
            public void windowClosing(WindowEvent arg0) {
                System.exit(1);                                 // 系统退出
            }
        });
    }
}
```