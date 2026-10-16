

## 3.3.4 表单和表单元素

### 3. 为表单元素书写脚本

#### （1）表单和表单元素的命名

每个表单元素都有name属性，如果要将表单提交给服务器程序，必须在相应的HTML标记中设置这一属性。

表单本身也有一个name属性，这个属性与表单的提交没有任何关系。它的存在是为了方便JavaScript程序设计者。

这样，就可以使用下面的表达式引用address表单中的zipcode元素：

```
document.address.zipcode
```

为了使表单中的一组Radio元素称为单选的，它们必须具有相同的name属性。对于不需要单选的Checkbox按钮，虽然不是必须的，但给它们定义相同的name属性也很常见。

当表单中的多个元素具有相同的name属性时，JavaScript就将这些元素存放在一个数组中，这个数组的名字就是name属性的值，数组元素的顺序就是它们在文档中出现的顺序。

#### （2）表单元素的属性

所有（或绝大多数）表单元素都具有下列性质：

- type：一个只读的字符串，参见前面表格的type列。
- form：只读属性，是对包含该元素的Form对象的引用。
- name：只读字符串属性，见前页。
- value：可读写字符串。与HTML表单元素的name属性对应。在提交表单时，它将作为name值变量的值发送到Web服务器。

#### （3）表单元素的事件处理程序

大多数表单元素都支持如下的事件处理程序：

- onclick: 在元素上点击鼠标时触发。
- onchange: 当用户改变了元素表示的值（输入文本且焦点改变，或选择了新的选项）时触发。
- onfocus: 元素收到输入焦点时触发。
- onblur: 元素失去输入焦点时触发。

表单元素还支持（几乎）所有HTML元素支持的各种事件处理程序（如 onmousedown）。

#### （4）按钮

Button按钮为用户触发脚本的动作提供了一种清晰可见的方法。它没有自己的默认行为，除非它具有onclick（或其它）事件处理程序，否则它在表单中没有任何用处。

需要注意的是，超链接提供了与按钮作用一样的onclick事件处理程序，任何按钮对象都可以用一个超链接对象替换，只要该链接在被点击时进行与按钮被点击时一样的操作。

Submit按钮和Reset按钮与Button按钮类似，只是它们有相关的默认动作，所以即使没有onclick事件处理程序，它们也有用。如果onclick事件处理程序返回false，这两种按钮的默认动作就不会被执行。可以使用Submit按钮的onclick事件处理程序执行表单验证，但使用Form对象自身的onsubmit事件处理程序进行表单验证更加常用。

可以用<button>标记代替<input>标记创建Button、Submit和Reset按钮。<button>标记更灵活一些，因为它不显示由value属性指定的纯文本，而是显示<button>和</button>之间的HTML内容（格式化的文本或图像），但它们的type属性具有相同的值。

#### （5）切换按钮

Radio元素和Checkbox元素都是切换按钮。一组Radio元素总是具有相同的name属性值，以便具有互斥功能；通常也将Checkbox元素进行分组，每组元素有相同的name属性值。这些同名元素被放在一个元素数组中，数组名即是name属性的值。

Radio元素和Checkbox元素都定义了布尔值属性checked。属性defaultChecked是只读的布尔值，指示装载页面时该元素是否被选中。

Radio元素和Checkbox元素自身不显示任何文本，而是显示相邻的HTML文本（可与一个<label>标记配合使用）。这意味着设置Radio元素和Checkbox元素的value属性不会改变它们的外观（像<button>元素一样），只能改变提交表单时发送给Web服务器的字符串。

用户点击切换按钮时，Radio元素或Checkbox元素将触发它的onclick事件处理程序，新的浏览器还会触发onchange事件处理程序。

#### （6）文本框

Text元素允许用户输入单行文本。它的可读写属性值value即表示其中的文本。当用户输入新文本或编辑已有文本，然后把焦点移开时，将触发onchange事件处理程序。

Textarea元素和Text元素相似，只是它允许输入多行文本。Textarea元素由<textarea>标记创建，而不是创建Text元素的<input>标记。可以像使用Text元素的value属性和onchange事件处理程序一样使用Textarea元素的这些属性。但其实两种元素的类之间没有继承关系。

Password元素是修改过的Text元素，在用户输入时它显示星号。注意：Password元素可以防止用户输入的密码被窥视，但当表单被提交时，其值并没有被加密（除非通过安全的HTTPS链接提交它），所以当它通过网络被提交时，便可能被看到。

File元素允许用户输入要上传到服务器的文件名。它实质上是一个与内置按钮组合在一起的Text元素，这个内置按钮可以弹出一个文件选择对话框。像Text元素一样，File元素也有onchange事件处理程序。但与Text元素不同的是，File元素的value值是只读的。

#### （7）Select元素和Option元素

Select元素表示用户可以选择的选项集合（由Option元素表示）。浏览器用下拉菜单或列表框表示Select元素（由size属性决定）。Select元素可以用两种完全不同的方式操作，其type属性值由其设置决定。如果<select>标记有multiple属性，就允许用户进行多选，其Select对象的type属性为“select-multiple”。否则，如果没有multiple属性，那么用户只能进行单元，其Select对象的type属性为“select-one”。

Select元素没有value属性，但Option元素有。

当用户选中或取消一个选项时，Select元素将触发它的onchange事件处理程序（Option元素没有事件处理程序）。对于“单选”型的Select元素，可读可写的属性selectedIndex用数字指示了当前被选中的选项。对于“多选”型的Select元素，要确定选中了哪些选项，必须遍历options[]数组中的所有元素，检查每个Option对象的selected属性的值。

除了selected属性外，Option元素还有text属性，用于读取或设置元素所呈现的文本。而value属性也是可读可写的字符串，通常表示的是表单提交时发送给Web服务器的值，也可以用来存储一个与text不同的值。

除了设置Option对象的text属性外，还有其它方法可以动态改变Select元素中显示的选项。可以通过把options.length设置为想要的数目来截取Option元素的数组（把options.length设置为0可以删除所有Option对象）；把options[]数组中的某个元素设置为null，就可以删除一个Option对象（其后的对象自动前移）。最后，利用构造函数Option()，可以动态创建新的Option元素，并把它附加在options[]数组的末尾给Select元素增加新的选项。例如：

```
var zaire = new Option("Zaire", // text 属性
"zaire", // value 属性
false, // defaultSelected 属性
false); // selected 属性
var countries = document.address.country; // 获取Select对象
countries.options[countries.options.length] = zaire;
```

可以用<optgroup>标记对Option元素进行分组(缩格)。<optgroup>标记具有label属性，是其呈现的文本。<optgroup>标记可见但不可选，也不会出现在Select元素的options[]数组中。

#### （8）Hidden元素

Hidden元素在表单中不可见。它的作用是在提交表单时把任意的文本发送给服务器。由于Hidden元素没有可视化的外观，所以它不能生成事件，没有事件处理程序。value属性允许你读写与Hidden元素相关的文本，它将被传送到服务器端处理程序。

## 3.3.5 文档对象模型

文档对象模型（Document Object Model，DOM）是表示文档、访问和操作构成文档的各种元素的应用程序接口（API）。

本章讨论W3C DOM，它是由World Wide Web委员会定义的标准文档对象模型，简称DOM。DOM标准是传统Web浏览器DOM（0级DOM）的全特性超集。

