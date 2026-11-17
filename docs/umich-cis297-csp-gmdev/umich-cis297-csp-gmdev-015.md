# 015：快艇骰子游戏（第一部分）

![](img/06e94836b3947e1792cafc0b09665c60_0.png)

## 概述
在本节课中，我们将开始构建一个快艇骰子游戏（Yatzy）。我们将学习如何运用面向对象的设计原则，规划并创建游戏所需的核心类，包括骰子（Dice）和记分卡（Scorecard）。我们将重点关注类的设计、属性的封装以及核心游戏逻辑的实现。

---

## 课程安排与项目更新

上一节我们完成了Yahtzee项目的提交。本节中，我们来看看后续的课程安排和新的项目。

以下是关于课程中期和后续的重要事项：

*   **研究讲座**：明天将有关于自动驾驶汽车中乘客情绪估计、以及CAD与结构分析无缝集成等主题的研究讲座，并提供免费食物。
*   **项目三**：新的项目（快艇骰子游戏）将于第7周截止。我们有两周时间来完成它。
*   **期中考试**：考试将在第7周进行，形式为开卷，时长为3小时。它更像是一个学习进度检查点。
*   **期中假期**：在第3个项目提交后，将有一个实际的假期。
*   **数据库编程**：期中之后，我们将进入为期两周的数据库编程专题学习。
*   **最终单元**：三月底开始，我们将学习通用Windows平台（UWP）和XAML编程，并可以在Xbox上运行程序。
*   **最终项目**：3月28日开始小组最终项目，这是一个2D雅达利风格的游戏克隆，将在4月25日进行演示。
*   **游戏实验室**：如需使用包含Xbox的游戏实验室，需要完成实验室安全测验并发送证书以获取门禁权限。
*   **额外资源**：图书馆的Skillsoft Books数据库提供了大量免费的编程和技术类电子书资源。

---

## 游戏设计与类规划

![](img/06e94836b3947e1792cafc0b09665c60_2.png)

![](img/06e94836b3947e1792cafc0b09665c60_4.png)

![](img/06e94836b3947e1792cafc0b09665c60_6.png)

![](img/06e94836b3947e1792cafc0b09665c60_8.png)

![](img/06e94836b3947e1792cafc0b09665c60_10.png)

在开始编码之前，我们需要进行设计。遵循良好的面向对象设计原则，我们应该先思考需要哪些类以及它们应该做什么，然后再构建用户界面。

我们分析游戏中的“名词”，可以确定以下几个核心类：

*   **骰子（Dice）**：管理一组（5个）骰子的投掷、数值和锁定状态。
*   **记分卡（Scorecard）**：记录玩家在所有得分项上的分数。
*   **玩家（Player）**：代表一个玩家，可以方便地管理多个玩家和回合。

我们将首先构建`Dice`和`Scorecard`类。

![](img/06e94836b3947e1792cafc0b09665c60_12.png)

---

![](img/06e94836b3947e1792cafc0b09665c60_14.png)

## 构建骰子（Dice）类

`Dice`类需要管理五个骰子的值、投掷次数以及每个骰子是否被“锁定”（即本轮不再重掷）。

### 属性与字段
我们使用私有列表来存储骰子值和锁定状态，并通过公共属性提供访问。

```csharp
public class Dice
{
    private List<int> _diceValues = new List<int> { 0, 0, 0, 0, 0 };
    private List<bool> _holdValues = new List<bool> { false, false, false, false, false };
    private Random _random = new Random();
    private static int _maxRolls = 3;
    private int _numberOfTimesRolled = 0;

    // 获取单个骰子值的属性
    public int Die1Value => _diceValues[0];
    public int Die2Value => _diceValues[1];
    public int Die3Value => _diceValues[2];
    public int Die4Value => _diceValues[3];
    public int Die5Value => _diceValues[4];

    // 获取和设置单个骰子锁定状态的属性
    public bool HoldDie1
    {
        get => _holdValues[0];
        set => _holdValues[0] = value;
    }
    // ... 为 HoldDie2 到 HoldDie5 定义类似属性 ...

    public int NumberOfTimesRolled => _numberOfTimesRolled;
}
```

### 构造函数
构造函数初始化所有骰子值为0，锁定状态为false，投掷次数为0。

