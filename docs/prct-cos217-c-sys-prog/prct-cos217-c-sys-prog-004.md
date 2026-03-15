# 004：Git入门与作业0设置指南 🚀

![](img/48899ad9c6213f5ec6b0911a0afcf35f_1.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_3.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_5.png)

在本节课中，我们将学习如何为COS 217课程作业设置Git和GitHub环境。本教程将详细介绍作业0中第2步到第5步的操作流程，帮助你配置Git、创建GitHub账户、建立仓库以及导入课程提供的初始代码库。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_7.png)

## 概述

![](img/48899ad9c6213f5ec6b0911a0afcf35f_9.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_10.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_12.png)

本教程将指导你完成以下核心步骤：
1.  在本地配置Git。
2.  创建并验证GitHub账户。
3.  创建你的第一个私有GitHub仓库。
4.  学习基本的Git命令（`init`, `add`, `commit`, `push`, `pull`, `clone`）。
5.  将课程提供的作业初始代码库导入到你自己的私有仓库中。

---

## 第2步：配置本地Git环境 ⚙️

上一节我们介绍了本教程的目标，本节中我们来看看如何配置你的本地Git环境。首先，你需要确保Git已安装在你的计算机上。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_14.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_15.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_17.png)

### 检查Git安装
在终端中运行以下命令来检查Git是否已安装：
```bash
git --version
```
如果系统返回了Git的版本号，说明Git已安装。如果未安装，请根据你的操作系统（Mac、Windows或Linux）按照Git官网的指引进行安装。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_19.png)

### 配置Git用户信息
安装Git后，你需要配置你的用户名和邮箱。这些信息将与你未来的每一次代码提交（commit）关联。你只需要配置一次。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_21.png)

以下是配置命令：
```bash
git config --global user.name "你的姓名"
git config --global user.email "你的邮箱"
git config --global color.ui auto
git config --global core.editor "你喜欢的编辑器命令（如：vim, nano, emacs）"
```
*   `--global` 参数表示此配置将应用于你在这台电脑上的所有Git仓库。
*   `user.name` 和 `user.email` 用于标识提交者。
*   `color.ui auto` 让Git在终端中输出彩色信息，便于阅读。
*   `core.editor` 设置Git使用的默认文本编辑器，用于编写提交信息等。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_23.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_25.png)

### 验证配置
配置完成后，你可以使用以下命令查看所有配置项：
```bash
git config --list
```
此命令会列出包括你刚才设置的所有Git配置。这些配置实际上保存在你的用户主目录下的 `.gitconfig` 文件中。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_27.png)

---

## 第3步：创建GitHub账户 👤

![](img/48899ad9c6213f5ec6b0911a0afcf35f_29.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_31.png)

上一节我们完成了本地Git的配置，本节中我们来看看如何创建GitHub账户。GitHub是一个基于Web的Git仓库托管服务，我们将用它来存储和管理作业代码。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_33.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_35.png)

### 注册账户
1.  访问 [GitHub官网](https://github.com)。
2.  点击“Sign up”按钮。
3.  按照页面提示，输入你的用户名、邮箱和密码。
4.  完成人机验证（例如，选择图片中的特定物体）。
5.  选择免费计划（Free plan）。
6.  你可以跳过后续的个人信息调查，直接完成设置。

### 验证邮箱
注册后，GitHub会向你提供的邮箱发送一封验证邮件。请登录你的邮箱，点击邮件中的验证链接以激活你的GitHub账户。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_37.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_38.png)

---

## 第4步：创建你的第一个GitHub仓库并学习基础操作 📂

![](img/48899ad9c6213f5ec6b0911a0afcf35f_40.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_42.png)

现在你已拥有GitHub账户，本节我们将学习如何创建一个私有仓库，并掌握最基本的Git工作流程：在本地修改代码，然后推送到远程仓库。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_44.png)

### 创建新仓库
1.  登录GitHub，点击页面右上角的 “+” 图标，选择 “New repository”。
2.  为仓库命名（例如 `step4-test`）。
3.  **重要：** 选择 “Private”（私有）。本课程的所有作业仓库都必须是私有的，以防止你的解决方案公开。
4.  暂时不需要勾选 “Initialize this repository with a README” 等选项，直接点击 “Create repository”。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_46.png)

### 本地操作与远程同步
创建仓库后，GitHub会显示指引。我们将在本地终端中操作：

![](img/48899ad9c6213f5ec6b0911a0afcf35f_48.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_50.png)

