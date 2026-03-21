# 010：数组与向量 Part 2

![](img/1cbd3c47fe55f0035380d791f7cc47f5_0.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_2.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_4.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_6.png)

在本节课中，我们将继续学习数组与向量的应用，并完成一个完整的“猜单词”游戏项目。我们将学习如何将程序分解为多个函数，以及如何使用向量来管理数据。

---

## 项目二：猜单词游戏实现

上一节我们介绍了项目的基本框架，本节中我们来看看如何实现具体的函数。

### 获取隐藏单词

首先，我们需要一个函数来从用户那里获取一个至少包含4个字符的隐藏单词。

以下是 `getWord` 函数的实现：

```cpp
string getWord() {
    string word;
    cout << "Enter a word at least four characters long: ";
    cin >> word;
    while (word.size() < 4) {
        cout << "Enter a word at least four characters long: ";
        cin >> word;
    }
    return word;
}
```

### 检查单词是否被猜出

接下来，我们需要一个函数来判断玩家是否已经猜出了隐藏单词。该函数接收隐藏单词和已猜字母作为参数。

以下是 `hasWordBeenGuessed` 函数的实现：

```cpp
bool hasWordBeenGuessed(string hiddenWord, string lettersGuessed) {
    for (char letter : hiddenWord) {
        bool matchFound = false;
        for (char guess : lettersGuessed) {
            if (letter == guess) {
                matchFound = true;
                break; // 找到匹配即可跳出内层循环
            }
        }
        if (!matchFound) {
            return false; // 只要有一个字母没被猜中，就返回false
        }
    }
    return true; // 所有字母都被猜中
}
```

### 判断玩家是否被“吊死”

这个函数根据错误的猜测次数来判断游戏是否结束。

以下是 `hasPersonBeenHanged` 函数的实现：

```cpp
bool hasPersonBeenHanged(int numGuesses) {
    return numGuesses >= 6; // 错误次数达到或超过6次则游戏结束
}
```

![](img/1cbd3c47fe55f0035380d791f7cc47f5_8.png)

### 显示当前单词状态

![](img/1cbd3c47fe55f0035380d791f7cc47f5_10.png)

这个函数用于在每一轮显示当前猜词进度，已猜出的字母显示出来，未猜出的显示为下划线。

以下是 `displayHiddenWord` 函数的实现：

```cpp
void displayHiddenWord(string hiddenWord, string lettersGuessed) {
    for (char letter : hiddenWord) {
        bool matchFound = false;
        for (char guess : lettersGuessed) {
            if (letter == guess) {
                matchFound = true;
                break;
            }
        }
        if (matchFound) {
            cout << letter << " ";
        } else {
            cout << "_ ";
        }
    }
    cout << endl;
}
```

![](img/1cbd3c47fe55f0035380d791f7cc47f5_12.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_14.png)

### 获取玩家猜测的字母

这个函数负责获取玩家输入的一个字母，并确保该字母之前没有被猜过。

![](img/1cbd3c47fe55f0035380d791f7cc47f5_16.png)

以下是 `getLetterGuessed` 函数的实现：

```cpp
char getLetterGuessed(string& lettersGuessed) {
    char guess;
    bool alreadyGuessed;
    do {
        alreadyGuessed = false;
        cout << "Guess a letter: ";
        cin >> guess;
        for (char letter : lettersGuessed) {
            if (letter == guess) {
                alreadyGuessed = true;
                cout << "You already guessed that letter." << endl;
                break;
            }
        }
    } while (alreadyGuessed);
    lettersGuessed += guess; // 将新猜的字母添加到已猜字母列表中
    return guess;
}
```

### 检查字母是否在单词中

这个函数检查玩家猜测的单个字母是否存在于隐藏单词中。

以下是 `isLetterInWord` 函数的实现：

```cpp
bool isLetterInWord(char guess, string hiddenWord) {
    for (char letter : hiddenWord) {
        if (letter == guess) {
            return true;
        }
    }
    return false;
}
```

### 绘制绞刑架

根据错误次数，分步骤绘制绞刑架的图形。

![](img/1cbd3c47fe55f0035380d791f7cc47f5_18.png)

以下是 `printGallows` 函数的实现：

![](img/1cbd3c47fe55f0035380d791f7cc47f5_20.png)

