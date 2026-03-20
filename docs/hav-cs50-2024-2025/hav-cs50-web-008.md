# 008：用户界面 🎨

![](img/7446320d86e81d3fe2c0cfe492353a7d_1.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_3.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_5.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_7.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_8.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_9.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_11.png)

在本节课中，我们将学习如何利用JavaScript创建交互式用户界面。我们将探讨单页应用、无限滚动、CSS动画以及React框架等核心概念，以构建动态且响应迅速的网络应用。

![](img/7446320d86e81d3fe2c0cfe492353a7d_13.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_15.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_17.png)

---

![](img/7446320d86e81d3fe2c0cfe492353a7d_19.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_21.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_23.png)

## 单页应用

![](img/7446320d86e81d3fe2c0cfe492353a7d_25.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_27.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_29.png)

上一节我们介绍了JavaScript的基础交互功能。本节中，我们来看看如何构建**单页应用**。单页应用是指整个网站由一个HTML页面构成，通过JavaScript动态替换页面内容，而无需向服务器请求加载新页面。这样做的好处是只更新页面中变化的部分，提高了效率。

![](img/7446320d86e81d3fe2c0cfe492353a7d_31.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_33.png)

以下是创建一个简单单页应用的步骤：

![](img/7446320d86e81d3fe2c0cfe492353a7d_35.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_37.png)

1.  **创建HTML结构**：在一个HTML文件中定义多个“页面”的容器，但默认隐藏它们。
    ```html
    <div id="page1" style="display: none;">
        <h1>这是页面一</h1>
    </div>
    <div id="page2" style="display: none;">
        <h1>这是页面二</h1>
    </div>
    <div id="page3" style="display: none;">
        <h1>这是页面三</h1>
    </div>
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_39.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_41.png)

2.  **添加导航按钮**：创建按钮，通过`data-*`属性标记它们应该显示哪个页面。
    ```html
    <button data-page="page1">页面一</button>
    <button data-page="page2">页面二</button>
    <button data-page="page3">页面三</button>
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_43.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_45.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_46.png)

3.  **编写JavaScript逻辑**：编写函数来显示特定页面并隐藏其他页面，并为按钮添加点击事件监听器。
    ```javascript
    function showPage(page) {
        // 隐藏所有页面
        document.querySelectorAll('div').forEach(div => {
            div.style.display = 'none';
        });
        // 显示请求的页面
        document.querySelector(`#${page}`).style.display = 'block';
    }

    document.addEventListener('DOMContentLoaded', function() {
        document.querySelectorAll('button').forEach(button => {
            button.onclick = function() {
                showPage(this.dataset.page);
            };
        });
    });
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_48.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_50.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_52.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_53.png)

---

![](img/7446320d86e81d3fe2c0cfe492353a7d_55.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_57.png)

## 动态加载内容

![](img/7446320d86e81d3fe2c0cfe492353a7d_59.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_61.png)

在单页应用中，我们并不总是预先加载所有内容。有时，我们需要从服务器动态获取数据。这可以通过JavaScript的`fetch` API实现。

![](img/7446320d86e81d3fe2c0cfe492353a7d_63.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_64.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_66.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_68.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_70.png)

以下是动态加载内容的步骤：

![](img/7446320d86e81d3fe2c0cfe492353a7d_72.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_73.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_75.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_77.png)

1.  **服务器端API**：在Django中创建一个视图，根据请求返回特定内容（例如JSON或纯文本）。
    ```python
    # views.py
    def section(request, num):
        if 1 <= int(num) <= 3:
            return HttpResponse(f"这是第{num}部分的内容")
        else:
            return HttpResponse("无效部分")
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_79.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_81.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_83.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_85.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_86.png)

2.  **客户端JavaScript**：在页面中，编写函数来获取数据并更新DOM。
    ```javascript
    function showSection(sectionNumber) {
        fetch(`/sections/${sectionNumber}`)
            .then(response => response.text())
            .then(text => {
                document.querySelector('#content').innerHTML = text;
            });
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_88.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_89.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_91.png)

