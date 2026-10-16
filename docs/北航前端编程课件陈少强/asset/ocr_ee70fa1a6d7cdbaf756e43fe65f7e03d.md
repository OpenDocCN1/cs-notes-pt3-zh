# 5.5.2 表单元素

jQuery Mobile允许使用HTML5中的新表单控件，例如滑块（input type="range"），并且自动将表单控件替换为对触摸更为友好的富控件（rich control）。默认情况下，每个表单控件独占一行。

# 1、文本标签

文本标签（label）附着在表单控件上。它不仅作为提示，也扩大了所附着控件的焦点的选择范围。就是说，表单元素的可点击范围为控件自身加上label标签。所以，应当尽量为所有控件加上文本标签。

例如：

```
<label for="company">Company Name:</label>
<input type="text" id="company">
```