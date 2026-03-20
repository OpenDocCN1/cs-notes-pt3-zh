# 007：JavaScript

![](img/f48bce20dd4d907f3ab6977220476d3e_1.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_3.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_5.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_6.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_8.png)

## 概述

![](img/f48bce20dd4d907f3ab6977220476d3e_10.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_11.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_13.png)

在本节课中，我们将要学习JavaScript，这是一种在用户浏览器中运行的客户端编程语言。我们将了解JavaScript如何使网页变得动态和交互，包括如何操作网页内容、响应用户事件以及如何与外部API进行通信。

![](img/f48bce20dd4d907f3ab6977220476d3e_15.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_17.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_19.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_21.png)

## 客户端与服务器端编程

![](img/f48bce20dd4d907f3ab6977220476d3e_23.png)

上一节我们介绍了服务器端编程，使用Python和Django处理请求并生成响应。本节中我们来看看客户端编程。

![](img/f48bce20dd4d907f3ab6977220476d3e_25.png)

互联网通信通常涉及用户（客户端）通过浏览器向Web服务器发送HTTP请求，服务器处理请求后返回响应。到目前为止，我们编写的所有代码（例如运行在Django应用中的Python代码）都是在服务器上运行的代码。

![](img/f48bce20dd4d907f3ab6977220476d3e_27.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_29.png)

JavaScript使我们能够开始编写客户端代码，即在用户浏览器内部运行的代码。这非常有用，原因如下：
*   如果有些计算不需要联系服务器，直接在客户端执行可以更快。
*   我们可以使网页更具交互性。
*   JavaScript使我们能够直接操作DOM（文档对象模型），即代表用户正在查看的网页的树状层次结构。

![](img/f48bce20dd4d907f3ab6977220476d3e_31.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_33.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_35.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_37.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_39.png)

## 在网页中添加JavaScript

![](img/f48bce20dd4d907f3ab6977220476d3e_41.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_43.png)

为了向网页添加编程逻辑，我们使用`<script>`标签。浏览器会将其中的内容解释为JavaScript代码并执行。

![](img/f48bce20dd4d907f3ab6977220476d3e_45.png)

我们的第一个程序可能如下所示：
```html
<script>
    alert('Hello, world!');
</script>
```
这里，`alert`是一个函数，用于向用户显示一个警告框。`'Hello, world!'`是传递给该函数的字符串参数。

![](img/f48bce20dd4d907f3ab6977220476d3e_47.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_49.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_50.png)

让我们来尝试一下。创建一个名为`hello.html`的文件：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Hello</title>
        <script>
            alert('Hello, world!');
        </script>
    </head>
    <body>
        Hello
    </body>
</html>
```
在浏览器中打开此文件，页面顶部会显示一个包含“Hello, world!”的警告框。

---

![](img/f48bce20dd4d907f3ab6977220476d3e_52.png)

## 事件驱动编程

![](img/f48bce20dd4d907f3ab6977220476d3e_54.png)

JavaScript的强大之处在于事件驱动编程。我们可以将网页上发生的事情（如用户点击按钮、选择下拉菜单、提交表单等）视为“事件”。

![](img/f48bce20dd4d907f3ab6977220476d3e_56.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_57.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_59.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_61.png)

我们可以使用JavaScript添加“事件监听器”或“事件处理器”，指定当特定事件发生时应运行哪段代码。

![](img/f48bce20dd4d907f3ab6977220476d3e_63.png)

让我们修改`hello.html`，使其在点击按钮时显示警告：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Hello</title>
        <script>
            function hello() {
                alert('Hello, world!');
            }
        </script>
    </head>
    <body>
        <button onclick="hello()">Click here</button>
    </body>
</html>
```
我们定义了一个名为`hello`的函数。在按钮的`onclick`属性中，我们调用这个函数。现在，点击按钮会触发警告框。

![](img/f48bce20dd4d907f3ab6977220476d3e_65.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_67.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_69.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_71.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_73.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_75.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_77.png)

## 变量与操作DOM

![](img/f48bce20dd4d907f3ab6977220476d3e_79.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_81.png)

