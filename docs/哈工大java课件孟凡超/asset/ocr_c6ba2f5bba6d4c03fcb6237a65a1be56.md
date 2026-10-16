# 7.2 容器

✓将组件放入内容窗格方法2：

创建新的内容窗格取代顶层容器默认的内容窗格。

```
JPanel contentPane=new JPanel();
contentPane.setLayout(new BorderLayout());
contentPane.add(button, BorderLayout.CENTER);
frame.setContentPane(contentPane);
```