# Python超全入门教程-p34-P34-Python-keyword-arguments-are-awesome--BV1fcdLYXEw9_p34-

Hey， friends， it's me again。 Today。 I'm going to explain keyword arguments。

 A keyword argument is an argument preceded by an identifier。 It has a few benefits。

 It helps with readability， and the order of the arguments doesn't matter if their're keywords。

 Keyword arguments are one of four basic styles of arguments。 We discuss positional default。

 Then next will'll discuss arbitrary。 But today， we'll be focusing on keyword。

 Suppose I have a function to display a message， like a greeting。



![](img/a333a25cc3dca4431fecef82dea2556e_1.png)

![](img/a333a25cc3dca4431fecef82dea2556e_2.png)

![](img/a333a25cc3dca4431fecef82dea2556e_3.png)

![](img/a333a25cc3dca4431fecef82dea2556e_4.png)

I will name this function the Ho function。 We will need a greeting。



![](img/a333a25cc3dca4431fecef82dea2556e_6.png)

A title， Mr。 Mrs doctor。A first name， then a last name。



![](img/a333a25cc3dca4431fecef82dea2556e_8.png)

All I'm going to do within this function is print an up string。 I will print。



![](img/a333a25cc3dca4431fecef82dea2556e_10.png)

My greeting。The user's title。

![](img/a333a25cc3dca4431fecef82dea2556e_12.png)

First name。Last name。Then to invoke the hello function， I will need to pass in four arguments。



![](img/a333a25cc3dca4431fecef82dea2556e_14.png)

A greeting， a title， a first name， and a last name。So from my greeting， let's say。



![](img/a333a25cc3dca4431fecef82dea2556e_16.png)

Hello。The title will be Mr。The first name will be sponongebob。Last name， Square pants。So， you know。

 this does work。 We're currently using positional arguments。

 The position of these arguments does matter。 So what if I were to switch these around。



![](img/a333a25cc3dca4431fecef82dea2556e_18.png)

We have Ho Sponongebob Square pants followed by Mr。 Hello， Spongebob Square pants， Mr。



![](img/a333a25cc3dca4431fecef82dea2556e_20.png)

An optional feature when sending arguments to a function is that we could turn these into keyword arguments。

 Prefix any arguments with the name of the parameter， followed by equals。



![](img/a333a25cc3dca4431fecef82dea2556e_22.png)

![](img/a333a25cc3dca4431fecef82dea2556e_23.png)

Title equals Mr。First， equal spongeebob。Last equal square pants。



![](img/a333a25cc3dca4431fecef82dea2556e_25.png)

Then with these keyword arguments， the order really doesn't matter。

 Maybe we move the first name to the end。

![](img/a333a25cc3dca4431fecef82dea2556e_27.png)

And this still would print out is the same thing。 We have title， first name， last name。

 If you're mixing and matching positional arguments and keyword arguments。

 you want to be sure that the positional arguments are first。

 So if I was to move the string or greeting to the end。



![](img/a333a25cc3dca4431fecef82dea2556e_29.png)

![](img/a333a25cc3dca4431fecef82dea2556e_30.png)

![](img/a333a25cc3dca4431fecef82dea2556e_31.png)

![](img/a333a25cc3dca4431fecef82dea2556e_32.png)

Well， this technically wouldn't work。 We have a syntax error。

 Poal arguments follow keyword arguments， So make sure any positional arguments are first before using any keyword arguments。



![](img/a333a25cc3dca4431fecef82dea2556e_34.png)

![](img/a333a25cc3dca4431fecef82dea2556e_35.png)

2 helpful benefits of using keyword arguments is that it helps with readability。

 and the order of the arguments doesn't matter。 We know what this argument is。

 as well as these two title， last name， first name。



![](img/a333a25cc3dca4431fecef82dea2556e_37.png)

![](img/a333a25cc3dca4431fecef82dea2556e_38.png)

![](img/a333a25cc3dca4431fecef82dea2556e_39.png)

Let's say we have。A first name and a last name， John。



![](img/a333a25cc3dca4431fecef82dea2556e_41.png)

James。These two names kind of sound like first names。Is our first name John， or is it James。

 We could use keyword arguments to clarify which is which you thought John was the first name。

 but it's actually the last name。 And the first name is James。



![](img/a333a25cc3dca4431fecef82dea2556e_43.png)

![](img/a333a25cc3dca4431fecef82dea2556e_44.png)

