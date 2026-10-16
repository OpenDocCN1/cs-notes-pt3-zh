# 5.6.2 配置

2、页面配置

页面由data-role="page"定义。缺省情况下，页面使用默认属性。如果想改变默认属性，可以在页面中使用data-*属性来设置。

这里所说的是改变所有页面使用的默认属性。这要通过页面原型的 options对象来改变。例如下例为页面增加了后退按钮并设置了默认主题。

```
$(document).bind('mobileinit', function() {
    $.mobile.page.prototype.options.addBackBtn = true;
    $.mobile.page.prototype.options.backBtnTheme = "e";
    $.mobile.page.prototype.options.headerTheme = "b";
    $.mobile.page.prototype.options.footerTheme = "d";
});
```