

## Trees

- 在本文中，我用来说明树结构的第一个例子是诺曼王朝 (诺曼王朝 (1066年–1135)) 的皇室家谱：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_425_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_425_1.png)

- 这个例子有助于定义术语：
  - William I 是树的*root*。
  - Adela 是 William I 的 *child* 并且是 Stephen 的 *parent*。
  - Robert、William II、Adela 和 Henry I 是 *siblings*。
  - Henry II 是 William I、Henry I 和 Matilda 的 *descendant*。
  - William I 是此树中其他所有人的 *ancestor*。

## Family Trees

- 英格兰皇室的家谱可能变得非常复杂。例如，右边的树就展示了玫瑰战争时期的皇室血统，涵盖了金雀花王朝、约克家族和兰开斯特家族。
- 这种树状图非常有帮助，例如，如果你想理解莎士比亚的历史剧。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_426_0.png)

## Family Trees

而这里是我最喜欢的来自 J. R. R. Tolkien（《指环王》）的家谱：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_427_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_427_1.png)

## Trees Are Everywhere

- 进化树的结构在恩斯特·海克尔 1866 年的生命之树图示中体现得更为清晰。
- 过去 150 年间，进化树图的细节发生了显著变化，但其总体结构——从单一根部开始并分支形成新的谱系——保持不变。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_429_0.png)

## Representing Family Trees

- 编写处理树的程序的第一步是设计合适的数据结构。
- 在图表形式中，目标是将树状图转换为如下所示的内部表示：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_430_0.png)

## A Recursive Definition for Trees

- 当你以表示其内部结构为目的思考树时，以下定义非常有用：
  - 一个 *tree* 是一个指向节点的指针。
  - 一个 *node* 是一个包含若干棵树的结构，通常还包含一些额外的数据。
- 尽管这个定义明显是循环的，但它不一定是无限的，因为
  - 树指针可以是 `NULL` 表示空树。
  - 节点可以包含一个空的子列表。
- 在 C++ 中，程序员通常定义一个结构或对象类型来表示节点，然后使用显式的指针类型来表示树。

## The familytree.h Interface

```
/*
 * File: familytree.h
 * -------------
 * This file is an interface to a simple class that represents
 * an individual person in a family tree.
 */

#ifndef _familytree_h
#define _familytree_h

#include <string>
#include "vector.h"

/*
 * Class: PersonNode
 * -------------
 * This class defines the structure of an individual in the family
 * tree, which consists of a name and a vector of children.
 */

class PersonNode {
public:
```

## The familytree.h Interface

```
/*
 * Constructor: PersonNode
 * Usage: PersonNode *person = new PersonNode(name);
 * ------------------------------------------------
 * This function constructs a new PersonNode with the specified
 * name. The newly constructed entry has no children, but clients
 * can add children by calling the addChild method.
 */
PersonNode(std::string name);

/*
 * Method: getName
 * Usage: string name = person->getName();
 * ------------------------------------------------
 * Returns the name of the person.
 */
std::string getName();

/*
 * Method: addChild
 * Usage: person->addChild(child);
 * ------------------------------------------------
 * Adds child to the end of the list of children for person, and
 * makes person the parent of child.
 */
void addChild(PersonNode *child);
```