Then our title is still the same。Hello， Mr。 James John。



![](img/a333a25cc3dca4431fecef82dea2556e_46.png)

Let's cover another example。I'm going to print the numbers 1 through 10。

 using a four loop 4 x in range 1 comma 11， because the second argument is exclusive。



![](img/a333a25cc3dca4431fecef82dea2556e_48.png)

![](img/a333a25cc3dca4431fecef82dea2556e_49.png)

Then I will print X。After each print statement， we print a new line。

 Do you remember in previous topics how we would follow our print statement with comma and then a new character。



![](img/a333a25cc3dca4431fecef82dea2556e_51.png)

![](img/a333a25cc3dca4431fecef82dea2556e_52.png)

Such as a space。

![](img/a333a25cc3dca4431fecef82dea2556e_54.png)

Well， end is a keyword argument found within the built in print statement。



![](img/a333a25cc3dca4431fecef82dea2556e_56.png)

In place of ending each print statement with a new line。

 we are using this keyword argument of end and sending it to be a space。



![](img/a333a25cc3dca4431fecef82dea2556e_58.png)

Another one is separate that's found within the print statement。



![](img/a333a25cc3dca4431fecef82dea2556e_60.png)

Maybe we have some numbers。They're all separate strings。The number one through 5。

I can use the separate keyword argument， then separate each of these strings with a given character or characters。

 I will separate each of these strings with a dash。



![](img/a333a25cc3dca4431fecef82dea2556e_62.png)

![](img/a333a25cc3dca4431fecef82dea2556e_63.png)

A lot of built in functions， such as the print function。

 they have some keyword arguments you can use。Let's go over an exercise now。

We are going to create a function to generate a phone number。

 but we'll need to pass in a country code area code。 The first three digits in the last four digits。

 Let's define this function as define。

![](img/a333a25cc3dca4431fecef82dea2556e_65.png)

![](img/a333a25cc3dca4431fecef82dea2556e_66.png)

![](img/a333a25cc3dca4431fecef82dea2556e_67.png)

Get phone to get a phone number。We have a country code。



![](img/a333a25cc3dca4431fecef82dea2556e_69.png)

Area code。

![](img/a333a25cc3dca4431fecef82dea2556e_71.png)

First meeting。 First few digits。Then last meeting， last few digits。 we will return an up string。

We will place our country code， first。

![](img/a333a25cc3dca4431fecef82dea2556e_73.png)

Dash。Then our area code。Dash。The first few digits。

![](img/a333a25cc3dca4431fecef82dea2556e_75.png)

Dash。The last few digits。

![](img/a333a25cc3dca4431fecef82dea2556e_77.png)

My phone number， phone number equals。 I will invoke the get phone number function we just created。



![](img/a333a25cc3dca4431fecef82dea2556e_79.png)

But we'll need a country code。An area code。First few digits， then last few digits。 And remember。

 the order doesn't necessarily matter。

![](img/a333a25cc3dca4431fecef82dea2556e_81.png)

Usually I try and be consistent with the order of the parameters。



![](img/a333a25cc3dca4431fecef82dea2556e_83.png)

Make up a phone number。 I'm in the United States。 My country code is one。Area code one， two，3。

The next few digits will be 4，5，6。 The last few will be 7，8，9，0。 Then let's print this phone number。

 Pri， phone numb。

![](img/a333a25cc3dca4431fecef82dea2556e_85.png)

![](img/a333a25cc3dca4431fecef82dea2556e_86.png)

And here is my phone number。

![](img/a333a25cc3dca4431fecef82dea2556e_88.png)

Although you can change it up based on how you do phone numbers in your country。

 This is typically how you would see a phone number in the United States。 All right， everybody。

 So those are keyword arguments。 They are just arguments preceded by an identifier。

 That matches the name of a function's parameters。 It does help with readability。

 and the order of the arguments doesn't matter when invoking a function。

 It could be helpful to identify some of these arguments。 And well， everybody。

 those are keyword arguments in Python。

![](img/a333a25cc3dca4431fecef82dea2556e_90.png)

![](img/a333a25cc3dca4431fecef82dea2556e_91.png)

![](img/a333a25cc3dca4431fecef82dea2556e_92.png)

![](img/a333a25cc3dca4431fecef82dea2556e_93.png)

![](img/a333a25cc3dca4431fecef82dea2556e_94.png)

![](img/a333a25cc3dca4431fecef82dea2556e_95.png)