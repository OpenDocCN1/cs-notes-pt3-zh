# 028：代码构建脚本 🛠️

![](img/8038d42c0442aa53f884ced67aae4b8c_0.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_2.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_4.png)

在本节课中，我们将学习如何使用 `make` 工具和 `Makefile` 来自动化编译和管理包含多个文件的C语言项目。我们将从一个简单的手动编译示例开始，逐步构建一个功能完善、高效且可维护的构建脚本。

![](img/8038d42c0442aa53f884ced67aae4b8c_6.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_8.png)

---

## 项目示例与手动编译的挑战

首先，我们来看一个简单的项目示例。该项目包含多个文件：
*   `main.c`：一个前端程序，通过命令行参数接收一个数字。
*   `fact.c`：定义计算阶乘的函数。
*   `fact.h`：声明 `fact.c` 中函数的原型，供 `main.c` 包含。
*   `README.md`：一个Markdown文件，可转换为HTML。

![](img/8038d42c0442aa53f884ced67aae4b8c_10.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_12.png)

如果手动编译这个项目，我们需要执行以下步骤：
1.  将每个 `.c` 文件编译成 `.o` 目标文件。
    ```bash
    gcc -c main.c -o main.o
    gcc -c fact.c -o fact.o
    ```
2.  将所有 `.o` 文件链接成一个可执行文件。
    ```bash
    gcc main.o fact.o -o myfact
    ```
3.  （可选）将Markdown文件转换为HTML。
    ```bash
    pandoc README.md -o README.html
    ```

![](img/8038d42c0442aa53f884ced67aae4b8c_14.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_15.png)

手动编译存在几个问题：
*   **效率低下**：每次修改源文件（如 `fact.c`、`main.c` 或 `fact.h`）后，都需要重新执行相关步骤。
*   **容易出错**：需要记住所有编译命令和依赖关系。
*   **难以维护**：更改编译选项（如添加 `-Wall` 标志）时，需要修改多处命令。

![](img/8038d42c0442aa53f884ced67aae4b8c_17.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_18.png)

为了解决这些问题，我们需要自动化构建过程，这正是 `make` 工具的用武之地。

![](img/8038d42c0442aa53f884ced67aae4b8c_20.png)

---

![](img/8038d42c0442aa53f884ced67aae4b8c_22.png)

## Makefile 基础：规则与结构

![](img/8038d42c0442aa53f884ced67aae4b8c_24.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_26.png)

`make` 是一个构建工具，它通过读取名为 `Makefile` 的配置文件来执行构建任务。一个典型的 `Makefile` 包含一系列**规则**。

![](img/8038d42c0442aa53f884ced67aae4b8c_28.png)

每个规则由三部分组成：
1.  **目标**：规则要生成的文件（例如 `myfact`）。
2.  **先决条件**：生成目标所依赖的文件（例如 `main.o fact.o`）。
3.  **命令**：生成目标需要执行的具体命令，**必须以一个真正的Tab字符开头**。

规则的基本语法如下：
```
目标: 先决条件
<Tab>命令
```

![](img/8038d42c0442aa53f884ced67aae4b8c_30.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_32.png)

注释以 `#` 开头。

![](img/8038d42c0442aa53f884ced67aae4b8c_34.png)

现在，让我们为示例项目编写一个基础的 `Makefile`。

---

![](img/8038d42c0442aa53f884ced67aae4b8c_36.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_37.png)

## 编写第一个 Makefile

![](img/8038d42c0442aa53f884ced67aae4b8c_39.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_40.png)

以下是一个能完成基本构建任务的 `Makefile`：

```makefile
myfact: main.o fact.o
	gcc main.o fact.o -o myfact

![](img/8038d42c0442aa53f884ced67aae4b8c_42.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_44.png)

main.o: main.c fact.h
	gcc -c main.c -o main.o

![](img/8038d42c0442aa53f884ced67aae4b8c_46.png)

fact.o: fact.c fact.h
	gcc -c fact.c -o fact.o

README.html: README.md
	pandoc README.md -o README.html
```

![](img/8038d42c0442aa53f884ced67aae4b8c_48.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_50.png)

在这个文件中：
*   第一条规则说明 `myfact` 依赖于 `main.o` 和 `fact.o`，并通过链接命令生成。
*   第二、三条规则分别说明如何从 `.c` 和 `.h` 文件生成对应的 `.o` 文件。
*   最后一条规则说明如何从 `.md` 文件生成 `.html` 文件。

