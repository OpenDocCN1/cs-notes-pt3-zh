# 4.4.5 排队效果

把非动画方法添加到队列中的一种方式，就是使用.queue()方法。

```
//在例4-4-16.js中：
$('div.label').click(function() {
    var paraWidth = $('div.speech p').outerWidth();
    var $switcher = $(this).parent();
    ...
    .fadeTo('slow', 1.0)
    .slideUp('slow')
    .queue(function(next) {
        $switcher.css({backgroundColor: '#f00'});
        next();
    })
    .slideDown('slow');
});
```

在这里，.queue()方法把一个回调函数添加到元素的效果队列中。

回调函数有一个函数参数，它用于将效果连接起来，否则动画将中断。