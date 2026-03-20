# 006：数据可视化

![](img/b578a31cadf51c1161c87af9767384e1_0.png)

![](img/b578a31cadf51c1161c87af9767384e1_2.png)

![](img/b578a31cadf51c1161c87af9767384e1_3.png)

在本节课中，我们将学习如何使用R语言中的`ggplot2`包来创建数据可视化图表。我们将从基础概念开始，逐步构建不同类型的图表，包括柱状图、散点图和折线图。

![](img/b578a31cadf51c1161c87af9767384e1_5.png)

![](img/b578a31cadf51c1161c87af9767384e1_6.png)

![](img/b578a31cadf51c1161c87af9767384e1_8.png)

## 概述：图形语法

`ggplot2`是`tidyverse`生态系统的一部分，它基于“图形语法”的理念。这意味着我们可以通过组合不同的组件来构建图表。核心组件包括：
*   **数据**：要可视化的表格。
*   **几何对象**：图表的视觉表现形式，如柱状、点或线。
*   **美学映射**：将数据中的列与图表的视觉特征（如x轴、y轴、颜色）关联起来。
*   **标度**：控制美学映射如何呈现，例如坐标轴的范围或颜色的分配。
*   **图层**：通过`+`运算符将上述组件叠加到基础画布上。

![](img/b578a31cadf51c1161c87af9767384e1_10.png)

![](img/b578a31cadf51c1161c87af9767384e1_11.png)

![](img/b578a31cadf51c1161c87af9767384e1_13.png)

![](img/b578a31cadf51c1161c87af9767384e1_14.png)

上一节我们介绍了图形语法的基本概念，本节中我们来看看如何用代码实现它。

![](img/b578a31cadf51c1161c87af9767384e1_16.png)

## 创建柱状图

我们将从一个简单的数据集开始，它包含候选人及其得票数。

![](img/b578a31cadf51c1161c87af9767384e1_18.png)

```r
# 加载必要的库
library(tidyverse)

# 读取数据
votes <- read_csv("votes.csv")
# 数据示例
# candidate | votes
# Mario     | 100
# Peach     | 200
# Bowser    | 150
```

### 构建基础图表

![](img/b578a31cadf51c1161c87af9767384e1_20.png)

![](img/b578a31cadf51c1161c87af9767384e1_22.png)

首先，我们使用`ggplot()`函数创建一个基础画布，并指定数据和美学映射。

![](img/b578a31cadf51c1161c87af9767384e1_24.png)

```r
# 创建基础图表，定义数据和美学映射
p <- ggplot(data = votes, aes(x = candidate, y = votes))
```

![](img/b578a31cadf51c1161c87af9767384e1_26.png)

![](img/b578a31cadf51c1161c87af9767384e1_27.png)

运行上述代码会生成一个带有坐标轴但没有任何几何对象的空白图表。接下来，我们需要添加一个几何对象层来展示数据。

![](img/b578a31cadf51c1161c87af9767384e1_29.png)

以下是添加几何对象的步骤：

![](img/b578a31cadf51c1161c87af9767384e1_31.png)

![](img/b578a31cadf51c1161c87af9767384e1_32.png)

![](img/b578a31cadf51c1161c87af9767384e1_33.png)

![](img/b578a31cadf51c1161c87af9767384e1_34.png)

1.  使用`+`运算符添加一个图层。
2.  使用`geom_col()`函数来绘制柱状图。

![](img/b578a31cadf51c1161c87af9767384e1_36.png)

```r
# 添加柱状几何对象层
p <- p + geom_col()
print(p)
```

![](img/b578a31cadf51c1161c87af9767384e1_38.png)

现在，我们得到了一个基础的柱状图，x轴显示候选人，y轴显示得票数。`ggplot2`会自动处理许多细节，例如坐标轴标签和范围。

### 自定义图表

默认设置可能不总是符合我们的需求。我们可以通过添加更多图层来自定义图表。

![](img/b578a31cadf51c1161c87af9767384e1_40.png)

**调整y轴范围**

![](img/b578a31cadf51c1161c87af9767384e1_42.png)

假设我们希望y轴的上限是250，以便为最高柱形留出更多顶部空间。我们可以使用`scale_y_continuous()`函数来调整连续型y轴的标度。

