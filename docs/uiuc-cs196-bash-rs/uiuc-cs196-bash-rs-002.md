# 002：Bash 第二部分 🐚

![](img/980cd4b18c5b1a14d5de6db97818aefd_1.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_3.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_5.png)

在本节课中，我们将继续学习Bash，构建于上一讲的知识之上。我们将介绍几个新的命令，然后超越单个命令，学习如何进行批处理脚本编写和在终端内编辑文本文件等更酷的操作。

## 概述 📋

本节课的目标是学习以下内容：
1.  几个新的Bash命令：`sudo`, `find`, `grep`, `diff`。
2.  终端文本编辑器：`vim`, `emacs`, `nano`。
3.  Bash脚本编程入门：变量、条件语句、循环和函数。
4.  命令别名。

![](img/980cd4b18c5b1a14d5de6db97818aefd_7.png)

我们将逐一深入探讨这些主题。

![](img/980cd4b18c5b1a14d5de6db97818aefd_9.png)

## 命令学习

![](img/980cd4b18c5b1a14d5de6db97818aefd_11.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_13.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_15.png)

上一节我们学习了基本的文件操作命令，本节中我们来看看几个更强大的工具。

![](img/980cd4b18c5b1a14d5de6db97818aefd_17.png)

### `sudo` 命令 🔑

`sudo` 代表“超级用户执行”。它为你提供计算机的根用户访问权限。根用户权限等同于管理员权限，你可以将根用户视为计算机的最高统治者，可以执行任何操作。

![](img/980cd4b18c5b1a14d5de6db97818aefd_19.png)

使用 `sudo` 需要谨慎，因为强大的能力也意味着重大的责任。你可以用它删除核心文件，因此使用时必须非常小心。

![](img/980cd4b18c5b1a14d5de6db97818aefd_21.png)

大多数日常操作（如列出目录文件）并不需要根权限，所以不必在每个命令前都使用 `sudo`。

以下是使用 `sudo` 的基本格式：
```bash
sudo [命令]
```
例如，要删除一个受保护的文件：
```bash
sudo rm protected_file.txt
```
输入命令后，系统会提示你输入密码。在终端输入密码时，屏幕上不会显示任何字符，这是为了保护你的密码安全。

![](img/980cd4b18c5b1a14d5de6db97818aefd_23.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_24.png)

### `find` 命令 🔍

![](img/980cd4b18c5b1a14d5de6db97818aefd_26.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_27.png)

`find` 是一个用于定位文件的强大工具。找到文件后，你还可以对这些文件执行命令。

![](img/980cd4b18c5b1a14d5de6db97818aefd_29.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_31.png)

基本用法是输入 `find`，后跟一个路径。它会递归地列出该路径下所有目录中的文件。
```bash
find .
```
上述命令会列出当前目录（`.`）及其所有子目录中的文件，包括隐藏文件。

![](img/980cd4b18c5b1a14d5de6db97818aefd_33.png)

为了更精确地查找，我们可以使用一些标志来改变 `find` 的行为。

以下是 `find` 命令的一些常用标志：
*   **`-name`**: 按文件名查找。可以使用通配符 `*` 进行模式匹配。
    *   示例：`find . -name "*.txt"` 查找当前目录下所有 `.txt` 文件。
*   **`-iname`**: 不区分大小写地按文件名查找。
    *   示例：`find . -iname "README"` 会找到 `README`、`readme`、`ReadMe` 等文件。
*   **`-delete`**: 删除找到的文件。**使用此标志需极其谨慎**。
    *   示例：`find . -name "temp_*.log" -delete` 会删除所有匹配 `temp_*.log` 模式的文件。

![](img/980cd4b18c5b1a14d5de6db97818aefd_35.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_37.png)

**重要提示**：在终端中使用 `rm` 或 `find -delete` 删除的文件不会进入回收站，而是被永久删除，无法撤销。

### `grep` 命令 📖