![](img/8038d42c0442aa53f884ced67aae4b8c_52.png)

在终端运行 `make` 命令时，`make` 会查找当前目录下的 `Makefile` 文件，并执行其中的第一条规则（默认规则）。因此，运行 `make` 只会生成 `myfact` 可执行文件。

如果想生成 `README.html`，需要明确指定目标：`make README.html`。

![](img/8038d42c0442aa53f884ced67aae4b8c_54.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_55.png)

---

## 改进 Makefile：默认目标与清理规则

![](img/8038d42c0442aa53f884ced67aae4b8c_57.png)

上一节我们介绍了基础规则，本节中我们来看看如何设置默认构建所有目标，并添加清理功能。

### 设置默认目标 `all`

为了让 `make` 默认构建所有目标（即可执行文件和HTML文件），我们可以添加一个名为 `all` 的**伪目标**。它本身不对应任何文件，但可以列出所有需要构建的真实目标作为其先决条件。

![](img/8038d42c0442aa53f884ced67aae4b8c_59.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_60.png)

```makefile
all: myfact README.html

myfact: main.o fact.o
	gcc main.o fact.o -o myfact

main.o: main.c fact.h
	gcc -c main.c -o main.o

fact.o: fact.c fact.h
	gcc -c fact.c -o fact.o

![](img/8038d42c0442aa53f884ced67aae4b8c_62.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_64.png)

README.html: README.md
	pandoc README.md -o README.html
```
现在，运行 `make` 就会同时生成 `myfact` 和 `README.html`。

![](img/8038d42c0442aa53f884ced67aae4b8c_66.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_68.png)

### 添加清理规则 `clean`

![](img/8038d42c0442aa53f884ced67aae4b8c_69.png)

我们还需要一个规则来清理所有生成的文件，保持目录整洁。

```makefile
clean:
	rm -f myfact README.html main.o fact.o
```
运行 `make clean` 会删除可执行文件、HTML文件和所有目标文件。

![](img/8038d42c0442aa53f884ced67aae4b8c_71.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_73.png)

至此，我们有了一个可用的 `Makefile`。但对于更复杂的项目，这个文件存在大量重复代码，难以维护。接下来，我们将对其进行优化。

![](img/8038d42c0442aa53f884ced67aae4b8c_75.png)

---

![](img/8038d42c0442aa53f884ced67aae4b8c_77.png)

## 优化 Makefile：变量与模式规则

![](img/8038d42c0442aa53f884ced67aae4b8c_79.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_80.png)

优秀的程序员追求简洁和高效。当前的 `Makefile` 存在多处重复，例如：
*   目标文件列表（`main.o fact.o`）出现了多次。
*   编译 `.o` 文件的规则几乎完全相同。
*   编译命令（`gcc -c ...`）被重复书写。

![](img/8038d42c0442aa53f884ced67aae4b8c_82.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_84.png)

以下是优化方法：

![](img/8038d42c0442aa53f884ced67aae4b8c_86.png)

### 1. 使用自动变量
自动变量可以在规则的命令中动态引用目标和先决条件。
*   `$@`：代表当前规则中的**目标**文件名。
*   `$<`：代表当前规则中的**第一个**先决条件文件名。
*   `$^`：代表当前规则中**所有**先决条件文件名。

使用自动变量后，链接规则可以简化为：
```makefile
myfact: main.o fact.o
	gcc $^ -o $@
```

### 2. 使用模式规则
模式规则使用通配符 `%` 来匹配一组文件，从而将多个相似规则合并为一个。

例如，将两个生成 `.o` 文件的规则合并：
```makefile
%.o: %.c fact.h
	gcc -c $< -o $@
```
这条规则表示：任何 `.o` 文件依赖于同名的 `.c` 文件和 `fact.h` 文件，并使用给定的命令编译。

![](img/8038d42c0442aa53f884ced67aae4b8c_88.png)

我们也可以为Markdown转换创建模式规则：
```makefile
%.html: %.md
	pandoc $< -o $@
```

### 3. 使用自定义变量
我们可以将常用的编译器、编译选项定义为变量，方便统一修改。

![](img/8038d42c0442aa53f884ced67aae4b8c_90.png)

