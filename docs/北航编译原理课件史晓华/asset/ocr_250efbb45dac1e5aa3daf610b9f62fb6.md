# 构造FIRSTVT(U)的算法

1) 若有规则U::= b...或U::= Vb...(存在U⁺⇒b...或U⁺⇒Vb...) 则b∈FIRSTVT(U)

2) 若有规则U::= V...且b∈FIRSTVT(V), 则b∈FIRSTVT(U)
说明:因为V⁺⇒b...或V⁺⇒Wb..., 所以有U⇒V...⁺⇒b...或U⇒V...⁺⇒Wb...