JavaScript支持变量、条件语句等编程特性。更重要的是，它允许我们操作DOM，动态更新网页内容。

让我们创建一个计数器应用。首先，创建一个`counter.html`文件：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Counter</title>
        <script>
            let counter = 0;

            function count() {
                counter++;
                document.querySelector('h1').innerHTML = counter;
            }
        </script>
    </head>
    <body>
        <h1>0</h1>
        <button onclick="count()">Count</button>
    </body>
</html>
```
*   `let counter = 0;` 定义了一个变量。
*   `counter++;` 将计数器加1。
*   `document.querySelector('h1')` 选择页面上的第一个`<h1>`元素。
*   `.innerHTML = counter;` 将该元素的内容更新为计数器的值。

![](img/f48bce20dd4d907f3ab6977220476d3e_83.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_85.png)

现在，每次点击按钮，标题中的数字都会增加。

![](img/f48bce20dd4d907f3ab6977220476d3e_87.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_89.png)

## 改进代码结构

![](img/f48bce20dd4d907f3ab6977220476d3e_91.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_93.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_95.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_97.png)

随着程序变得复杂，最好将JavaScript代码与HTML结构分离，并确保代码在DOM加载完成后执行。

![](img/f48bce20dd4d907f3ab6977220476d3e_99.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_100.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_102.png)

我们可以将JavaScript移入单独的文件，并使用`DOMContentLoaded`事件监听器。

![](img/f48bce20dd4d907f3ab6977220476d3e_104.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_106.png)

创建`counter.js`：
```javascript
document.addEventListener('DOMContentLoaded', function() {
    let counter = 0;
    const h1 = document.querySelector('h1');

    document.querySelector('button').onclick = function() {
        counter++;
        h1.innerHTML = counter;
    };
});
```
在`counter.html`中引用它：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Counter</title>
        <script src="counter.js"></script>
    </head>
    <body>
        <h1>0</h1>
        <button>Count</button>
    </body>
</html>
```
这种分离使代码更清晰、更易于维护。

![](img/f48bce20dd4d907f3ab6977220476d3e_108.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_110.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_112.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_113.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_115.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_117.png)

## 响应用户输入

![](img/f48bce20dd4d907f3ab6977220476d3e_119.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_121.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_123.png)

我们可以创建表单，并响应用户的提交操作。例如，创建一个问候页面：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Greet</title>
        <script>
            document.addEventListener('DOMContentLoaded', function() {
                document.querySelector('form').onsubmit = function() {
                    const name = document.querySelector('#name').value;
                    alert(`Hello, ${name}!`);
                    return false; // 阻止表单实际提交
                };
            });
        </script>
    </head>
    <body>
        <h1>Greet</h1>
        <form>
            <input id="name" placeholder="Name" type="text">
            <input type="submit">
        </form>
    </body>
</html>
```
*   `document.querySelector('#name').value` 获取ID为`name`的输入框的值。
*   使用模板字符串（反引号 `` ` `` 和 `${}`）将变量嵌入字符串。

![](img/f48bce20dd4d907f3ab6977220476d3e_125.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_127.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_129.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_131.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_133.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_135.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_137.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_139.png)

## 操作CSS样式

![](img/f48bce20dd4d907f3ab6977220476d3e_141.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_142.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_143.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_145.png)

JavaScript也可以动态改变元素的样式。例如，创建一个可以改变标题颜色的页面：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Colors</title>
        <script>
            document.addEventListener('DOMContentLoaded', function() {
                // 为所有按钮添加点击事件
                document.querySelectorAll('button').forEach(function(button) {
                    button.onclick = function() {
                        document.querySelector('#hello').style.color = button.dataset.color;
                    };
                });
            });
        </script>
    </head>
    <body>
        <h1 id="hello">Hello</h1>
        <button data-color="red">Red</button>
        <button data-color="blue">Blue</button>
        <button data-color="green">Green</button>
    </body>
