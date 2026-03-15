# 003：Git与GitHub入门教程 🚀

![](img/696f4c51e790d086182d7dd7e5beae4b_1.png)

在本节课中，我们将要学习版本控制系统Git以及代码托管平台GitHub的核心概念和基本工作流程。我们将从Git是什么以及为什么使用它开始，逐步深入到其核心概念、基本命令和一个完整的实战演示。

## 什么是Git？🤔

Git是一个分布式版本控制系统。版本控制系统允许你跟踪计算机文件中的更改。因此，你可以用它来恢复工作的先前版本。另一个重要用途是能够与团队中的其他开发者在同一项目上进行协作。

Git是目前最常用的版本控制系统。虽然今天仍在使用一些更旧的版本控制系统，但Git是最流行的。在你的职业生涯中，你会经常遇到它。因此，确保你透彻理解它极其重要。

关于Git，它可能看起来非常可怕。但重要的是要理解，只要对Git及其良好实践有充分的理解，你就能确保永远不会遇到这些问题。即使你最终犯了这些错误，它们也都是可以修复的。

## Git核心概念与工作环境 🏗️

上一节我们介绍了Git的基本定义，本节中我们来看看Git的核心工作环境。

Git有四个主要的工作环境：工作目录、暂存区、本地仓库和远程仓库。

![](img/696f4c51e790d086182d7dd7e5beae4b_3.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_5.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_7.png)

*   **工作目录**：这就是普通的文件夹，你的操作系统所认识的样子。它包含所有文件，无论它们是否被Git跟踪。
*   **暂存区**：这是一个中间区域。Git只能跟踪它知道的文件。你需要将文件或更改放入暂存区，这样Git才能知道如何处理它们，并在你提交、推送和拉取时跟踪它们。
*   **本地仓库**：这是位于你计算机上的仓库。它包含你最终想要同步到远程仓库的所有更改。
*   **远程仓库**：这是你本地仓库的镜像，通常托管在像GitHub这样的平台上。它包含你本地仓库中所有更改的历史记录，是团队协作的中心。

![](img/696f4c51e790d086182d7dd7e5beae4b_9.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_10.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_12.png)

## Git基本命令 📟

理解了Git的环境后，我们来看看在这些环境之间移动所需的基本命令。

以下是六个核心的Git命令：

1.  **`git init`**：此命令在你的文件夹中初始化一个新的Git仓库，创建一个隐藏的`.git`文件夹。
2.  **`git clone <repository_url>`**：此命令从远程源（如GitHub）复制一个仓库到你的本地计算机。
3.  **`git add <file_name>`** 或 **`git add .`**：此命令将文件从工作目录添加到暂存区，让Git开始跟踪它们。
4.  **`git commit -m "Your message here"`**：此命令将暂存区的更改保存到本地仓库，创建一个“快照”。提交信息应简洁且描述性强。
5.  **`git push`**：此命令将你本地仓库的提交传输到远程仓库。
6.  **`git pull`**：此命令从远程仓库拉取最新的更改到你的本地仓库。

## 基础工作流程演示 🎬

![](img/696f4c51e790d086182d7dd7e5beae4b_14.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_16.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_18.png)

现在，让我们将理论付诸实践，通过一个简单的例子来演示一个基础的Git工作流程。

![](img/696f4c51e790d086182d7dd7e5beae4b_20.png)

首先，我在GitHub上创建了一个名为`196-lecture`的新仓库。然后，我使用`git clone`命令将其复制到我的本地计算机。

![](img/696f4c51e790d086182d7dd7e5beae4b_22.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_23.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_25.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_27.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_28.png)

```bash
git clone https://github.com/your-username/196-lecture.git
cd 196-lecture
```

接下来，我创建一个新文件`demo.txt`，并添加一些内容（一个购物清单）。

```bash
touch demo.txt
# 使用文本编辑器（如VS Code、nano）打开demo.txt并添加内容：
# shopping list
# watermelon
# onions
```

现在，我需要将这些更改提交到仓库。第一步是将文件添加到暂存区。

![](img/696f4c51e790d086182d7dd7e5beae4b_30.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_32.png)

```bash
git add demo.txt
# 或者使用 git add . 添加所有更改
```

![](img/696f4c51e790d086182d7dd7e5beae4b_34.png)

然后，提交这些更改到本地仓库，并附上描述性的信息。

![](img/696f4c51e790d086182d7dd7e5beae4b_36.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_38.png)

```bash
git commit -m "Create a shopping list with two items"
```

![](img/696f4c51e790d086182d7dd7e5beae4b_40.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_41.png)

最后，将本地提交推送到远程仓库（GitHub）。

![](img/696f4c51e790d086182d7dd7e5beae4b_43.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_44.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_46.png)

```bash
git push
```

![](img/696f4c51e790d086182d7dd7e5beae4b_48.png)

此时，如果你刷新GitHub页面，就会看到`demo.txt`文件及其内容。

现在，假设我的队友在GitHub上直接编辑了`demo.txt`，添加了“laptop”。为了获取这个远程更改，我需要在本地运行：

![](img/696f4c51e790d086182d7dd7e5beae4b_50.png)

```bash
git pull
```

![](img/696f4c51e790d086182d7dd7e5beae4b_52.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_54.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_56.png)

![](img/696f4c51e790d086182d7dd7e5beae4b_58.png)

这个命令会将远程仓库的最新内容（包括队友添加的“laptop”）拉取到我的本地`demo.txt`文件中。

## 总结 📚

![](img/696f4c51e790d086182d7dd7e5beae4b_60.png)

本节课中我们一起学习了Git和GitHub的基础知识。我们了解了Git作为一个分布式版本控制系统，如何通过跟踪文件更改来帮助管理项目历史和团队协作。我们明确了Git的四个核心环境：工作目录、暂存区、本地仓库和远程仓库，并学习了在这些环境间移动的基本命令：`init`、`clone`、`add`、`commit`、`push`和`pull`。最后，我们通过一个创建文件、添加、提交和推送的完整演示，实践了基础的Git工作流程。掌握这些是进行高效、安全软件开发的第一步。