```cpp
void printGallows(int incorrectGuesses) {
    if (incorrectGuesses == 0) {
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    } else if (incorrectGuesses == 1) {
        // 绘制头部
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "  O    |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    } else if (incorrectGuesses == 2) {
        // 绘制身体
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "  O    |" << endl;
        cout << "  |    |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    } else if (incorrectGuesses == 3) {
        // 绘制一只手臂
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "  O    |" << endl;
        cout << " /|    |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    } else if (incorrectGuesses == 4) {
        // 绘制两只手臂
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "  O    |" << endl;
        cout << " /|\\   |" << endl;
        cout << "       |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    } else if (incorrectGuesses == 5) {
        // 绘制一条腿
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "  O    |" << endl;
        cout << " /|\\   |" << endl;
        cout << " /     |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    } else if (incorrectGuesses >= 6) {
        // 绘制两条腿，游戏结束
        cout << "  ______" << endl;
        cout << "  |    |" << endl;
        cout << "  O    |" << endl;
        cout << " /|\\   |" << endl;
        cout << " / \\   |" << endl;
        cout << "       |" << endl;
        cout << "========" << endl;
    }
}
```

![](img/1cbd3c47fe55f0035380d791f7cc47f5_22.png)

---

![](img/1cbd3c47fe55f0035380d791f7cc47f5_24.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_25.png)

## 项目三预告：票务管理系统

在下一个项目中，我们将构建一个控制台票务管理系统。这个程序将综合运用文件操作和向量。

![](img/1cbd3c47fe55f0035380d791f7cc47f5_27.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_28.png)

以下是该项目的三个主要功能：

![](img/1cbd3c47fe55f0035380d791f7cc47f5_30.png)

1.  **添加演出**：用户输入演出名称和总票数。程序会创建一个以演出名称命名的文件，并写入指定数量的空票（票号、空白姓名、确认码为0）。
2.  **售票**：用户输入演出名称。程序读取对应文件的所有票务信息到三个平行的向量中（分别存储票号、姓名、确认码）。然后提示用户可购买的最高票号，并询问其想购买的票号。检查该票是否可用（确认码为0）。如果可用，则询问购票者姓名，生成一个随机的6位确认码，更新向量并重写整个文件。
3.  **生成报告**：用户输入演出名称。程序读取文件并显示所有票务信息（票号、姓名、确认码），供检票员核对。

这个项目将重点练习文件的读取、写入、检查是否存在，以及使用向量来管理动态数量的数据。我们将使用平行向量的概念，即相同索引下的元素属于同一条记录。

---

## 平行向量的概念与应用

![](img/1cbd3c47fe55f0035380d791f7cc47f5_32.png)

在票务管理项目中，我们需要管理三种信息：票号、姓名和确认码。由于我们尚未学习结构体或类，一个实用的方法是使用三个独立的向量，但确保它们在相同索引位置的数据是关联的。

![](img/1cbd3c47fe55f0035380d791f7cc47f5_34.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_36.png)

以下是一个简单的示例，演示如何使用平行向量来管理球员姓名和球衣号码：

![](img/1cbd3c47fe55f0035380d791f7cc47f5_38.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_40.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_42.png)

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

![](img/1cbd3c47fe55f0035380d791f7cc47f5_44.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_46.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_48.png)

int main() {
    vector<string> playerNames;
    vector<int> jerseyNumbers;
    string inputName;
    int inputNumber;

    cout << "Enter player name (or 'quit' to stop): ";
    getline(cin, inputName);

    while (inputName != "quit") {
        playerNames.push_back(inputName);

        cout << "Enter jersey number for " << inputName << ": ";
        cin >> inputNumber;
        jerseyNumbers.push_back(inputNumber);

        // 清除输入缓冲区中的换行符
        cin.ignore();

        cout << "Enter player name (or 'quit' to stop): ";
        getline(cin, inputName);
    }

    // 查找示例
    int searchNumber;
    cout << "Enter a jersey number to look up: ";
    cin >> searchNumber;

    bool found = false;
    for (size_t i = 0; i < jerseyNumbers.size(); ++i) {
        if (jerseyNumbers[i] == searchNumber) {
            cout << "Number " << searchNumber << " belongs to " << playerNames[i] << endl;
            found = true;
            break;
        }
    }
    if (!found) {
        cout << "Could not find jersey number " << searchNumber << endl;
    }

    return 0;
}
```

在这个例子中，`playerNames[i]` 和 `jerseyNumbers[i]` 总是指向同一个球员的信息。这就是平行向量的核心思想。

![](img/1cbd3c47fe55f0035380d791f7cc47f5_50.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_52.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_54.png)

---

![](img/1cbd3c47fe55f0035380d791f7cc47f5_56.png)

## 总结

![](img/1cbd3c47fe55f0035380d791f7cc47f5_58.png)

![](img/1cbd3c47fe55f0035380d791f7cc47f5_60.png)

本节课中我们一起学习了如何将一个完整的猜单词游戏分解为多个函数来实现，包括获取输入、检查状态、显示界面和绘制图形。我们还预告了下一个项目——票务管理系统，并介绍了平行向量的概念，即使用多个索引对齐的向量来管理相关联的不同类型数据。掌握这些技能对于构建更复杂、结构更清晰的程序至关重要。