```r
# 调整y轴标度的范围
p <- p + scale_y_continuous(limits = c(0, 250))
```

**添加和修改标签**

![](img/b578a31cadf51c1161c87af9767384e1_44.png)

![](img/b578a31cadf51c1161c87af9767384e1_45.png)

我们可以使用`labs()`函数来修改坐标轴标签和添加标题。

```r
# 添加和修改标签
p <- p + labs(
  x = "Candidate",
  y = "Votes",
  title = "Election Results"
)
```

![](img/b578a31cadf51c1161c87af9767384e1_47.png)

**根据数据为柱形着色**

![](img/b578a31cadf51c1161c87af9767384e1_49.png)

我们可以通过美学映射，将柱形的填充颜色与“候选人”这一列关联起来。这需要在`geom_col()`函数内部指定。

![](img/b578a31cadf51c1161c87af9767384e1_51.png)

![](img/b578a31cadf51c1161c87af9767384e1_52.png)

```r
# 首先，更新几何对象层，根据候选人设置填充色
p <- ggplot(data = votes, aes(x = candidate, y = votes)) +
  geom_col(aes(fill = candidate)) # fill美学映射到candidate列
```

![](img/b578a31cadf51c1161c87af9767384e1_54.png)

**使用对色盲友好的配色**

![](img/b578a31cadf51c1161c87af9767384e1_56.png)

`ggplot2`提供了`scale_fill_viridis_d()`函数，它可以应用一套对色盲友好的离散颜色标度。

```r
# 应用对色盲友好的填充色标度，并修改图例标题
p <- p + scale_fill_viridis_d(name = "Candidate")
```

![](img/b578a31cadf51c1161c87af9767384e1_58.png)

![](img/b578a31cadf51c1161c87af9767384e1_59.png)

**移除冗余图例**

由于x轴已经标明了候选人，右侧的颜色图例可能显得冗余。我们可以在`geom_col()`中关闭它。

![](img/b578a31cadf51c1161c87af9767384e1_61.png)

```r
# 在几何对象层中关闭图例显示
p <- ggplot(data = votes, aes(x = candidate, y = votes)) +
  geom_col(aes(fill = candidate), show.legend = FALSE)
```

![](img/b578a31cadf51c1161c87af9767384e1_63.png)

![](img/b578a31cadf51c1161c87af9767384e1_65.png)

**应用主题**

![](img/b578a31cadf51c1161c87af9767384e1_67.png)

![](img/b578a31cadf51c1161c87af9767384e1_68.png)

![](img/b578a31cadf51c1161c87af9767384e1_69.png)

![](img/b578a31cadf51c1161c87af9767384e1_70.png)

主题可以控制图表的整体外观，如背景色、网格线等。`theme_classic()`提供了一个简洁的经典主题。

![](img/b578a31cadf51c1161c87af9767384e1_72.png)

![](img/b578a31cadf51c1161c87af9767384e1_74.png)

```r
# 应用经典主题
p <- p + theme_classic()
```

![](img/b578a31cadf51c1161c87af9767384e1_76.png)

**保存图表**

最后，我们可以使用`ggsave()`函数将图表保存为图像文件。

```r
# 保存图表为PNG文件
ggsave(
  filename = "votes_plot.png",
  plot = p,
  width = 1200,
  height = 900,
  units = "px"
)
```

## 创建散点图

当数据包含两个连续变量时，散点图是展示它们之间关系的有效方式。我们使用一个糖果数据集，其中包含糖果的价格百分位数和糖分百分位数。

![](img/b578a31cadf51c1161c87af9767384e1_78.png)

```r
# 读取糖果数据
candy <- read_rds("candy.rds")
# 数据包含列：pricepercent, sugarpercent
```

![](img/b578a31cadf51c1161c87af9767384e1_80.png)

### 构建散点图

构建过程与柱状图类似：创建画布、定义美学映射、添加几何对象。

```r
# 创建散点图基础
p_scatter <- ggplot(data = candy, aes(x = pricepercent, y = sugarpercent))
```

对于散点图，我们使用`geom_point()`几何对象。

![](img/b578a31cadf51c1161c87af9767384e1_82.png)

