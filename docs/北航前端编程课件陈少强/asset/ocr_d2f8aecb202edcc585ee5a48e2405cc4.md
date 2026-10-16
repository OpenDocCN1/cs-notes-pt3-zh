# 4.3.5 改变事件的传播过程

2、停止事件传播

事件对象提供了一个.stopPropagation()方法，可以阻止事件冒泡。这样就可以不使用event.target == this，仍然得到正确的结果。

```
/* 在4-3-6.css中 */
$(document).ready(function() {
    $('#switcher').click(function(event) {
        $('#switcher button').toggleClass('hidden');
    });});
$(document).ready(function() {
    $('#switcher-default').addClass('selected');
    $('#switcher button').click(function(event) {
        var bodyClass = this.id.split('-')[1];
        $('body').removeClass().addClass(bodyClass);
        $('#switcher button').removeClass('selected');
        $(this).addClass('selected');
        event.stopPropagation();
    });});
```