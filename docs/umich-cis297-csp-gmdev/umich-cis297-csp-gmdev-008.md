# 008：WinForms桌面开发

![](img/ebec260aa31c2af2c1d0b7e869071eed_0.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_2.png)

## 概述

![](img/ebec260aa31c2af2c1d0b7e869071eed_4.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_5.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_7.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_9.png)

在本节课中，我们将学习如何使用C#和Windows Forms来创建具有图形用户界面的桌面应用程序。我们将从控制台应用程序过渡到事件驱动的窗体程序，学习如何添加按钮、文本框、标签等控件，并响应用户的交互。

![](img/ebec260aa31c2af2c1d0b7e869071eed_11.png)

---

## 从控制台到图形界面

![](img/ebec260aa31c2af2c1d0b7e869071eed_13.png)

上一节我们介绍了控制台应用程序的基础。本节中，我们来看看如何创建带有点击按钮和输入框的图形界面程序。

![](img/ebec260aa31c2af2c1d0b7e869071eed_15.png)

Windows Forms是.NET框架中用于构建桌面应用程序的技术。它允许我们通过拖放控件来设计界面，并通过编写代码来响应事件（如按钮点击）。

## 创建第一个Windows Forms应用

首先，我们需要创建一个新的Windows Forms应用项目。

![](img/ebec260aa31c2af2c1d0b7e869071eed_17.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_19.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_21.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_22.png)

以下是创建新项目的步骤：
1.  在Visual Studio中，选择“创建新项目”。
2.  选择“Windows窗体应用(.NET Framework)”或“Windows窗体应用”。
3.  为项目命名（例如 `WinFormsApp1`）并创建。

创建后，你会看到设计视图和一个名为 `Form1` 的空白窗口。

![](img/ebec260aa31c2af2c1d0b7e869071eed_24.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_26.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_28.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_30.png)

## 设计用户界面

![](img/ebec260aa31c2af2c1d0b7e869071eed_32.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_34.png)

在设计视图中，工具箱提供了所有可用的控件。

以下是向窗体添加基本控件的步骤：
1.  从工具箱的“公共控件”中，将一个 `Button` 拖放到窗体上。
2.  选中按钮，在“属性”窗口中，将 `Text` 属性改为“点击我”。
3.  从工具箱中，将一个 `Label` 拖放到窗体上。
4.  选中标签，在“属性”窗口中，将 `(名称)` 改为 `clickMeLabel`，并清空 `Text` 属性。
5.  再从工具箱中，将一个 `TextBox` 拖放到窗体上，用于用户输入。
6.  选中文本框，将 `(名称)` 改为 `nameTextBox`。
7.  添加另一个 `Label`，将其 `Text` 属性改为“请输入你的名字：”。这个标签我们不需要在代码中访问，因此可以不改名。

## 编写事件处理代码

![](img/ebec260aa31c2af2c1d0b7e869071eed_36.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_38.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_40.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_42.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_44.png)

窗体应用程序是事件驱动的。程序启动后等待用户操作，当事件（如点击按钮）发生时，运行相应的代码。

![](img/ebec260aa31c2af2c1d0b7e869071eed_46.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_48.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_50.png)

要为按钮添加点击事件：
1.  在设计视图中，双击按钮。这将自动切换到代码视图，并生成一个名为 `button1_Click` 的方法框架。
2.  在这个方法中，编写代码来更新标签的文本。我们可以使用字符串插值将文本框的内容包含进去。

```csharp
private void button1_Click(object sender, EventArgs e)
{
    clickMeLabel.Text = $"你好, {nameTextBox.Text}!";
}
```

现在运行程序，在文本框中输入名字，然后点击按钮，标签就会显示个性化的问候语。

## 处理其他事件

除了按钮点击，我们还可以处理其他事件，例如在文本框中按下回车键。

以下是处理文本框按键事件的步骤：
1.  在设计视图中，选中文本框。
2.  在“属性”窗口中，点击闪电图标切换到“事件”视图。
3.  找到 `KeyPress` 事件，双击它生成事件处理方法。
4.  在生成的方法中，判断按下的键是否是回车键，如果是，则执行与按钮点击相同的操作。

```csharp
private void nameTextBox_KeyPress(object sender, KeyPressEventArgs e)
{
    if (e.KeyChar == (char)Keys.Enter)
    {
        UpdateLabel(); // 调用更新标签的方法
        e.Handled = true; // 阻止系统提示音
    }
}

private void UpdateLabel()
{
    clickMeLabel.Text = $"你好, {nameTextBox.Text}!";
}

![](img/ebec260aa31c2af2c1d0b7e869071eed_52.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_54.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_55.png)

// 修改按钮点击事件，也调用同一个方法
private void button1_Click(object sender, EventArgs e)
{
    UpdateLabel();
}
```

![](img/ebec260aa31c2af2c1d0b7e869071eed_57.png)

通过将共同逻辑提取到 `UpdateLabel` 方法中，我们避免了代码重复。

![](img/ebec260aa31c2af2c1d0b7e869071eed_59.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_61.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_63.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_65.png)

## 探索更多控件

![](img/ebec260aa31c2af2c1d0b7e869071eed_67.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_69.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_71.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_73.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_75.png)

![](img/ebec260aa31c2af2c1d0b7e869071eed_77.png)

Windows Forms 提供了丰富的控件来构建复杂界面。

以下是几种常用控件的简介：
*   **RadioButton（单选按钮）**：用于在一组互斥的选项中选择一个（例如，选择报税身份：单身或已婚）。
*   **CheckBox（复选框）**：用于选择多个独立的选项（例如，选择汉堡的配料）。
*   **ListBox（列表框）**：显示一个项目列表供用户选择。可以通过代码动态添加或移除项目。
*   **PictureBox（图片框）**：用于在窗体上显示图像。

## 项目结构解析

在解决方案资源管理器中，你会看到几个关键文件：
*   `Program.cs`：包含应用程序的入口点 `Main` 方法，它启动窗体。
*   `Form1.cs`：包含窗体类的主代码文件，我们在这里编写事件处理方法。
*   `Form1.Designer.cs`：这是一个分部类文件，由设计器自动生成。它包含了所有控件的声明、初始化代码以及事件委托的设置。通常不需要手动修改此文件。

`InitializeComponent()` 方法（在 `Form1.cs` 的构造函数中调用）负责根据设计视图创建和设置所有控件。

## 总结

![](img/ebec260aa31c2af2c1d0b7e869071eed_79.png)

本节课中我们一起学习了Windows Forms桌面开发的基础。我们创建了一个带有按钮、标签和文本框的图形界面，并编写代码来响应按钮点击和键盘事件。我们了解了事件驱动的编程模型，并探索了如何通过提取方法避免代码重复。最后，我们简要介绍了其他常用控件并解析了WinForms项目的文件结构。掌握了这些，你就可以开始构建具有交互功能的桌面应用程序了。