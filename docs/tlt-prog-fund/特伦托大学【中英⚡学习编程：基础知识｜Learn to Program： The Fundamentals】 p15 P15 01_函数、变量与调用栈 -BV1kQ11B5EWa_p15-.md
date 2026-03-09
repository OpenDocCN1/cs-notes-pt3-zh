# 特伦托大学【中英⚡学习编程：基础知识｜Learn to Program： The Fundamentals】 p15 P15 01_函数、变量与调用栈 -BV1kQ11B5EWa_p15-

![](img/4105a3d1442b5a29abef10dce5dfde43_0.png)

In this video， we're going to explore when variables are created。

 how long they exist in computer memory and what happens when two variables have the same name in two different functions。



![](img/4105a3d1442b5a29abef10dce5dfde43_2.png)

Here we see function convert to minutes， which we explored in the function visualization lecture。

We have added function convert to seconds， which converts a number of hours to an equivalent number of seconds。



![](img/4105a3d1442b5a29abef10dce5dfde43_4.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_5.png)

Convert to seconds does its work by calling， convert to minutes。

 and then multiplying the result by 60。

![](img/4105a3d1442b5a29abef10dce5dfde43_7.png)

Let's use the visualizer to explore this。We'll quickly step over the function definitions。

2 function objects are created。 Con to minutes refers to one of these function objects。

 and convert to seconds， refers to the other。Now， we are about to execute an assignment statement。

The first step is to evaluate the right hand side， which is a function call。

 Python first evaluates the argument and creates an object for that value。 Next。

 Python creates a frame on the call stack and stores the memory address of two in the parameter。

 not hours。

![](img/4105a3d1442b5a29abef10dce5dfde43_9.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_10.png)

As a reminder， this area is called the call stack。 It is shown as an upside down stack of frames。

 During execution of a function call， a new stack frame is created。 Whenever a function exits。

 the current stack frame is erased and execution of the previous function continues。

The first line in the body of convert to seconds is another assignment statement。

The right hand side is a function call。 We follow the same rules， as always。



![](img/4105a3d1442b5a29abef10dce5dfde43_12.png)

Evaluate the argument， No hours， which contains the memory address of value 2。



![](img/4105a3d1442b5a29abef10dce5dfde43_14.png)

Then a stack frame is created for the call on convert to minutes。

 and its parameter1 hours contains the memory address of that value。

There are two variables called nu hours。 One of them is in the frame for the call on convert to minutes。

 and one of them is in the frame for the call and convert to seconds。

Python keeps these two running functions in separate areas of memory。

 so it does not get confused about which variable to use。



![](img/4105a3d1442b5a29abef10dce5dfde43_16.png)

Ac to tracing the execution。The first line in the body of convert to minutes is an assignment statement。

On the right hand side does an expression， numb hours time 60。 but which nu hours do we use。

The answer is that Python looks in the current stack frame。Noumb hours refers to two。

 so no hours times 60 evaluates to 120。The second step of the assignment statement is to assign 120 to variable minutes。



![](img/4105a3d1442b5a29abef10dce5dfde43_18.png)

If minutes does not exist in the current stack frame。Then it will be created。

Each stack frame contains its own set of variables in the frame for convert to minutes are variables。

 nu hours and minutes。 The frame for convert to seconds currently only has variable nu hours。

 although by the end of its execution， it will also have both minutes and seconds。



![](img/4105a3d1442b5a29abef10dce5dfde43_20.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_21.png)

The stack frame for the main program currently has convert to minutes and convert to seconds。

 although by the time the assignment statement on line 20 is done executing。

 variableable seconds will exist there。

![](img/4105a3d1442b5a29abef10dce5dfde43_23.png)

![](img/4105a3d1442b5a29abef10dce5dfde43_24.png)

We're now about to return the value of variable minutes and exit the current function。

 But where do we return to。The answer is always to the next frame on the call stack。

 The current stack frame was created during this call on convert to minutes。

 When this call is complete， the current stack frame is erased。

 and Python produces the return value as the value of this function call expression。



![](img/4105a3d1442b5a29abef10dce5dfde43_26.png)

This call is on the right hand side of an assignment statement。To complete the assignment。

 variable minutes will be created， and Python will store the memory address of the return value。



![](img/4105a3d1442b5a29abef10dce5dfde43_28.png)

Let's watch that happen。Notice that the frame for convert to minutes has been erased and variable minutes has been created in the frame for convert to seconds。



![](img/4105a3d1442b5a29abef10dce5dfde43_30.png)

Here we have another assignment statement。 The right hand side。

 minutesute time 60 evaluates to whatever 120 times 60 is。

And a new variable seconds will be created and contain the memory address of that new value。



![](img/4105a3d1442b5a29abef10dce5dfde43_32.png)

Next， we return seconds。 Second refers to 7200。 So that's the value that gets produced by the call on convert to seconds on line 20。



![](img/4105a3d1442b5a29abef10dce5dfde43_34.png)