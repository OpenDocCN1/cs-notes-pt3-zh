# 003：Git 🚀

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_1.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_3.png)

在本节课中，我们将要学习一个强大的工具——Git。Git是一个版本控制系统，它不仅能帮助我们追踪代码的每一次修改，还能让我们与团队成员高效协作，管理项目的不同版本。无论你是独自开发还是团队合作，Git都是现代软件开发中不可或缺的工具。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_5.png)

上一节我们介绍了如何使用HTML和CSS来设计和美化网页。本节中，我们来看看如何利用Git来管理和协作开发我们的网页项目。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_7.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_8.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_9.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_11.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_12.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_13.png)

## 什么是Git？

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_15.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_16.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_18.png)

Git是一个命令行工具，它主要为我们提供两大核心功能：

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_20.png)

1.  **追踪代码变更**：Git可以记录我们对代码所做的每一次修改，并保存为一个个“快照”（称为提交）。这样，我们就能轻松回顾历史版本，甚至在需要时回退到之前的某个状态。
2.  **同步多人协作**：在大型项目中，通常不止一个人参与开发。Git使得多人可以同时在一个项目上工作，并轻松地将各自的修改合并到一起，保持代码同步。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_22.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_24.png)

此外，Git还允许我们：
*   在不影响主代码的情况下，创建独立的分支来测试新功能。
*   轻松地回退到任何旧的代码版本。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_26.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_28.png)

## 核心概念与工作流程

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_30.png)

Git的核心操作围绕着本地仓库和远程仓库（如GitHub）的交互。以下是基本的工作流程：

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_32.png)

1.  **克隆 (`git clone`)**：将远程仓库的代码完整地下载到本地计算机。
    ```bash
    git clone <repository-url>
    ```
2.  **添加 (`git add`)**：将修改过的文件标记为“待提交”状态，告诉Git下次提交时要包含这些文件。
    ```bash
    git add <filename>
    ```
3.  **提交 (`git commit`)**：将已添加的文件变更，创建一个永久的快照记录。每次提交都需要一个描述性的信息。
    ```bash
    git commit -m “描述本次提交的修改内容”
    ```
4.  **推送 (`git push`)**：将本地提交的更改上传到远程仓库（如GitHub），使他人能看到你的最新工作。
    ```bash
    git push
    ```
5.  **拉取 (`git pull`)**：从远程仓库下载最新的更改到本地，确保你拥有项目的最新版本。
    ```bash
    git pull
    ```

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_34.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_35.png)

## 实战演练：从创建到提交

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_37.png)

让我们通过一个简单的例子，体验Git的基本操作。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_39.png)

### 1. 创建GitHub仓库并克隆

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_41.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_42.png)

首先，我们需要一个在线存储代码的地方。我们使用GitHub。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_44.png)

*   访问 `github.com/new` 创建一个新仓库，命名为 `hello`。
*   创建后，你会获得一个空的在线仓库。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_46.png)

接下来，在本地计算机的终端中，使用 `git clone` 命令将这个仓库下载到本地：
```bash
git clone https://github.com/你的用户名/hello.git
cd hello
```
现在，你本地就有了一个名为 `hello` 的文件夹，它是远程仓库的副本。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_48.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_49.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_51.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_53.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_55.png)

### 2. 创建文件并提交更改

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_57.png)

在本地 `hello` 文件夹中，我们创建一个简单的HTML文件。
```bash
touch hello.html
```
然后，用文本编辑器打开 `hello.html`，写入以下内容：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello</title>
    </head>
    <body>
        <h1>Hello, world!</h1>
    </body>
</html>
```
保存文件后，我们需要告诉Git追踪这个文件，并保存当前状态。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_59.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_60.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_61.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_63.png)

以下是操作步骤：
```bash
# 1. 将 hello.html 文件添加到暂存区
git add hello.html

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_65.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_67.png)

# 2. 提交更改，并附上说明信息
git commit -m “添加了 hello.html 文件”

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_69.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_70.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_72.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_73.png)

