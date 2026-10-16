
## 使用ListModel构造JList

在JList的构造方法中有一个使用ListModel构造JList对象的操作，ListModel是一个专门用于创建JList列表内容操作的接口。

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | void addListDataListener(ListDataListener l) | 普通 | 加入数据改变事件的监听 |
| 2 | void removeListDataListener(ListDataListener l) | 普通 | 加入数据删除时的监听 |
| 3 | Object getElementAt(int index) | 普通 | 返回指定索引处的内容 |
| 4 | int getSize() | 普通 | 返回列表长度 |

## 利用ListModel创建JList

```
import javax.swing.ListSelectionModel;
class MyListModel extends AbstractListModel{
private String nations[] = { "中国", "巴西", "美国", "韩国", "意大利", "法国" };
public Object getElementAt(int ind) {
if (ind < this.nations.length) {
return this.nations[ind];
} else {
return null;
}
}
public int getSize() {
return this.nations.length;
}
}
class MyList {
private JFrame frame = new JFrame("Welcome To MLDN") ;
private Container cont = frame.getContentPane() ;
private JList list1 = null ;
public MyList() {
this.list1 = new JList(new MyListModel()) ;
list1.setBorder(BorderFactory.createTitledBorder("你喜欢去那个国家旅游？")) ;
list1.setSelectionMode(ListSelectionModel.MULTIPLE_INTERVAL_SELECTION) ;
}
}

// 定义列表内容
// 定义窗体
// 得到窗体容器
// 定义列表框
// 实例化JList
// 定义一个列表框的边框显示条
// 第一个列表框每次可以选择多个选项
// 设置选择模式
```

![](img/b706331eacf49a62651c2c9b2de81ca5_811_0.png)

## JList事件处理

在JList中可以使用ListSelectionListener的监听接口实现对JList中所选项进行监听，此接口定义了如下的方法。

| No. | 方法 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | void valueChanged(ListSelectionEvent e) | 普通 | 当值发生变化时调用 |

此方法会产生ListSelectionEvent事件，此事件中的常用方法如下所示。

| No. | 方法 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | public int getFirstIndex() | 普通 | 返回选择的第一个选项的索引值 |
| 2 | public int getLastIndex() | 普通 | 返回选择的最后一个选项的索引值 |

## 对JList进行监听

```
class MyListModel extends AbstractListModel{
    private String nations[] = { "中国", "巴西", "美国", "韩国", "意大利", "法国" };
    public Object getElementAt(int ind) {
        if (ind < this.nations.length) {
            return this.nations[ind];
        } else {
            return null;
        }
    }
    public int getSize() {
        return this.nations.length;
    }
}
class MyList implements ListSelectionListener{
    private JFrame frame = new JFrame("Welcome To MLDN");
    private Container cont = frame.getContentPane();
    private JList list1 = null;
    public MyList() {
        this.list1 = new JList(new MyListModel());
        list1.setBorder(BorderFactory.createTitledBorder("你喜欢去那个国家旅游？"));
        list1.addListSelectionListener(this);
        cont.add(new JScrollPane(this.list1));
        ...
    }
    public void valueChanged(ListSelectionEvent e) {
        int temp[] = list1.getSelectedIndices();
        System.out.print("选定的内容：");
        for (int i = 0; i < temp.length; i++) {
            System.out.print(list1.getModel().getElementAt(i) + ", ");
        }
        System.out.println();
    }
}
```

![](img/b706331eacf49a62651c2c9b2de81ca5_813_0.png)

图形界面
—— 菜单组件

## 本章目标

- □ 了解菜单组件的使用
- □ 了解JMenu、JMenuBar、JMenuItem类的使用

## JMenu与JMenuBar

- 若在Java中实现菜单，则可以使用JMenu组件，当然，如果要使用JMenu则首先要了解JMenuBar组件，JMenuBar组件的功能是用来摆放JMenu组件，当建立完许多的JMenu组件之后，需要通过JMenuBar组件来将JMenu组件加入到窗口中

![](img/b706331eacf49a62651c2c9b2de81ca5_816_0.png)

## JMenuBar的常用方法

| No. | 方法 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | public JMenuBar() | 构造 | 创建新的JMenuBar对象 |
| 2 | public JMenu add(JMenu c) | 普通 | 将指定的JMenu加入到JMenuBar之中 |
| 3 | public JMenu getMenu(int index) | 普通 | 返回指定位置的菜单 |
| 4 | public int getMenuCount() | 普通 | 返回菜单栏上的菜单数 |

## JMenu的常用方法

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public JMenu(String s) | 构造 | 创建新的JMenu，并指定菜单名称 |
| 2 | public JMenuItem add(JMenuItem menuItem) | 普通 | 增加新的菜单项 |
| 3 | public void addSeparator() | 普通 | 加入分隔线 |

## 使用JMenu和JMenuBar构建简单的菜单

```
public class JMenuDemo01 {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Welcome To MLDN");                // 定义窗体
        JTextArea text = new JTextArea();                             // 定义文本域
        text.setEditable(true);                                       // 定义文本组件可编辑
        frame.getContentPane().add(new JScrollPane(text));            // 在面板中加入文本框及滚动条
        JMenu menuFile = new JMenu("文件");                          // 定义JMenu组件
        menuFile.setIcon(new ImageIcon("d:" + File.separator + "icons" + File.separator + "file.gif")); // 定义显示图标
        JMenuBar menuBar = new JMenuBar();                            // 定义JMenuBar
        menuBar.add(menuFile);                                        // 加入JMenu
        frame.addWindowListener(new WindowAdapter() {                 // 加入事件监听
            public void windowClosing(WindowEvent arg0) {             // 覆盖窗口关闭方法
                System.exit(1);                                       // 系统退出
            }
        });
        frame.setJMenuBar(menuBar);                                   // 在窗体中加入JMenuBar组件
        frame.setVisible(true);                                       // 显示组件
        frame.setSize(300, 100);                                      // 定义窗体大小
        frame.setLocation(300, 200);                                  // 设置显示位置
    }
}
```
