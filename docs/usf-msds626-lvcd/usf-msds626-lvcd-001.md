# 001：第1讲 - 终端与环境管理 🖥️

![](img/77c40038f6f834cf551b10cd57b2be62_1.png)

![](img/77c40038f6f834cf551b10cd57b2be62_3.png)

在本节课中，我们将学习如何从零开始设置一个高效、无冲突的Python数据科学工作环境。我们将重点介绍终端的使用、Python环境的独立管理，以及如何通过Mamba Forge安装核心工具。

## 概述

数据科学工作流的第一步是建立一个可靠且易于管理的计算环境。一个常见的陷阱是使用系统自带的Python，这会导致库版本冲突和权限问题。本节课将引导你通过终端，使用Mamba Forge创建一个独立的、干净的环境，并安装Jupyter Lab和PyTorch等核心工具。

## 1. 认识终端与Shell

上一节我们介绍了课程目标，本节中我们来看看数据科学家的核心工具之一：终端（Terminal）。

终端是一个程序，它提供了一个文本界面来运行另一个叫做“Shell”的程序。Shell（如Bash或Zsh）才是真正接收并执行你输入命令（如`ls`、`cd`）的组件。虽然我们常将两者混用，但了解其区别是有帮助的。

![](img/77c40038f6f834cf551b10cd57b2be62_5.png)

使用终端而非图形界面（GUI）的优势在于效率与自动化。你可以将一系列操作写入脚本，一键执行，这类似于用语言交流比用手势交流更强大、更精确。

![](img/77c40038f6f834cf551b10cd57b2be62_7.png)

**不同操作系统的启动方式：**
*   **Mac:** 按 `Command + 空格`，搜索“Terminal”并打开。
*   **Windows:** 从Microsoft Store安装“Windows Terminal”。首次启动后，建议安装WSL（Windows Subsystem for Linux）。
*   **Linux:** 通常已预装，可通过应用菜单找到。

![](img/77c40038f6f834cf551b10cd57b2be62_9.png)

![](img/77c40038f6f834cf551b10cd57b2be62_11.png)

![](img/77c40038f6f834cf551b10cd57b2be62_13.png)

对于Windows用户，建议在PowerShell（管理员模式）中运行 `wsl --install` 来安装Ubuntu，并将Ubuntu设置为Windows Terminal的默认配置文件。

## 2. 安装独立的Python环境

我们已经打开了终端，接下来要确保我们使用的是独立的Python环境，而非系统自带的Python。

首先，检查当前Python的路径：
```bash
which python
```
如果返回类似 `/usr/bin/python` 的路径，说明你正在使用系统Python，这不是我们想要的。

![](img/77c40038f6f834cf551b10cd57b2be62_15.png)

我们需要一个安装在用户主目录下的Python。为此，我们选择安装 **Mamba Forge**（一个Conda的快速替代品）。以下是安装步骤：

![](img/77c40038f6f834cf551b10cd57b2be62_17.png)

1.  访问Mamba Forge的GitHub发布页面，找到适合你操作系统（Linux/macOS）的安装脚本链接。
2.  在终端中，使用 `wget` 命令下载该安装脚本。
3.  运行该脚本以完成安装。

![](img/77c40038f6f834cf551b10cd57b2be62_19.png)

![](img/77c40038f6f834cf551b10cd57b2be62_21.png)

在安装过程中，当询问是否“初始化”时，请选择“是”。这样每次打开终端时，环境都会自动激活。

![](img/77c40038f6f834cf551b10cd57b2be62_23.png)

安装完成后，关闭并重新打开终端。你应该能在提示符前看到 `(base)` 字样，这表示你已处于基础环境中。再次运行 `which python`，路径应指向你的用户主目录（如 `/home/yourname/mambaforge/bin/python`）。

![](img/77c40038f6f834cf551b10cd57b2be62_25.png)

![](img/77c40038f6f834cf551b10cd57b2be62_26.png)

![](img/77c40038f6f834cf551b10cd57b2be62_28.png)

## 3. 使用Mamba管理包

环境设置好后，我们就可以用Mamba来安装和管理软件包了。Mamba与Conda命令兼容，但速度更快。

![](img/77c40038f6f834cf551b10cd57b2be62_30.png)

![](img/77c40038f6f834cf551b10cd57b2be62_32.png)

![](img/77c40038f6f834cf551b10cd57b2be62_34.png)

**核心命令是 `mamba install`**。例如，安装一个交互式Python环境（IPython）：
```bash
mamba install ipython
```
Mamba会解析依赖关系并征得你的同意后开始安装。安装完成后，输入 `ipython` 即可进入交互模式。

