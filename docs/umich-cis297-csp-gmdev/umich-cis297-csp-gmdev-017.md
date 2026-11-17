# 017：扑克牌手牌与异常处理


在本节课中，我们将学习如何创建一个扑克牌手牌类，并探讨如何使用异常处理来确保程序的健壮性。我们将从定义卡牌和手牌类开始，然后实现手牌的比较逻辑，最后深入了解C#中的异常处理机制。



![](img/9832b4c3f637ce48ed90d1bed529770e_6.png)

## 卡牌类

首先，我们需要创建一个`Card`类来表示一张扑克牌。每张牌有两个属性：面值（如A、2、3...K）和花色（如黑桃、红心、梅花、方块）。我们可以使用枚举（`enum`）来清晰地定义这些有限的选项。

![](img/9832b4c3f637ce48ed90d1bed529770e_8.png)

以下是卡牌面值和花色的枚举定义：

```csharp
public enum Face
{
    Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten, Jack, Queen, King, Ace
}

public enum Suit
{
    Spades, Hearts, Clubs, Diamonds
}
```

接下来，我们创建`Card`类。它包含两个属性，并通过构造函数进行初始化。为了让卡牌可以排序（例如，判断顺子时），我们让`Card`类实现`IComparable<Card>`接口。

![](img/9832b4c3f637ce48ed90d1bed529770e_10.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_12.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_14.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_16.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_18.png)

```csharp
public class Card : IComparable<Card>
{
    public Face Face { get; set; }
    public Suit Suit { get; set; }

    public Card(Face face, Suit suit)
    {
        Face = face;
        Suit = suit;
    }

    public int CompareTo(Card? other)
    {
        // 比较两张牌的面值。负值表示当前牌小，0表示相等，正值表示当前牌大。
        return Face.CompareTo(other?.Face);
    }

    public override string ToString()
    {
        // 重写ToString方法，方便显示卡牌信息
        return $"{Face} of {Suit}";
    }
}
```

![](img/9832b4c3f637ce48ed90d1bed529770e_20.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_22.png)

## 扑克手牌类

![](img/9832b4c3f637ce48ed90d1bed529770e_24.png)

上一节我们介绍了卡牌类，本节中我们来看看如何构建一个五张牌的扑克手牌类`PokerHand`。这个类需要管理一组卡牌，并能判断手牌的等级（如对子、顺子、同花等），同时还要能与其他手牌进行比较。

![](img/9832b4c3f637ce48ed90d1bed529770e_26.png)

首先，我们定义一个表示手牌等级的枚举：

![](img/9832b4c3f637ce48ed90d1bed529770e_28.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_30.png)

```csharp
public enum HandRank
{
    HighCard,
    OnePair,
    TwoPair,
    ThreeOfAKind,
    Straight,
    Flush,
    FullHouse,
    FourOfAKind,
    StraightFlush
}
```

`PokerHand`类包含一个卡牌列表。为了简化，我们暂时将列表设为公共属性，但请注意这在实际项目中可能不是最佳实践。我们还需要实现`IComparable<PokerHand>`接口以便比较手牌。

![](img/9832b4c3f637ce48ed90d1bed529770e_32.png)

```csharp
public class PokerHand : IComparable<PokerHand>
{
    public List<Card> Cards { get; set; }

    public PokerHand()
    {
        Cards = new List<Card>();
    }

    // 一个用于获取手牌等级的方法（暂未完全实现）
    public HandRank GetHandRank()
    {
        // 待实现：根据Cards列表判断手牌等级
        return HandRank.HighCard;
    }

    public int CompareTo(PokerHand? other)
    {
        // 首先检查双方手牌是否都有恰好5张牌
        if (Cards.Count != 5 || other?.Cards.Count != 5)
        {
            throw new ArgumentException("A poker hand must have exactly 5 cards.");
        }

        // 先比较手牌等级
        int rankComparison = GetHandRank().CompareTo(other.GetHandRank());
        if (rankComparison != 0)
        {
            return rankComparison;
        }

        // 如果等级相同，则进入具体的“打破平局”逻辑（待实现）
        return BreakTie(other);
    }

    private int BreakTie(PokerHand other)
    {
        // 待实现：根据不同的手牌等级（如对子、顺子等）进行详细比较
        return 0;
    }

    public override string ToString()
    {
        // 将手牌中的每张牌和手牌等级连接成一个字符串
        string result = "";
        foreach (var card in Cards)
        {
            result += card.ToString() + " ";
        }
        result += $"({GetHandRank()})";
        return result;
    }
}
```

