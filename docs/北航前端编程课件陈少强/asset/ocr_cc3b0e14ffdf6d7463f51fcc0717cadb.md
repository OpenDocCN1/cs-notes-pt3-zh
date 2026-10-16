# 5.2.2 文档结构

jQuery Mobile的文档结构主要由页面(page)构成。一个页面仅仅是一个带有data-role="page"属性的div元素。一个HTML文档可以包含多个页面。

使用简单的HTML标记（例如超链接标记a），可以连接到同一个HTML文档中的另一个页面，也可以连接到外部HTML文档中的页面。

# 1、 data-role属性

jQuery Mobile使用标准的HTML标记，如div标记。只要给这些标记增加data-role属性，就可以使其具有不同的作用。例如<div data-role="page">

HTML5有一个自定义数据属性的特性，可以用来在标记上添加任何形如data-*的属性。data-role只不过是jQuery Mobile使用该特性添加的一个自定义数据属性。jQuery Mobile中大量使用这种特性。