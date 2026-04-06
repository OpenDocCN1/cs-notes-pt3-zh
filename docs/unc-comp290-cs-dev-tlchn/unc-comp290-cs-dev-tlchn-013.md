# 013：构建系统与GitHub Actions入门教程 🛠️

在本节课中，我们将要学习构建系统（Build Systems）和GitHub Actions的基本概念。我们将了解什么是构建系统，为什么需要它们，以及如何利用GitHub Actions来自动化代码的构建、测试和部署流程。课程内容将从一个简单的Python构建脚本示例开始，逐步引导你创建一个完整的自动化工作流。

---

## 概述 📋

构建系统是一套用于自动将源代码转换为可执行文件或成品的工具。GitHub Actions是GitHub平台提供的一项功能，允许我们在代码仓库中设置自动化任务，例如在推送代码时自动运行构建脚本。本节课将结合两者，演示如何创建一个自动化工作流，将简单的HTML网站构建并部署到GitHub Pages。

---

## 构建系统简介

上一节我们介绍了课程概述，本节中我们来看看什么是构建系统。

构建系统可以定义为**任何用于自动将代码以某种方式转换的工具或程序集合**。这个定义听起来可能比较抽象，我们可以通过一些具体例子来理解。

*   **编译代码**：例如，将Java代码编译成计算机可以运行的字节码。
*   **创建Docker容器**：将应用程序及其依赖打包，便于部署。
*   **自定义脚本**：针对特定项目需求编写的自动化脚本。

构建系统的目的是**自动化重复且繁琐的手动操作**。随着项目规模扩大，手动管理哪些文件需要编译、如何构建会变得非常困难。作为“懒惰”的程序员，我们希望通过构建系统一键完成这些工作。

![](img/e257caba128277fb0ae6d1e024c15d58_1.png)

需要注意的是，**没有适用于所有场景的单一构建系统**。不同的技术栈和项目类型会使用不同的工具。

![](img/e257caba128277fb0ae6d1e024c15d58_3.png)

![](img/e257caba128277fb0ae6d1e024c15d58_4.png)

![](img/e257caba128277fb0ae6d1e024c15d58_5.png)

以下是几种常见的构建系统：
*   **Make**：常用于C/C++项目。
*   **Gradle/Maven**：常用于Java项目。
*   **Xcode命令行工具**：用于构建iOS或macOS应用。
*   **自定义脚本**：在Web开发等领域非常常见，用于处理特定的构建流程。

构建系统是将程序员编写的代码转化为可供他人使用的产品的关键桥梁。例如，当你下载Chrome浏览器时，你点击安装的是一个已经构建好的可执行文件，而不是需要你手动编译的源代码。

---

## 从构建到部署的完整流程

理解了构建系统的基本概念后，我们来看看它在软件开发完整流程中的位置。

通常，一个完整的软件交付流程可以看作一个三阶段的管道：

1.  **测试（Test）**：确保代码行为符合预期。例如使用 `pytest` 进行单元测试。
2.  **构建（Build）**：将源代码转换为可执行文件或成品。这正是构建系统的职责所在。
3.  **部署（Deploy）**：将构建好的成品发布到某个位置，使其可被访问。例如，将网站文件上传到服务器，或将应用程序安装包上传到下载站点。

一个健壮的自动化流程通常会在构建之后再次进行测试，以确保构建过程没有引入错误，然后再进行部署。因此，流程可能演变为：**测试 -> 构建 -> 测试 -> 部署**。

这个流程不仅限于软件开发，在网络安全、游戏开发等领域同样至关重要。例如，之前导致大规模系统故障的CrowdStrike事件，其根源就是在自动构建和部署管道中未能有效检测出有问题的更新。

---

## GitHub Actions 简介

![](img/e257caba128277fb0ae6d1e024c15d58_7.png)

上一节我们介绍了从构建到部署的流程，本节中我们来看看如何用GitHub Actions来实现这个流程的自动化。

GitHub Actions是GitHub提供的一项功能（**注意：它与Git版本控制系统是分开的**）。它允许我们在代码仓库中定义并运行特定的自动化任务。

![](img/e257caba128277fb0ae6d1e024c15d58_9.png)

![](img/e257caba128277fb0ae6d1e024c15d58_11.png)

