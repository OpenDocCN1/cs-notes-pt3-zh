# 3.3.3 Document对象

6、链接

Document对象的links[]数组中存放着文档中的超文本链接的Link对象。HTML中的带href属性的<a>标记和影像地图map中的<area>标记都可以创建超链接。

Link对象代表超文本链接的URL，它拥有Location对象的所有属性。通过重新设置这些属性，可以对超链接进行重定向。

Link对象支持大量有趣的事件处理程序，如： onclick、onmouseover 和onmouseout。

7、锚（书签）

Document对象的数组anchors[]包含了代表HTML中已命名位置的Anchor对象，这些位置由标记<a>和它的name属性标识。

Anchor对象是一种比较简单的对象，它所定义的唯一标准属性是name，即标记<a>的属性name的值。