# 4.3.3 复合事件

```
/* 在4-3-4.js中 */
$(document).ready(function() {
  $('#switcher h3').toggle(
    function() {$('#switcher button').addClass('hidden');},
    function() {$('#switcher button').removeClass('hidden');}
  );
});
```

在本例这种特殊的情况下，可以使用.toggleClass()方法。例如：

```
$(document).ready(function() {
  $('#switcher h3').click(function() {
    $('#switcher button').toggleClass('hidden');
  });
});
```

该方法在自动检查该类是否存在，从而决定是为元素应用还是移除该类名。