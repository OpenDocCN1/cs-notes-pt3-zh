
## 4.1.3 第一个jQuery驱动的页面

## 6.开发工具

推荐适用firefox浏览器及其firebug工具

## 4.2 选择元素

这里所说的元素即DOM元素。jQuery不仅利用了CSS选择元素的方式，而且还自定义了它独有的选择符。

### 4.2.1 DOM

文档对象模型是JavaScript和网页之间的接口，它以对象网络(树)而非文本的形式来表现HTML的源代码。例如：

### DOM一个例

```html
<html>
  <head>
    <title>the title</title>
  </head>
  <body>
    <div>
      <p>This is a paragraph.</p>
      <p>This is another paragraph.</p>
      <p>This is yet another paragraph.</p>
    </div>
  </body>
</html>
```

![](img/e6e6db66e3939a2cb9a18b01dd5c3fae_171_0.png)

### 4.2.2 选择函数$()

在jQuery中，所有选择由$()函数完成。它的参数通常是CSS选择符，返回结果是一个jQuery对象（一个集合对象）。需要说明的是，$是JavaScript的合法标识符，而且很多类似jQuery的JavaScript库都使用了这个标识符。当同时使用多个JavaScript函数库时，是会引起冲突的。

其实在jQuery中，$标识符不过是就jQuery的“别名”。在引起冲突的情况下，需要在自定义的jQuery文件中，将$标识符全部替换为jQuery。

### 4.2.3 CSS选择符

jQuery支持几乎所有CSS选择符。有三种基本的CSS选择符：标签名、ID和类。它们可以单独使用，也可以与其它选择符组合使用。

| 选择符 | CSS | jQuery | 说明 |
|---|---|---|---|
| 基本的选择符 |  |  |  |
| 标签名 | p{} | $('p') | 取得文档中的所有段落 |
| ID | #some-id{} | $('#some-id') | 取得文档中ID为some-id的一个元素 |
| 类 | .some-class{} | $('.some-class') | 取得文档中类为some-class的所有元素 |

jQuery支持从CSS1到CSS3的几乎所有选择符，只要启用JavaScript，你不必关心浏览器支持什么版本。

通过在jQuery中使用CSS选择符，4-2-1.html利用一个无序列表实现了一个常用的导航菜单。

### 4.2.3 CSS选择符

4-2-1.html: 一个无序列表

# Selected Shakespeare Plays

- Comedies
  - *As You Like It*
  - All's Well That Ends Well
  - A Midsummer Night's Dream
  - Twelfth Night
- Tragedies
  - *Hamlet*
  - Macbeth
  - Romeo and Juliet
- Histories
  - Henry IV (email)
    - Part I
    - Part II
  - *Henry V*
  - Richard II

### 4.2.3 CSS选择符

- 1. 基于列表项的级别添加样式
  1）使顶级项水平排列。
  2）为非顶级项添加样式

```
/* 4-2-1.css */
.horizontal {
    float: left;
    list-style: none;
    margin: 10px;
}
.sub-level {
    background: #ccc;
}
```

```
/* 4-2-1.js */
$(document).ready(function() {
    $('#selected-plays > li').addClass('horizontal');
    $('#selected-plays li:not(.horizontal)').addClass('sub-level');
});
```

**注：** 这里使用了新的否定式伪类选择符 **:not(.horizontal)**

### 4.2.3 CSS选择符

## 2. 属性选择符

属性选择符是CSS选择符中特别有用的一类选择符，HTML标记的属性放在方括号[]中，用于选择具有该属性的标记（元素）。

在属性选择符中可以使用通配符：

- ^ : 值在字符串的开始
- $ : 值在字符串的结尾
- * : 值可以在字符串的任意位置
- ! : 对值取反

下面将为4-2-1.html中的链接添加样式。

```
/* 4-2-1.css */
a { color: #00c;}
a.mailto {
    background: url(email.png) no-repeat 100% 2px;
    padding-right: 18px;}
a.pdflink {
    background: url(pdf.png) no-repeat 100% 0;
    padding-right: 18px;}
a.henrylink {
    background-color: #fff;
    padding: 2px;
    border: 1px solid #000;}
/* 4-2-1.js */
$(document).ready(function() {
    $("a[href^=\"mailto:\"]").addClass('mailto');
    $("a[href$=\".pdf\"]").addClass('pdflink');
    $("a[href^=\"http\"][href*=\"henry\"]").addClass('henrylink');
});
```

注：这里使用了组合的属性选择符，它们是“与”的关系。

### 4.2.4 jQuery自定义选择符

jQuery自定义选择符的语法与CSS中的伪类选择符语法相同，即选择符以冒号（：）开头。它通常跟在一个CSS选择符后面，基于已经选择的元 素集的位置来查找元素。例如：
$("div.horizontal:eq(1)")
用来确定原选择集中的第二个元素（JavaScript中的编号从0开始）。
需要注意的是，由于CSS中的编号则是从1开始的，所以：
$("div:nth-child(1)")
获取的是作为其父元素的第一个子元素的 所有div元素，也可以写为：
$("div:first-child")。
下面介绍jQuery中的三个十分有用的自定义选择符:odd、:even和contains()。

### 4.2.4 jQuery自定义选择符

4-2-2.html: 两个表格

# Shakespeare's Plays

As You Like It        Comedy
All's Well that Ends Well  Comedy 1601
Hamlet                  Tragedy 1604
Macbeth                 Tragedy 1606
Romeo and Juliet        Tragedy 1595
Henry IV, Part I        History 1596
Henry V                 History 1599

# Shakespeare's Sonnets

The Fair Youth  1-126
The Dark Lady  127-152
The Rival Poet 78-86

```
/* 4-2-2.css */
.alt {
    background-color: #ccc;
}
/* 4-2-2.js */
$(document).ready(function() {
    //$('tr:even').addClass('alt');
    $('tr:nth-child(odd)').addClass('alt');
    $('td:contains(Henry)').addClass('highlight');
});
```

**注意：**

- ① 这里使用的 **:nth-child()** 是 jQuery 中唯一从 1 开始计数的选择符。它的参数可以是数值、**odd** 或 **even**。
- ② **contains()** 选择符区分大小写。
