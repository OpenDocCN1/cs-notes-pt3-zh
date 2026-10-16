# 不符合开闭原则的情况

<<Interface>>
Creator
+getObjA: ProductA
+getObjB: ProductB
+getObjC: ProductC

ConcreteCreator1
+getObjA: ProductA
+getObjB: ProductB
+getObjC: ProductC

ConcreteCreator2
+getObjA: ProductA
+getObjB: ProductB
+getObjC: ProductC

<<Interface>>
ProductA
+operationA

ProductA1
+operationA

ProductA2
+operationA

<<Interface>>
ProductB
+operationB

ProductB1
+operationB

ProductB2
+operationB

<<Interface>>
ProductC
+operationC

ProductC1
+operationC

ProductC2
+operationC

When you want to add a whole new class hierarchy productC, this pattern doesn’t follow open-closed principle, since in both Concrete creator classes, you need to add getObjC method

Back