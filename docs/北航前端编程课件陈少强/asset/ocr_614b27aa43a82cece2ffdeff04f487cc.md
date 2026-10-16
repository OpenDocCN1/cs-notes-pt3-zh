# 3.3.6 文档对象模型

上例中的debug()函数可以将调试信息附加在文档的后面。可用于下面的HTML文档：

```
<!-- 3-7.html -->
<body>
    <script>var numtimes=0;</script>
    <button onclick="debug('clicked: ' + numtimes++);">
    press me
    </button>
</body>
```

这个例子中示范了一个给文档添加内容的新方法。即：使用了<div>元素的innerHTML属性。把任何元素的innerHTML属性设置成一个HTML文本串，都会使那段HTML被解析为元素的内容。虽然这个属性不属于DOM API，但它非常简便，而且所有的浏览器都支持它。