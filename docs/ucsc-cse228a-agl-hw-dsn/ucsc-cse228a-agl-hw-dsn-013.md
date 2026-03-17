# 013：测试 🧪

![](img/9030807e2298d0684ac3f1365257bccc_1.png)

![](img/9030807e2298d0684ac3f1365257bccc_3.png)

![](img/9030807e2298d0684ac3f1365257bccc_5.png)

![](img/9030807e2298d0684ac3f1365257bccc_7.png)

![](img/9030807e2298d0684ac3f1365257bccc_9.png)

在本节课中，我们将要学习硬件设计中的测试。测试是确保硬件功能正确性的关键环节，也是敏捷开发流程中不可或缺的一部分。我们将探讨测试的重要性、如何测试组合逻辑与时序逻辑模块，并介绍如何利用Scala、Chisel和ChiselTest等工具高效地组织和执行测试。

上一节我们介绍了如何使用优先级编码器和独热编码构建仲裁器与交叉开关。本节中，我们来看看如何为这些设计建立可靠的测试。

## 为什么需要测试？ 🤔

![](img/9030807e2298d0684ac3f1365257bccc_11.png)

![](img/9030807e2298d0684ac3f1365257bccc_13.png)

测试至关重要，原因如下：
1.  确保硬件按预期工作。
2.  向自己和他人证明硬件功能正确。
3.  在开发过程中，测试有助于设计出更好的硬件。如果测试不仅是最终环节，而是贯穿整个开发流程，将有助于设计出更正确、更易于测试的硬件，并提高测试质量。

![](img/9030807e2298d0684ac3f1365257bccc_15.png)

因此，测试是开发流程的一部分，也是我们今天课程的核心论点。

![](img/9030807e2298d0684ac3f1365257bccc_17.png)

![](img/9030807e2298d0684ac3f1365257bccc_19.png)

![](img/9030807e2298d0684ac3f1365257bccc_21.png)

![](img/9030807e2298d0684ac3f1365257bccc_23.png)

## 测试的组成部分 🧩

一个完整的测试包含三个主要部分：
1.  **测试用例**：定义需要测试的具体场景。最初可以手动编写，对于输入较多的情况，可能需要使用代码生成，例如随机生成或定向随机生成。
2.  **正确输出**：对于给定的输入，硬件模块应产生的预期结果。初期可以手动指定，但更可靠的方法是使用**模型生成**。我们编写一个纯Scala的功能模型，用它来计算预期输出，并与Chisel设计的结果进行比较。
3.  **测试执行**：驱动硬件模块、施加输入、获取输出并进行比较的机制。本课程使用基于Scala的模拟器**Treadle**来执行Chisel代码的仿真。测试的组织和执行通过**ChiselTest**和**ScalaTest**来完成。

![](img/9030807e2298d0684ac3f1365257bccc_25.png)

以下是测试流程的简要概述：
*   输入同时提供给**被测设计**和**功能模型**。
*   模型计算出预期输出。
*   测试框架自动比较DUT的输出与模型的预期输出。

## 测试的考量与最佳实践 💡

在编写测试时，需要考虑以下几点：
*   **尽早闭环**：采用测试驱动开发，尽快让最简单的测试用例在最简单的模块版本上运行起来。
*   **覆盖率**：确保测试覆盖了硬件模块的所有功能。
*   **测试视角**：
    *   **黑盒测试**：不了解模块内部实现，只根据功能规格进行测试，有助于全面验证。
    *   **白盒测试**：了解内部实现，可以针对代码中的边界情况和特殊逻辑进行测试。建议结合两者。

![](img/9030807e2298d0684ac3f1365257bccc_27.png)

![](img/9030807e2298d0684ac3f1365257bccc_29.png)

测试应成为开发流程的有机组成部分，而不仅仅是最终验证。这包括：
*   **持续集成**：让测试在后台自动运行。
*   **协作**：当外部贡献者提交代码时，运行测试是验证其正确性的关键。
*   **设计空间探索**：对于参数化的硬件生成器，可以使用测试来评估不同参数下的性能。

![](img/9030807e2298d0684ac3f1365257bccc_31.png)

![](img/9030807e2298d0684ac3f1365257bccc_32.png)

**为测试而设计**：在早期考虑测试，可以调整模块边界和抽象层次，使测试更容易。例如，将设计分解为无状态的组合逻辑部分和有状态的时序逻辑部分，可以简化测试。

![](img/9030807e2298d0684ac3f1365257bccc_34.png)

![](img/9030807e2298d0684ac3f1365257bccc_35.png)

![](img/9030807e2298d0684ac3f1365257bccc_37.png)

## 测试参数化生成器 🛠️

![](img/9030807e2298d0684ac3f1365257bccc_39.png)

![](img/9030807e2298d0684ac3f1365257bccc_41.png)

Chisel鼓励编写**生成器**而非单一设计。测试生成器意味着需要测试多种参数组合。我们推荐的方法是**参数化测试环境**。用户可以为生成器的特定参数实例化测试平台，从而验证他们实际使用的设计，而无需为每个可能的参数组合编写独立的测试。