# 3. 将本地的提交推送到 GitHub
git push
```
完成 `git push` 后，刷新你的GitHub仓库页面，就能看到 `hello.html` 文件已经出现在线上了。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_75.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_77.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_78.png)

### 3. 查看状态与处理后续修改

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_80.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_82.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_84.png)

`git status` 命令非常有用，它可以随时告诉你仓库的当前状态：哪些文件被修改了，哪些已暂存等。
```bash
git status
```
如果你后续修改了 `hello.html` 文件（例如添加了一个 `<h2>` 标题），并想快速提交所有更改，可以使用一个组合命令：
```bash
git commit -am “添加了二级标题”
```
这里的 `-a` 参数代表自动添加所有已修改的文件，`-m` 则是添加提交信息。然后同样需要 `git push` 来同步到远程。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_86.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_87.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_89.png)

## 处理合并冲突 🤝

当多人修改同一文件的同一部分时，就会发生合并冲突。例如，你和同事同时修改了 `hello.html` 中 `<h1>` 标签的同一行。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_91.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_93.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_94.png)

当你尝试 `git pull` 获取同事的更改时，Git会提示冲突。打开冲突文件，你会看到类似这样的标记：
```html
<<<<<<< HEAD
<h1 style=“color: blue;”>Welcome to my site!!</h1>
=======
<h1 style=“color: red;”>Welcome to my site!</h1>
>>>>>>> some-commit-hash
```
*   `<<<<<<< HEAD` 和 `=======` 之间是你的本地修改。
*   `=======` 和 `>>>>>>>` 之间是远程（同事）的修改。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_96.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_98.png)

**解决冲突的方法是**：你需要手动编辑文件，决定保留哪种修改，或者进行融合。删除所有冲突标记（`<<<<<<<`, `=======`, `>>>>>>>`），将文件修改为你最终想要的样子。例如，你可以决定保留蓝色和两个感叹号：
```html
<h1 style=“color: blue;”>Welcome to my site!!</h1>
```
解决冲突后，提交并推送你的更改：
```bash
git add hello.html
git commit -m “解决合并冲突”
git push
```

## 分支管理 🌿

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_100.png)

分支允许你在不干扰主开发线（通常是 `master` 或 `main` 分支）的情况下开发新功能或修复Bug。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_102.png)

以下是分支的常用命令：
```bash
# 查看所有分支，当前分支前会标有 *
git branch

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_104.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_105.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_106.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_108.png)

# 创建并切换到一个名为 “new-feature” 的新分支
git checkout -b new-feature

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_110.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_112.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_114.png)

# 切换到已存在的 “master” 分支
git checkout master

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_116.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_117.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_119.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_121.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_122.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_123.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_125.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_126.png)

# 将 “new-feature” 分支的更改合并到当前分支（如 master）
git merge new-feature
```
**工作流程示例**：
1.  在 `master` 分支上进行稳定开发。
2.  想尝试一个新功能时，创建并切换到 `feature-branch` 分支。
3.  在 `feature-branch` 上自由地提交更改。
4.  功能完成后，切换回 `master` 分支，然后运行 `git merge feature-branch` 进行合并。
5.  如果合并时发生冲突，按上述方法解决即可。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_128.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_130.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_131.png)

## 其他实用命令

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_133.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_135.png)

*   `git log`：查看项目的提交历史记录，包括提交者、日期和描述。
*   `git reset`：将仓库状态回退到指定的历史提交。**（谨慎使用）**
    ```bash
    # 硬重置到某个特定提交（丢弃之后的所有更改）
    git reset --hard <commit-hash>
    # 重置到与远程 master 分支一致的状态
    git reset --hard origin/master
    ```

## GitHub 特色功能

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_137.png)

*   **Fork（复刻）**：在GitHub上复制别人的仓库到你自己的账户下。你可以自由修改这个副本，而不会影响原项目。
*   **Pull Request（拉取请求）**：如果你在Fork的仓库中做了有用的改进，可以向原仓库发起一个“拉取请求”，请求作者将你的修改合并进去。这是开源协作的核心。
*   **GitHub Pages**：GitHub提供的免费静态网站托管服务。只需创建一个名为 `<你的用户名>.github.io` 的仓库，并将HTML/CSS/JS文件推送到该仓库，GitHub就会自动为你生成一个可通过该URL访问的网站。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_139.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_141.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_143.png)

## 总结

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_145.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_147.png)

本节课中我们一起学习了Git这一强大的版本控制工具。我们了解了它的核心用途：追踪代码变更和协同工作。我们实践了从克隆仓库、添加文件、提交更改到推送远程的基本工作流。我们还探讨了如何处理合并冲突，以及如何使用分支来并行开发不同功能。最后，我们简要介绍了GitHub的复刻、拉取请求和Pages等实用功能。

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_149.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_151.png)

![](img/fc15ab32beaa65dcdbeed3fe5bc8dcc3_152.png)

掌握Git是成为一名高效开发者的关键一步。它不仅能让你更好地管理自己的项目，更是你未来参与任何团队或开源项目协作的基石。下一节，我们将开始学习Python编程语言，为构建更复杂的Web应用后端打下基础。