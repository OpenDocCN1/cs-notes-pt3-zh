# 5.3.3 按钮

# 1、内联按钮

内联按钮不会占满整个屏幕宽度，可以在元素上使用属性 `data-inline="true"` 来实现。例如：

```
```html
<a href="" data-role="button" data-inline="true">Button 1</a>
<a href="" data-role="button" data-inline="true">Button 2</a>
<a href="" data-role="button" data-inline="true">Button 2</a>
```
```

![](bbox=[0.216, 0.5, 0.748, 0.847])

如果想要内联按钮占满整个屏幕宽度，可以使用前面介绍的布局网格，每列包含一个按钮。