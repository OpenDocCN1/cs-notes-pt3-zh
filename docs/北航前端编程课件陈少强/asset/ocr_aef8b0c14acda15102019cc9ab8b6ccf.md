# 4.4.4 创建自定义动画

//例4-4-11.js同时实现了文本尺寸盒的移动、增加高度和边框宽度：

```
$('div.label').click(function() {
    var paraWidth = $('div.speech p').outerWidth();
    var $switcher = $(this).parent();
    var switcherWidth = $switcher.outerWidth();
    $switcher.css({
        position: 'relative'
    }).animate({
        borderWidth: '5px',
        left: paraWidth - switcherWidth,
        height: '+=20px'
    },
    'slow');
});
```

其中

.outerWidth()方法用来计算元素的外宽度。

height: '+=20px'用来增加元素的CSS高度。

![](bbox=[0.55, 0.62, 0.95, 0.82])