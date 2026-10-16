
## JMenuItem

- JMenuItem继承AbstractButton类，因此JMenuItem也可以理解为一种特殊的JButton组件，当选择某个菜单项时也会触发ActionEvent事件

## JMenuItem类的常用方法

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public JMenuItem(Icon icon) | 构造 | 创建带有图标的JMenuItem |
| 2 | public JMenuItem(String text) | 构造 | 创建带有指定文本的JMenuItem |
| 3 | public JMenuItem(String text,Icon icon) | 构造 | 创建带有指定文本和图标的JMenuItem |
| 4 | public JMenuItem(String text, int mnemonic) | 构造 | 创建带有指定文本的JMenuItem，并指定助记符 |
| 5 | public void setMnemonic(int mnemonic) | 普通 | 指定菜单项的助记符 |
| 6 | public void setAccelerator(KeyStroke keyStroke) | 普通 | 设置快捷键的组合键 |

## 构建菜单项

```
public class JMenuDemo02 {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Welcome To MLDN");                 // 定义窗体
        JTextArea text = new JTextArea();                               // 定义文本域
        text.setEditable(true);                                         // 在文本域中加入文本框及滚动条
        frame.getContentPane().add(new JScrollPane(text));              // 在面板中加入文本框及滚动条
        JMenu menuFile = new JMenu("文件");                            // 定义JMenu组件
        menuFile.setIcon(new ImageIcon("d:" + File.separator + "icons"+ File.separator + "file.gif")); // 定义显示图标
        JMenuBar menuBar = new JMenuBar();                              // 定义JMenuBar
        JMenuItem newItem = new JMenuItem("新建",
                new ImageIcon("d:" + File.separator + "icons" + File.separator + "new.gif"));     // 创建MenuItem
        JMenuItem openItem = new JMenuItem("打开",
                new ImageIcon("d:" + File.separator + "icons" + File.separator + "open.gif"));    // 创建MenuItem
        JMenuItem closeItem = new JMenuItem("关闭",
                new ImageIcon("d:" + File.separator + "icons" + File.separator + "close.gif"));   // 创建MenuItem
        JMenuItem exitItem = new JMenuItem("退出",
                new ImageIcon("d:" + File.separator + "icons" + File.separator + "exit.gif"));    // 创建MenuItem
        newItem.setMnemonic('N');                                       // 设置快捷键N
        openItem.setMnemonic('O');                                      // 设置快捷键O
        closeItem.setMnemonic('C');                                     // 设置快捷键C
        exitItem.setMnemonic('E');                                      // 设置快捷键E
        newItem.setAccelerator(KeyStroke.getKeyStroke('N',java.awt.Event.CTRL_MASK));      // Ctrl + N
        openItem.setAccelerator(KeyStroke.getKeyStroke('O',java.awt.Event.CTRL_MASK));     // Ctrl + O
        closeItem.setAccelerator(KeyStroke.getKeyStroke('C',java.awt.Event.ALT_MASK));     // Alt + C
        exitItem.setAccelerator(KeyStroke.getKeyStroke('E', java.awt.Event.ALT_MASK));     // Alt + E
        menuFile.add(newItem);                                          // 加入菜单项
        menuFile.add(openItem);                                         // 加入菜单项
        menuFile.add(closeItem);                                        // 加入菜单项
        menuFile.addSeparator();                                        // 加入分隔线
        menuFile.add(exitItem);                                         // 加入菜单项
        menuBar.add(menuFile);                                          // 加入JMenu
    }
}
```

## 事件处理

```
newItem.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e){
        text.append("=== 选择了“新建”菜单项\n");
    }});
    // 为菜单项加入事件监听
openItem.addActionListener(new ActionListener(){
    public void actionPerformed(ActionEvent e){
        text.append("=== 选择了“打开”菜单项\n");
    }});
    // 为菜单项加入事件监听
closeItem.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e){
        text.append("=== 选择了“关闭”菜单项\n");
    }});
    // 为菜单项加入事件监听
exitItem.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e){
        text.append("=== 选择了“退出”菜单项\n");
    }});
    // 为菜单项加入事件监听
```

## 数组与方法
—— 数组定义及使用

## 目标

- □ 掌握数组的作用
- □ 掌握数组的声明及内存分配
- □ 通过数组的简单范例加深数组操作的理解
- □ 掌握多维数组的定义及使用
