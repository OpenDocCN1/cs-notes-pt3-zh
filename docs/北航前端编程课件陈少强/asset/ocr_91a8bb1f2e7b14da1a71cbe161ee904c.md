# 4.2.4 jQuery自定义选择符

jQuery自定义选择符的语法与CSS中的伪类选择符语法相同，即选择符以冒号（：）开头。它通常跟在一个CSS选择符后面，基于已经选择的元 素集的位置来查找元素。例如：
$("div.horizontal:eq(1)")
用来确定原选择集中的第二个元素（JavaScript中的编号从0开始）。
需要注意的是，由于CSS中的编号则是从1开始的，所以：
$("div:nth-child(1)")
获取的是作为其父元素的第一个子元素的 所有div元素，也可以写为：
$("div:first-child")。
下面介绍jQuery中的三个十分有用的自定义选择符:odd、:even和contains()。