![](img/980cd4b18c5b1a14d5de6db97818aefd_39.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_41.png)

`grep` 代表“全局正则表达式打印”，用于在文件中搜索文本。

基本用法是输入 `grep`，后跟要搜索的术语和文件名。`grep` 会返回包含该术语的所有行。
```bash
grep "搜索词" 文件名.txt
```
例如，在一个包含多行文本的文件中搜索 “Rohan”，会输出所有包含 “Rohan” 的行，即使是作为长单词的一部分（如 “RohanAndSammy”）也会被匹配。

![](img/980cd4b18c5b1a14d5de6db97818aefd_43.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_45.png)

为了进行更精确的搜索，`grep` 提供了几个有用的标志。

![](img/980cd4b18c5b1a14d5de6db97818aefd_47.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_49.png)

以下是 `grep` 命令的一些常用标志：
*   **`-w`**: 仅匹配整个单词，而不是单词的一部分。
*   **`-i`**: 使搜索不区分大小写。
*   **`-n`**: 显示匹配行所在的行号。

这些标志可以组合使用。例如，`grep -wi "rohan" file.txt` 会进行不区分大小写的全词匹配搜索。

![](img/980cd4b18c5b1a14d5de6db97818aefd_51.png)

### `diff` 命令 ⚖️

`diff` 命令用于比较两个文件，并逐行标识它们之间的差异。

![](img/980cd4b18c5b1a14d5de6db97818aefd_53.png)

用法是输入 `diff`，后跟两个文件名。
```bash
diff file1.txt file2.txt
```
如果文件完全相同，则没有输出。如果存在差异，`diff` 会输出哪些行不同。差异输出中，`<` 表示第一个文件的行，`>` 表示第二个文件的行。空行也被视为差异。

### 逻辑运算符 ⛓️

![](img/980cd4b18c5b1a14d5de6db97818aefd_55.png)

逻辑运算符允许你将多个 Bash 命令串联在一起执行。

![](img/980cd4b18c5b1a14d5de6db97818aefd_57.png)

使用 `&&`（逻辑与）可以连接命令。其含义是：只有前一个命令成功执行（返回退出状态码0），后一个命令才会执行。
```bash
命令1 && 命令2 && 命令3
```
例如：
```bash
mkdir new_dir && cd new_dir && touch some_file.txt && cd ..
```
这条命令会依次执行：创建目录、进入目录、创建文件、返回上级目录。这样做的好处是，你可以通过按上箭头键轻松地重复执行这一系列命令，而不必逐个输入。

### `ssh` 命令 🌐

![](img/980cd4b18c5b1a14d5de6db97818aefd_59.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_61.png)

`ssh`（安全外壳协议）用于访问和控制远程计算机的终端。

![](img/980cd4b18c5b1a14d5de6db97818aefd_62.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_63.png)

这在连接虚拟机或服务器时非常有用。基本用法是：
```bash
ssh 用户名@主机地址
```
例如：`ssh user@server.example.com`。连接后，会提示输入密码，成功验证后，你的终端就连接到了远程机器，可以执行命令。要退出远程连接，输入 `exit`。

## 终端文本编辑器 ✏️

当你通过 `ssh` 连接到远程机器时，通常无法使用图形界面的文本编辑器。这时就需要在终端内直接编辑文件的工具。

![](img/980cd4b18c5b1a14d5de6db97818aefd_65.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_67.png)

### `vim` 编辑器

![](img/980cd4b18c5b1a14d5de6db97818aefd_69.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_71.png)

`vim` 是一个功能强大但学习曲线较陡峭的终端编辑器。要打开文件，使用 `vim 文件名`。

![](img/980cd4b18c5b1a14d5de6db97818aefd_73.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_75.png)

`vim` 有多种模式，最常用的是：
*   **命令模式**：打开 `vim` 时的默认模式，可以执行导航、删除、搜索等命令，但不能直接输入文本。
*   **插入模式**：可以像普通编辑器一样输入和编辑文本。

