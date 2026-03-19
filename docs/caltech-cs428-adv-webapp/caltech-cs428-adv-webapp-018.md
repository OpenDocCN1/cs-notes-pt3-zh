# 018：Bug修复 🐛

![](img/e2b69eb057e8abc59bb25d080c1911eb_0.png)

在本节课中，我们将学习如何构建一个前端REST客户端，用于连接我们之前开发的后端API，从而创建一个完整的“猜数字”游戏应用。我们将重点复习异步JavaScript、DOM操作以及如何设计一个遵循MVC架构的前端应用。

## 概述

上一节我们介绍了如何构建一个RESTful API服务器。本节中，我们将基于该API，构建一个与之交互的前端客户端。通过本教程，你将拥有一个完整的前后端分离的“猜数字”游戏应用。

## 客户端架构设计

在开始编码之前，我们需要规划前端应用的结构。我们将采用MVC（模型-视图-控制器）架构来分离职责，确保代码清晰且易于维护。

以下是项目文件夹结构：
```
highlow-client/
├── index.html
└── scripts/
    ├── data.js
    ├── views.js
    ├── game.js
    └── controllers.js
```

![](img/e2b69eb057e8abc59bb25d080c1911eb_2.png)

## 创建主菜单视图 🏠

![](img/e2b69eb057e8abc59bb25d080c1911eb_4.png)

首先，我们需要创建应用的入口页面，即主菜单视图。这个视图将提供“新游戏”和“加入游戏”两个选项。

以下是实现主菜单的步骤：

![](img/e2b69eb057e8abc59bb25d080c1911eb_6.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_8.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_9.png)

1.  在 `index.html` 中定义视图容器并引入JavaScript文件。
2.  在 `views.js` 中创建 `mainMenu` 函数，用于渲染主菜单的HTML内容。
3.  在 `controllers.js` 中设置按钮的事件监听器。

**代码示例 (`views.js`):**
```javascript
function mainMenu() {
    const view = document.getElementById('view');
    const html = `
        <section>
            <button id="new-game-button">新游戏</button>
            <button id="join-game-button">加入游戏</button>
        </section>
    `;
    view.innerHTML = html;
}
```

## 实现新游戏视图 🎮

当用户点击“新游戏”按钮时，应用应切换到新游戏视图，允许用户设置数字范围并开始游戏。

![](img/e2b69eb057e8abc59bb25d080c1911eb_11.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_13.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_15.png)

以下是创建新游戏视图的步骤：

1.  在 `views.js` 中创建 `newGameMenu` 函数来渲染输入界面。
2.  在 `controllers.js` 中定义回调函数，并绑定到“开始游戏”按钮。
3.  在 `game.js` 中实现 `startGame` 函数，该函数将获取用户输入的范围，并通过 `fetch` 请求后端API来创建新游戏。

**核心概念：异步请求**
我们使用 `async/await` 和 `fetch` 来发送HTTP请求到后端服务器，并等待响应。

![](img/e2b69eb057e8abc59bb25d080c1911eb_17.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_19.png)

**公式/代码描述:**
```javascript
async function startGame() {
    const min = getMinValue(); // 从DOM获取最小值
    const max = getMaxValue(); // 从DOM获取最大值
    const url = `http://localhost:3000/api/game/new?start=${min}&end=${max}`;
    const response = await fetch(url);
    const data = await response.json();
    gameId = data.gameId; // 保存游戏ID
    viewGame(); // 切换到游戏视图
}
```

![](img/e2b69eb057e8abc59bb25d080c1911eb_21.png)

## 构建加入游戏视图 🔗

![](img/e2b69eb057e8abc59bb25d080c1911eb_23.png)

用户也可以选择加入一个已存在的游戏。我们需要创建一个视图，让用户输入游戏ID。

![](img/e2b69eb057e8abc59bb25d080c1911eb_25.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_27.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_29.png)

实现加入游戏视图的步骤如下：

![](img/e2b69eb057e8abc59bb25d080c1911eb_31.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_33.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_35.png)

1.  在 `views.js` 中创建 `joinGameMenu` 函数。
2.  在 `game.js` 中实现 `findGame` 函数，该函数根据用户输入的游戏ID，向后端请求该游戏的数据。
3.  根据后端返回的成功状态，决定是跳转到游戏视图还是返回主菜单。

## 创建游戏核心视图 🎲

![](img/e2b69eb057e8abc59bb25d080c1911eb_37.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_39.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_41.png)

游戏视图是用户进行猜测的核心界面。它需要显示游戏信息、提供输入框并展示历史线索。

![](img/e2b69eb057e8abc59bb25d080c1911eb_43.png)

以下是游戏视图的实现要点：

![](img/e2b69eb057e8abc59bb25d080c1911eb_45.png)

1.  在 `views.js` 的 `viewGame` 函数中，渲染游戏ID、数字范围、输入框和提交按钮。
2.  实现提交猜测的逻辑。在 `game.js` 的 `submitGuess` 函数中，将用户的猜测发送到后端API。
3.  根据API返回的线索（如“太高”、“太低”、“正确”或“游戏结束”），更新前端界面。

**代码示例 (`game.js` 提交猜测):**
```javascript
async function submitGuess() {
    const guess = getGuessValue(); // 从DOM获取猜测值
    const url = `http://localhost:3000/api/game/${gameId}/guess?guess=${guess}`;
    const response = await fetch(url);
    const data = await response.json();

    if (data.success) {
        if (data.guess === 'correct') {
            gameOverMenu('你赢了！');
        } else if (data.guess === 'game over') {
            gameOverMenu('你输了！');
        } else {
            // 显示线索（太高或太低）
            viewClue(data.guess, guess);
        }
    }
}
```

![](img/e2b69eb057e8abc59bb25d080c1911eb_47.png)

## 实现游戏结束视图 🏁

当游戏分出胜负后，我们需要向用户展示结果，并提供“重玩”或“返回主菜单”的选项。

![](img/e2b69eb057e8abc59bb25d080c1911eb_49.png)

创建游戏结束视图的步骤：

![](img/e2b69eb057e8abc59bb25d080c1911eb_51.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_53.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_55.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_57.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_59.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_61.png)

1.  在 `views.js` 中创建 `gameOverMenu` 函数，接收“赢”或“输”的结果参数进行显示。
2.  实现“重玩”功能。在 `game.js` 中创建 `resetGame` 函数，调用后端API重置当前游戏。
3.  实现“退出”功能，简单地调用 `mainMenu` 函数返回主界面。

## 总结

![](img/e2b69eb057e8abc59bb25d080c1911eb_63.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_65.png)

![](img/e2b69eb057e8abc59bb25d080c1911eb_67.png)

本节课中，我们一起学习了如何为一个“猜数字”游戏构建完整的前端REST客户端。我们回顾并应用了以下核心概念：
*   使用 `async/await` 和 `fetch` 进行异步HTTP通信。
*   操作DOM来动态更新单页面应用(SPA)的视图。
*   采用MVC架构来组织前端代码，分离数据、视图和逻辑。
*   解析和使用JSON格式的数据。
*   设计用户流程，并实现各个视图之间的切换。

![](img/e2b69eb057e8abc59bb25d080c1911eb_69.png)

通过将此前独立学习的后端API与前端技术相结合，你现在已经能够创建功能完整的全栈Web应用了。可以尝试为此应用添加样式、用户系统或使用WebSocket实现实时功能，作为进一步的练习。