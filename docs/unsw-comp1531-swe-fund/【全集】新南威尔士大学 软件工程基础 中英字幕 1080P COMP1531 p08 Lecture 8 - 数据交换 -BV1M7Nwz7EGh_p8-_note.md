# 软件工程基础：第8讲：数据交换 📡

![](img/96822b5c0dd7257b1aac86c81918d9a3_1.png)

在本节课中，我们将要学习数据交换。这是计算机科学中一个至关重要的概念，它支撑着未来数月乃至数年里你将进行的许多工作。我们将首先从哲学角度探讨标准接口，然后深入研究三种用于以标准方式表示或传输数据的具体技术。

## 什么是标准接口？🤔

上一节我们介绍了数据交换的重要性，本节中我们来看看其核心思想：标准接口。

标准接口是一种连接不同系统的通用方法。它是一套被广泛认可的简单规则，有助于系统间相互通信。虽然它可能无法处理所有边缘情况，但其核心目标是促进互操作性。

以下是标准接口的一些常见例子：

![](img/96822b5c0dd7257b1aac86c81918d9a3_3.png)

*   **USB 电缆**：可以在不同设备（如手机、电脑、耳机）之间实现物理连接和数据传输。
*   **螺栓和螺钉**：尽管由不同公司制造，但尺寸（如M4螺栓）遵循统一标准。
*   **互联网协议**：例如HTTP，它是网络上交换网页的标准协议。
*   **铁轨轨距**：不同地区可能采用不同标准，但标准化的轨距使得跨国铁路运输成为可能。

所有这些系统都有一个共同点：它们提供了一种连接不同系统的通用方法。

![](img/96822b5c0dd7257b1aac86c81918d9a3_5.png)

## 数据交换格式 📄

在软件领域，应用程序系统交互最重要的方式之一就是数据传输。我们需要一种标准接口来让数据在不同系统间流动，这就是数据交换格式。

数据交换格式是一种足够简单的“语言”，能让所有人都能理解。它就像人类社会中的挥手告别或微笑，是跨文化的通用表达方式。

本节课我们将讨论三种格式。其中一些更多地用于数据交换，另一些则用于标准数据表示。

![](img/96822b5c0dd7257b1aac86c81918d9a3_7.png)

### JSON：JavaScript 对象表示法

![](img/96822b5c0dd7257b1aac86c81918d9a3_9.png)

我们将要讨论的主要格式是JSON。JSON是一种简单的标记语言，主要用于描述对象、数字、字符串和布尔值。它功能并不丰富，但非常轻量。

![](img/96822b5c0dd7257b1aac86c81918d9a3_11.png)

JSON代表JavaScript Object Notation。尽管名称中包含JavaScript，但它实际上与JavaScript关系不大，在其他非JavaScript语言中同样是一种标准。

JSON是一种轻量级的、基于文本的、独立于语言的数据交换格式。
*   **轻量级**意味着简单。
*   **基于文本**意味着它完全由字符表示，人类可以直接阅读。
*   **独立于语言**意味着无论你使用C、JavaScript还是其他语言，它都能工作。

![](img/96822b5c0dd7257b1aac86c81918d9a3_13.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_14.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_16.png)

JSON的语法与JavaScript数据结构非常相似，它使用花括号 `{}` 表示对象，方括号 `[]` 表示数组，所有非数字项都需要用双引号 `""` 包裹。

![](img/96822b5c0dd7257b1aac86c81918d9a3_18.png)

以下是一个JSON示例，表示一个包含地点列表的对象：

```json
{
  "locations": [
    {
      "suburb": "Kensington",
      "postcode": 2033
    },
    {
      "suburb": "Randwick",
      "postcode": 2031
    }
  ]
}
```

![](img/96822b5c0dd7257b1aac86c81918d9a3_20.png)

与JavaScript对象的主要区别在于：
1.  JSON**不允许**在数组或对象末尾使用尾随逗号。
2.  JSON中对象的键**必须**是字符串，并且**必须**用双引号包裹。

![](img/96822b5c0dd7257b1aac86c81918d9a3_22.png)

JSON的强大之处在于，大多数编程语言都内置或通过库支持读写JSON。这些库的作用通常是将语言特定的数据结构转换为JSON字符串（因为JSON本质上是文本），或者将JSON字符串解析回该语言的数据结构。

以下是使用JavaScript读写JSON文件的核心代码示例：

**将数据写入JSON文件：**
```javascript
const fs = require('fs');
const dataStructure = { locations: [ { suburb: "Kensington", postcode: 2033 } ] };

// 将JavaScript对象转换为JSON字符串
const jsonString = JSON.stringify(dataStructure);

// 将JSON字符串写入文件
fs.writeFileSync('export.json', jsonString, { flag: 'w' });
```

