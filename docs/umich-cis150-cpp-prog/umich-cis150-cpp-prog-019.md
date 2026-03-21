# 019：项目2 - 月球着陆器与刽子手游戏 🚀

![](img/eed819226e74faba2054c16ff8e23248_0.png)

![](img/eed819226e74faba2054c16ff8e23248_2.png)

![](img/eed819226e74faba2054c16ff8e23248_4.png)

![](img/eed819226e74faba2054c16ff8e23248_6.png)

![](img/eed819226e74faba2054c16ff8e23248_8.png)

在本节课中，我们将回顾项目1（月球着陆器游戏）的解决方案，并介绍项目2（刽子手游戏）的具体要求。我们将重点学习如何运用函数进行功能分解，将复杂问题拆解为更小、更易管理的部分。

![](img/eed819226e74faba2054c16ff8e23248_10.png)

## 回顾项目1：月球着陆器游戏

![](img/eed819226e74faba2054c16ff8e23248_12.png)

![](img/eed819226e74faba2054c16ff8e23248_14.png)

![](img/eed819226e74faba2054c16ff8e23248_16.png)

![](img/eed819226e74faba2054c16ff8e23248_18.png)

![](img/eed819226e74faba2054c16ff8e23248_20.png)

上一节我们完成了函数章节的学习。本节中，我们来看看如何将函数应用到实际项目中。项目1的目标是创建一个简单的文本游戏，玩家需要调整飞船的X轴和Y轴倾斜度，并使用推进器安全降落在月球表面。

![](img/eed819226e74faba2054c16ff8e23248_22.png)

### 核心游戏逻辑与功能分解

解决此类问题的关键在于功能分解：将一个大问题分解为一系列小步骤。对于月球着陆器游戏，我们可以识别出以下主要步骤：

![](img/eed819226e74faba2054c16ff8e23248_24.png)

![](img/eed819226e74faba2054c16ff8e23248_26.png)

![](img/eed819226e74faba2054c16ff8e23248_28.png)

![](img/eed819226e74faba2054c16ff8e23248_30.png)

*   **生成随机倾斜度**：需要为X轴和Y轴生成一个介于-10到10之间的随机初始值。
*   **显示与更新状态**：需要向玩家显示当前的倾斜度和距离，并根据玩家选择更新这些值。
*   **处理玩家输入**：需要提供一个菜单让玩家选择操作，并验证输入的合法性。
*   **实现自毁序列**：当选择自毁时，游戏应进入特殊状态，只允许输入取消代码。
*   **判断游戏结果**：根据最终状态（倾斜度是否为0）判断是成功着陆还是坠毁。
*   **游戏循环**：允许玩家在单局游戏结束后选择重新开始。

![](img/eed819226e74faba2054c16ff8e23248_32.png)

![](img/eed819226e74faba2054c16ff8e23248_34.png)

![](img/eed819226e74faba2054c16ff8e23248_36.png)

![](img/eed819226e74faba2054c16ff8e23248_38.png)

以下是部分核心步骤的代码框架示例：

```cpp
// 示例：获取随机数的函数框架
int getRandomNumber() {
    // TODO: 返回一个-10到10之间的随机数
    return 0; // 占位符
}

// 示例：获取玩家选择的函数框架
string getChoice() {
    // TODO: 显示菜单并获取、验证玩家输入
    return “”; // 占位符
}

// 示例：打印当前游戏状态的函数
void printDetails(int xTilt, int yTilt, int distance) {
    cout << “X轴倾斜度: “ << xTilt << endl;
    cout << “Y轴倾斜度: “ << yTilt << endl;
    cout << “距离月面: “ << distance << endl;
}
```

### 项目1实现要点

![](img/eed819226e74faba2054c16ff8e23248_40.png)

![](img/eed819226e74faba2054c16ff8e23248_42.png)

在实现过程中，有几点需要注意：

1.  **使用常量增强可读性**：用有意义的常量名称（如 `X_TILT_POSITIVE`）代替魔法数字（如 `1`），使代码更易理解。
2.  **合理规划函数范围**：有些操作（如简单的加减法）可能不需要单独写成函数，而有些复杂流程（如自毁序列）则适合封装。
3.  **处理自毁状态**：自毁激活后，需要通过一个布尔标志（如 `selfDestructActive`）改变主循环的行为，暂时禁用其他命令，只处理取消代码的输入。
4.  **随机数生成**：使用 `srand(time(0))` 初始化随机种子，并通过模运算和偏移来得到特定范围的随机数。

通过将问题分解并逐个实现这些小函数，最终在 `main` 函数中组合它们，就能构建出完整的游戏。这种方法使得代码结构清晰，易于调试和维护。

