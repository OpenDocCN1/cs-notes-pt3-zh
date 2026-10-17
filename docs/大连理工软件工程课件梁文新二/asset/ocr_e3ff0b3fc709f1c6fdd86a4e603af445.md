# 12.4 设计测试用例

# 2. 从动态模型导出测试用例

+   在本书第9章中已经讲过，怎样用状态转换图作为表示类的动态行为模型。

+   类的状态图可以帮助导出测试该类(及与其协作的那些类)的动态行为的测试用例。

+   图12.4给出了前面讨论过的account类的状态图，从图可见，初始转换经过了empty acct和setup acct这两个状态，而类实例的大多数行为发生在working acct状态中，最终的withdraw和close使得account类分别向nonworking acct状态和dead acct状态转换。