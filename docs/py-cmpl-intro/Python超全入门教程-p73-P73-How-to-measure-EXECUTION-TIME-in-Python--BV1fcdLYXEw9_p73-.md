# Python超全入门教程-p73-P73-How-to-measure-EXECUTION-TIME-in-Python--BV1fcdLYXEw9_p73-

Hey， what's going on， everybody。 So in today's video。

 I'm going to show you how we can calculate execution time in Python。

 Say there's some code we would like to measure。 I wrote a little comment that says your code goes here。

 What we're going to do is measure the time before and after the code by finding the difference between these two points。

 That will give us the eapse time。 So in this example。

 we're going to need the help of the time module。 We will import time preceding the code we would like to measure。

 We're going to create a variable named start time equals。 We will access the time modules。

 performance counter method。😊。

![](img/c845f0f1ef028ec39c68f2f027bb94a0_1.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_2.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_3.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_4.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_5.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_6.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_7.png)

This method will return an arbitrary point in time。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_9.png)

Following our code， we need to get the end time。

![](img/c845f0f1ef028ec39c68f2f027bb94a0_11.png)

I will assign that to a variable again we're going to access the time modules performance counter method。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_13.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_14.png)

We will create an lapse time variable。Eelappsse time equals。The end time。Minus the start time。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_16.png)

How much time has passed？

![](img/c845f0f1ef028ec39c68f2f027bb94a0_18.png)

Then we will print， I'll use enough string。The elapsed time is I'll add a placeholder。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_20.png)

I will display our elapsed time。

![](img/c845f0f1ef028ec39c68f2f027bb94a0_22.png)

Then the word seconds。All right， currently， I don't have any code that we're measuring。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_24.png)

Our elapsed time is going to be an extremely small number。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_26.png)

How don't even know what number that is？It's 5。2 E to the negative sixth power。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_28.png)

All right， now we need some code to measure。

![](img/c845f0f1ef028ec39c68f2f027bb94a0_30.png)

In this example， for our code， let's create a four loop， for I in range。

 we will iterate this loop 1 million times。

![](img/c845f0f1ef028ec39c68f2f027bb94a0_32.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_33.png)

All we'll do is pass， we won't do anything。In this program。

 how long does1 million iterations of a loop take？

![](img/c845f0f1ef028ec39c68f2f027bb94a0_35.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_36.png)

。06 seconds。How about 10 million？7 seconds，100 million。This might take a little bit。6。8 seconds。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_38.png)

Just to clean up the output， I'm going to add a format specifier。

 We're going to display one digit after the decimal。 I'll add 01 F。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_40.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_41.png)

6。7 seconds。Al right， everybody。 So that's how you can calculate execution time in Python Before the code you would like to measure。

 use the performance counter method to give you a start time。 After your code。

 use that method again to give you an end time。 Subtract the start time from the end time to give you the eappsse time。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_43.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_44.png)

![](img/c845f0f1ef028ec39c68f2f027bb94a0_45.png)

And well， everybody， that's how to calculate execution time in Python。



![](img/c845f0f1ef028ec39c68f2f027bb94a0_47.png)