**从JSON文件读取数据：**
```javascript
const fs = require('fs');

// 从文件读取文本（JSON字符串）
const jsonStringFromFile = fs.readFileSync('export.json', { encoding: 'utf8', flag: 'r' });

![](img/96822b5c0dd7257b1aac86c81918d9a3_24.png)

// 将JSON字符串解析为JavaScript对象
const parsedData = JSON.parse(jsonStringFromFile);

![](img/96822b5c0dd7257b1aac86c81918d9a3_26.png)

// 现在可以使用数据了
console.log(parsedData.locations[0].suburb); // 输出: Kensington
```

![](img/96822b5c0dd7257b1aac86c81918d9a3_28.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_30.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_32.png)

这个过程同样适用于其他语言。例如，在Python中，你可以使用内置的 `json` 库来读取由JavaScript程序生成的 `export.json` 文件。

```python
import json

with open('export.json', 'r') as file:
    data = json.load(file)
    print(data['locations'][0]['suburb'])  # 输出: Kensington
```

JSON本身不是数据存储，也不是编程语言。它是一种标准接口定义，一种用于表示数据的文本格式，就像CSV文件一样。它是在不同语言间传输数据的桥梁。

### YAML：YAML Ain‘t Markup Language

![](img/96822b5c0dd7257b1aac86c81918d9a3_34.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_36.png)

YAML是一种流行的现代数据交换格式，以其易于编辑和简洁性而闻名。你可以将其视为JSON的替代品，两者各有优劣，并无绝对好坏。

JSON更常用于存储数据和通过网络传输数据。YAML则更常用于配置文件，例如项目的 `package.json` 如果换成YAML格式可能会更简洁。

![](img/96822b5c0dd7257b1aac86c81918d9a3_38.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_40.png)

YAML的核心特点是**缩进有意义**。它不使用花括号、方括号和大量引号，而是依靠缩进和短横线 `-` 来表示数据结构。

以下YAML代码等价于之前展示的JSON示例：

```yaml
locations:
  - suburb: Kensington
    postcode: 2033
  - suburb: Randwick
    postcode: 2031
```

*   最左侧的 `locations:` 是主对象的键。
*   缩进表示属于该键的内容。
*   短横线 `-` 表示列表中的一个新项。

![](img/96822b5c0dd7257b1aac86c81918d9a3_42.png)

与JSON相比，YAML的表示更加紧凑，可读性更强，特别适合编写配置文件。但在本课程中，我们主要使用JSON，YAML可能仅在某些场景下被提及。

![](img/96822b5c0dd7257b1aac86c81918d9a3_44.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_45.png)

### XML：可扩展标记语言

![](img/96822b5c0dd7257b1aac86c81918d9a3_47.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_48.png)

XML是一种较为陈旧的表达数据的方式。它看起来复杂且冗长，其根源与HTML类似。

XML的每个元素都需要开始和结束标签，导致数据与结构代码的比例很低，大部分内容都是样板标签。在JSON和YAML流行之前，XML曾广泛用于网络数据交互。

![](img/96822b5c0dd7257b1aac86c81918d9a3_50.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_52.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_54.png)

以下XML代码同样等价于之前的示例：

![](img/96822b5c0dd7257b1aac86c81918d9a3_56.png)

```xml
<root>
  <locations>
    <location>
      <suburb>Kensington</suburb>
      <postcode>2033</postcode>
    </location>
    <location>
      <suburb>Randwick</suburb>
      <postcode>2031</postcode>
    </location>
  </locations>
</root>
```

![](img/96822b5c0dd7257b1aac86c81918d9a3_58.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_59.png)

XML在现代语言中已较少使用，本课程也不会涉及。了解它的存在是为了让大家对数据交换格式的演进有一个完整的认识。

## 总结 📝

![](img/96822b5c0dd7257b1aac86c81918d9a3_61.png)

![](img/96822b5c0dd7257b1aac86c81918d9a3_63.png)

本节课中我们一起学习了数据交换的核心概念。我们首先探讨了标准接口的哲学意义，即作为连接不同系统的通用桥梁。然后，我们深入研究了三种具体的数据交换格式：

1.  **JSON**：我们重点学习的格式。它是一种轻量级、基于文本、语言无关的数据交换格式，广泛用于网络数据传输和存储。核心操作是 `JSON.stringify()`（序列化）和 `JSON.parse()`（反序列化）。
2.  **YAML**：一种更简洁的格式，依赖缩进语法，常用于配置文件，作为JSON的替代选择。
3.  **XML**：一种较旧的标记语言，结构冗长，在现代开发中已不常用，但为了知识完整性有所了解。

![](img/96822b5c0dd7257b1aac86c81918d9a3_65.png)

本课程将主要聚焦于JSON的应用。理解这些格式背后的“为什么”比记住具体语法更重要，它们体现了软件工程中标准化和互操作性的核心思想。