![](img/06e94836b3947e1792cafc0b09665c60_16.png)

![](img/06e94836b3947e1792cafc0b09665c60_18.png)

```csharp
public Dice()
{
    // 列表已在声明时初始化，此处无需额外操作
}
```

### 投掷方法
`Roll`方法模拟投掷行为。只有当投掷次数未达上限（3次）时，才对未被锁定的骰子生成新的随机数（1-6）。

```csharp
public void Roll()
{
    if (_numberOfTimesRolled >= _maxRolls) return;

    for (int i = 0; i < _diceValues.Count; i++)
    {
        if (!_holdValues[i])
        {
            _diceValues[i] = _random.Next(1, 7); // 最大值7是独占的，所以实际范围是1-6
        }
    }
    _numberOfTimesRolled++;
}
```

---

## 构建记分卡（Scorecard）类

![](img/06e94836b3947e1792cafc0b09665c60_20.png)

![](img/06e94836b3947e1792cafc0b09665c60_22.png)

`Scorecard`类负责存储玩家在所有可能得分项上的分数。我们使用可空整数（`int?`）来表示某项尚未计分。

![](img/06e94836b3947e1792cafc0b09665c60_24.png)

![](img/06e94836b3947e1792cafc0b09665c60_26.png)

![](img/06e94836b3947e1792cafc0b09665c60_28.png)

![](img/06e94836b3947e1792cafc0b09665c60_30.png)

### 属性定义
记分卡分为上分区（单个数字得分）、上分区奖励和下分区（各种组合得分）。

```csharp
public class Scorecard
{
    // 上分区分数
    public int? OnesScore { get; set; }
    public int? TwosScore { get; set; }
    public int? ThreesScore { get; set; }
    public int? FoursScore { get; set; }
    public int? FivesScore { get; set; }
    public int? SixesScore { get; set; }

    // 上分区总和与奖励
    public int UpperSum => (OnesScore ?? 0) + (TwosScore ?? 0) + (ThreesScore ?? 0) +
                           (FoursScore ?? 0) + (FivesScore ?? 0) + (SixesScore ?? 0);
    private static int _upperBonusThreshold = 63;
    private static int _upperBonusValue = 35;
    public int UpperBonus => UpperSum >= _upperBonusThreshold ? _upperBonusValue : 0;

    // 下分区分数
    public int? ThreeOfAKindScore { get; set; }
    public int? FourOfAKindScore { get; set; }
    public int? FullHouseScore { get; set; }
    public int? SmallStraightScore { get; set; }
    public int? LargeStraightScore { get; set; }
    public int? ChanceScore { get; set; }
    public int? YahtzeeScore { get; set; }

    // 总分
    public int Total => UpperSum + UpperBonus +
                        (ThreeOfAKindScore ?? 0) + (FourOfAKindScore ?? 0) +
                        (FullHouseScore ?? 0) + (SmallStraightScore ?? 0) +
                        (LargeStraightScore ?? 0) + (ChanceScore ?? 0) +
                        (YahtzeeScore ?? 0);
}
```

### 构造函数
构造函数将所有得分项初始化为`null`。

![](img/06e94836b3947e1792cafc0b09665c60_32.png)

![](img/06e94836b3947e1792cafc0b09665c60_33.png)

```csharp
public Scorecard()
{
    OnesScore = null;
    TwosScore = null;
    // ... 初始化所有其他分数属性为 null ...
}
```

![](img/06e94836b3947e1792cafc0b09665c60_35.png)

---

## 在骰子类中计算可能得分

![](img/06e94836b3947e1792cafc0b09665c60_37.png)

![](img/06e94836b3947e1792cafc0b09665c60_39.png)

我们需要一个方法，根据当前骰子的值，计算所有可能得分项的分值。我们在`Dice`类中添加一个`GetPossibleScores`方法。

### 辅助方法：计算特定数字得分
例如，计算“一点”的得分就是统计骰子中值为1的个数，然后乘以1。

```csharp
private int GetScoreForNumber(int number)
{
    int sum = 0;
    foreach (int die in _diceValues)
    {
        if (die == number)
        {
            sum += number;
        }
    }
    return sum;
}
```

### 辅助方法：统计各点数出现次数
这个方法返回一个列表，索引1到6分别对应点数1到6出现的次数。

