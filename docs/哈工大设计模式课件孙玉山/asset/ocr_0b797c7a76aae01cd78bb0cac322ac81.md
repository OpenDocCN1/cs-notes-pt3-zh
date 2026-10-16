# Design Example Using the State Pattern

# BankContext class

+   1. 保持数据 (Maintains data):
+      - balance,
+      - account number
+      - State object, and
+      - the transaction limits
+   2. 给客户程序提供基本的存款与取款方法。 Offers the basic methods deposit(double amt) and withdraw(double amt) inside which the same methods inside a state subclass will be called.