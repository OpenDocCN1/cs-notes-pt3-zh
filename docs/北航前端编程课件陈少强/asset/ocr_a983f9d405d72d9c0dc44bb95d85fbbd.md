# 5.3.1 工具栏

被选中的元素

每个导航栏都可以有一个被选中的元素，使用类名ui-btn-active标识。激活的元素会在当前主题的UI基础上高亮显示。

将一个导航栏作为Web应用的主导航时，最好将主页作为导航栏的第一个元素，并表示为已选中。例如：

```
<div data-role="footer" data-position="fixed">
<div data-role="navbar">
<ul>
<li><a href="#index" class="ui-btn-active">Home</a>
<li><a href="#contacts">Contacts</a>
<li><a href="#events">Events</a>
<li><a href="#news">News</a>
</ul>
</div>
</div>
```

![](bbox=[0.58, 0.72, 0.92, 0.82])

用户操作导航元素时，当前选中元素会自动切换为选中状态，不用自己更新ui-btn-active类。