# 004：函数的应用

![](img/a1049fce81243cff6ba2110197cc5d09_1.png)

![](img/a1049fce81243cff6ba2110197cc5d09_2.png)

![](img/a1049fce81243cff6ba2110197cc5d09_4.png)

![](img/a1049fce81243cff6ba2110197cc5d09_5.png)

在本节课中，我们将学习如何定义和使用自定义函数，探索不同类型的循环结构，并初步了解如何将函数与循环结合，步入函数式编程的世界。

![](img/a1049fce81243cff6ba2110197cc5d09_7.png)

## 概述

我们将从分析一个现有程序开始，识别其重复代码，并学习如何通过创建自定义函数来优化设计。接着，我们将学习三种循环结构（`repeat`、`while`、`for`），以实现代码的重复执行。最后，我们将结合函数与循环，并介绍R语言中强大的`apply`函数族，以更高效、简洁的方式处理数据。

## 创建自定义函数

上一节我们回顾了一个统计投票的程序。本节中，我们来看看如何通过创建函数来优化它。

在R语言中，使用`function`关键字来创建函数。基本语法结构如下：

```r
函数名 <- function(参数1, 参数2, ...) {
  # 函数体：要执行的代码
  return(返回值)
}
```

![](img/a1049fce81243cff6ba2110197cc5d09_9.png)

以下是为投票程序创建的第一个函数：

```r
get_votes <- function(prompt = "Enter votes") {
  votes <- as.integer(readline(prompt = paste0(prompt, ": ")))
  return(votes)
}
```

![](img/a1049fce81243cff6ba2110197cc5d09_11.png)

这个函数名为`get_votes`，它接受一个参数`prompt`（提示信息），并设置了一个默认值。函数体内，它使用`readline`获取用户输入，并用`as.integer`将其转换为整数，最后返回这个值。在R中，如果函数体的最后一行是一个计算值，可以省略`return`语句，该值会被自动返回。

## 处理错误输入

用户可能不会总是输入数字。我们需要在函数中加入错误处理机制。

当用户输入非数字内容时，`as.integer`会返回`NA`（不可用）并产生警告。我们可以使用条件语句和`ifelse`函数来处理这种情况：

![](img/a1049fce81243cff6ba2110197cc5d09_13.png)

```r
get_votes <- function(prompt = "Enter votes") {
  votes <- suppressWarnings(as.integer(readline(prompt = paste0(prompt, ": "))))
  return(ifelse(is.na(votes), 0, votes))
}
```

![](img/a1049fce81243cff6ba2110197cc5d09_15.png)

这里，`suppressWarnings`用于抑制转换失败时产生的警告。`ifelse`函数检查`votes`是否为`NA`：如果是，则返回0；否则，返回`votes`本身的值。

## 理解作用域

在函数内部创建的对象（如`votes`和`prompt`）只存在于该函数的**作用域**内。这意味着在函数外部无法直接访问它们。这种设计保护了函数的内部实现细节，是模块化编程的重要概念。

## 循环结构

有时我们需要重复执行某段代码，直到满足特定条件。这时就需要用到循环。

以下是R语言中的三种主要循环结构：

### 1. repeat循环
`repeat`循环会无限次地执行其代码块，直到遇到`break`语句才会退出。

```r
i <- 3
repeat {
  cat("quack\n")
  i <- i - 1
  if (i == 0) {
    break
  }
}
```

![](img/a1049fce81243cff6ba2110197cc5d09_17.png)

![](img/a1049fce81243cff6ba2110197cc5d09_19.png)

### 2. while循环
`while`循环会在每次迭代前检查一个条件。只要条件为`TRUE`，就会继续执行循环体。

![](img/a1049fce81243cff6ba2110197cc5d09_21.png)

![](img/a1049fce81243cff6ba2110197cc5d09_22.png)

```r
i <- 1
while (i <= 3) {
  cat("quack\n")
  i <- i + 1
}
```