</html>
```
*   `document.querySelectorAll('button')` 选择所有按钮。
*   `.forEach(...)` 为每个按钮执行函数。
*   `button.dataset.color` 访问HTML元素上自定义的`data-color`属性。
*   `.style.color` 修改元素的CSS颜色属性。

![](img/f48bce20dd4d907f3ab6977220476d3e_147.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_149.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_151.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_153.png)

## 使用本地存储

![](img/f48bce20dd4d907f3ab6977220476d3e_155.png)

`localStorage`允许我们在用户的浏览器中存储数据，即使页面刷新或关闭后数据依然存在。

![](img/f48bce20dd4d907f3ab6977220476d3e_157.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_159.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_161.png)

让我们改进计数器，使其记住上次的计数值：
```javascript
// 在 counter.js 中
document.addEventListener('DOMContentLoaded', function() {
    // 如果本地存储中没有计数器，则初始化为0
    if (!localStorage.getItem('counter')) {
        localStorage.setItem('counter', 0);
    }

    let counter = localStorage.getItem('counter');
    const h1 = document.querySelector('h1');
    h1.innerHTML = counter;

    document.querySelector('button').onclick = function() {
        counter++;
        h1.innerHTML = counter;
        localStorage.setItem('counter', counter);
    };
});
```
*   `localStorage.getItem('key')` 获取存储的值。
*   `localStorage.setItem('key', value)` 设置存储的值。

![](img/f48bce20dd4d907f3ab6977220476d3e_163.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_165.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_167.png)

---

## 与API交互：Ajax

![](img/f48bce20dd4d907f3ab6977220476d3e_169.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_171.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_173.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_174.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_176.png)

我们可以使用`fetch`函数进行异步JavaScript请求（Ajax），从其他服务器获取数据，而无需重新加载页面。

![](img/f48bce20dd4d907f3ab6977220476d3e_177.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_179.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_181.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_183.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_185.png)

例如，创建一个货币汇率转换器：
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Currency Exchange</title>
        <script>
            document.addEventListener('DOMContentLoaded', function() {
                document.querySelector('form').onsubmit = function() {
                    // 获取用户输入的货币代码并转为大写
                    const currency = document.querySelector('#currency').value.toUpperCase();

                    // 从API获取汇率数据
                    fetch(`https://api.exchangeratesapi.io/latest?base=USD`)
                        .then(response => response.json())
                        .then(data => {
                            const rate = data.rates[currency];
                            if (rate !== undefined) {
                                document.querySelector('#result').innerHTML = `1 USD = ${rate.toFixed(3)} ${currency}`;
                            } else {
                                document.querySelector('#result').innerHTML = 'Invalid currency.';
                            }
                        })
                        .catch(error => {
                            console.log('Error:', error);
                        });

                    return false; // 阻止表单提交
                };
            });
        </script>
    </head>
    <body>
        <h1>Currency Exchange</h1>
        <form>
            <input id="currency" placeholder="Currency (e.g., EUR)" type="text">
            <input type="submit" value="Convert">
        </form>
        <div id="result"></div>
    </body>
</html>
```
*   `fetch(url)` 向指定URL发起网络请求，返回一个Promise。
*   `.then(response => response.json())` 当请求完成，将响应转换为JSON格式。
*   `.then(data => { ... })` 处理获取到的JSON数据。
*   `.catch(error => { ... })` 处理请求过程中可能发生的错误。
*   `data.rates[currency]` 使用变量作为键名访问对象属性。

![](img/f48bce20dd4d907f3ab6977220476d3e_187.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_188.png)

---

![](img/f48bce20dd4d907f3ab6977220476d3e_190.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_192.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_194.png)

## 总结

![](img/f48bce20dd4d907f3ab6977220476d3e_196.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_198.png)

![](img/f48bce20dd4d907f3ab6977220476d3e_200.png)

本节课中我们一起学习了JavaScript的核心概念。我们了解了JavaScript作为客户端语言的作用，学习了如何通过`<script>`标签将其添加到网页中。我们探索了事件驱动编程，使用事件监听器响应用户交互。我们掌握了如何操作DOM来动态更新网页内容和样式，并使用了变量、函数和条件语句。我们还学习了如何通过`localStorage`在浏览器中存储数据，以及如何使用`fetch`进行Ajax调用与外部API通信，从而创建动态、交互式的现代Web应用。