![](img/06e94836b3947e1792cafc0b09665c60_41.png)

![](img/06e94836b3947e1792cafc0b09665c60_43.png)

```csharp
private List<int> GetDieValueOccurrences()
{
    List<int> occurrences = new List<int>(new int[7]); // 索引0-6，忽略0
    foreach (int die in _diceValues)
    {
        occurrences[die]++;
    }
    return occurrences;
}
```

![](img/06e94836b3947e1792cafc0b09665c60_45.png)

![](img/06e94836b3947e1792cafc0b09665c60_46.png)

![](img/06e94836b3947e1792cafc0b09665c60_48.png)

### 实现 GetPossibleScores 方法
现在我们可以组合这些辅助方法来填充一个`Scorecard`对象。

![](img/06e94836b3947e1792cafc0b09665c60_50.png)


![](img/06e94836b3947e1792cafc0b09665c60_52.png)

![](img/06e94836b3947e1792cafc0b09665c60_54.png)

```csharp
public Scorecard GetPossibleScores()
{
    Scorecard possibleScores = new Scorecard();
    List<int> occurrences = GetDieValueOccurrences();
    int sumOfAllDice = _diceValues.Sum();

    // 上分区
    possibleScores.OnesScore = GetScoreForNumber(1);
    possibleScores.TwosScore = GetScoreForNumber(2);
    // ... 设置 ThreesScore 到 SixesScore ...

    // 下分区
    // 三条和四条：检查是否有至少3个或4个相同的骰子
    possibleScores.ThreeOfAKindScore = occurrences.Contains(3) || occurrences.Contains(4) || occurrences.Contains(5) ? sumOfAllDice : 0;
    possibleScores.FourOfAKindScore = occurrences.Contains(4) || occurrences.Contains(5) ? sumOfAllDice : 0;

    // 满堂红：检查是否同时包含3个相同和2个相同的骰子
    possibleScores.FullHouseScore = (occurrences.Contains(3) && occurrences.Contains(2)) || occurrences.Contains(5) ? 25 : 0;

    // 小顺子和大顺子：需要对骰子值排序后检查连续序列
    int[] sortedValues = _diceValues.ToArray();
    Array.Sort(sortedValues);
    possibleScores.SmallStraightScore = HasSmallStraight(sortedValues) ? 30 : 0;
    possibleScores.LargeStraightScore = HasLargeStraight(sortedValues) ? 40 : 0;

    // 机会和快艇
    possibleScores.ChanceScore = sumOfAllDice;
    possibleScores.YahtzeeScore = occurrences.Contains(5) ? 50 : 0;

    return possibleScores;
}
// 检查小顺子（四个连续数字）
private bool HasSmallStraight(int[] sortedDice)
{
    // 检查 1-2-3-4, 2-3-4-5, 3-4-5-6 这三种模式
    for (int i = 0; i <= sortedDice.Length - 4; i++)
    {
        if (sortedDice[i] == sortedDice[i + 1] - 1 &&
            sortedDice[i] == sortedDice[i + 2] - 2 &&
            sortedDice[i] == sortedDice[i + 3] - 3)
        {
            return true;
        }
    }
    return false;
}

// 检查大顺子（五个连续数字）
private bool HasLargeStraight(int[] sortedDice)
{
    // 检查 1-2-3-4-5 或 2-3-4-5-6
    return (sortedDice[0] == sortedDice[1] - 1 &&
            sortedDice[0] == sortedDice[2] - 2 &&
            sortedDice[0] == sortedDice[3] - 3 &&
            sortedDice[0] == sortedDice[4] - 4);
}
```

---

![](img/06e94836b3947e1792cafc0b09665c60_56.png)

![](img/06e94836b3947e1792cafc0b09665c60_58.png)

## 总结

![](img/06e94836b3947e1792cafc0b09665c60_60.png)

本节课中我们一起学习了快艇骰子游戏项目的第一部分。我们重点进行了面向对象的设计，创建了`Dice`类和`Scorecard`类。`Dice`类负责管理骰子的状态和行为，包括投掷和锁定；`Scorecard`类负责记录和计算各种得分。我们还初步实现了根据骰子状态计算所有可能得分的核心逻辑。在下一部分，我们将把这些类与用户界面连接起来，并完成游戏的回合与玩家管理逻辑。