### 3. for循环
`for`循环用于遍历一个向量（或列表）中的每个元素，并对每个元素执行相同的操作。

![](img/a1049fce81243cff6ba2110197cc5d09_24.png)

![](img/a1049fce81243cff6ba2110197cc5d09_25.png)

```r
for (i in 1:3) {
  cat("quack\n")
}
```

你也可以遍历字符向量：

```r
candidates <- c("Mario", "Peach", "Bowser")
for (candidate in candidates) {
  cat(paste0(candidate, " says quack\n"))
}
```

## 应用循环改进程序

我们可以使用循环来改进投票程序，确保即使用户输入无效内容，程序也会持续提示，直到获得有效输入。

![](img/a1049fce81243cff6ba2110197cc5d09_27.png)

以下是在`get_votes`函数中使用`repeat`循环的实现：

![](img/a1049fce81243cff6ba2110197cc5d09_29.png)

```r
get_votes <- function(prompt = "Enter votes") {
  repeat {
    votes <- suppressWarnings(as.integer(readline(prompt = paste0(prompt, ": "))))
    if (!is.na(votes)) {
      return(votes)
    }
    # 如果votes是NA，循环会继续，再次提示用户
  }
}
```

此外，我们可以使用`for`循环来为多个候选人获取投票，并计算总票数：

```r
candidates <- c("Mario", "Peach", "Bowser")
total <- 0
for (candidate in candidates) {
  votes <- get_votes(prompt = candidate)
  total <- total + votes
}
cat("Total votes:", total, "\n")
```

## 函数式编程与apply函数族

在数据分析中，经常需要对数据框的每一行或每一列应用同一个函数。虽然可以用`for`循环实现，但R提供了更优雅的解决方案——`apply`函数族。

![](img/a1049fce81243cff6ba2110197cc5d09_31.png)

假设我们有一个数据框`votes_df`，包含不同候选人在不同投票方式下的得票数。

![](img/a1049fce81243cff6ba2110197cc5d09_33.png)

```r
# 假设votes_df结构如下：
#         Poll Mail
# Mario    37   63
# Peach    43  107
# Bowser   21   99
```

![](img/a1049fce81243cff6ba2110197cc5d09_35.png)

![](img/a1049fce81243cff6ba2110197cc5d09_36.png)

![](img/a1049fce81243cff6ba2110197cc5d09_38.png)

**计算每位候选人的总票数（行和）：**

![](img/a1049fce81243cff6ba2110197cc5d09_40.png)

![](img/a1049fce81243cff6ba2110197cc5d09_42.png)

```r
row_totals <- apply(votes_df, MARGIN = 1, FUN = sum)
```

**计算每种投票方式的总票数（列和）：**

```r
col_totals <- apply(votes_df, MARGIN = 2, FUN = sum)
```

`apply`函数的参数：
*   第一个参数：要操作的数据框或矩阵。
*   `MARGIN`：维度。`1`表示按行操作，`2`表示按列操作。
*   `FUN`：要应用的函数，例如`sum`、`mean`等。

这种将函数作为参数传递给另一个函数（`apply`）的做法，是**函数式编程**的核心思想之一。它使代码更简洁、更易读，且通常效率更高。

![](img/a1049fce81243cff6ba2110197cc5d09_44.png)

## 总结

![](img/a1049fce81243cff6ba2110197cc5d09_46.png)

![](img/a1049fce81243cff6ba2110197cc5d09_48.png)

本节课中我们一起学习了R语言编程中的几个核心概念。
我们首先学习了如何**定义自定义函数**，包括参数设置、默认值和返回值，并加入了基本的错误处理。
接着，我们探索了三种**循环结构**（`repeat`、`while`、`for`），理解了它们各自适用的场景，并利用循环改进了用户交互流程。
最后，我们初步接触了**函数式编程**，通过`apply`函数族，学会了如何高效地对数据框的行或列进行操作，从而写出更简洁、强大的数据分析代码。
掌握这些基础是构建更复杂R程序的关键步骤。