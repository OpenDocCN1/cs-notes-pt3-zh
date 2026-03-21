# 011：数组与向量 part3 🎯

![](img/e1e0a6021328e1f91c111c57045d41aa_0.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_2.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_4.png)

在本节课中，我们将继续学习向量（vector）的高级操作，包括如何查找最大值、计算平均值，以及实现两种基础的排序算法：选择排序和插入排序。最后，我们将通过一个井字棋游戏的例子，学习如何使用向量的向量（二维向量）来构建一个简单的游戏棋盘。

![](img/e1e0a6021328e1f91c111c57045d41aa_6.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_7.png)

---

![](img/e1e0a6021328e1f91c111c57045d41aa_9.png)

## 查找最大值与计算平均值 🔍

![](img/e1e0a6021328e1f91c111c57045d41aa_11.png)

上一节我们介绍了向量的基本操作。本节中，我们来看看如何从向量中提取有用的信息，例如最大值和平均值。

### 查找最大值
要找到一个整数向量中的最大值，我们可以遍历整个向量，并不断更新当前找到的最大值。

**核心思路**：
1.  假设第一个元素是最大值。
2.  遍历后续的每个元素。
3.  如果当前元素比已知的最大值更大，则更新最大值。

![](img/e1e0a6021328e1f91c111c57045d41aa_13.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_14.png)

**代码实现**：
```cpp
int getMax(const vector<int>& numbers) {
    int largest = numbers[0]; // 假设第一个元素最大
    for (int i = 1; i < numbers.size(); ++i) {
        if (numbers[i] > largest) {
            largest = numbers[i]; // 发现更大的值，更新最大值
        }
    }
    return largest;
}
```

### 计算平均值
计算平均值需要将所有元素相加，然后除以元素的总数。需要注意的是，为了避免整数除法丢失精度，总和应使用`double`类型。

**代码实现**：
```cpp
double getAverage(const vector<int>& numbers) {
    double total = 0.0; // 使用double类型存储总和
    for (int value : numbers) {
        total += value; // 累加所有值
    }
    return total / numbers.size(); // 返回平均值
}
```

---

## 排序算法：选择排序与插入排序 📊

理解了如何获取数据后，我们来看看如何组织数据。排序是编程中的常见任务，我们将实现两种基础的排序算法。

### 选择排序
选择排序的思路是：重复从未排序的部分中找到最大（或最小）的元素，并将其放到已排序部分的末尾。

**算法步骤**：
1.  从最后一个位置开始，作为待放置最大元素的位置。
2.  在未排序的部分（从第一个元素到当前待放置位置）中找到最大元素的索引。
3.  将该最大元素与待放置位置的元素进行交换。
4.  将待放置位置向前移动一位，重复步骤2-3，直到所有元素排序完成。

![](img/e1e0a6021328e1f91c111c57045d41aa_16.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_18.png)

**代码实现**：
```cpp
void selectionSort(vector<int>& numbers) {
    for (int indexToPutBiggest = numbers.size() - 1; indexToPutBiggest > 0; --indexToPutBiggest) {
        int indexOfBiggest = 0; // 假设第一个元素最大
        // 在 0 到 indexToPutBiggest 的范围内寻找最大元素的索引
        for (int indexToCompare = 1; indexToCompare <= indexToPutBiggest; ++indexToCompare) {
            if (numbers[indexToCompare] > numbers[indexOfBiggest]) {
                indexOfBiggest = indexToCompare;
            }
        }
        // 将找到的最大元素交换到目标位置
        int temp = numbers[indexToPutBiggest];
        numbers[indexToPutBiggest] = numbers[indexOfBiggest];
        numbers[indexOfBiggest] = temp;
    }
}
```

![](img/e1e0a6021328e1f91c111c57045d41aa_20.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_22.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_24.png)

### 插入排序
插入排序通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。

![](img/e1e0a6021328e1f91c111c57045d41aa_26.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_28.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_30.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_32.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_34.png)

**算法步骤**：
1.  假设第一个元素自身已经是有序的。
2.  取下一个元素，在已经排序的元素序列中从后向前扫描。
3.  如果该元素（已排序）大于新元素，将该元素移到下一位置。
4.  重复步骤3，直到找到已排序的元素小于或等于新元素的位置。
5.  将新元素插入到该位置后。
6.  重复步骤2~5，直到所有元素排序完成。

**代码实现**：
```cpp
void insertionSort(vector<int>& numbers) {
    for (int indexToSort = 1; indexToSort < numbers.size(); ++indexToSort) {
        for (int indexToSwap = indexToSort; indexToSwap > 0; --indexToSwap) {
            if (numbers[indexToSwap] < numbers[indexToSwap - 1]) {
                // 交换元素
                int temp = numbers[indexToSwap];
                numbers[indexToSwap] = numbers[indexToSwap - 1];
                numbers[indexToSwap - 1] = temp;
            } else {
                break; // 如果不需要交换，则中断内层循环
            }
        }
    }
}
```

