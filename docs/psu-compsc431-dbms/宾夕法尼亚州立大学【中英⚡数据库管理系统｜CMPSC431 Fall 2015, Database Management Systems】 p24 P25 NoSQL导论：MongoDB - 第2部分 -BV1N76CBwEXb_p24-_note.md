# 数据库管理系统：第24-25讲：NoSQL导论：MongoDB - 第2部分 🚀

## 概述
在本节课中，我们将继续学习MongoDB，完成NoSQL部分的介绍。我们将重点学习更新文档、查询结果的筛选与排序、以及聚合操作等核心功能。

---

## 课程安排与作业提醒
本周将进行第一次项目演示。演示时间表已发布，请各位同学查看。演示时，请确保已向数据库填充数据，并能通过一个简单的界面（如网页、GUI或手机应用）与数据库进行交互。

关于作业4，我们将使用一个Yelp数据集进行练习。如果发布时间较晚，截止日期会相应顺延。

---

## 回顾与衔接
上一节我们介绍了NoSQL的概念，并学习了MongoDB的基础知识，包括数据库、集合、文档和字段。我们还实践了CRUD操作中的创建、读取和删除。

本节中，我们将重点学习CRUD中的更新操作，并探索更多高级查询功能。

---

![](img/f914ddc5876808955acd34ad139da803_1.png)

![](img/f914ddc5876808955acd34ad139da803_3.png)

![](img/f914ddc5876808955acd34ad139da803_5.png)

## 数据准备
为了进行后续操作，我们需要重新插入“独角兽”数据。首先，切换到`unicorns`集合。

```javascript
use unicorns
```

然后，执行插入数据的脚本。现在，我们的集合中已包含所有独角兽的数据。

---

## 复杂查询：使用 `$or` 运算符
在查询4中，我们希望找到**雌性**独角兽，并且它们**要么**喜欢苹果，**要么**体重小于500磅。

在MongoDB中，我们使用 `find()` 函数进行查询。多个条件默认是“与”关系。要实现“或”逻辑，需要使用 `$or` 运算符。

以下是查询的构建方法：
1.  首先指定性别为雌性：`{gender: ‘f’}`。
2.  然后使用 `$or` 运算符列出“或”关系的条件。

```javascript
db.unicorns.find({
    gender: ‘f’,
    $or: [
        {loves: ‘apple’},
        {weight: {$lt: 500}}
    ]
})
```

这个查询的含义是：寻找性别为雌性，并且（喜欢苹果 或 体重小于500磅）的独角兽。

---

## 投影：选择返回的字段
默认情况下，`find()` 会返回文档的所有字段。为了只查看特定字段，我们可以使用**投影**，即在 `find()` 的第二个参数中指定要包含或排除的字段。

*   `1` 表示包含该字段。
*   `0` 表示排除该字段。

例如，如果我们只想查看独角兽的`name`和`weight`，并排除默认的 `_id` 字段：

```javascript
db.unicorns.find({}, {name: 1, weight: 1, _id: 0})
```

**注意**：在同一个投影对象中，不能混合使用包含和排除（`_id` 字段除外）。

---

## 更新文档操作
更新是CRUD中我们尚未学习的部分。MongoDB的更新操作需要特别注意，因为直接替换可能导致数据丢失。

### 错误示范：直接替换
如果我们想将名为“Roodles”的独角兽体重更新为590，**错误**的做法是：

```javascript
db.unicorns.update({name: ‘Roodles’}, {weight: 590})
```

这条命令会找到匹配 `{name: ‘Roodles’}` 的文档，然后用新文档 `{weight: 590}` **完全替换**它，导致其他字段全部丢失。

### 正确方法：使用 `$set` 运算符
正确的更新方法是使用 `$set` 运算符，它只修改指定的字段，而不影响其他字段。

```javascript
db.unicorns.update(
    {name: ‘Roodles’},
    {$set: {weight: 590}}
)
```

### 其他更新运算符
*   **`$inc` (递增)**：对数字字段进行增减。例如，将名为“Pilot”的独角兽杀死的吸血鬼数量减少2：

    ```javascript
    db.unicorns.update(
        {name: ‘Pilot’},
        {$inc: {vampires: -2}}
    )
    ```

*   **`$push`**：向数组字段添加元素。例如，为名为“Aurora”的独角兽的食物列表中添加“sugar”：

    ```javascript
    db.unicorns.update(
        {name: ‘Aurora’},
        {$push: {loves: ‘sugar’}}
    )
    ```

    如果原字段不是数组，`$push` 会将其转换为数组。

---

## 高级更新选项
### `upsert`
`upsert` 是 “update + insert” 的组合。如果找不到匹配的文档，则插入一个新文档。需要将 `upsert` 选项设为 `true`。

例如，更新一个不存在的独角兽“Walla”的吸血鬼数量，如果不存在则创建它：

```javascript
db.unicorns.update(
    {name: ‘Walla’},
    {$inc: {vampires: 1}},
    {upsert: true}
)
```

### `multi`
默认情况下，`update()` 只更新匹配的第一个文档。要更新所有匹配的文档，需要将 `multi` 选项设为 `true`。

例如，为所有独角兽添加“已接种疫苗”的字段：

```javascript
db.unicorns.update(
    {},
    {$set: {vaccinated: true}},
    {multi: true}
)
```

---

## 查询结果排序与限制
### 排序 (`sort()`)
我们可以使用 `sort()` 方法对查询结果进行排序。`1` 表示升序，`-1` 表示降序。

例如，按体重降序排列所有独角兽，并只显示姓名和体重：

```javascript
db.unicorns.find({}, {name:1, weight:1, _id:0}).sort({weight: -1})
```

也可以按多个字段排序，例如先按姓名升序，再按体重降序：

```javascript
.sort({name: 1, weight: -1})
```

### 限制数量 (`limit()`) 与跳过 (`skip()`)
*   `limit(n)`：只返回前 `n` 个结果。
*   `skip(n)`：跳过前 `n` 个结果。

例如，获取体重最重的5只独角兽：

```javascript
db.unicorns.find({}, {name:1, weight:1, _id:0}).sort({weight: -1}).limit(5)
```

获取体重第二和第三重的独角兽（跳过最重的1个，再取2个）：

```javascript
.sort({weight: -1}).skip(1).limit(2)
```

`skip()` 和 `limit()` 的执行顺序不影响结果。

---

## 计数操作 (`count()`)
`count()` 方法用于统计文档数量。

统计集合中所有独角兽的数量：

```javascript
db.unicorns.count()
```

统计满足条件的文档数量，例如杀死吸血鬼超过50只的独角兽：

```javascript
db.unicorns.count({vampires: {$gt: 50}})
```

这等价于先执行 `find()` 再计数：

```javascript
db.unicorns.find({vampires: {$gt: 50}}).count()
```

---

## 总结
本节课我们一起完成了MongoDB核心功能的学习。我们深入探讨了如何正确使用 `update()` 进行文档更新，包括 `$set`、`$inc`、`$push` 等运算符，以及 `upsert` 和 `multi` 选项。此外，我们还学习了如何使用投影筛选返回字段，如何对查询结果进行排序、限制和跳过，以及如何进行计数操作。

掌握这些操作后，你已具备使用MongoDB进行基本数据管理和查询的能力。请结合演示作业和即将发布的作业进行实践，以巩固所学知识。下节课我们将进入第6章的学习。