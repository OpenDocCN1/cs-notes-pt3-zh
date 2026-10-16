# 4.4.5 排队效果

为了对不同组元素的动画效果进行排队，jQuery为每个动画方法提供了回调函数。作为参数的回调函数将在动画执行之后作为本次动画内容被调用。

```
//在例4-4-18.js中：
$('p').eq(2)
.css('border', '1px solid #333')
.click(function() {
    var $clickedItem = $(this);
    $clickedItem.next().slideDown('slow', function() {
        $clickedItem.slideUp('slow');
    });
});
$('p').eq(3).css('backgroundColor', '#ccc').hide();
```