# 5.3.1 工具栏

添加logo

使用图片或logo代替文本是很常见的。在带有标准左右按钮的页头中显示图片，最好的方式是在对应的h1中使用img标记，例如：

```
<div data-role="header">
<a href="cancel" data-icon="delete">Cancel</a>
<h1><img src="images/logo.png"></h1>
<a href="save" data-icon="check" data-theme="b">Save</a>
</div>
```

页头会自动适应图片的高度，但不要使用高度超过125像素的图片。

![](bbox=[0.3, 0.68, 0.68, 0.78])