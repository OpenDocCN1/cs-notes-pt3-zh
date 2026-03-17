# 014：证明与遍历 🌳

![](img/e27caf7ee56efecf116f85e5d9af8ac3_1.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_3.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_5.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_7.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_9.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_11.png)

在本节课中，我们将继续学习树结构。我们将从证明一个关于二叉树空指针数量的定理开始，然后探讨如何遍历树结构，并实现一种称为“前序遍历”的算法。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_13.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_15.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_17.png)

---

![](img/e27caf7ee56efecf116f85e5d9af8ac3_19.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_21.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_23.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_25.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_27.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_28.png)

## 树与链表的相似性

![](img/e27caf7ee56efecf116f85e5d9af8ac3_30.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_31.png)

上一节我们介绍了树的基本概念。树与我们之前学习的链表非常相似，但我们将对树进行更深入的探讨。实际上，我们将在本月的大部分时间里研究树结构。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_33.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_34.png)

在硬件层面，树的节点在内存中的实际布局如下图所示。每个节点包含数据以及指向左子树和右子树的指针。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_36.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_38.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_1.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_40.png)

虽然内存布局图看起来有些复杂，但为了便于理解和推理，我们通常采用左侧这种更直观的图形化表示方式。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_41.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_42.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_11.png)

然而，一个常见的疑问是：与链表相比，树似乎浪费了大量空间。在链表中，我们只有一个空指针（尾指针）。但在二叉树中，我们似乎有很多空指针。例如，在下图所示的树中，有8个数据节点，却有9个空指针。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_44.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_45.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_46.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_17.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_48.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_50.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_52.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_54.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_56.png)

本节中，我们将通过一个证明来精确计算任意二叉树中空指针的数量。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_58.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_60.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_61.png)

---

![](img/e27caf7ee56efecf116f85e5d9af8ac3_63.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_65.png)

## 定理：二叉树空指针数量证明 🔍

![](img/e27caf7ee56efecf116f85e5d9af8ac3_67.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_69.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_71.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_73.png)

我们的定理是：在一个包含 `n` 个节点的二叉树中，空指针的数量是 `n + 1`。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_75.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_77.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_79.png)

为了证明这一点，我们首先进行一些直观的验证。观察上面的例子，`n = 8`，空指针数量为 `9`，符合 `n + 1`。我们再检查几个小例子：
*   包含 `0` 个节点的树（空树）：有 `1` 个空指针（根指针）。`0 + 1 = 1`，成立。
*   包含 `1` 个节点的树：有 `2` 个空指针。`1 + 1 = 2`，成立。
*   包含 `2` 个节点的树：所有可能的结构都有 `3` 个空指针。`2 + 1 = 3`，成立。
*   包含 `3` 个节点的树：所有可能的结构都有 `4` 个空指针。`3 + 1 = 4`，成立。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_81.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_82.png)

这些基础案例增强了我们的信心。现在，我们使用数学归纳法进行正式证明。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_84.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_86.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_87.png)

### 归纳证明步骤

![](img/e27caf7ee56efecf116f85e5d9af8ac3_89.png)

1.  **定义函数**：设 `nulls(n)` 为具有 `n` 个节点的二叉树中的空指针数量。
2.  **归纳假设**：假设对于所有 `n < k`（其中 `k > 0`），定理成立，即 `nulls(n) = n + 1`。
3.  **归纳步骤**：考虑一个任意具有 `k` 个节点的二叉树 `T`。
    *   任何二叉树 `T` 都可以看作由一个根节点、一个左子树和一个右子树组成。
    *   设左子树有 `m` 个节点（`0 ≤ m ≤ k-1`），则右子树有 `(k - m - 1)` 个节点。
    *   根据归纳假设：
        *   左子树的空指针数为 `nulls(m) = m + 1`
        *   右子树的空指针数为 `nulls(k - m - 1) = (k - m - 1) + 1 = k - m`
    *   整个树 `T` 的空指针数等于左、右子树空指针数之和（注意：根节点本身没有空指针，其左右指针的空性已计入子树）：
        ```
        nulls(k) = nulls(m) + nulls(k - m - 1)
                 = (m + 1) + (k - m)
                 = k + 1
        ```