```r
# 添加点几何对象层
p_scatter <- p_scatter + geom_point()
print(p_scatter)
```

![](img/b578a31cadf51c1161c87af9767384e1_84.png)

**处理点重叠**

![](img/b578a31cadf51c1161c87af9767384e1_86.png)

![](img/b578a31cadf51c1161c87af9767384e1_87.png)

如果多个数据点具有相同的x和y值，它们会重叠在一起。我们可以使用`geom_jitter()`来为点添加少量随机抖动，使其分开。

![](img/b578a31cadf51c1161c87af9767384e1_89.png)

![](img/b578a31cadf51c1161c87af9767384e1_91.png)

```r
# 使用抖动点来避免重叠
p_scatter <- p_scatter + geom_jitter()
```

**自定义点的外观**

![](img/b578a31cadf51c1161c87af9767384e1_93.png)

我们可以在几何对象函数内部直接设置美学参数（而不是映射），来统一改变所有点的外观。

![](img/b578a31cadf51c1161c87af9767384e1_95.png)

![](img/b578a31cadf51c1161c87af9767384e1_97.png)

```r
# 自定义点的颜色、大小和形状
p_scatter <- ggplot(data = candy, aes(x = pricepercent, y = sugarpercent)) +
  geom_jitter(
    color = "darkorchid4", # 边框颜色
    fill = "orchid",       # 填充颜色（对某些形状有效）
    shape = 21,            # 形状编号（21是有边框的圆）
    size = 2               # 点的大小
  ) +
  labs(
    x = "Price Percentile",
    y = "Sugar Percentile",
    title = "Price and Sugar"
  ) +
  theme_classic()
```

## 创建折线图（时间序列）

折线图非常适合展示数据随时间的变化趋势。我们使用飓风Anita的风速观测数据。

![](img/b578a31cadf51c1161c87af9767384e1_99.png)

```r
# 读取飓风数据
anita <- read_rds("anita.rds")
# 数据包含列：timestamp, wind
```

### 构建折线图

![](img/b578a31cadf51c1161c87af9767384e1_101.png)

![](img/b578a31cadf51c1161c87af9767384e1_103.png)

我们将时间戳映射到x轴，风速映射到y轴。

```r
# 创建折线图基础
p_line <- ggplot(data = anita, aes(x = timestamp, y = wind))
```

为了同时显示数据点和连接线，我们可以叠加两个几何对象层。**图层的顺序很重要**，后添加的图层会绘制在先添加的图层之上。

![](img/b578a31cadf51c1161c87af9767384e1_105.png)

![](img/b578a31cadf51c1161c87af9767384e1_107.png)

```r
# 先添加线，再添加点，这样点会绘制在线的上方
p_line <- p_line +
  geom_line(color = "black", linewidth = 0.5) + # 添加线层
  geom_point(color = "deepskyblue4", size = 2)   # 添加点层
```

![](img/b578a31cadf51c1161c87af9767384e1_109.png)

**添加参考线**

我们可以添加一条水平参考线来标记飓风形成的风速阈值（65节）。

```r
# 添加一条标记飓风阈值的水平参考线
p_line <- p_line +
  geom_hline(yintercept = 65, linetype = "dashed", color = "gray50")
```

**完善图表**

最后，添加标签和主题来完成图表。

```r
p_line <- p_line +
  labs(
    x = "Date",
    y = "Wind Speed (knots)",
    title = "Hurricane Anita Wind Speed Over Time"
  ) +
  theme_classic()
print(p_line)
```

![](img/b578a31cadf51c1161c87af9767384e1_111.png)

![](img/b578a31cadf51c1161c87af9767384e1_113.png)

## 总结

![](img/b578a31cadf51c1161c87af9767384e1_115.png)

本节课中我们一起学习了使用`ggplot2`包进行数据可视化的核心技能。我们掌握了图形语法的关键组成部分：数据、美学映射、几何对象、标度和图层。通过具体的例子，我们实践了如何创建和自定义柱状图、散点图和折线图。记住，好的可视化始于清晰的数据和明确的目标，通过`ggplot2`的分层语法，我们可以逐步构建出既美观又信息丰富的图表。