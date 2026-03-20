# 001：课程概述与Shell介绍 🚀

## 概述
在本节课中，我们将学习“编程缺失主题”课程的总体介绍，并深入探讨Shell（命令行界面）的基础知识。Shell是计算机的文本接口，是程序员和系统管理员的核心工具。我们将了解它的基本概念、常用命令以及如何组合命令来执行复杂任务。

## 课程介绍
“编程缺失主题”这门课程最初于2019年开设，并在2020年再次运行。由于许多学生发现这门课程非常有用，并且自上次开课以来技术环境发生了变化，我们决定再次开设这门课。

我们三位讲师都是麻省理工学院的校友，在攻读博士学位期间都曾教授过许多课程。我们经常发现，在答疑时间中，我们教授的内容往往不是课程的核心主题，而是如何使用Shell、如何高效使用文本编辑器等工具和技巧。因此，我们决定将这些主题单独提炼出来，开设一门专门的课程，以便学生能在答疑时间专注于课程的核心内容。

这门课程的目标是覆盖那些构成幕后知识主体的工具、技术和概念。这些知识通常是其他课程（如编译器或算法课）所不教的，但却是高效使用计算机环境、自动化任务的关键。我们希望通过这门课，让大家了解有哪些工具可用，以及在需要时如何找到并使用它们。

课程共有九次一小时的讲座。时间有限，我们无法深入讲解所有工具或技术的细节。我们的方法更像是“接触疗法”——向大家展示什么是可能的，以及你应该了解哪些工具。我们鼓励大家通过课后练习和自行探索来深入学习。

## Shell是什么？
计算机有多种交互界面。我们最熟悉的是图形用户界面（GUI），通过鼠标点击进行操作。GUI虽然好用，但通常局限于程序作者设计的功能，并且很难将不同程序的功能组合起来。

Shell是计算机的文本接口，它允许你直接输入命令，并获取命令的输出结果。它运行在终端（Terminal）的环境中。终端可以看作是一个GUI窗口，而Shell则是运行在这个窗口内的程序。

*   **打开终端**：
    *   **Linux**：通常按 `Ctrl+Alt+T`，或在应用启动器中搜索“terminal”。
    *   **Windows**：按 `Win+R`，输入 `cmd` 或 `powershell`。
    *   **macOS**：按 `Cmd+Space` 打开聚焦搜索，搜索“terminal”。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_1.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_2.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_4.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_5.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_6.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_8.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_9.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_10.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_11.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_13.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_14.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_15.png)

*   **常见的Shell**：
    *   **Bash (Bourne Again SHell)**：Linux系统上最常见的Shell，macOS过去也使用它。
    *   **Zsh (Z Shell)**：现在是macOS和一些Linux发行版的默认Shell。它与Bash兼容，并提供了许多人性化改进和功能增强。
    *   **Fish**：另一个旨在提供更好命令行体验的Shell。
    *   **Windows**：有 `cmd` (命令提示符) 和 `PowerShell`。它们的语法与Bash系Shell不同。在本课程中，我们将主要关注Bash及其衍生版本（如Zsh）。如果你使用Windows，建议安装WSL（Windows Subsystem for Linux）或Linux虚拟机来获得完整的Bash环境。

## 为什么使用Shell？
*   **效率**：一旦熟悉，用键盘输入命令通常比用鼠标点击更快，尤其是对于复杂任务。
*   **自动化**：Shell本质上是一种编程语言。你可以在命令行编写脚本，自动执行重复性任务。
*   **组合性**：Shell非常适合将多个程序组合起来，将一个程序的输出作为另一个程序的输入，形成强大的处理流水线。
*   **开源社区与工作流**：许多开源工具的安装、构建说明都基于Shell命令。在工业界，软件构建、测试和部署的流水线配置也广泛使用Shell脚本。
*   **理解与安全**：了解常用命令的作用，可以让你更安全、更明白地执行从网上找到的指令，而不是盲目复制粘贴。