4.  **结论**：因此，对于 `n = k`，定理也成立。结合基础案例，由数学归纳法可知，对于所有 `n ≥ 0`，定理 `nulls(n) = n + 1` 成立。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_91.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_93.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_95.png)

这个证明的关键在于将树递归地分解为根节点和两个更小的子树，这正是处理树和图这类递归数据结构时常用的技巧。这种“分解”思想与递归算法本身的结构是相呼应的。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_97.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_99.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_101.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_103.png)

---

![](img/e27caf7ee56efecf116f85e5d9af8ac3_105.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_107.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_109.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_110.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_112.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_114.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_116.png)

## 树的遍历 🚶

![](img/e27caf7ee56efecf116f85e5d9af8ac3_118.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_120.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_121.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_123.png)

在链表中，遍历是直接的：从头节点开始，依次访问下一个节点，直到末尾。但对于树，访问所有节点的方式有多种选择。本节我们来看看其中一种最简单的方式：**前序遍历**。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_125.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_126.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_127.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_128.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_130.png)

前序遍历的定义是递归的：
1.  访问根节点。
2.  前序遍历左子树。
3.  前序遍历右子树。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_132.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_133.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_135.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_137.png)

以下是一个简单的二叉树示例，我们手动模拟前序遍历的过程：

![](img/e27caf7ee56efecf116f85e5d9af8ac3_139.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_141.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_141.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_143.png)

遍历顺序为：`+ a * b c`。算法会递归地访问每个节点，当遇到空指针（`null`）时，递归调用返回。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_145.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_147.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_149.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_150.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_152.png)

### 前序遍历的C++实现

![](img/e27caf7ee56efecf116f85e5d9af8ac3_154.png)

以下是前序遍历算法的C++递归实现代码：

![](img/e27caf7ee56efecf116f85e5d9af8ac3_155.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_157.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_158.png)

```cpp
void preOrderTraversal(Node* cur) {
    if (cur) { // 如果当前节点不为空（非null）
        // 1. 访问根节点（此处操作为打印数据）
        std::cout << cur->data << " ";

        // 2. 前序遍历左子树
        preOrderTraversal(cur->left);

        // 3. 前序遍历右子树
        preOrderTraversal(cur->right);
    }
    // 如果 cur 为 null，则直接返回（递归的基态）
}
```

![](img/e27caf7ee56efecf116f85e5d9af8ac3_160.png)

代码说明：
*   `if (cur)` 是 `if (cur != nullptr)` 的简写，在C/C++中，空指针在布尔上下文中为 `false`，非空指针为 `true`。
*   访问节点的操作（`std::cout`）可以替换为任何需要对节点数据进行的处理。
*   递归会深入到每个子树，直到遇到空节点后逐层返回。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_162.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_164.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_166.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_168.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_169.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_171.png)

### 算法复杂度分析

![](img/e27caf7ee56efecf116f85e5d9af8ac3_173.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_175.png)

前序遍历的时间复杂度是 **O(n)**，其中 `n` 是树中的节点数。因为每个节点恰好被访问一次，并且每个递归调用只产生常数时间的开销（不包括递归调用本身）。同时，这也是一个 **Ω(n)** 的操作，因为要遍历所有节点，所以其运行时间是严格的线性时间 Θ(n)。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_177.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_179.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_181.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_183.png)

对于树的操作，递归实现通常比迭代实现更简洁易懂，因此在课程中，我们主要使用递归方式。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_185.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_187.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_188.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_190.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_191.png)

---

![](img/e27caf7ee56efecf116f85e5d9af8ac3_193.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_195.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_196.png)

## 总结

![](img/e27caf7ee56efecf116f85e5d9af8ac3_198.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_200.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_202.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_204.png)

本节课中我们一起学习了两个核心内容：
1.  **定理证明**：我们使用数学归纳法证明了在包含 `n` 个节点的二叉树中，空指针的数量恰好为 `n + 1`。这个证明展示了处理递归数据结构时，将其分解为更小子结构的通用证明技巧。
2.  **树遍历**：我们介绍了**前序遍历**算法，它按照“根-左-右”的顺序访问树中的每个节点。我们给出了该算法的递归定义、手动模拟示例以及C++实现代码，并分析了其线性时间复杂度。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_206.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_207.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_209.png)

理解这些基础概念和技巧，是后续学习更复杂树形结构和算法的重要基石。