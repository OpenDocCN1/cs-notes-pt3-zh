# # 12.4 设计测试用例

+   - 测试用例#r4:verifyAcctBank
+     - `[validAcctValidationInfo]` · `verifyPINBank`
+     - `[validPINvalidationInfo]` · `depositReq` · `[depositaccount]`

+   - 多个类的划分测试方法类似于单个类的划分测试方法(见12.4.1节)。  
+     但是，对于多类测试来说，应该扩充测试序列以包括那些通过发送给协作类的消息而被调用的操作。

+   - 另一种划分测试方法，根据与特定类的接口来划分类操作。如图12.3所示，Bank类接收来自ATM类和Cashier类的消息，因此，可以通过把Bank类中的方法划分成服务于ATM的和服务于Cashier的两类来测试它们。