1.  **创建本地目录并初始化Git仓库：**
    ```bash
    mkdir step4-test
    cd step4-test
    git init
    ```
    `git init` 命令将这个目录初始化为一个Git仓库，创建一个隐藏的 `.git` 文件夹来存储所有版本控制数据。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_52.png)

2.  **创建文件并添加到暂存区：**
    ```bash
    echo “# My First Repo” > README.md
    git add README.md
    ```
    `git add` 命令将文件添加到“暂存区”（staging area），表示你准备将这些更改保存下来。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_54.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_56.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_58.png)

3.  **提交更改到本地仓库：**
    ```bash
    git commit -m “Add README file”
    ```
    `git commit` 命令将暂存区的更改正式保存到本地仓库的历史记录中。`-m` 参数后面是本次提交的说明信息。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_60.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_62.png)

4.  **将本地仓库链接到远程GitHub仓库：**
    ```bash
    git remote add origin https://github.com/你的用户名/step4-test.git
    ```
    这条命令为你本地的仓库添加了一个名为 `origin` 的远程地址，指向你刚刚在GitHub上创建的仓库。

5.  **将本地提交推送到远程仓库：**
    ```bash
    git push -u origin main
    ```
    `git push` 命令将你本地的提交上传到远程仓库（GitHub）。`-u` 参数设置了上游分支，以后可以直接使用 `git push`。

### 在另一台机器（如课程服务器）上获取代码
假设你需要在课程服务器（如armlab）上工作，你可以通过 `git clone` 命令轻松获取代码：
```bash
git clone https://github.com/你的用户名/step4-test.git
cd step4-test
```
这会在服务器上创建一份仓库的完整副本。

### 同步更改
这是一个典型的双向工作流程：
*   **从本地推送到远程/服务器：** 在本地 `commit` 后，使用 `git push`。
*   **从远程/服务器拉取到本地：** 在另一处使用 `git pull` 来获取最新的更改。

---

![](img/48899ad9c6213f5ec6b0911a0afcf35f_64.png)

## 第5步：导入课程作业仓库（镜像仓库） 🧩

![](img/48899ad9c6213f5ec6b0911a0afcf35f_66.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_68.png)

上一节我们学习了管理自己仓库的基础操作，本节中我们来看看如何获取课程提供的作业初始代码。你不能直接向课程的公共仓库提交代码，而是需要将其“复制”到你自己的私有仓库中，这个过程称为“镜像”或“导入”。

### 使用Git命令导入
以下是标准步骤：

![](img/48899ad9c6213f5ec6b0911a0afcf35f_70.png)

1.  **裸克隆课程仓库：** 这只会下载仓库的元数据（历史、分支等），不包含实际的工作文件。
    ```bash
    git clone --bare https://github.com/COS217/assignment-repository.git
    ```
    这会在当前目录创建一个名为 `assignment-repository.git` 的文件夹。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_72.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_74.png)

2.  **在GitHub上创建新的私有仓库：** 例如，命名为 `my-assignment-repo`。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_76.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_77.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_79.png)

3.  **将裸克隆的仓库镜像推送到你的新仓库：**
    ```bash
    cd assignment-repository.git
    git push --mirror https://github.com/你的用户名/my-assignment-repo.git
    ```
    `--mirror` 参数会推送所有分支、标签和提交历史，完整地复制整个仓库。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_81.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_83.png)

4.  **克隆你自己的新仓库到本地开始工作：**
    ```bash
    cd ..
    git clone https://github.com/你的用户名/my-assignment-repo.git
    cd my-assignment-repo
    ```
    现在，你本地就有了一个包含课程初始代码的私有仓库副本，你可以在此基础之上开始你的作业，并使用第4节学习的 `push` 和 `pull` 命令来同步代码。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_85.png)

![](img/48899ad9c6213f5ec6b0911a0afcf35f_87.png)

---

![](img/48899ad9c6213f5ec6b0911a0afcf35f_89.png)

## 总结 🎯

本节课我们一起学习了为COS 217课程设置Git和GitHub的完整流程：
1.  我们配置了本地Git环境，设置了用户信息。
2.  我们创建并验证了GitHub账户。
3.  我们创建了第一个私有GitHub仓库，并练习了 `init`、`add`、`commit`、`push`、`pull`、`clone` 等核心Git命令。
4.  我们掌握了如何将课程提供的公共作业仓库镜像导入到自己的私有仓库中，为开始实际编程工作做好了准备。

![](img/48899ad9c6213f5ec6b0911a0afcf35f_91.png)

通过这套流程，你可以轻松地在个人电脑和课程服务器之间同步代码，并基于课程提供的框架开始你的作业开发。