3.  **更新URL和历史记录**：为了保持URL与页面状态同步，可以使用History API。
    ```javascript
    // 点击按钮时更新URL
    history.pushState({section: sectionNumber}, '', `section${sectionNumber}`);

    // 监听浏览器前进/后退按钮
    window.onpopstate = function(event) {
        showSection(event.state.section);
    };
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_93.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_95.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_97.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_99.png)

---

![](img/7446320d86e81d3fe2c0cfe492353a7d_101.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_103.png)

## 无限滚动

![](img/7446320d86e81d3fe2c0cfe492353a7d_105.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_107.png)

无限滚动是一种常见的用户体验模式，当用户滚动到页面底部时，自动加载更多内容。实现这一功能需要结合滚动事件检测和异步数据加载。

![](img/7446320d86e81d3fe2c0cfe492353a7d_109.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_111.png)

以下是实现无限滚动的步骤：

![](img/7446320d86e81d3fe2c0cfe492353a7d_113.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_115.png)

1.  **检测滚动到底部**：通过比较窗口高度、滚动距离和文档总高度来判断用户是否到达页面底部。
    ```javascript
    window.onscroll = function() {
        if (window.innerHeight + window.scrollY >= document.body.offsetHeight) {
            // 用户已滚动到底部，加载更多内容
            loadMorePosts();
        }
    };
    ```

2.  **加载更多内容**：编写一个函数，从服务器获取下一批数据（例如帖子）并将其添加到页面中。
    ```javascript
    let start = 1;
    const quantity = 20;

    function load() {
        fetch(`/posts?start=${start}&end=${start + quantity - 1}`)
            .then(response => response.json())
            .then(data => {
                data.posts.forEach(addPost);
                start += quantity;
            });
    }

    function addPost(postContent) {
        const postDiv = document.createElement('div');
        postDiv.innerHTML = postContent;
        document.querySelector('#posts').append(postDiv);
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_117.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_118.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_120.png)

---

## CSS动画

![](img/7446320d86e81d3fe2c0cfe492353a7d_122.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_124.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_125.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_126.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_128.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_130.png)

CSS动画可以为用户界面添加平滑的视觉效果，增强用户体验。我们可以定义关键帧来控制元素在不同时间点的样式。

![](img/7446320d86e81d3fe2c0cfe492353a7d_132.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_133.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_135.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_137.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_139.png)

以下是创建CSS动画的步骤：

![](img/7446320d86e81d3fe2c0cfe492353a7d_141.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_143.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_145.png)

1.  **定义动画关键帧**：使用`@keyframes`规则指定动画的起始和结束状态。
    ```css
    @keyframes grow {
        from { font-size: 20px; }
        to { font-size: 100px; }
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_147.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_149.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_150.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_151.png)

2.  **应用动画**：将动画绑定到HTML元素，并设置持续时间、迭代次数等属性。
    ```css
    h1 {
        animation-name: grow;
        animation-duration: 2s;
        animation-iteration-count: infinite;
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_153.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_155.png)

3.  **使用JavaScript控制动画**：可以通过修改元素的`style.animationPlayState`属性来暂停或播放动画。
    ```javascript
    const heading = document.querySelector('h1');
    heading.style.animationPlayState = 'paused';

    document.querySelector('button').onclick = function() {
        if (heading.style.animationPlayState === 'paused') {
            heading.style.animationPlayState = 'running';
        } else {
            heading.style.animationPlayState = 'paused';
        }
    };
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_157.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_159.png)

---

![](img/7446320d86e81d3fe2c0cfe492353a7d_161.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_162.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_163.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_164.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_166.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_168.png)

## React框架简介

![](img/7446320d86e81d3fe2c0cfe492353a7d_170.png)

随着应用复杂度增加，管理状态和UI更新变得困难。React是一个流行的JavaScript库，它采用**声明式编程**范式，通过组件和状态管理来简化UI开发。

![](img/7446320d86e81d3fe2c0cfe492353a7d_172.png)

以下是React的核心概念：

![](img/7446320d86e81d3fe2c0cfe492353a7d_174.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_176.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_178.png)

1.  **组件**：React应用由可复用的组件构成。组件是一个返回描述UI的JSX代码的函数。
    ```jsx
    function Hello(props) {
        return <h1>Hello, {props.name}!</h1>;
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_180.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_182.png)

2.  **状态**：使用`useState`钩子来在组件内部管理状态。状态变化会自动触发UI更新。
    ```jsx
    function Counter() {
        const [count, setCount] = useState(0);

        function increment() {
            setCount(count + 1);
        }

        return (
            <div>
                <p>{count}</p>
                <button onClick={increment}>增加</button>
            </div>
        );
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_184.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_186.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_188.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_190.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_192.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_194.png)

3.  **基于状态的UI渲染**：在JSX中，可以嵌入JavaScript表达式，根据状态动态决定渲染内容。
    ```jsx
    function Game() {
        const [score, setScore] = useState(0);

        return (
            <div>
                {score >= 10 ? <h1>你赢了！</h1> : <p>得分: {score}</p>}
            </div>
        );
    }
    ```

![](img/7446320d86e81d3fe2c0cfe492353a7d_196.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_198.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_200.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_202.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_204.png)

---

![](img/7446320d86e81d3fe2c0cfe492353a7d_206.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_208.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_210.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_212.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_214.png)

## 总结

![](img/7446320d86e81d3fe2c0cfe492353a7d_216.png)

![](img/7446320d86e81d3fe2c0cfe492353a7d_217.png)

本节课中我们一起学习了如何构建现代、交互式的Web用户界面。我们从创建基本的单页应用开始，学习了如何动态加载内容、实现无限滚动以及添加CSS动画。最后，我们介绍了React框架，它通过组件和状态管理，极大地简化了复杂用户界面的开发流程。掌握这些技术，你将能够创建出既高效又吸引用户的Web应用程序。