其核心工作机制是：**当特定事件发生时（如推送代码到仓库），触发预定义的工作流，在GitHub的服务器上自动执行一系列任务**。

![](img/e257caba128277fb0ae6d1e024c15d58_13.png)

![](img/e257caba128277fb0ae6d1e024c15d58_15.png)

这对于构建系统来说非常有用。我们可以设置一个Action，使得每次推送代码时，自动触发构建过程，生成最新的可执行文件，甚至自动完成部署。

GitHub Actions的相关术语：
*   **动作/脚本（Action/Script）**：要执行的具体任务。可以是预制的Action，也可以是项目内的自定义脚本。
*   **作业（Job）**：由一系列动作组成的执行单元。
*   **工作流（Workflow）**：由一个或多个作业组成，定义了完整的自动化流程。工作流文件采用YAML格式编写。

简单来说，GitHub Actions就是一个**在代码推送到GitHub时自动运行指定任务**的系统，而这些任务常常就包含了构建我们的代码。

---

![](img/e257caba128277fb0ae6d1e024c15d58_17.png)

![](img/e257caba128277fb0ae6d1e024c15d58_18.png)

![](img/e257caba128277fb0ae6d1e024c15d58_19.png)

## 实践演示：使用Python脚本与GitHub Actions

![](img/e257caba128277fb0ae6d1e024c15d58_21.png)

![](img/e257caba128277fb0ae6d1e024c15d58_22.png)

![](img/e257caba128277fb0ae6d1e024c15d58_23.png)

![](img/e257caba128277fb0ae6d1e024c15d58_25.png)

理论部分已经介绍完毕，现在让我们通过一个动手示例来将以上概念串联起来。

![](img/e257caba128277fb0ae6d1e024c15d58_27.png)

本节课的实践计划如下：
1.  使用一个自定义的Python脚本作为我们的构建系统。
2.  利用GitHub Actions创建一个工作流，在代码推送时自动运行该构建脚本。
3.  将构建产物（一个简单的网站）自动部署到GitHub Pages。

我们将创建一个工作流（Workflow），其中包含两个作业（Job），总共涉及四个动作/脚本（Action/Script）。

### 第一步：了解项目与构建脚本

![](img/e257caba128277fb0ae6d1e024c15d58_29.png)

![](img/e257caba128277fb0ae6d1e024c15d58_31.png)

我们有一个非常简单的网站，核心是一个 `index.html` 文件。这个页面上显示“Hello World”以及一个页脚，页脚文字是“This page was last built at current time here”。

![](img/e257caba128277fb0ae6d1e024c15d58_33.png)

![](img/e257caba128277fb0ae6d1e024c15d58_35.png)

显然，“current time here”是一个占位符，我们需要在构建时将其替换为真实的当前时间。为此，我们编写了一个Python构建脚本 `build.py`。

以下是 `build.py` 脚本的核心逻辑：
```python
# 读取 index.html 文件内容
with open('index.html', 'r') as file:
    file_data = file.read()

# 获取当前时间
current_time = datetime.now(eastern).strftime('%Y-%m-%d %H:%M:%S %Z')

# 构建步骤：替换占位符
file_data = file_data.replace('current time here', current_time)

# 将结果写入新目录下的新文件，不覆盖原文件
os.makedirs('out', exist_ok=True)
with open('out/index.html', 'w') as file:
    file.write(file_data)
```
这个脚本的作用就是**构建系统**的核心：转换源代码（替换时间戳），并输出成品（`out/index.html`）。

手动运行 `python build.py` 后，可以在 `out` 目录下看到生成的新网页，页脚时间已经更新。

### 第二步：创建GitHub Actions工作流

![](img/e257caba128277fb0ae6d1e024c15d58_37.png)

![](img/e257caba128277fb0ae6d1e024c15d58_39.png)

![](img/e257caba128277fb0ae6d1e024c15d58_40.png)

我们的目标是自动化这个过程。我们需要创建GitHub Actions的配置文件。

![](img/e257caba128277fb0ae6d1e024c15d58_42.png)

以下是创建步骤：
1.  在代码仓库根目录创建 `.github/workflows/` 文件夹。
2.  在 `workflows` 文件夹内创建一个YAML文件，例如 `action.yml`。