![](img/980cd4b18c5b1a14d5de6db97818aefd_77.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_79.png)

在命令模式下，可以使用以下按键导航（而非箭头键）：
*   `h` (左), `j` (下), `k` (上), `l` (右)
*   `$` 跳到行尾，`0` 跳到行首
*   `w` 向前移动一个单词，`b` 向后移动一个单词
*   `/搜索词` 搜索文件内容

![](img/980cd4b18c5b1a14d5de6db97818aefd_81.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_83.png)

要从命令模式进入插入模式，按 `i`。要从插入模式返回命令模式，按 `Esc`。

![](img/980cd4b18c5b1a14d5de6db97818aefd_85.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_87.png)

要保存并退出 `vim`，在命令模式下输入：
*   `:wq` 保存并退出
*   `:q!` 不保存强制退出

### `emacs` 编辑器

![](img/980cd4b18c5b1a14d5de6db97818aefd_89.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_91.png)

`emacs` 是另一个流行的终端编辑器。与 `vim` 不同，它没有严格区分模式，主要通过组合键（前缀）来执行命令。

![](img/980cd4b18c5b1a14d5de6db97818aefd_93.png)

打开文件使用 `emacs 文件名`。打开后可以直接输入文本。

![](img/980cd4b18c5b1a14d5de6db97818aefd_95.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_97.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_98.png)

常用组合键包括：
*   `Ctrl-a` / `Ctrl-e`: 移动到行首/行尾
*   `Ctrl-v` / `Alt-v`: 向下/向上翻页
*   `Alt-f` / `Alt-b`: 向前/向后移动一个单词
*   `Ctrl-x Ctrl-s`: 保存文件
*   `Ctrl-x Ctrl-c`: 退出 `emacs`

![](img/980cd4b18c5b1a14d5de6db97818aefd_100.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_101.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_103.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_105.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_106.png)

在 Mac 上，`Alt` 键通常对应 `Option` 键，但可能需要额外配置终端才能正常使用。

![](img/980cd4b18c5b1a14d5de6db97818aefd_108.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_110.png)

### `nano` 编辑器

![](img/980cd4b18c5b1a14d5de6db97818aefd_112.png)

`nano` 是三者中最易上手的终端编辑器，学习曲线平缓。

![](img/980cd4b18c5b1a14d5de6db97818aefd_114.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_116.png)

打开文件使用 `nano 文件名`。编辑器底部会显示所有常用命令的提示（如 `^O` 保存，`^X` 退出）。

![](img/980cd4b18c5b1a14d5de6db97818aefd_118.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_120.png)

在 `nano` 中，你可以直接输入文本，使用箭头键导航。要执行操作，使用 `Ctrl` 加字母键（如 `Ctrl-O` 保存，`Ctrl-X` 退出）。退出时如果有未保存的更改，会提示你是否保存。

![](img/980cd4b18c5b1a14d5de6db97818aefd_122.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_124.png)

对于只需要进行少量快速编辑的情况，`nano` 是一个极佳的选择。

![](img/980cd4b18c5b1a14d5de6db97818aefd_126.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_128.png)

## Bash 脚本编程入门 📜

![](img/980cd4b18c5b1a14d5de6db97818aefd_130.png)

除了手动输入命令，你还可以编写脚本来自动化执行一系列命令。Bash 脚本通常以 `.sh` 扩展名结尾，使用 `bash 脚本名.sh` 来运行。

### 变量

![](img/980cd4b18c5b1a14d5de6db97818aefd_132.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_134.png)

在 Bash 中声明变量很简单，直接赋值即可，无需指定类型。注意，等号 `=` 两边不能有空格。
```bash
变量名=值
```
要使用变量的值，需要在变量名前加上美元符号 `$`。
```bash
my_var="Hello"
echo $my_var
echo "The value is $my_var"
```
如果要原样输出 `$` 符号，可以使用单引号 `'`，因为单引号内的所有字符都会按字面意义解释。