## 介绍项目2：刽子手游戏

接下来，我们将开始项目2。本项目的主要目的是练习编写和使用函数。我们将构建一个经典的刽子手猜字游戏。

### 项目2概述与要求

![](img/eed819226e74faba2054c16ff8e23248_44.png)

在这个项目中，我将提供一个 `main` 函数的框架。你的任务是按照严格的规范，完成一系列指定的函数。当所有函数都正确实现后，提供的 `main` 函数应该能正常运行整个游戏。

![](img/eed819226e74faba2054c16ff8e23248_46.png)

![](img/eed819226e74faba2054c16ff8e23248_48.png)

以下是需要你实现的函数列表及其简要说明：

![](img/eed819226e74faba2054c16ff8e23248_50.png)

*   `getWord()`：提示用户输入一个单词，并确保该单词至少包含4个字符。该函数返回这个隐藏单词。
*   `displayHiddenWord(string hiddenWord, string lettersGuessed)`：接收隐藏单词和已猜字母作为参数。在一行中打印出隐藏单词的当前状态：已猜出的字母显示其本身，未猜出的字母显示为下划线 `_`。
*   `getLetterGuess(string lettersGuessed)`：接收已猜字母字符串，提示用户输入一个字母猜测。此函数需验证：1) 输入是单个字母；2) 该字母之前没有被猜过。返回验证通过的猜测字母。
*   `isLetterGuessedInWord(char guess, string hiddenWord)`：接收猜测字母和隐藏单词，检查该字母是否存在于隐藏单词中。存在则返回 `true`，否则返回 `false`。
*   `hasWordBeenGuessed(string hiddenWord, string lettersGuessed)`：接收隐藏单词和所有已猜字母，检查是否所有隐藏单词中的字母都已被猜出。是则返回 `true`，否则返回 `false`。
*   `printGallows(int incorrectGuesses)`：接收错误猜测的次数，根据次数打印出对应阶段的绞刑架和“小人”图案。这是一个较长的函数，因为需要处理从0次到6次错误的不同情况。
*   `hasPersonBeenHanged(int incorrectGuesses)`：接收错误猜测的次数，如果次数达到或超过6次（即小人被完全画出），则返回 `true`，表示游戏失败。

### 提供的main函数框架

你的代码将围绕以下主循环构建：

```cpp
// 假设所有函数已正确实现
int main() {
    string lettersGuessed = “”;
    string hiddenWord = getWord();
    int incorrectGuesses = 0;

    while (!hasWordBeenGuessed(hiddenWord, lettersGuessed) && !hasPersonBeenHanged(incorrectGuesses)) {
        displayHiddenWord(hiddenWord, lettersGuessed);
        char guess = getLetterGuess(lettersGuessed);
        // 将新猜的字母加入已猜字母列表
        lettersGuessed += guess;

        if (!isLetterGuessedInWord(guess, hiddenWord)) {
            incorrectGuesses++;
        }
        printGallows(incorrectGuesses);
    }

    // 游戏结束，判断输赢
    // ...
    return 0;
}
```

![](img/eed819226e74faba2054c16ff8e23248_52.png)

![](img/eed819226e74faba2054c16ff8e23248_54.png)

### 项目2评分要点与建议

![](img/eed819226e74faba2054c16ff8e23248_56.png)

![](img/eed819226e74faba2054c16ff8e23248_57.png)

本项目共20分，每个指定函数（除 `hasPersonBeenHanged` 为2分外）各值3分。评分将严格依据函数是否按描述正确实现。

在实现过程中，请注意：

*   **字符串处理**：你将需要运用循环来遍历字符串，检查字符是否存在。
*   **输入验证**：在 `getWord` 和 `getLetterGuess` 函数中，确保对用户输入进行充分的验证。
*   **函数协作**：注意函数之间的数据传递。例如，`lettersGuessed` 字符串需要在 `main` 函数中维护，并传递给多个函数使用。
*   `printGallows` **函数**：这是最繁琐的部分，建议使用 `if-else if` 或 `switch` 语句，根据 `incorrectGuesses` 的值打印不同的ASCII艺术图案。

## 总结

本节课中我们一起回顾了如何通过功能分解的方法，使用函数构建了项目1（月球着陆器游戏）。接着，我们详细介绍了项目2（刽子手游戏）的要求，你需要按照给定的函数规范完成实现，以练习编写具有特定输入、输出和功能的模块化代码。

![](img/eed819226e74faba2054c16ff8e23248_59.png)

记住，从大问题中识别出独立的小任务，并为每个任务编写函数，是结构化编程的核心技能。开始项目2时，请逐一实现每个函数并进行测试，确保它们能正确集成到提供的 `main` 函数框架中。