![](img/77c40038f6f834cf551b10cd57b2be62_36.png)

![](img/77c40038f6f834cf551b10cd57b2be62_38.png)

![](img/77c40038f6f834cf551b10cd57b2be62_40.png)

![](img/77c40038f6f834cf551b10cd57b2be62_42.png)

**为什么优先使用Mamba/Conda而非pip？**
*   **管理二进制依赖：** Mamba能处理非Python的库（如CUDA驱动），安装更完整。
*   **环境隔离：** 轻松创建独立环境，避免项目间的包冲突。
*   **可靠性：** 对于PyTorch等复杂库，通过指定频道（如 `-c pytorch`）安装更可靠。

![](img/77c40038f6f834cf551b10cd57b2be62_44.png)

![](img/77c40038f6f834cf551b10cd57b2be62_46.png)

若要安装PyTorch（CPU版本），可以复制官网提供的Conda命令，并将开头的 `conda` 替换为 `mamba`：
```bash
mamba install pytorch torchvision torchaudio cpuonly -c pytorch
```

## 4. 安装与运行Jupyter Lab

![](img/77c40038f6f834cf551b10cd57b2be62_48.png)

![](img/77c40038f6f834cf551b10cd57b2be62_50.png)

对于数据科学工作，Jupyter Lab是一个强大的交互式笔记本环境。

![](img/77c40038f6f834cf551b10cd57b2be62_52.png)

使用Mamba安装Jupyter Lab：
```bash
mamba install jupyterlab
```
安装完成后，为了组织文件，建议先创建一个专用目录：
```bash
mkdir nbs
cd nbs
```
然后启动Jupyter Lab。为了避免它自动打开浏览器可能产生的问题，可以加上 `--no-browser` 参数：
```bash
jupyter lab --no-browser
```
启动后，终端会显示一个本地URL（如 `http://localhost:8888/lab`）。你可以按住 `Ctrl` 键并点击该链接，在浏览器中打开Jupyter Lab界面。

![](img/77c40038f6f834cf551b10cd57b2be62_54.png)

## 5. 提高效率的技巧

![](img/77c40038f6f834cf551b10cd57b2be62_56.png)

![](img/77c40038f6f834cf551b10cd57b2be62_58.png)

![](img/77c40038f6f834cf551b10cd57b2be62_60.png)

为了提升日常使用效率，这里有一些实用技巧：

![](img/77c40038f6f834cf551b10cd57b2be62_62.png)

**终端操作技巧：**
*   **Tab键自动补全：** 输入命令或路径的前几个字母后按Tab键。
*   **上下箭头：** 翻阅历史命令。
*   **Ctrl + R：** 反向搜索历史命令。
*   **Ctrl + A / Ctrl + E：** 快速跳转到命令行的开头或结尾。
*   **Ctrl + D：** 退出当前程序（如IPython或Shell）。

**创建命令别名：**
如果觉得 `jupyter lab --no-browser` 太长，可以为其创建一个别名（alias）：
```bash
alias jl='jupyter lab --no-browser'
```
但这样设置的别名只在当前会话有效。若要永久生效，需要将这条别名命令添加到Shell的配置文件中（如 `~/.bashrc` 或 `~/.zshrc`）。这样每次打开新终端时，都可以直接输入 `jl` 来启动Jupyter Lab。

![](img/77c40038f6f834cf551b10cd57b2be62_64.png)

![](img/77c40038f6f834cf551b10cd57b2be62_66.png)

![](img/77c40038f6f834cf551b10cd57b2be62_68.png)

## 总结

![](img/77c40038f6f834cf551b10cd57b2be62_70.png)

![](img/77c40038f6f834cf551b10cd57b2be62_72.png)

![](img/77c40038f6f834cf551b10cd57b2be62_74.png)

![](img/77c40038f6f834cf551b10cd57b2be62_76.png)

![](img/77c40038f6f834cf551b10cd57b2be62_78.png)

![](img/77c40038f6f834cf551b10cd57b2be62_80.png)

本节课中我们一起学习了数据科学环境搭建的“正确打开方式”。我们从认识终端开始，逐步完成了使用Mamba Forge安装独立Python环境、用Mamba管理包（以IPython和PyTorch为例）、安装并启动Jupyter Lab，最后还介绍了一些提升终端使用效率的技巧。关键在于将用户环境与系统环境分离，并优先使用Mamba进行包管理，这能为后续平滑、无冲突的学习和实践打下坚实基础。