接下来，我们来编写这个工作流文件的内容。工作流文件的结构遵循我们之前介绍的术语：**工作流 -> 作业 -> 步骤**。

首先，定义工作流的触发条件：
```yaml
on: [push]
```
这表示当向仓库推送代码时，触发此工作流。

接着，定义第一个作业 `build`，它负责构建代码：
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v4

      - name: Build index.html file
        run: python build.py

      - name: Upload build files
        uses: actions/upload-pages-artifact@v3
        with:
          path: 'out'
```
*   `runs-on`: 指定任务在何种系统环境的GitHub服务器上运行，这里使用最新的Ubuntu系统。
*   `steps`: 定义了作业内的步骤序列。
    *   第一步：使用 `actions/checkout` 动作，将仓库代码检出到服务器。
    *   第二步：`run` 命令直接执行我们的构建脚本 `python build.py`。
    *   第三步：使用 `actions/upload-pages-artifact` 动作，将构建产物（`out` 目录）上传为一个“工件”，供后续步骤使用。

然后，定义第二个作业 `deploy`，它依赖于 `build` 作业的成功完成，并负责部署：
```yaml
  deploy:
    runs-on: ubuntu-latest
    needs: build
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```
*   `needs: build`: 表示此作业必须在 `build` 作业成功完成后才能开始。
*   `permissions` 和 `environment`: 为部署到GitHub Pages设置必要的权限和环境变量。
*   步骤：使用 `actions/deploy-pages` 动作，将上传的工件部署到GitHub Pages。

### 第三步：启用GitHub Pages并触发工作流

![](img/e257caba128277fb0ae6d1e024c15d58_44.png)

![](img/e257caba128277fb0ae6d1e024c15d58_46.png)

1.  在GitHub仓库的 **Settings** -> **Pages** 页面，将 **Source** 从 `Branch` 改为 **GitHub Actions**。
2.  将包含工作流文件（`action.yml`）的更改提交并推送到GitHub仓库。
    ```bash
    git add .
    git commit -m "Add GitHub Actions workflow"
    git push origin main
    ```
3.  推送完成后，进入仓库的 **Actions** 标签页，即可看到运行中的工作流。点击进入可以查看每个步骤的详细日志。

工作流成功运行后，在 **Settings** -> **Pages** 页面，或者部署作业的日志输出中，你可以找到你的网站地址（通常格式为 `https://<你的用户名>.github.io/<仓库名>/`）。访问该链接，你应该能看到页脚时间已更新为工作流运行时刻的网站。

---

## 总结 🎉

本节课中我们一起学习了构建系统和GitHub Actions。

![](img/e257caba128277fb0ae6d1e024c15d58_48.png)

![](img/e257caba128277fb0ae6d1e024c15d58_50.png)

我们首先了解了**构建系统**的概念，它是自动化代码转换的工具集合，对于提高开发效率和保证交付质量至关重要。接着，我们探讨了从测试、构建到部署的完整软件交付流程。

![](img/e257caba128277fb0ae6d1e024c15d58_52.png)

然后，我们深入介绍了**GitHub Actions**，这是一个强大的自动化平台，可以响应仓库事件（如代码推送）并执行自定义任务。我们学习了其核心概念：工作流、作业和步骤。

![](img/e257caba128277fb0ae6d1e024c15d58_54.png)

![](img/e257caba128277fb0ae6d1e024c15d58_55.png)

最后，通过一个完整的实践演示，我们将理论应用于实际。我们创建了一个自定义的Python构建脚本，并编写了一个GitHub Actions工作流来自动化构建和部署流程，成功将一个简单网站发布到了GitHub Pages。

![](img/e257caba128277fb0ae6d1e024c15d58_57.png)

![](img/e257caba128277fb0ae6d1e024c15d58_59.png)

![](img/e257caba128277fb0ae6d1e024c15d58_60.png)

![](img/e257caba128277fb0ae6d1e024c15d58_62.png)

![](img/e257caba128277fb0ae6d1e024c15d58_63.png)

通过本节课的学习，你应该对如何利用自动化工具来简化和规范软件开发流程有了初步的认识，这是现代软件开发实践中一项非常实用的技能。