
## 12.4 设计测试用例

这就是对account类的最小测试序列。但是，在下面的序列中可能发生许多其他行为：

- open·setup·deposit·（deposit | withdraw | balance | summarize | creditLimit）·"withdraw·close

从上列序列可以随机产生一系列不同的操作序列，如：

- #r1:open·setup·deposit·deposit·balance·summarize·withdraw·close
- #r2:open·setup·deposit·withdraw·deposit·balance·creditLimit·withdraw·close

执行上述这些及另外一些随机产生的测试用例，可以测试类实例的不同生存历史。

## 2. 划分测试(partition testing)

- 与测试传统软件时采用等价划分方法类似，采用划分测试方法可以减少测试类时所需要的测试用例的数量。
- 首先，把输入和输出分类，然后设计测试用例以测试划分出的每个类别。下面介绍划分类别的方法。

## （2）基于属性的划分

这种方法根据类操作使用的属性来划分类操作。对于account类来说，可以使用属性balance来定义划分，从而把操作划分成三个类别：

- 使用balance的操作：balance, summarize
- 修改balance的操作：deposit, withdraw
- 不使用也不修改balance的操作：creditLimit

然后，为每个类别设计测试序列。

## （3）基于功能的划分

- 这种方法根据类操作所完成的功能来划分类操作。对于account类来说，可以分类为
- 初始化操作(open, setup)
- 计算操作(deposit, withdraw)
- 查询操作(balance, summarize, creditLimit)
- 终止操作(close)
- 然后，为每个类别设计测试序列。

## 3. 基于故障的测试(fault-based testing)

- 基于故障的测试与传统的错误推测法类似，也是首先推测软件中可能有的错误，然后设计出最可能发现这些错误的测试用例。
- 例如，软件工程师经常在问题的边界处犯错误，因此，在测试SQRT(计算平方根)操作(该操作在输入为负数时返回出错信息)时，应该着重检查边界情况：一个接近零的负数和零本身。
- 其中“零本身”用于检查程序员是否犯了如下错误：

- 把语句if(x>=0)calculate-square-root();
- 误写成if(x>0)calculate-square-root();
- 为了推测出软件中可能有的错误，应该仔细研究分析模型和设计模型，而且在很大程度上要依靠测试人员的经验和直觉。
- 如果推测得比较准确，则使用基于故障的测试方法能够用相当低的工作量发现大量错误；反之，如果推测不准，则这种方法的效果并不比随机测试技术的效果好。

## 12.4.2 集成测试方法

- 开始集成面向对象系统以后，测试用例的设计变得更加复杂。在这个测试阶段，必须对类间协作进行测试。
- 为了举例说明设计类间测试用例的方法，扩充12.4.1小节引入的银行系统的例子，使它包含图12.3所示的类和协作。

图中箭头方向代表消息的传递方向，箭头线上的标注给出了作为由消息所蕴含的协作的结果而调用的操作。

图12.3 银行系统的类—协作图

## 1. 多类测试

- Kirani和Tsai建议使用下列步骤，以生成多个类的随机测试用例。
- 对每个客户类，使用类操作符列表来生成一系列随机测试序列。这些操作符向服务器类实例发送消息。
- 对所生成的每个消息，确定协作类和在服务器对象中的对应操作符。
- 对服务器对象中的每个操作符(已经被来自客户对象的消息调用)，确定传递的消息。
- 对每个消息，确定下一层被调用的操作符，并把这些操作符结合进测试序列中。

- 考虑Bank类相对于ATM类（见图12.3）的操作序列：
- `verifyAcct·verifyPIN·[（verifyPolicy·withdrawReq）depositReqAcctInfoREQ]ⁿ`
- 对Bank类的随机测试用例可能是：
  - 测试用例#r3：`verifyAcct verifyPIN depositReq`

为了考虑在上述这个测试中涉及的协作者，需要考虑与测试用例#r3中的每个操作相关联的消息。Bank必须和ValidationInfo协作以执行verifyAcct和verifyPIN，Bank还必须和Account协作以执行depositReq。因此，测试上面提到的协作的新测试用例是：

- 测试用例#r4:verifyAcctBank
  - `[validAcctValidationInfo]` · `verifyPINBank`
  - `[validPINvalidationInfo]` · `depositReq` · `[depositaccount]`

多个类的划分测试方法类似于单个类的划分测试方法(见12.4.1节)。  
但是，对于多类测试来说，应该扩充测试序列以包括那些通过发送给协作类的消息而被调用的操作。

另一种划分测试方法，根据与特定类的接口来划分类操作。如图12.3所示，Bank类接收来自ATM类和Cashier类的消息，因此，可以通过把Bank类中的方法划分成服务于ATM的和服务于Cashier的两类来测试它们。

## 2. 从动态模型导出测试用例

在本书第9章中已经讲过，怎样用状态转换图作为表示类的动态行为模型。

类的状态图可以帮助导出测试该类(及与其协作的那些类)的动态行为的测试用例。

图12.4给出了前面讨论过的account类的状态图，从图可见，初始转换经过了empty acct和setup acct这两个状态，而类实例的大多数行为发生在working acct状态中，最终的withdraw和close使得account类分别向nonworking acct状态和dead acct状态转换。

图 12.4 account类的状态转换图

- 设计出的测试用例应该**覆盖所有状态**，也就是说，操作序列应该使得account类实例**遍历**所有允许的状态转换：
  - 测试用例
    - `$s1:open·setupAccnt·deposit(initial)·withdraw(final)·close`

应该注意，上面列出的序列与12.4.1节讨论的最小测试序列相同。向最小序列中加入附加的测试序列，可以得出其他测试用例：

- 测试用例
  - `#s2:open·setupAccnt·deposit(initial)·deposit·balance·credit·withdraw(final)·close`

- 测试用例
  - `#s3:open·setupAccnt·deposit(initial)·deposit·withdraw·accntInfo·withdraw(final)·close`

还可以导出更多测试用例，以保证该类的所有行为都被适当地测试了。在类的行为导致与一个或多个类协作的情况下，使用多个状态图去跟踪系统的行为流。

软件工程导论

梁文新
办公室：综合楼105
电话：87571625
liang@computer.org

# 第13章 软件项目管理

- 软件项目失败的主要原因是因为**管理不善**。
- 所谓**管理**就是通过**计划、组织和控制**等一系列活动，合理地配置和使用各种资源，以达到既定目标的过程。
- **软件项目管理（Software Project Management）**先于任何技术活动之前开始，并且贯穿于软件的整个生命周期之中。
- 目的：在一定的时间和预设范围内，有效地利用人力、资源、技术和工具，使软件系统或软件产品按原定计划和质量要求如期完成。