![](img/980cd4b18c5b1a14d5de6db97818aefd_136.png)

### 条件语句

![](img/980cd4b18c5b1a14d5de6db97818aefd_138.png)

Bash 中的条件语句使用 `if`、`elif`、`else` 结构，以 `fi` 结束。

**重要**：条件表达式必须放在方括号 `[ ]` 内，并且括号与表达式之间必须有空格。
```bash
if [ 条件1 ]
then
    # 执行语句
elif [ 条件2 ]
then
    # 执行语句
else
    # 执行语句
fi
```
比较数字时，使用 `-eq`（等于）、`-ne`（不等于）等操作符。
```bash
if [ $num -eq 10 ]
then
    echo "数字是10"
fi
```

![](img/980cd4b18c5b1a14d5de6db97818aefd_140.png)

### 循环

![](img/980cd4b18c5b1a14d5de6db97818aefd_142.png)

`for` 循环的基本格式如下：
```bash
for 变量 in 序列
do
    # 循环体
done
```
例如，打印数字1到5：
```bash
for i in 1 2 3 4 5
do
    echo "循环次数: $i"
done
```
也可以使用 `{1..5}` 这种形式生成数字序列。

![](img/980cd4b18c5b1a14d5de6db97818aefd_144.png)

### 函数

![](img/980cd4b18c5b1a14d5de6db97818aefd_146.png)

定义函数时，使用函数名后跟括号 `()` 的形式，函数体放在 `{ }` 中。
```bash
函数名() {
    # 函数体
}
```
向函数传递参数时，在函数内部通过 `$1`、`$2` 等来引用第一个、第二个参数。
```bash
greet() {
    echo "Hello, $1"
}
greet "Alice" # 输出：Hello, Alice
```

![](img/980cd4b18c5b1a14d5de6db97818aefd_148.png)

## 命令别名 🏷️

如果你经常需要输入一个很长的命令，可以为其创建一个简短的别名。

![](img/980cd4b18c5b1a14d5de6db97818aefd_150.png)

使用 `alias` 命令来创建别名。
```bash
alias 简称='长命令'
```
例如，将 `python3` 别名为 `python`：
```bash
alias python='python3'
```
创建后，每次输入 `python`，实际上执行的是 `python3`。请注意，这样设置的别名仅在当前终端会话中有效。要永久生效，需要将别名定义添加到你的 shell 配置文件（如 `~/.bashrc` 或 `~/.zshrc`）中。

## 总结 🎯

![](img/980cd4b18c5b1a14d5de6db97818aefd_152.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_154.png)

本节课我们一起学习了Bash的更多高级功能。

我们首先介绍了几个关键命令：使用 `sudo` 获取管理员权限，用 `find` 精准定位文件，用 `grep` 在文件中搜索文本，用 `diff` 比较文件差异，以及用 `ssh` 连接远程计算机。

![](img/980cd4b18c5b1a14d5de6db97818aefd_156.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_158.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_160.png)

接着，我们探索了在终端内编辑文件的三种主要工具：功能强大但稍复杂的 `vim` 和 `emacs`，以及简单易用的 `nano`。你可以根据需求选择最适合你的编辑器。

![](img/980cd4b18c5b1a14d5de6db97818aefd_162.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_163.png)

然后，我们入门了Bash脚本编程，学习了如何定义和使用变量、编写条件判断和循环语句，以及创建函数来封装可重用的代码块。

最后，我们了解了如何使用 `alias` 为常用命令创建快捷方式，提升工作效率。

今天涵盖的内容很多，节奏较快。不必担心无法立刻掌握所有细节。Bash和终端技能的提升很大程度上依赖于实践。当你完成作业或在日常中使用终端时，你会越来越熟悉这些工具和命令。请尝试不同的文本编辑器，找到你最顺手的那一个。

![](img/980cd4b18c5b1a14d5de6db97818aefd_165.png)

下一讲，我们将开始学习 `git` 版本控制系统。