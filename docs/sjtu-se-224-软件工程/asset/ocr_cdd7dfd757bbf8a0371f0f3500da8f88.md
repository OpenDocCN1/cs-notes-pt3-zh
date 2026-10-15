# Software Engineering

# Extend 关系示例(续)

Get Quote Use Case
Basic Flow:
1. Include "Identify Customer" to verify customer identity.
2. Display options.
3. Customer selects "Get Quote".
4. Customer gets quote.
5. Customer gets other quotes.
6. Customer logs off.
A1. Quote System unavailable
Extension Points:
The "Optional Services" extension point occurs at Step 3 in the Basic Flow.

Get News Use Case
This use case extends the Get Quote Use Case, at extension point "Optional Services".
Basic Flow:
1. If Customer selects "Get News", the system asks customer for time period and number of news items.
2. Customer enters time period and log of items. The system sends stock trading symbol to News System, receives reply, and displays the news to the customer.
3. The Get Quote Use Case continues.
A1: News System Unavailable
A2: No News About This Stock

# 面向对象分析

# 执行Extend

+   - 当到达扩展点并且扩展条件为真时执行

![](bbox=[0.62, 0.32, 0.88, 0.55])

# 什么是 Use-Case Generalization?

+   - 从子用例到父用例的关系
+   - 在父用例中描述通用的共享的行为
+   - 在子用例中描述特殊的行为
+   - 共享共同的目标

![](bbox=[0.22, 0.8, 0.42, 0.92])

# Generalization示例

![](bbox=[0.62, 0.72, 0.88, 0.88])

# Generalization 关系示例

Execute Trade Use Case
Basic Flow:
1. Customer Logs On
Include "Identify Customer" to verify customer identity.
2. Customer Selects "Trade".
Customer chooses trade...
3. Customer Selects Account
System displays account...
Perform Trade
4. Customer Begins New Trade
If customer wants other trades, repeat from Step 3...
6. Display Summary
System displays summary...
A1. Account Not Operational...

Execute Securities Trade Use Case
This use case is a child of the Execute Trade Use Case.
Trade Use Case.
Basic Flow:
1. Customer Logs On
2. Customer Selects "Trade"
3. Customer Selects Account
4. Perform Trade
If customer selects trade order type. The system performs... Limit Sell, Limit Buy...
The system sends...
5. Customer Begins New Trade
6. Display Summary
A1: Limit Sell Order...

# 什么是Actor Generalization?

+   - Actors 可能有公共的属性
+   - 多个 actors 和Use-Case交互时可能有公共的角色或其的

![](bbox=[0.7, 0.95, 0.85, 1.0])

4.2 - 11