## Shell基础
当你打开终端时，会看到一个**提示符（Prompt）**。它通常显示用户名、主机名和当前工作目录等信息，并等待你输入命令。

**运行命令**：最简单的命令就是输入一个程序名。例如，输入 `date` 会打印当前日期。命令后可以跟**参数（Arguments）**，参数之间用空格分隔。例如，`echo hello world` 会打印“hello world”。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_17.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_19.png)

**参数解析**：Shell会将你输入的文本在空格处分割成多个部分，第一部分作为要执行的程序名，其余部分作为参数传递给该程序。如果参数本身包含空格，需要使用引号（单引号 `'` 或双引号 `"`）将其括起来，或者使用反斜杠 `\` 进行转义。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_21.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_22.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_24.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_25.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_27.png)

**获取帮助**：
*   `man <command>`：查看命令的详细手册页。例如 `man echo`。
*   `<command> --help` 或 `-h`：通常可以获取命令的简要帮助信息。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_29.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_31.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_32.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_33.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_35.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_36.png)

## 在文件系统中导航
*   `pwd`：打印当前工作目录。
*   `cd <path>`：更改当前工作目录到指定路径。
*   `ls <path>`：列出指定目录的内容。如果不指定路径，则列出当前目录。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_38.png)

**路径类型**：
*   **绝对路径**：从根目录 `/` 开始，如 `/home/user/docs`。
*   **相对路径**：相对于当前目录。
    *   `.` 表示当前目录。
    *   `..` 表示父目录。
    *   `~` 表示当前用户的家目录。
*   **路径组合**：可以使用 `/` 分隔路径组件，例如 `cd ../project/src`。

**高效导航技巧**：
*   **Tab键自动补全**：输入路径或命令的前几个字母，按 `Tab` 键可以自动补全。如果存在多个可能选项，按两次 `Tab` 会显示所有选项。
*   **工具**：可以使用像 `zoxide` 这样的工具来快速跳转到常用目录。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_40.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_42.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_44.png)

## 程序与PATH
当你输入一个命令（如 `date`）时，Shell如何知道该执行哪个程序？它通过一个叫做 **`PATH`** 的环境变量来查找。

*   `echo $PATH`：查看 `PATH` 变量的内容，它是一系列用冒号 `:` 分隔的目录路径。
*   `which <command>`：显示Shell将执行哪个路径下的命令。例如 `which date`。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_46.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_47.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_48.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_50.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_52.png)

Shell会按照 `PATH` 中列出的目录顺序，查找与命令名同名的可执行文件，并执行找到的第一个。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_54.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_56.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_58.png)

## 常用命令示例
以下是一些在Shell中非常有用的命令：

![](img/14b6ec9561a61d0e95daa708f4cbeae2_60.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_61.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_63.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_65.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_66.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_67.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_69.png)

*   `cat <file>`：连接文件并打印其内容到标准输出。
*   `sort <file>`：对文件的行进行排序。
*   `uniq <file>`：报告或省略重复的行（通常与 `sort` 结合使用，因为 `uniq` 只处理相邻的重复行）。
*   `head/tail <file>`：显示文件的开头或结尾部分（默认10行）。可以使用 `-n` 指定行数，如 `head -n 5 file.txt`。
*   `grep <pattern> <file>`：在文件中搜索匹配指定模式的行。模式支持**正则表达式**，功能强大。
    *   `-r`：递归搜索目录。
*   `sed`：流编辑器，用于对输入流（或文件）执行基本的文本转换。常用于搜索和替换。
    *   例如：`sed -i 's/old/new/g' file.txt` 将文件中所有的“old”替换为“new”。
*   `find <path> <expression>`：在目录树中查找文件。功能非常强大，可以根据名称、类型、大小、修改时间等条件进行搜索。
    *   例如：`find . -name "*.txt" -type f` 查找当前目录下所有 `.txt` 文件。
    *   可以与 `-exec` 结合，对找到的每个文件执行命令。例如：`find . -name "*.tmp" -exec rm {} \;` 删除所有 `.tmp` 文件。
*   `awk`：一种用于文本处理的编程语言和工具。它特别适合处理按列（字段）组织的数据。
    *   默认按空白字符（空格、制表符）分割行。例如 `awk '{print $2}' file.txt` 会打印每行的第二个字段。
    *   可以指定字段分隔符，例如 `awk -F',' '{print $1}' data.csv` 处理CSV文件。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_71.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_72.png)

## 组合命令与重定向
Shell的强大之处在于能够将简单的命令组合起来。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_74.png)

*   **管道（Pipe） `|`**：将一个命令的输出作为另一个命令的输入。
    *   例如：`history | grep git | tail -n 5` 先获取命令历史，然后过滤出包含“git”的行，最后显示最后5行。
*   **输出重定向 `>` 和 `>>`**：将命令的输出写入文件，而不是显示在终端。
    *   `command > file.txt`：将输出写入文件（覆盖原有内容）。
    *   `command >> file.txt`：将输出追加到文件末尾。
*   **输入重定向 `<`**：从文件读取数据作为命令的输入，而不是从键盘。
    *   例如：`sort < data.txt`。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_76.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_78.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_79.png)

## Shell脚本编程
当命令变得复杂时，可以将它们写入一个文件，形成一个**Shell脚本**。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_80.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_82.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_84.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_85.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_86.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_88.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_90.png)

**创建脚本**：
1.  创建一个新文件，例如 `myscript.sh`。
2.  在文件第一行添加 **shebang** 行，指定解释器：`#!/bin/bash`。
3.  在下面编写你的Shell命令。
4.  保存文件。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_92.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_94.png)