```makefile
CC = gcc
CFLAGS = -Wall -Wextra

![](img/8038d42c0442aa53f884ced67aae4b8c_92.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_93.png)

%.o: %.c fact.h
	$(CC) $(CFLAGS) -c $< -o $@
```
定义变量后，在命令中使用 `$(变量名)` 来引用。这样，要修改编译选项（例如添加 `-g` 调试信息），只需在 `CFLAGS` 变量处更改一次。

![](img/8038d42c0442aa53f884ced67aae4b8c_95.png)

### 4. 集中管理文件列表
将最终目标和中间对象文件列表也定义为变量。

```makefile
TARGETS = myfact README.html
OBJECTS = main.o fact.o

![](img/8038d42c0442aa53f884ced67aae4b8c_97.png)

all: $(TARGETS)

![](img/8038d42c0442aa53f884ced67aae4b8c_99.png)

myfact: $(OBJECTS)
	$(CC) $^ -o $@

![](img/8038d42c0442aa53f884ced67aae4b8c_101.png)

clean:
	rm -f $(TARGETS) $(OBJECTS)
```
现在，项目的主要配置信息都集中在文件开头的变量定义处，维护起来非常方便。

![](img/8038d42c0442aa53f884ced67aae4b8c_103.png)

经过这些优化，`Makefile` 变得简洁而通用。接下来，我们让它看起来更专业。

![](img/8038d42c0442aa53f884ced67aae4b8c_105.png)

---

## 美化输出与控制详细程度

![](img/8038d42c0442aa53f884ced67aae4b8c_107.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_109.png)

默认情况下，`make` 会打印出它执行的每一条命令。输出可能显得冗长。我们可以美化输出，只显示简洁的编译进度信息。

![](img/8038d42c0442aa53f884ced67aae4b8c_111.png)

### 隐藏命令回显
在命令前添加 `@` 符号，可以阻止 `make` 将该命令本身打印到终端。

![](img/8038d42c0442aa53f884ced67aae4b8c_113.png)

```makefile
%.o: %.c fact.h
	@echo "CC $<"
	@$(CC) $(CFLAGS) -c $< -o $@
```
这样，终端只会显示 `CC main.c` 这样的提示，而不是完整的 `gcc -Wall -Wextra -c main.c -o main.o` 命令。

### 添加详细模式
虽然美化后的输出更清晰，但在调试时，我们可能需要看到完整的命令。我们可以通过**条件变量**来实现一个“详细模式”。

![](img/8038d42c0442aa53f884ced67aae4b8c_115.png)

```makefile
ifeq ($(V),1)
Q =
else
Q = @
endif

%.o: %.c fact.h
	$(Q)echo "CC $<"
	$(Q)$(CC) $(CFLAGS) -c $< -o $@
```
*   当运行 `make`（`V` 未定义）时，`Q` 被赋值为 `@`，命令被隐藏。
*   当运行 `make V=1` 时，`Q` 被赋值为空，命令会完整显示。

现在，我们的 `Makefile` 功能强大且外观专业。但它还有一个关键缺陷：头文件依赖处理不通用。

---

![](img/8038d42c0442aa53f884ced67aae4b8c_117.png)

## 自动处理头文件依赖

![](img/8038d42c0442aa53f884ced67aae4b8c_119.png)

当前的模式规则 `%.o: %.c fact.h` 硬编码了 `fact.h` 这个依赖。如果项目扩大，有的 `.c` 文件不包含 `fact.h`，或者包含了其他头文件，这个规则就不准确了。

错误的依赖关系会导致严重问题：修改头文件后，`make` 可能不会重新编译依赖它的 `.c` 文件，从而产生不一致的构建结果。

![](img/8038d42c0442aa53f884ced67aae4b8c_121.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_122.png)

### 解决方案：让 GCC 生成依赖关系
幸运的是，GCC 编译器可以帮我们自动生成依赖关系。使用 `-MMD` 编译选项，GCC 会在编译 `.c` 文件生成 `.o` 文件的同时，生成一个对应的 `.d` 依赖文件。

![](img/8038d42c0442aa53f884ced67aae4b8c_124.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_126.png)

例如，编译 `fact.c` 时：
```bash
gcc -MMD -c fact.c -o fact.o
```
这会额外生成一个 `fact.d` 文件，其内容类似于：
```makefile
fact.o: fact.c fact.h
```
这正是我们需要的规则！

![](img/8038d42c0442aa53f884ced67aae4b8c_128.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_130.png)

### 在 Makefile 中集成自动依赖
以下是集成自动依赖跟踪的步骤：

