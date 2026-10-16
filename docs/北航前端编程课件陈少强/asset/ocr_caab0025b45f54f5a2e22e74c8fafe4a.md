# 5.3.3 按钮

2、分组按钮

jQuery Mobile提供了分组控件技术。借助它可以将一组彼此相关的按钮组合起来。

控件组是一个容器，通常是一个带有data-role="controlgroup"的div元素。其中的按钮不需要声明为内联。

分组按钮在垂直方向彼此相连，但并没有选中状态。例如：

```
<div data-role="controlgroup">
<a href="#" data-role="button">Button 1</a>
<a href="#" data-role="button">Button 2</a>
<a href="#" data-role="button">Button 2</a>
</div>
```

![](bbox=[0.25, 0.7, 0.7, 0.88])

也可以通过在控件组上使用data-type="horizontal"属性来创建水平布局的分组控件。