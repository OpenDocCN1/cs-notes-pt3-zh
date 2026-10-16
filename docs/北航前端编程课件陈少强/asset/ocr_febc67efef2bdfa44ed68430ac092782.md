# 4.2.5 jQuery中用于遍历DOM的方法

# 1. filter()方法的作用

该方法可以完成简单选择符表达式的功能，例如：

```
$('tr').filter(':even').addClass('alt');
```

可以用来代替：$('tr:even').addClass('alt');

而且由于该方法可以接受函数作参数，执行复杂的测试，因此功能十分强大。下面的代码为所有外部链接添加类名：external。

```
/* 添加在4-2-1.css中 */
a.external {
    background: #fff url(external.png) no-repeat 100% 2px;
    padding-right: 16px;
}
```

```
/* 添加在4-2-1.js中 */
$('a').filter(function() {
    return this.hostname && this.hostname != location.hostname;
}).addClass('external');
```

注：更准确地说，.filter()方法会迭代所有匹配的元素，对每个元素(this)都调用的函数并测试返回值，如果函数返回false，则从匹配集合中删除相应元素；如果返回true，则保留相应元素。