**使脚本可执行**：
```bash
chmod +x myscript.sh
```
**运行脚本**：
```bash
./myscript.sh
```
注意：运行当前目录下的脚本需要使用 `./` 前缀，否则Shell会在 `PATH` 中查找，而通常当前目录不在 `PATH` 中（这是出于安全考虑）。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_96.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_98.png)

**脚本中的控制结构**：
Shell脚本支持 `if`、`while`、`for` 等控制结构。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_100.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_102.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_103.png)

*   **条件判断**：通常使用 `test` 命令或其别名 `[`。
    *   例如：`if [ "$name" = "Alice" ]; then echo "Hi Alice!"; fi`
    *   更多条件测试（如检查文件是否存在 `-f`，检查目录是否存在 `-d`）请参考 `man test`。
*   **循环**：
    *   `for` 循环：`for i in 1 2 3; do echo $i; done`
    *   可以使用命令生成序列：`for i in $(seq 1 5); do echo $i; done`
    *   `while` 循环：`while true; do echo "Looping..."; sleep 1; done`

![](img/14b6ec9561a61d0e95daa708f4cbeae2_105.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_107.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_109.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_111.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_113.png)

## 总结
本节课我们一起学习了Shell的基础知识。我们了解了什么是Shell以及为什么它如此重要。我们学习了如何在文件系统中导航、如何运行程序、如何使用 `PATH` 变量。我们介绍了一系列强大的命令行工具，如 `grep`、`find`、`sed` 和 `awk`，并学习了如何通过管道和重定向将它们组合起来。最后，我们了解了如何将一系列命令保存为Shell脚本，并使其可执行，从而实现任务的自动化。

![](img/14b6ec9561a61d0e95daa708f4cbeae2_115.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_116.png)

![](img/14b6ec9561a61d0e95daa708f4cbeae2_118.png)

Shell是一个极其强大的环境，掌握它将极大地提升你的工作效率和对计算机的控制能力。请务必完成课程提供的练习，这是巩固知识的最佳方式。下一节课，我们将深入探讨命令行环境本身，包括终端配置、作业控制、远程连接等内容。