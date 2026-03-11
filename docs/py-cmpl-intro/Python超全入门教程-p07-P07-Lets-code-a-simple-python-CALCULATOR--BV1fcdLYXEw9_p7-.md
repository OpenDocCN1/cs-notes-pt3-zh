# Python超全入门教程-p07-P07-Lets-code-a-simple-python-CALCULATOR--BV1fcdLYXEw9_p7-

Hey， everybody， this is a remake of my Python calculator program for absolute beginners。

 All you need to know to complete this exercise is just if statements and how they work。

 So let's get started for this exercise。 A user is going to select an arithmetic operator。

 operator equals input。😊。

![](img/896cf68bbf4345f93aa6e564a1107929_1.png)

![](img/896cf68bbf4345f93aa6e564a1107929_2.png)

![](img/896cf68bbf4345f93aa6e564a1107929_3.png)

We will ask the user to enter an operator。This will be plus for addition， minus for subtraction。

 As risk for multiplication and a forward slash for division。 You could enter more than this。

 but I don't want to make this exercise too complicated。

 We will create a variable of nu1 to contain our first number。

 Let's say we would like to add two numbers together。What is the first number going to be？

Enter the first number。And let's do this with the second number。Numb2。And turn the second number。

Let me show you something。I am going to add nu1 and nu two together。Numb 1 plus number2。

We'll do a test run。Enter an operator。 I would like to use addition。Enter the first number。10 and 11。

Well， the result is 1011。When we accept user input， they are string data types。

 What we've ended up doing is string account。 We've concatenated the string of 11 to 10。

 That's why we ended up with 1011。 We'll have to convert these two strings。



![](img/896cf68bbf4345f93aa6e564a1107929_5.png)

To be floating point numbers by typecasting them as a float。

So enclose your input functions with a typecast afloat。



![](img/896cf68bbf4345f93aa6e564a1107929_7.png)

And now we should be able to add those two numbers together。So let's add 10 and 11。And we get 21。0。

 depending on the operator that the user selects， we'll use some if statements to determine that We will check if our operator variable。



![](img/896cf68bbf4345f93aa6e564a1107929_9.png)

![](img/896cf68bbf4345f93aa6e564a1107929_10.png)

Is equal to a character of plus。And for now， I'll write pass as a placeholder。

 We'll get back to this later。Else， if our operator。Is equal to minus， we will use subtraction。



![](img/896cf68bbf4345f93aa6e564a1107929_12.png)

And for now， I'll write pass。Else， if operator is equal to an asterisk for multiplication。

 we will multiply。

![](img/896cf68bbf4345f93aa6e564a1107929_14.png)

Else， if our operator is equal to a forward slash for division， we will divide。



![](img/896cf68bbf4345f93aa6e564a1107929_16.png)

If our operator is addition。Let's create a variable of result。Result equals nu 1 plus nu 2。

For subtraction。It's going to be number1， minus number2。Multulplication would be nu1 times nu 2。

Then division would be nu 1， divided by nu 2。

![](img/896cf68bbf4345f93aa6e564a1107929_18.png)

Then we just have to print the result。

![](img/896cf68bbf4345f93aa6e564a1107929_20.png)

Print or result。Be sure to do this with each of the LCSIF statements as well。



![](img/896cf68bbf4345f93aa6e564a1107929_22.png)

And let's see what we have。

![](img/896cf68bbf4345f93aa6e564a1107929_24.png)

Let's add。5。5 plus 6。9。That gives us 12。4。Let's subtract。420。Mine- 0。69。



![](img/896cf68bbf4345f93aa6e564a1107929_26.png)

That gives us 419。31。Let's test multiplication。

![](img/896cf68bbf4345f93aa6e564a1107929_28.png)

Multiply 3。14。Times 3。14， which gives us 9。8596。Than division。Let's divide 69 by 13。

And that gives us a really long number。

![](img/896cf68bbf4345f93aa6e564a1107929_30.png)

So you could round a number if you would like， we would enclose our result within the round function。

And we'll just update each of these print statements。



![](img/896cf68bbf4345f93aa6e564a1107929_32.png)

This will round to the nearest hole integer。So let's divide 420 by 13。



![](img/896cf68bbf4345f93aa6e564a1107929_34.png)

Let's say that we would like three digits after the decimal。



![](img/896cf68bbf4345f93aa6e564a1107929_36.png)

Within the round function， we could add comma 3 for three decimal places。



![](img/896cf68bbf4345f93aa6e564a1107929_38.png)

Enter an operator， let's use division。Divide 420 by 69。So that gives me at 6。087。

 so we can round to a given digit after a decimal。 in this case， three places。

What if somebody types in an operator that doesn't exist， like the word pizza？

Then I will divide two numbers。Well， let's add an else statement。



![](img/896cf68bbf4345f93aa6e564a1107929_40.png)

If somebody selects some input that is invalid， let's let them know。I'll use enough string。

Let's say that the operator that the user has selected。



![](img/896cf68bbf4345f93aa6e564a1107929_42.png)

Is not valid。 And let's try this again。

![](img/896cf68bbf4345f93aa6e564a1107929_44.png)

Enter an operator， P。Enter the first number，4，20 and 69。Pizza is not valid。 Let's say。

 is not a valid。Operator， instead。That makes more sense。Pizza will be my operator。

First number is 420， second number is 69。

![](img/896cf68bbf4345f93aa6e564a1107929_46.png)

Pizza is not a valid operator。All right everybody， so that is a very simple Python calculator program you can make as a beginner。



![](img/896cf68bbf4345f93aa6e564a1107929_48.png)

![](img/896cf68bbf4345f93aa6e564a1107929_49.png)