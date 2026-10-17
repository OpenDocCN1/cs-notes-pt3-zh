# 12.4 设计测试用例

+   - 考虑Bank类相对于ATM类（见图12.3）的操作序列：

+   - `verifyAcct·verifyPIN·[（verifyPolicy·withdrawReq）depositReqAcctInfoREQ]ⁿ`

+   - 对Bank类的随机测试用例可能是：

+     - 测试用例#r3：`verifyAcct verifyPIN depositReq`

+   - 为了考虑在上述这个测试中涉及的协作者，需要考虑与测试用例#r3中的每个操作相关联的消息。Bank必须和ValidationInfo协作以执行verifyAcct和verifyPIN，Bank还必须和Account协作以执行depositReq。因此，测试上面提到的协作的新测试用例是：