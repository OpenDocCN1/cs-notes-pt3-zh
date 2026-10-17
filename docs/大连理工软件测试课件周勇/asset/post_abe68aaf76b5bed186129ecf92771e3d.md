

## 集成测试

第2步：根据深度优先或宽度优先的策略，每次用一个实际模块代换一个 stub。

![](img/5fda969404f5a602484516ab14b14f48_219_0.png)

第3步：在结合进一个模块的同时进行测试。

第4步：回归测试（regression testing）——全部或部分地重复以前做过的测试。

## 集成测试

第3步：去掉Driver，自下而上把子功能族合成更大的子功能族。

![](img/5fda969404f5a602484516ab14b14f48_221_0.png)

> 注意：两种策略的优、缺点刚好互补，但单用其中任一种都不实际，通常根据软件的特点将二者混用。

## 集成测试

### 两种方式的比较：

- Incremental testing 可以较早发现模块间的接口错误；Big-bang testing 最后才组装，因此错误发现得晚。
- Big-bang testing 中发现错误后难以诊断定位；Incremental testing 中，出现的错误往往跟最新加入的模块有关。
- Incremental testing 在不断集成的过程中使模块不断在新的条件下受到新的检测，测试更彻底。
- Incremental testing 较 Big-bang testing 费时。Big-bang testing 可以同时并行测试所有模块，能充分利用人力。

![](img/5fda969404f5a602484516ab14b14f48_222_0.png)

## OO中的集成测试

- OO没有层次控制结构，传统方式不再适用
- OO集成测试的策略
  - 基于线程的测试
    - 集成对回应系统的一个输入或事件所需的一组类，每个线程被集成并分别测试。
  - 基于使用的测试
    - 首先，测试独立类，从而开始构造系统
    - 然后，测试下一层的依赖类，通过依赖类层次的测试序列逐步构造完整的系统

## 面向对象的集成测试

## 集成测试的UML支持

在采用UML定义的面向对象软件中，协同图和序列图是集成测试的基础。在系统层，UML描述由各种层次的“用例”、“用例”图、类定义和类图组成。一旦定义了这一层，就增加了集成层细节。协同图显示类之间的（部分）信息传输。图18-1是o-oCalendar应用程序的协同图。

![](img/5fda969404f5a602484516ab14b14f48_226_0.png)

### O-OCalendar的协同图

根据协同图，可以得到以下要集成的类对：

- testIt和Date，为Year、Month和Day建立桩。
- Date和Year，为testIt、Month和Day建立桩。
- Date和Month，为testIt、Year和Day建立桩。
- Date和Day，为testIt、Month和Year建立桩。
- Year和Month，为Date和Day建立桩。
- Month和Day，为Date和Year建立桩。

![](img/5fda969404f5a602484516ab14b14f48_227_0.png)

以协同图为基础进行面向对象集成测试的缺点是，在类级，UML所选的行为模型是“状态图”。对于类级行为，“状态图”是测试用例的很好的基础，特别适合以类为单元的测试。不过问题是，一般来说很难合并“状态图”，以便在较高层次上观察行为。

这种序列图的实际测试应该采用与以下类似的伪代码：

1. testDriver
2. m.setMonth(1)
3. d.setDay(15)
4. y.setYear(2002)
5. Output(“expected value is 1/15/2002”)
6. Output(“actual output is”)
7. test.printDate()
8. End testDriver

## 面向对象软件的MM一路径

面向对象软件中的MM-路径是由消息连接起来的方法执行序列。

原子功能（ASF）是一种MM-路径，从输入端口事件开始，到输出端口事件结束。

```
Class Date
private Day d
private Month m
private Year y

4    Date(pMonth,pDay,pYear)                         msg4
5    y=instantiate Year(pYear)                       msg5
6    m=instantiate Month(pMonth,y)                    msg6
7    d=instantiate Day(pDay,m)
     End     ‘Date constructor
8    increment()
9    if(NOT(d.increment()))                            msg7
10   Then
11       if(NOT(m.increment()))                        msg8
12       Then
13	y.increment()msg9
14	m.setMonth(1,y)							msg10
15	Else
16	d.setDay(1,m)							msg11
17	EndIf
18	EndIf
End	'increment
19	printDate()
20	Output(m.getMonth()+"/"+d.getDay()+"/"+y.getYear())
msg12,msg13,msg14
End	'printDate
class Day isA calendarUnit
Private month m
21	Day(pDay,Month pMonth)
22	setDay(pDay,pMonth)							msg15
```

```
End    ‘Day constructor

23     setDay(pDay,Month pMonth)
24     setCurrentPos(pDay)                         msg16
25     m=pMonth
End    ‘setDay
26     getDay()
27     return currentPos
End    ‘getDay

28     boolean increment()
29     currentPos=currentPos+1
30     if(currentPos<=m.getMonthSize())             msg17
31     Then return true
32     Else return false
33     EndIf
End    ‘increment
```

## Class Month isA CalendarUnit

private Year y

private sizeIdx=<31,28,31,30,31,30,31,31,30,31,30,31>

34 Month(pcur,Year pYear)

35 setMonth(pCurrentPos,Year pyear) msg18

End ‘Month constructor

36 setMonth(pcur,Year pYear)

37 setCurrentPos(pcur) msg19

38 y=pYear

End ‘setMonth

39 getMonth()

40 return currentPos

End ‘getMonth

41 getMonthSize()

```
42 if(y.isleap())
43 Then sizeIndex[1]=29
44 Else sizeIndex[1]=28
45 EndIf
46 rturn sizeIndex[currentPos-1]
End 'getMonthSize
47 boolean increment()
48 currentPos=currentPos+1
49 if(currentPos>12)
50 Then return flase
51 Else return true
52 EndIf
End 'increment
class Year isACalendarUnit
53 Year(pYear)
```

```
54    setCurrentPos(pYear)
    End   'Year constructor
55    getYear()
56    return currentPos
    End   'getYear
57    boolean increment()
58    currentPos=currentPos+1
59    return true
    End   'increment
60    boolean isleap()
61    if(((currentPos MOD4=0)AND NOT(currentPos MOD400=0))OR
    (currentPos MOD400=0))
62    Then return true
63    Else return false
64    EndIf
    End   'isleap
```

