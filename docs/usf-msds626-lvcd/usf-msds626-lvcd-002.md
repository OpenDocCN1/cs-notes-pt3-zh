# 002：Linux与Git开发流程 🐧📚

![](img/15adab7f9346ac744fdda4d4db73110d_0.png)

![](img/15adab7f9346ac744fdda4d4db73110d_2.png)

在本节课中，我们将学习如何在Linux环境下使用Git进行版本控制，并建立一个完整的开发工作流程。我们将从创建GitHub仓库开始，逐步学习克隆、编辑、提交和推送代码，同时介绍一些提高效率的终端工具。

![](img/15adab7f9346ac744fdda4d4db73110d_3.png)

---

![](img/15adab7f9346ac744fdda4d4db73110d_5.png)

## 概述

我们将从零开始，创建一个GitHub仓库，将其克隆到本地计算机，然后使用Jupyter Lab编辑一个笔记本文件。接着，我们会学习如何使用Git跟踪更改、提交版本，并将更改推送回GitHub。在此过程中，我们还会介绍SSH密钥认证、Tmux终端复用器等实用工具，帮助你建立一个流畅的开发环境。

---

## 创建GitHub仓库

首先，我们需要在GitHub上创建一个新的代码仓库（Repository）。仓库本质上是一个包含文件和子文件夹的目录，Git可以跟踪其所有版本变化，并允许你轻松地将代码存储和分享到GitHub等平台。

以下是创建仓库的步骤：

1.  登录GitHub，点击右上角你的头像，选择 “Your repositories”。
2.  点击 “New” 按钮创建一个新仓库。
3.  为仓库命名（例如 `walkthrough2`）。
4.  可以添加一个描述（可选）。
5.  选择仓库的可见性（公开或私有）。对于学习和分享，公开仓库通常更有益。
6.  勾选 “Add a README file” 来初始化一个说明文件。
7.  在 “.gitignore” 模板中选择 `Python`，这会自动生成一个忽略临时文件的配置。
8.  选择一个开源许可证（例如 Apache License 2.0），以便他人使用你的代码。
9.  点击 “Create repository” 完成创建。

创建完成后，你会看到一个包含 `README.md` 文件的仓库页面。`README.md` 是一个特殊的Markdown文件，其内容会自动显示在仓库主页，用于介绍项目。

---

## 编辑README文件

现在，我们可以直接在线编辑 `README.md` 文件来完善项目介绍。Markdown是一种轻量级标记语言，在Jupyter和GitHub中广泛使用。

![](img/15adab7f9346ac744fdda4d4db73110d_7.png)

点击文件右上角的铅笔图标进入编辑模式。你可以使用 `#` 创建标题，用空行分隔段落，用 `-` 创建列表。编辑完成后，在页面底部填写本次更改的摘要（Commit message），然后点击 “Commit changes” 保存。每次提交都会在Git历史中创建一个新的版本。

![](img/15adab7f9346ac744fdda4d4db73110d_9.png)

![](img/15adab7f9346ac744fdda4d4db73110d_11.png)

---

## 克隆仓库到本地

![](img/15adab7f9346ac744fdda4d4db73110d_13.png)

![](img/15adab7f9346ac744fdda4d4db73110d_15.png)

虽然可以在线编辑，但更常见的做法是在本地计算机上工作。为此，我们需要将远程仓库“克隆”（Clone）到本地。

首先，在GitHub仓库页面点击绿色的 “Code” 按钮，选择 “SSH” 选项卡，并复制提供的URL。

![](img/15adab7f9346ac744fdda4d4db73110d_17.png)

![](img/15adab7f9346ac744fdda4d4db73110d_19.png)

然后，打开终端（Terminal），导航到你希望存放代码的目录（例如 `~/git`），执行克隆命令：
```bash
git clone <你复制的SSH_URL>
```
如果这是你第一次使用SSH连接GitHub，可能会遇到权限错误。这是因为SSH认证需要密钥对。

---

## 设置SSH密钥认证

SSH使用非对称加密进行认证，比输入密码更方便、安全。你需要生成一对密钥：私钥（保密）和公钥（可公开）。

![](img/15adab7f9346ac744fdda4d4db73110d_21.png)

![](img/15adab7f9346ac744fdda4d4db73110d_22.png)

![](img/15adab7f9346ac744fdda4d4db73110d_24.png)

在终端中运行以下命令生成密钥：
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
连续按回车接受默认设置。这会在 `~/.ssh/` 目录下生成私钥（`id_ed25519`）和公钥（`id_ed25519.pub`）。

![](img/15adab7f9346ac744fdda4d4db73110d_26.png)

![](img/15adab7f9346ac744fdda4d4db73110d_28.png)

![](img/15adab7f9346ac744fdda4d4db73110d_30.png)

接下来，需要将公钥添加到GitHub账户：
1.  在终端中显示公钥内容：`cat ~/.ssh/id_ed25519.pub`
2.  复制输出的全部内容。
3.  登录GitHub，点击头像 -> “Settings” -> “SSH and GPG keys”。
4.  点击 “New SSH key”，粘贴公钥内容，为其命名（如 “My Laptop”），然后保存。

完成后，重新运行 `git clone` 命令，应该就能成功克隆仓库了。

![](img/15adab7f9346ac744fdda4d4db73110d_32.png)

![](img/15adab7f9346ac744fdda4d4db73110d_34.png)

---

![](img/15adab7f9346ac744fdda4d4db73110d_36.png)

