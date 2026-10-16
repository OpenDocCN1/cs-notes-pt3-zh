# 4.4.5 排队效果

```
$switcher
.css({position: 'relative'})
.fadeTo('fast', 0.5)
.animate({
    left: paraWidth - switcherWidth
}, {
    duration: 'slow',
    queue: false
})
.fadeTo('slow', 1.0)
.slideUp('slow')
.slideDown('slow');
});
```

本例中，.animate()的第二个参数包含了queue选项，把该选项设置为false可将当前动画与前一个动画同时开始，而不是顺序开始。由于两个动画的速度不同，这是.animate()的第一种形式所做不到的。