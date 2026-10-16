# 3.3.6 文档对象模型

# （3）节点属性的命名规则

属性名应该以小写字母开头。如果属性名由多个单词构成，第二个单词开始的每个单词的首字母都要大写。因此，`<input>`标记的 `maxlength` 属性将命名为 `maxLength`。

当HTML属性名与JavaScript关键字发生冲突时，应该在属性名前加前缀“html”。因此，`<label>`标记的for属性被命名htmlFor。这个规则的一个例外是class属性，它被命名为className属性。

> 记住：**JavaScript的所有事件处理程序属性都必须小写。**