![](img/9030807e2298d0684ac3f1365257bccc_43.png)

![](img/9030807e2298d0684ac3f1365257bccc_45.png)

## 测试组合逻辑模块 ➕

![](img/9030807e2298d0684ac3f1365257bccc_47.png)

![](img/9030807e2298d0684ac3f1365257bccc_48.png)

![](img/9030807e2298d0684ac3f1365257bccc_50.png)

![](img/9030807e2298d0684ac3f1365257bccc_51.png)

![](img/9030807e2298d0684ac3f1365257bccc_52.png)

组合逻辑模块无内部状态，其输出仅取决于当前输入，因此相对容易测试。如果输入空间和参数组合的可能性足够小，可以进行**穷举测试**，从而获得极高的置信度。

![](img/9030807e2298d0684ac3f1365257bccc_54.png)

![](img/9030807e2298d0684ac3f1365257bccc_56.png)

![](img/9030807e2298d0684ac3f1365257bccc_58.png)

让我们以**符号-数值加法器**为例。其功能是：若符号相同，则输出同号，数值相加；若符号不同，则输出绝对值较大者的符号，数值相减。

![](img/9030807e2298d0684ac3f1365257bccc_60.png)

首先，我们建立一个功能模型。由于硬件设计有固定的位宽 `W`，需要考虑**截断**行为，而Scala的Int类型是32位。模型需要模拟这种位宽限制下的加法与截断。

![](img/9030807e2298d0684ac3f1365257bccc_62.png)

![](img/9030807e2298d0684ac3f1365257bccc_63.png)

![](img/9030807e2298d0684ac3f1365257bccc_65.png)

![](img/9030807e2298d0684ac3f1365257bccc_67.png)

```scala
// 符号-数值加法模型示例（概念）
def signMagAddModel(a: (Boolean, Int), b: (Boolean, Int), w: Int): (Boolean, Int) = {
  // 实现考虑位宽w的符号-数值加法与截断逻辑
  // ...
}
```

有了模型后，我们可以编写一个测试函数来自动化输入激励和输出验证。

![](img/9030807e2298d0684ac3f1365257bccc_69.png)

![](img/9030807e2298d0684ac3f1365257bccc_71.png)

```scala
def testAddition(a: Int, b: Int, dut: SignMagAdder): Unit = {
  // 根据a, b设置dut的输入（符号和数值）
  poke(dut.io.a.sign, a < 0)
  poke(dut.io.a.mag, a.abs)
  // ...
  // 计算模型预期输出
  val expected = signMagAddModel((a<0, a.abs), (b<0, b.abs), dut.w)
  // 验证dut输出
  expect(dut.io.out.sign, expected._1)
  expect(dut.io.out.mag, expected._2)
}
```

这样，添加新的测试用例就变得非常简单，只需一行代码调用 `testAddition` 函数，无需手动计算和验证输出。

![](img/9030807e2298d0684ac3f1365257bccc_73.png)

对于小位宽，我们可以轻松进行穷举测试。当位宽增大导致穷举不可行时，可以采用**随机测试**，随机生成大量输入进行验证。

![](img/9030807e2298d0684ac3f1365257bccc_75.png)

## 使用 ScalaTest 组织测试 📚

我们使用 **ScalaTest** 作为测试框架。它提供了清晰的结构来组织测试用例。ChiselTest 构建于 ScalaTest 之上。

![](img/9030807e2298d0684ac3f1365257bccc_77.png)

![](img/9030807e2298d0684ac3f1365257bccc_79.png)

![](img/9030807e2298d0684ac3f1365257bccc_81.png)

```scala
import org.scalatest.flatspec.AnyFlatSpec
import chiseltest._
import chisel3._

![](img/9030807e2298d0684ac3f1365257bccc_83.png)

![](img/9030807e2298d0684ac3f1365257bccc_85.png)

class SignMagAdderTest extends AnyFlatSpec with ChiselScalatestTester {
  behavior of "SignMagAdder"
  // 测试用例1
  it should "add positive numbers correctly" in {
    test(new SignMagAdder(4)) { dut => testAddition(2, 3, dut) }
  }
  // 测试用例2
  it should "handle overflow with truncation" in {
    test(new SignMagAdder(3)) { dut => testAddition(4, 4, dut) }
  }
}
```

![](img/9030807e2298d0684ac3f1365257bccc_87.png)

![](img/9030807e2298d0684ac3f1365257bccc_89.png)

![](img/9030807e2298d0684ac3f1365257bccc_91.png)

![](img/9030807e2298d0684ac3f1365257bccc_93.png)

![](img/9030807e2298d0684ac3f1365257bccc_94.png)

`behavior of` 和 `it should` 语法使得测试报告非常易读。测试运行时会显示清晰的通过/失败信息。

## 测试时序逻辑模块：队列 ⏳

![](img/9030807e2298d0684ac3f1365257bccc_96.png)

