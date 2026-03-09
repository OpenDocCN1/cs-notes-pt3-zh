# 特伦托大学【中英⚡学习编程：基础知识｜Learn to Program： The Fundamentals】 p04 P4 03_Python与计算机内存 -BV1kQ11B5EWa_p4-

![](img/3b9b242cd8ffa237e49e8e16692c15dc_0.png)

Programs keep track of a lot of information。 Some of it is visible to the user。

 such as values in a spreadsheet， but a lot of it is hidden。For example。

 when a spreadsheet program calculates the average of a group of numbers。

 the program first adds up all the numbers， then counts how many there are。

 and then does the appropriate division。

![](img/3b9b242cd8ffa237e49e8e16692c15dc_2.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_3.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_4.png)

All of these values are stored in computer memory。 for the purposes of this course。

 We think of computer memory as being a very long list of storage locations。

 each of which has a unique number called a memory address。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_6.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_7.png)

We will usually write memory addresses with an X prefix so that they look different from other numbers。

 X 201 is memory address 201。

![](img/3b9b242cd8ffa237e49e8e16692c15dc_9.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_10.png)

You can think of these memory addresses as being much like house numbers on a long street。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_12.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_13.png)

As we've said， values are stored in computer memory。 So the number 8。

5 might be at memory address X 34， x 34， and the number 44 might be at memory address X 35。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_15.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_16.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_17.png)

Programs need a way to keep track of all these values。 They do this using something called variables。

 A variable is a named location in memory。

![](img/3b9b242cd8ffa237e49e8e16692c15dc_19.png)

Python keeps track of variables in a separate area of memory from the values。

 We might have a variable shoe size that stores memory address X 3，4。

 That means that shoe size refers to the value 8。5。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_21.png)

In the same way， we might have a variable Paul age， whose value is 44。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_23.png)

We accomplish this by storing memory address X35 with variable Paul H。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_25.png)

A nice thing about Python is that you don't have to worry about which particular memory addresses are chosen。

 Python will keep track of all of this for you。 In fact。

 you can't even pick which memory addresses are used。 However。

 it really helps to keep this model in mind when your're programming。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_27.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_28.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_29.png)

![](img/3b9b242cd8ffa237e49e8e16692c15dc_30.png)

Here is some terminology that will use throughout the course。 A value has a memory address。

 A variable contains memory address。 A variable refers or points to a value。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_32.png)

Here are some examples of how we use this terminology。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_34.png)

Value 8。5 has memory address x34。

![](img/3b9b242cd8ffa237e49e8e16692c15dc_36.png)

Variable shoe size contains memory address， X 34。

![](img/3b9b242cd8ffa237e49e8e16692c15dc_38.png)

The value of shoe size is 8。5。 Sho size refers to value 8。5 Sho size points to value 8。5。



![](img/3b9b242cd8ffa237e49e8e16692c15dc_40.png)