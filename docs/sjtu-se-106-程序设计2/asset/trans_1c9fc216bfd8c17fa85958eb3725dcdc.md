

## Maps and Hashing

Eric Roberts
CS 106B

## Part I: Basic Concepts

## An Illustrative Mapping Application

- 假设你想编写一个程序，根据两位邮政缩写显示州名。
- 这个程序是 Map 类的理想应用，因为你需要的是两位代码与州名之间的映射。每个两位代码唯一标识一个特定的州，因此可作为 Map 的键；州名是对应的值。
- 要在 C++ 中实现此程序，你需要执行以下步骤，这些步骤在下一张幻灯片中进行了说明：
  1. 创建一个 Map<string, string> 包含键/值对。
  2. 读取要翻译的两位缩写。
  3. 调用 Map 上的 get 来查找州名。
  4. 打印出州名。

## The PostalLookup Program

```
int main() {
    Map<string,string> stateMap;
    initStateMap(stateMap);
    while (true) {
        cout << "Enter two-letter state abbreviation: ";
        string code = getLine();
        if (code == "") break;
        if (stateMap.containsKey(code)) {
            cout << code << " = " << stateMap.get(code) << endl;
        } else {
            cout << code << " = ???" << endl;
        }
    }
}
```

PostalLookup
Enter two-letter state abbreviation: HI
HI = Hawaii
Enter two-letter state abbreviation: WI
WI = Wisconsin
Enter two-letter state abbreviation: VE
VE = ???
Enter two-letter state abbreviation:

- AL=Alabama
- AK=Alaska
- AZ=Arizona
- ...
- FL=Florida
- GA=Georgia
- HI=Hawaii
- ...
- WI=Wisconsin
- WY=Wyoming

## A Simplified Version of the Map Class

| Method | Description |
|---|---|
| `map.size()` | Returns the number of key/value pairs in the map. |
| `map.isEmpty()` | Returns **true** if the map is empty. |
| `map.clear()` | Removes all key/value pairs from the map. |
| `map.put(key, value)` | Makes an association between **key** and **value**, discarding any existing one. |
| `map.get(key)` | Returns the most recent value associated with **key**. |
| `map.containsKey(key)` | Returns **true** if there is a value associated with **key**. |

## Implementation Strategies for Maps

There are several strategies you might choose to implement the map operations `get` and `put`. Those strategies include:

- 1. *Linear search*. Keep track of all the name/value pairs in an array. In this model, both the `get` and `put` operations run in O(N) time.

## Exercise: Linear Search Map

As our programming exercise, we’ll build the linear search version of the map. We start with the `PostalLookup.cpp` program and the `map.h` interface. What we need to write are the following files:

- The `mappriv.h` file that describes the representation.
- The `mapimpl.cpp` file that implements the public methods.

## Implementation Strategies for Maps

There are several strategies you might choose to implement the map operations `get` and `put`. Those strategies include:

- 1. *Linear search*. Keep track of all the name/value pairs in an array. In this model, both the `get` and `put` operations run in O(N) time.
- 2. *Binary search*. If you keep the array sorted by the two-character code, you can use binary search to find the key. Using this strategy improves the performance of `get` to O(log N).
- 3. *Table lookup in a grid*. In this specific example, you can store the state names in a 26×26 `Grid<string>` in which the first and second indices correspond to the two letters in the code. Because you can now find any code in a single step, this strategy is O(1), although this performance comes at a cost in memory space.

## The Idea of Hashing

- 前一幻灯片中的第三种策略表明，可以使 `get` 和 `put` 操作运行得非常快，甚至达到查找键的成本与表中键的数量无关。 这种 $O(1)$ 性能只有在你知道在哪里查找特定键时才可能实现。
- 为了了解在实践中如何实现这一目标，有助于思考你在字典中查找单词的方式。大多数字典都有拇指标签，指示每个字母出现的位置。以 $A$ 开头的单词在 $A$ 部分，依此类推。
- 最常见的映射实现使用一种称为 *hashing* 的策略，其概念上类似于字典中的拇指标签。关键思想是，如果你使用键来确定查找位置，则可以极大地提高性能。

