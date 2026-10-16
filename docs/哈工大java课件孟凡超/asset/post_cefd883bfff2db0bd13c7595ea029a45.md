
## 组合框

添加/删除选项：

- public void addItem(Object anObject);
- public void insertItemAt(Object anObject, int index);
- public void removeAllItems();
- public void removeItem(Object anObject);
- public void removeItemAt(int anIndex);

### JComboBox例子

```
JComboBox jcb1;
String[] itemList={"One","Two","Three","Four","Five"};
jcb1 = new JComboBox(itemList);
jcb1.setSelectedIndex(1);
```

```
JComboBox jcb2 = new JComboBox();
jcb2.addItem("Six");
jcb2.addItem("Seven");
jcb2.addItem("Eight");
jcb2.addItem("Nine");
jcb2.setSelectedIndex(2);
jcb2.setEditable(true);
```

## 列表

列表(JList)是可供用户进行选择的一系列可选项。

JList的构造方法：

- JList();
- JList(ListModel dataModel);
- JList(Object[] listData);
- JList(Vector listData);

```
String[] listData={"one", "two", "three", "four"};
JList jl=new JList(listData);
```

```
Vector listData=new Vector();
listData.addElement("one");
listData.addElement("two");
listData.addElement("three");
listData.addElement("four");
JList jl=new JList(listData);
```

```java
DefaultListModel listModel = new DefaultListModel();
listModel.addElement("one");
listModel.addElement("two");
listModel.addElement("three");
listModel.addElement("four");
JList jl = new JList(listModel);
```

```
public void go(){
    listModel=new DefaultListModel();
    listModel.addElement("one");
    listModel.addElement("two");
    listModel.addElement("three");
    listModel.addElement("four");
    list=new JList(listModel);//
    JScrollPane jsp=new JScrollPane(list,JScrollPane.VERTICAL_SCROLLBAR_AS_NEEDED,
        JScrollPane.HORIZONTAL_SCROLLBAR_AS_NEEDED);
    Container cp=frame.getContentPane();
    cp.add(jsp);
    tf=new JTextField(15);
    button=new JButton("add new item");
    //注册事件监听器
    button.addActionListener(new ActionListener(){//事件监听器(匿名类)
        public void actionPerformed(ActionEvent e){
            listModel.addElement(tf.getText());
        }
    });
    panel=new JPanel();
    panel.add(tf);
    panel.add(button);
    cp.add(panel,BorderLayout.SOUTH);
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    frame.pack();
    frame.setVisible(true);
}
```

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_294_0.png)

## 菜单组件

菜单组件的继承关系

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_295_0.png)

### 菜单栏(JMenuBar)

菜单栏是窗口中的主菜单，用来包容一组菜单。

JFrame、JApplet和JDialog等类中定义了 setJMenuBar(JMenuBar menu)方法，可以把菜单栏放到窗口的上方。

```
JFrame frame=new JFrame("Menu Demo");
JMenuBar mb=new JMenuBar();
frame.setJMenuBar(mb);
```

### 菜单(JMenu)

菜单是最基本的下拉菜单，用来包容一组菜单项或子菜单。

```
JMenu menu1=new JMenu("File");
JMenu menu2=new JMenu("Edit");
JMenu menu3=new JMenu("Source");
mb.add(menu1);
mb.add(menu2);
mb.add(menu3);
```

### 菜单项(JMenuItem)

如果将整个菜单系统看作是一棵树，那么菜单项就是这棵树的叶子，是菜单系统的最下一级。

菜单项构造方法：

- JMenuItem(Icon icon);
- JMenuItem(String text);
- JMenuItem(String text, Icon icon);
- JMenuItem(String text, int mnemonic);

```
JMenuItem mi1 = new JMenuItem("New", KeyEvent.VK_S);
JMenuItem mi2 = new JMenuItem("Open");
mi2.setMnemonic(KeyEvent.VK_O); // 设置快捷键
JMenuItem mi3 = new JMenuItem("Close", KeyEvent.VK_C);
menu1.add(mi1);
menu1.add(mi2);
menu1.add(mi3);
```

## 对话框、标准对话框与文件对话框

### 对话框(JDialog)

分为有模式和无模式。

JDialog构造方法：

- JDialog(Frame owner);
- JDialog(Frame owner, boolean modal);
- JDialog(Frame owner, String title);
- JDialog(Frame owner, String title, boolean modal);

### 标准对话框(JOptionPane)

- 确认对话框：显示问题，要求用户确认。
- 输入对话框：提示用户输入。
- 信息对话框：显示信息，告知用户发生了什么情况。
- 选项对话框：显示选项，要求用户选择。

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_301_0.png)

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_301_1.png)

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_301_2.png)

![](img/ca8bdf2cb3b7905fc97ee695aef3ed57_301_3.png)

### 文件对话框(JFileChooser)

构造方法：

- JFileChooser();
- JFileChooser(File currentDirectory);
- JFileChooser(String currentDirectoryPath);

刚刚创建的文件对话框是不可见的，可以调用以下方法显示：

- showOpenDialog(Component parent);
- showSaveDialog(Component parent);
- showDialog(Component parent, String approveButtonText);