时序逻辑模块（如队列）包含内部状态（寄存器），测试更具挑战性，因为输出不仅取决于当前输入，还取决于历史输入。穷举测试通常不可行。

我们为Chisel的 `Queue` 模块构建一个测试。关键在于建立一个**行为模型**。我们可以使用Scala的 `mutable.Queue` 来模拟队列的行为，但需要仔细建模其就绪-有效握手接口和内部状态更新时机。

![](img/9030807e2298d0684ac3f1365257bccc_98.png)

![](img/9030807e2298d0684ac3f1365257bccc_100.png)

模型需要模拟：
*   `deq` 端是否有效（`valid`）：取决于内部队列是否非空。
*   尝试出队（`deq`）：仅在 `deq.ready` 和 `deq.valid` 同时为真时发生，从模型队列中弹出元素。
*   尝试入队（`enq`）：取决于队列是否未满，或是否启用了管道模式（`pipe`）。

![](img/9030807e2298d0684ac3f1365257bccc_102.png)

**关键点**：在软件模型中更新内部状态（如 `mutable.Queue`）时，需模拟硬件寄存器的行为。最佳实践是，在一个“周期”内，先读取所有寄存器的值用于计算，最后再更新寄存器的值，以避免组合逻辑反馈问题。

![](img/9030807e2298d0684ac3f1365257bccc_104.png)

![](img/9030807e2298d0684ac3f1365257bccc_106.png)

建立模型后，我们编写一个自动化交互函数，在每个周期：
1.  根据测试意图（是否入队、出队、数据值）设置DUT的输入。
2.  同时更新模型的状态。
3.  比较DUT的输出与模型的预期输出。

![](img/9030807e2298d0684ac3f1365257bccc_108.png)

![](img/9030807e2298d0684ac3f1365257bccc_110.png)

![](img/9030807e2298d0684ac3f1365257bccc_112.png)

![](img/9030807e2298d0684ac3f1365257bccc_114.png)

```scala
def stepQueue(enqValid: Boolean, enqData: Option[Int], deqReady: Boolean, dut: Queue[UInt], model: QueueModel): Unit = {
  // 1. 设置DUT输入
  poke(dut.io.enq.valid, enqValid)
  enqData.foreach(data => poke(dut.io.enq.bits, data.U))
  poke(dut.io.deq.ready, deqReady)
  // 2. 更新模型并获取预期输出
  val (expectedDeqValid, expectedDeqData) = model.step(enqValid, enqData, deqReady)
  // 3. 比较DUT输出
  expect(dut.io.deq.valid, expectedDeqValid)
  if(expectedDeqValid) {
    expect(dut.io.deq.bits, expectedDeqData.get.U)
  }
}
```

![](img/9030807e2298d0684ac3f1365257bccc_116.png)

有了这个基础框架，编写有意义的测试用例就变得非常简洁：

![](img/9030807e2298d0684ac3f1365257bccc_118.png)

```scala
// 填充队列
for (i <- 0 until 5) {
  stepQueue(enqValid = true, enqData = Some(i), deqReady = false, dut, model)
}
// 排空队列
for (i <- 0 until 5) {
  stepQueue(enqValid = false, enqData = None, deqReady = true, dut, model)
}
```

![](img/9030807e2298d0684ac3f1365257bccc_120.png)

我们也可以轻松实现随机测试，随机决定每个周期是入队、出队还是两者同时进行。

![](img/9030807e2298d0684ac3f1365257bccc_122.png)

![](img/9030807e2298d0684ac3f1365257bccc_124.png)

## 总结 🎯

![](img/9030807e2298d0684ac3f1365257bccc_126.png)

本节课中我们一起学习了硬件设计测试的核心概念和方法：
1.  **自动化是关键**：目标是构建自动化的测试，通过编写代码和抽象来生成测试用例、执行验证，减少人工干预。
2.  **测试三要素**：测试用例、预期输出（通常来自功能模型）和测试执行框架。
3.  **模型生成法**：使用高级语言（Scala）编写参考模型，是生成可靠预期输出的有效方法。
4.  **分层测试**：对于组合逻辑，可进行穷举或随机测试。对于时序逻辑，需构建状态模型并自动化周期级交互。
5.  **工具链**：利用 **ChiselTest**（基于 **ScalaTest**）和 **Treadle** 模拟器，可以高效地组织、运行和调试测试。
6.  **测试是开发的一部分**：采用测试驱动开发、持续集成和为测试而设计的思想，能显著提高硬件开发的质量和效率。

![](img/9030807e2298d0684ac3f1365257bccc_128.png)

![](img/9030807e2298d0684ac3f1365257bccc_130.png)

![](img/9030807e2298d0684ac3f1365257bccc_132.png)

![](img/9030807e2298d0684ac3f1365257bccc_134.png)

记住，查看波形和打印语句对于调试很有用，但那不是自动化测试。**断言**是测试的补充，可以帮助在问题发生时立即捕获，但也不能替代完整的测试。通过构建强大的测试基础设施，你可以更自信地进行迭代和优化你的硬件设计。