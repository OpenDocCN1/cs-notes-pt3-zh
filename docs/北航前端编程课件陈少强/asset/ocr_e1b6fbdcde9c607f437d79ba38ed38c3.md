# 4.3.1 $(document).ready()说明

```
<script src="prototype.js"></script>
<script src="jquery.js"></script>
<script> jQuery.noConflict(); </script>
<script src="myscript.js"></script>
```

上面的带代码将对$的控制权交给了prototype.js库。这时，在自己的脚本(myscript.js)中，可以使用两个库。当然，在使用jQuery方法时，需要用jQuery代替$。

在这种情况下，仍然有一种在.ready()方法中使用$的技巧。在传递给ready的回调函数中可以接收一个参数——jQuery对象本身。利用这个参数，可以重新命名jQuery为$，而不必担心冲突：

```
jQuery(document).ready(function($) {
    // 在这里，可以正常使用$
});
```

或者简写为：

```
jQuery(function($) {
// Code that uses $.
});
```