![](img/15adab7f9346ac744fdda4d4db73110d_38.png)

## 使用Tmux管理终端会话

在终端中运行Jupyter Lab等服务时，该终端会被占用。Tmux是一个终端复用器，可以让你在一个窗口内创建多个面板（Pane），并能保持会话在后台运行，即使关闭终端窗口也不会中断进程。

![](img/15adab7f9346ac744fdda4d4db73110d_40.png)

![](img/15adab7f9346ac744fdda4d4db73110d_42.png)

![](img/15adab7f9346ac744fdda4d4db73110d_44.png)

安装Tmux（Ubuntu/Debian）：
```bash
sudo apt install tmux
```
启动Tmux：
```bash
tmux
```
你会看到屏幕底部出现一个状态栏。以下是一些常用快捷键（所有操作先按 `Ctrl+b` 作为前缀）：
*   `%`：垂直分割当前面板。
*   `"`：水平分割当前面板。
*   方向键：在面板间切换焦点。
*   `z`：最大化/恢复当前面板。
*   `d`：分离当前Tmux会话（让它在后台运行）。
*   `tmux attach`：重新连接到后台的Tmux会话。

使用Tmux，你可以在一个面板运行Jupyter，在另一个面板执行Git命令，互不干扰。

---

![](img/15adab7f9346ac744fdda4d4db73110d_46.png)

## 在本地使用Jupyter Lab

![](img/15adab7f9346ac744fdda4d4db73110d_48.png)

在终端中，导航到克隆的仓库目录，然后启动Jupyter Lab：
```bash
jupyter lab
```
终端会输出一个带有令牌（Token）的URL。在浏览器中打开此URL即可访问Jupyter Lab界面。

在Jupyter Lab中，你可以创建新的笔记本（`.ipynb` 文件）或Python脚本。使用 `y` 键将单元格切换为代码模式，使用 `m` 键切换为Markdown模式。编辑完成后，记得为文件起一个清晰的名称。

![](img/15adab7f9346ac744fdda4d4db73110d_50.png)

![](img/15adab7f9346ac744fdda4d4db73110d_52.png)

![](img/15adab7f9346ac744fdda4d4db73110d_54.png)

![](img/15adab7f9346ac744fdda4d4db73110d_55.png)

![](img/15adab7f9346ac744fdda4d4db73110d_57.png)

---

## Git基本工作流程

现在，我们有了本地的代码更改（例如新创建的笔记本），需要将其纳入版本控制并同步到GitHub。

![](img/15adab7f9346ac744fdda4d4db73110d_59.png)

以下是核心的Git命令流程：

1.  **检查状态**：随时使用 `git status` 查看哪些文件被修改或尚未跟踪。
2.  **添加更改**：使用 `git add <文件名>` 将文件放入暂存区（Staging Area），准备提交。例如 `git add sample.ipynb`。
3.  **提交更改**：使用 `git commit -m “提交信息”` 创建一个本地版本记录。提交信息应简洁描述本次更改。
4.  **推送至远程**：使用 `git push` 将本地提交上传到GitHub远程仓库。

![](img/15adab7f9346ac744fdda4d4db73110d_61.png)

完成推送后，刷新你的GitHub仓库页面，就能看到新增的文件了。整个流程可以概括为：**修改 -> 添加 -> 提交 -> 推送**。

---

![](img/15adab7f9346ac744fdda4d4db73110d_63.png)

![](img/15adab7f9346ac744fdda4d4db73110d_65.png)

## Fork与协作

![](img/15adab7f9346ac744fdda4d4db73110d_67.png)

你不仅可以管理自己的仓库，还可以参与他人的项目。Fork（分叉）功能允许你创建某个仓库的个人副本，你可以在副本上自由实验和修改，而不会影响原项目。

![](img/15adab7f9346ac744fdda4d4db73110d_69.png)

![](img/15adab7f9346ac744fdda4d4db73110d_71.png)

![](img/15adab7f9346ac744fdda4d4db73110d_72.png)

![](img/15adab7f9346ac744fdda4d4db73110d_74.png)

在GitHub上找到你感兴趣的项目（如FastAI的 `fastbook` 仓库），点击右上角的 “Fork” 按钮。这会在你的账户下创建一个完全独立的副本。然后，你可以像操作自己的仓库一样克隆、修改和推送这个副本。

![](img/15adab7f9346ac744fdda4d4db73110d_76.png)

![](img/15adab7f9346ac744fdda4d4db73110d_78.png)

![](img/15adab7f9346ac744fdda4d4db73110d_80.png)

如果你想将改进贡献回原项目，可以在你的Fork仓库页面发起 “Pull Request”（拉取请求）。

![](img/15adab7f9346ac744fdda4d4db73110d_82.png)

---

![](img/15adab7f9346ac744fdda4d4db73110d_84.png)

![](img/15adab7f9346ac744fdda4d4db73110d_86.png)

## 总结

![](img/15adab7f9346ac744fdda4d4db73110d_88.png)

本节课我们一起学习了Linux与Git的核心开发流程。我们从创建GitHub仓库开始，配置了SSH密钥以实现安全便捷的认证，并使用Tmux来高效管理终端任务。我们实践了完整的Git工作循环：在本地修改代码，通过 `git add` 和 `git commit` 进行版本控制，最后用 `git push` 同步到远程仓库。此外，我们还了解了如何通过Fork参与开源项目协作。掌握这些工具和流程，将为你的后续学习和项目开发打下坚实的基础。