## 异常处理

![](img/9832b4c3f637ce48ed90d1bed529770e_34.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_36.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_38.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_40.png)

在编写`CompareTo`方法时，我们加入了一个检查：如果手牌不是恰好5张，就抛出一个异常。这引出了C#中一个非常重要的概念——异常处理。

异常是程序运行时发生的错误或意外情况。与简单地输出错误信息到控制台不同，抛出异常可以强制调用方代码处理这个错误，否则程序就会崩溃。这是一种更健壮的错误处理方式。


以下是如何抛出和捕获异常：

![](img/9832b4c3f637ce48ed90d1bed529770e_44.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_46.png)


![](img/9832b4c3f637ce48ed90d1bed529770e_48.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_50.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_52.png)

```csharp
// 在方法中抛出异常
if (sideLength < 0)
{
    throw new ArgumentException("Side length cannot be less than 0.");
}
// 在调用方捕获并处理异常
try
{
    // 尝试执行可能抛出异常的代码
    SomeMethodThatMightThrow();
}
catch (FormatException ex)
{
    // 捕获特定类型的异常（例如，格式错误）
    Console.WriteLine($"A format error occurred: {ex.Message}");
}
catch (ArgumentException ex)
{
    // 捕获另一种特定类型的异常
    Console.WriteLine($"An argument error occurred: {ex.Message}");
}
catch (Exception ex)
{
    // 捕获所有其他类型的异常（最通用的）
    Console.WriteLine($"An unexpected error occurred: {ex.Message}");
    // ex.StackTrace 包含详细的错误堆栈跟踪信息，对调试很有用
}
```

![](img/9832b4c3f637ce48ed90d1bed529770e_54.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_56.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_58.png)

![](img/9832b4c3f637ce48ed90d1bed529770e_60.png)

使用`try-catch`块，你可以优雅地处理错误，向用户显示友好的信息，同时将详细的错误信息记录下来供开发者排查。



## 扩展方法



C#提供了一个强大的特性叫扩展方法，它允许你向现有类型“添加”新的方法，而无需修改原始类型的代码或创建新的派生类型。这在为系统类或第三方库添加便捷功能时非常有用。

定义一个扩展方法需要在一个静态类中创建一个静态方法，并使用`this`关键字修饰第一个参数（指定要扩展的类型）。

以下是一个为`string`类型添加一个奇怪功能的示例：

```csharp
public static class StringExtensions
{
    public static string ToAlternatingCase(this string input)
    {
        char[] chars = input.ToCharArray();
        for (int i = 0; i < chars.Length; i++)
        {
            if (i % 2 == 0)
                chars[i] = char.ToUpper(chars[i]);
            else
                chars[i] = char.ToLower(chars[i]);
        }
        return new string(chars);
    }
}

// 使用扩展方法
string myString = "hello world";
string result = myString.ToAlternatingCase(); // 结果为 "HeLlO WoRlD"
```

许多强大的库（如LINQ）都大量使用了扩展方法，使得我们可以对集合进行流畅的查询和操作。




## 课程总结

![](img/9832b4c3f637ce48ed90d1bed529770e_76.png)

本节课中我们一起学习了几个核心的C#高级主题。我们创建了`Card`和`PokerHand`类，并利用`IComparable`接口使它们可以排序和比较。我们深入探讨了异常处理机制，学会了如何使用`throw`抛出异常以及使用`try-catch`块来捕获和处理异常，从而编写出更健壮、容错性更好的代码。最后，我们简要介绍了扩展方法的概念，它为我们扩展现有类型的功能提供了强大的工具。在接下来的课程中，我们将利用这些知识，继续完善扑克手牌的逻辑，并探索更多C#的高级特性。