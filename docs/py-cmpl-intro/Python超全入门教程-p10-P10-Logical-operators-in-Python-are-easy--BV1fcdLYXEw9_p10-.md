# Python超全入门教程-p10-P10-Logical-operators-in-Python-are-easy--BV1fcdLYXEw9_p10-

All right。 Another day another video In this topic， I'm going to explain logical operators。

 logical operators are used on conditional statements， such as an if statement。

 There's three types we'll talk about and or not。 Each exhibits different behavior and we'll check to see if two or more conditions are true。



![](img/d8147ec1d2bf4a124432b69e1a01005a_1.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_2.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_3.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_4.png)

Or checks if at least one condition is true。Not is a little different。

 Not will change the result of a condition。 If a condition is true， it's now false。

 If it was originally false， it's now true。

![](img/d8147ec1d2bf4a124432b69e1a01005a_6.png)

Here's an example。 Say we have a program to check the temperature。 Temp equals 25。

 The temperature will be in Celsius。 In this example。

 if the temperature falls within a certain range， I would like to print a message that says the temperature is good。

 I can check more than one condition using the and logical operator。



![](img/d8147ec1d2bf4a124432b69e1a01005a_8.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_9.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_10.png)

Let's check if our temperature falls between the range of between 0 and 30。

 If temp is greater than 0。

![](img/d8147ec1d2bf4a124432b69e1a01005a_12.png)

And temp is less than。

![](img/d8147ec1d2bf4a124432b69e1a01005a_14.png)

30。Then， we will print。Temperature。

![](img/d8147ec1d2bf4a124432b69e1a01005a_16.png)

Is good。 If this condition is true and this condition is true， then we will execute this code。



![](img/d8147ec1d2bf4a124432b69e1a01005a_18.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_19.png)

Else， we will print。

![](img/d8147ec1d2bf4a124432b69e1a01005a_21.png)

The temperature is bad。Our temp is currently 25。

![](img/d8147ec1d2bf4a124432b69e1a01005a_23.png)

The temperature is good。 What if it was negative 10 degreesC。Well， the temperature is bad。



![](img/d8147ec1d2bf4a124432b69e1a01005a_25.png)

What if it was over 30， like 40 degrees Celsius。Well， then the temperature is still bad。



![](img/d8147ec1d2bf4a124432b69e1a01005a_27.png)

Using an and logical operator， if one of these conditions is false。

 then this entire statement will evaluate to be false。

 We would then skip over any subcode and continue on using the and logical operator is pretty convenient。

 If you need to check to see if something is within a certain range， like a temperature。

 There is another way we can write this， too， using the or logical operator Let's replace and with or。



![](img/d8147ec1d2bf4a124432b69e1a01005a_29.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_30.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_31.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_32.png)

If at least one of these conditions is true， then the entire statement is true。



![](img/d8147ec1d2bf4a124432b69e1a01005a_34.png)

How about if temp is less than or equal to 0 or if temp is greater than or equal to 30。



![](img/d8147ec1d2bf4a124432b69e1a01005a_36.png)

Then， the temperature is bad。Else， the temperature is good。Currently， our temperature is set to 40。



![](img/d8147ec1d2bf4a124432b69e1a01005a_38.png)

Well， the temperature is bad。This is false， but this is true。 usingsing the or logical operator。

 only one of these conditions needs to be true。

![](img/d8147ec1d2bf4a124432b69e1a01005a_40.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_41.png)

If our temperature was negative 15。

![](img/d8147ec1d2bf4a124432b69e1a01005a_43.png)

Well， the temperature is still bad。But if it was。20。Well， then the temperature is good and。

 as well as or are fairly similar with and two or more conditions need to be true for the statement to be true with or only one of them needs to be true。

 Is this true or is this true。

![](img/d8147ec1d2bf4a124432b69e1a01005a_45.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_46.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_47.png)

Now， not is a little different。 Let's say we have a Boolean variable named Sunny。

 Is it sunnyny outside。 I'll set this to be true。

![](img/d8147ec1d2bf4a124432b69e1a01005a_49.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_50.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_51.png)

Using an if statement， if sunny is equal to true。 But if you're working with the Boolean。

 you can just shorten this to the Boolean itself。

![](img/d8147ec1d2bf4a124432b69e1a01005a_53.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_54.png)

If sunny。Then， print。It is sunny。Outside。

![](img/d8147ec1d2bf4a124432b69e1a01005a_56.png)

Else。Print。It is cloudy。Outside Sonia set to true。

![](img/d8147ec1d2bf4a124432b69e1a01005a_58.png)

Therefore， it is sunny outside。 If sunny were set to false。



![](img/d8147ec1d2bf4a124432b69e1a01005a_60.png)

It is cloudy outside using the a not logical operator。 that would flip the result。



![](img/d8147ec1d2bf4a124432b69e1a01005a_62.png)

So， if not sunny。Then it is cloudy outside。Else， it is sunny outside。



![](img/d8147ec1d2bf4a124432b69e1a01005a_64.png)

Sonia is set to false。 It is cloudy outside。If Sony were true。



![](img/d8147ec1d2bf4a124432b69e1a01005a_66.png)

Well， then it's sunny outside。 The not logical operator will change something that's true to be false。

 or if it was originally false， it's now true。

![](img/d8147ec1d2bf4a124432b69e1a01005a_68.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_69.png)

All right， everybody。 So those are logical operators。 They're used with conditional statements。

 theirs and or not。 We'll have more practice with these in the future。 And yeah。

 those are a few logical operators in Python。

![](img/d8147ec1d2bf4a124432b69e1a01005a_71.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_72.png)

![](img/d8147ec1d2bf4a124432b69e1a01005a_73.png)