**性能对比**：选择排序无论数据是否有序，都需要进行大量比较。而插入排序在数据已经基本有序的情况下会快很多，但在数据完全逆序时，性能与选择排序类似。

---

## 应用：使用二维向量构建井字棋游戏 🎮

掌握了向量的基本操作和排序后，我们可以进行更复杂的应用。下面我们将使用“向量的向量”（即二维向量）来模拟一个井字棋游戏的棋盘。

### 初始化棋盘
棋盘可以看作是一个3x3的网格，我们用二维向量`vector<vector<char>>`来表示，每个位置初始为空格。

**代码示例**：
```cpp
vector<vector<char>> board = {
    {' ', ' ', ' '},
    {' ', ' ', ' '},
    {' ', ' ', ' '}
};
```
要访问特定位置，例如第1行第2列（索引从0开始），可以使用`board[1][2]`。

### 游戏主循环
游戏的主逻辑是一个循环，直到游戏结束（分出胜负或平局）为止。

**伪代码框架**：
```cpp
char currentPlayer = 'X';
while (!isGameOver(board)) {
    printBoard(board);
    markBoard(board, currentPlayer);
    // 切换玩家
    currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
}
printBoard(board); // 打印最终棋盘
```

### 核心功能函数
以下是实现游戏所需的一些关键函数：

![](img/e1e0a6021328e1f91c111c57045d41aa_36.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_38.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_40.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_42.png)

**1. 打印棋盘**
```cpp
void printBoard(const vector<vector<char>>& board) {
    for (int i = 0; i < 3; ++i) {
        cout << board[i][0] << "|" << board[i][1] << "|" << board[i][2] << endl;
        if (i < 2) {
            cout << "-----" << endl;
        }
    }
}
```

![](img/e1e0a6021328e1f91c111c57045d41aa_44.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_46.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_48.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_49.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_51.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_53.png)

**2. 判断游戏是否结束**
游戏结束的条件是：有一方获胜，或者棋盘已满（平局）。
```cpp
bool isGameOver(const vector<vector<char>>& board) {
    return hasWinner(board) || isTied(board);
}
```

![](img/e1e0a6021328e1f91c111c57045d41aa_55.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_57.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_59.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_61.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_63.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_65.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_67.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_69.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_71.png)

**3. 判断是否平局**
如果棋盘上没有任何空格，则为平局。
```cpp
bool isTied(const vector<vector<char>>& board) {
    for (const auto& row : board) {
        for (char spot : row) {
            if (spot == ' ') {
                return false; // 发现空格，游戏未平局
            }
        }
    }
    return true; // 没有空格，游戏平局
}
```

**4. 判断是否有获胜者**
获胜的条件是：任意一行、一列或一条对角线上的三个字符相同且不为空格。
```cpp
bool hasWinner(const vector<vector<char>>& board) {
    // 检查行
    for (const auto& row : board) {
        if (row[0] != ' ' && row[0] == row[1] && row[0] == row[2]) {
            return true;
        }
    }
    // 检查列
    for (int col = 0; col < 3; ++col) {
        if (board[0][col] != ' ' && board[0][col] == board[1][col] && board[0][col] == board[2][col]) {
            return true;
        }
    }
    // 检查对角线
    if (board[1][1] != ' ') {
        if ((board[0][0] == board[1][1] && board[0][0] == board[2][2]) ||
            (board[0][2] == board[1][1] && board[0][2] == board[2][0])) {
            return true;
        }
    }
    return false;
}
```

**5. 玩家落子**
此函数需要修改棋盘，因此参数必须为引用。它需要处理玩家的输入，并确保输入有效（位置在范围内且该位置为空）。
```cpp
void markBoard(vector<vector<char>>& board, char currentPlayer) {
    int row, col;
    cout << "Player " << currentPlayer << "'s turn. Enter row and column (0-2): ";
    cin >> row >> col;

    // 验证输入有效性
    while (row < 0 || row > 2 || col < 0 || col > 2 || board[row][col] != ' ') {
        cout << "Invalid move. Try again: ";
        cin >> row >> col;
    }
    board[row][col] = currentPlayer; // 在棋盘上标记
}
```

![](img/e1e0a6021328e1f91c111c57045d41aa_73.png)

---

![](img/e1e0a6021328e1f91c111c57045d41aa_75.png)

## 总结 📝

![](img/e1e0a6021328e1f91c111c57045d41aa_77.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_79.png)

本节课中我们一起学习了向量的更多实用操作。我们掌握了如何从向量中查找最大值和计算平均值。接着，我们深入探讨了两种基础的排序算法——选择排序和插入排序，并理解了它们的工作原理和代码实现。最后，我们通过构建一个完整的井字棋游戏，综合运用了二维向量的概念，实践了函数分解、游戏逻辑设计和用户交互处理。这些知识为处理更复杂的数据结构和算法问题奠定了坚实的基础。