1.  **修改编译标志**：在 `CFLAGS` 中添加 `-MMD` 选项。
    ```makefile
    CFLAGS = -Wall -Wextra -MMD
    ```

![](img/8038d42c0442aa53f884ced67aae4b8c_132.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_134.png)

2.  **生成依赖文件名**：从对象文件列表推导出依赖文件列表。
    ```makefile
    DEPS = $(OBJECTS:.o=.d)
    ```
    这行代码将 `OBJECTS` 变量中所有 `.o` 后缀替换为 `.d`。

![](img/8038d42c0442aa53f884ced67aae4b8c_136.png)

3.  **包含依赖文件**：使用 `-include` 指令将生成的 `.d` 文件包含到 `Makefile` 中。
    ```makefile
    -include $(DEPS)
    ```
    `-` 前缀表示即使某些 `.d` 文件暂时不存在（首次编译时），`make` 也不会报错。

![](img/8038d42c0442aa53f884ced67aae4b8c_138.png)

4.  **修正模式规则**：移除规则中硬编码的 `fact.h`。
    ```makefile
    %.o: %.c
    	$(Q)echo "CC $<"
    	$(Q)$(CC) $(CFLAGS) -c $< -o $@
    ```

**工作原理**：
1.  首次运行 `make` 时，没有 `.d` 文件，`-include` 被忽略。GCC 编译 `.c` 文件生成 `.o` 文件，同时生成 `.d` 文件。
2.  后续运行 `make` 时，`.d` 文件被包含进来，提供了精确的头文件依赖规则。
3.  当修改头文件（如 `fact.h`）后，对应的依赖规则会触发相关 `.o` 文件的重新编译，从而保证构建的正确性。

![](img/8038d42c0442aa53f884ced67aae4b8c_140.png)

---

## 最终的高级 Makefile

结合以上所有技巧，我们得到一个功能完善、通用性强的高级 `Makefile`：

```makefile
# 工具和标志定义
CC = gcc
CFLAGS = -Wall -Wextra -MMD

# 详细输出控制
ifeq ($(V),1)
Q =
else
Q = @
endif

![](img/8038d42c0442aa53f884ced67aae4b8c_142.png)

# 文件列表定义
TARGETS = myfact README.html
OBJECTS = main.o fact.o
DEPS = $(OBJECTS:.o=.d) # 依赖文件列表

![](img/8038d42c0442aa53f884ced67aae4b8c_144.png)

# 默认目标
all: $(TARGETS)

![](img/8038d42c0442aa53f884ced67aae4b8c_146.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_148.png)

# 链接可执行文件
myfact: $(OBJECTS)
	$(Q)echo "LD $@"
	$(Q)$(CC) $^ -o $@

# 编译C源文件为对象文件
%.o: %.c
	$(Q)echo "CC $<"
	$(Q)$(CC) $(CFLAGS) -c $< -o $@

![](img/8038d42c0442aa53f884ced67aae4b8c_150.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_152.png)

# 转换Markdown为HTML
%.html: %.md
	$(Q)echo "PANDOC $<"
	$(Q)pandoc $< -o $@

![](img/8038d42c0442aa53f884ced67aae4b8c_154.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_156.png)

# 清理生成文件
clean:
	$(Q)echo "CLEAN"
	$(Q)rm -f $(TARGETS) $(OBJECTS) $(DEPS)

![](img/8038d42c0442aa53f884ced67aae4b8c_158.png)

# 包含自动生成的依赖关系
-include $(DEPS)
```

![](img/8038d42c0442aa53f884ced67aae4b8c_160.png)

---

## 总结

本节课中我们一起学习了如何编写一个高效的 `Makefile` 来自动化C语言项目的构建过程。我们从手动编译的弊端出发，逐步引入了 `make` 工具的基础规则、变量、模式规则和自动变量。为了提升可维护性和用户体验，我们学习了如何设置默认目标、添加清理功能、美化输出以及通过条件变量控制详细程度。最后，我们解决了构建中的关键挑战——自动跟踪头文件依赖，利用GCC的 `-MMD` 选项自动生成并包含依赖关系，确保了构建的准确性和高效性。

![](img/8038d42c0442aa53f884ced67aae4b8c_162.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_163.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_164.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_166.png)

通过本教程，你应该能够为你的项目创建结构清晰、功能强大且易于维护的构建脚本。