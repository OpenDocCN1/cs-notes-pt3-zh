# 7.2 容器

# 内容窗格

每个顶层容器都有一个内容窗格(ContentPane)，顶层容器中除菜单之外的组件都放在这个内容窗格中。

# 将组件放入内容窗格方法1：

通过顶层容器的getContentPane()方法获取默认的内容窗格，然后将组件添加到内容窗格中。

```
Container contentPane=frame.getContentPane();
contentPane.add(button, BorderLayout.CENTER);
```

```
frame.getContentPane().add(button, BorderLayout.CENTER);
```