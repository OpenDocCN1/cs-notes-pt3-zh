# Python超全入门教程-p06-P06-If-statements-in-Python-are-easy-(if,-elif,-else)--BV1fcdLYXEw9_p6-

Everybody， in this topic， I'm going to explain if statements。

 and if statement is used to do some code only if some condition we set is true else。

 we could do something else。 It's a basic form of decision making。 If it's true， we do something。

 If it's not true。 We don't do it。 Let's ask a user for their age。 age equals input。



![](img/26574ae142fbb06f2cf03bdeb4f00980_1.png)

Enter your age。 I will type cast the input as an integer。



![](img/26574ae142fbb06f2cf03bdeb4f00980_3.png)

Depending on what the user's age is， we can do one of a few things。

 Let's pretend that the user would like to sign up for a credit card， But in order to do so。

 their age needs to be greater than or equal to 18。 Well。

 we can check that to use an if statement type if。

![](img/26574ae142fbb06f2cf03bdeb4f00980_5.png)

Then some condition。 What would we like to check。 Let's check to see if the user's age is greater than or equal to 18。

 Then add a colon， then hit enter。Any code underneath the ifstatement should be indented。

 Make sure to pay attention to that， because that's easy to miss。

If the user's age is greater than or equal to 18， let's print。 You are now signed up。

If I were to run this code， I'll type in my age， I'll type 21， hit enter。This statement is true。

 Therefore， we will execute any code found within the if statement。 You are now signed up。

 What if this condition was not true。Let's say my age is 13。Well， nothing happens。



![](img/26574ae142fbb06f2cf03bdeb4f00980_7.png)

If the condition we check is instead false， we skip over this code。

 If you need to take a different course of action， you could add an L statement。



![](img/26574ae142fbb06f2cf03bdeb4f00980_9.png)

If this is true， do this else。 We can do something else。Let's print a different message。

You must be 18 plus to sign up。I'll type in my age again。 I'll say that I'm 13。 Hi enter。

 You must be 18 plus to sign up。 That's basically an if statement。

 Do some code only if some condition is true。 else， you can do something else entirely。

 It's a basic form of decision making。 The L statement is kind of like a last resort。

 We can check more than one condition before reaching the L statement， we can add an else。

 if statement。

![](img/26574ae142fbb06f2cf03bdeb4f00980_11.png)

![](img/26574ae142fbb06f2cf03bdeb4f00980_12.png)

![](img/26574ae142fbb06f2cf03bdeb4f00980_13.png)

Which we dish shorten to E， L， I F， meaning else if。Else， if， let's check if age is less than 0。



![](img/26574ae142fbb06f2cf03bdeb4f00980_15.png)

Then we'll print a different message。You haven't been born yet。Now if I run this code。



![](img/26574ae142fbb06f2cf03bdeb4f00980_17.png)

I'll say that my age is negative one。This condition is false。 We skip this code。



![](img/26574ae142fbb06f2cf03bdeb4f00980_19.png)

This condition is true。 Therefore， we will execute this code。



![](img/26574ae142fbb06f2cf03bdeb4f00980_21.png)

And we ski the L statement。 You haven't been born yet。



![](img/26574ae142fbb06f2cf03bdeb4f00980_23.png)

Let's add another Elif statement。 You can add as many elsesif statements as you want。

 Let's check to see if somebody's age is greater than or equal to 100。

 We'll print a different message。

![](img/26574ae142fbb06f2cf03bdeb4f00980_25.png)

Let's print。You are too old to sign up。

![](img/26574ae142fbb06f2cf03bdeb4f00980_27.png)

If I were to say my age is 111 years old。

![](img/26574ae142fbb06f2cf03bdeb4f00980_29.png)

While it states you are now signed up。 the reason that we didn't reach this part of our Elsive statement。

 that's because this condition is still technically true。



![](img/26574ae142fbb06f2cf03bdeb4f00980_31.png)

You do need to pay attention to your order of if and Elsif statements。

 If I want to be sure that nobody over 100 is signing up。



![](img/26574ae142fbb06f2cf03bdeb4f00980_33.png)

I should probably move this to the beginning。

![](img/26574ae142fbb06f2cf03bdeb4f00980_35.png)

If age is greater than or equal to 100。Then else， if age is greater than or equal to 18。

 will' do something else。

![](img/26574ae142fbb06f2cf03bdeb4f00980_37.png)

And to your age， I am 111 years old。 You are too old to sign up。 So those are if statements。

 If some condition is true， do something else， if you can check something else。



![](img/26574ae142fbb06f2cf03bdeb4f00980_39.png)

If no above conditions are true， you could do something else entirely。 It's kind of like the default。

 Here's another example。 We'll ask a user if they would like some food。



![](img/26574ae142fbb06f2cf03bdeb4f00980_41.png)

Response equals input。Would you like food。We'll have the user type in Y for yes or and for no。



![](img/26574ae142fbb06f2cf03bdeb4f00980_43.png)

If our response。Now， to check to see if two values are equal， you would use double equals。



![](img/26574ae142fbb06f2cf03bdeb4f00980_45.png)

If the response is equal to。Why。Then， we will print。



![](img/26574ae142fbb06f2cf03bdeb4f00980_47.png)

Have some food。The doubles equal sign is the comparison operator。

 It will check to see if two values are equal。 You don't want one equals because that's the assignment operator。

 Python， in this case， thinks we're attempting to assign the character Y to response。

 So for comparisons， use double equals。Else。We can print。No food for you。So would you like food。

 I'll type why， have some food。Let's try it again。 I'll type no， and for no。No food for you。

Here's a third example， we'll have a user type in their name， name equals input。Enter your name。

If our name。Is equal to an empty string。 That means they didn't type in anything。

So let's yell at the user。You did not type in your name。Else， we will print using an F string。Hello。

 whatever the name is。And to your name， I'm just going to hit enter。You did not type in your name。

Let's run this again， I'll type in my name。And we have executed the L statement this time。 Ho， bro。



![](img/26574ae142fbb06f2cf03bdeb4f00980_49.png)

So one important thing that you should know is the use of Boolean's with if statements。

 Suppose we have some Boolean variable named for sale。 I'll set this to be true。



![](img/26574ae142fbb06f2cf03bdeb4f00980_51.png)

Now， using an if statement， you can just use the Boolean variable in place of a condition because a condition would evaluate to be true or false。

We could just say， if for sale， if that's true， then let's print。This item is for sale。Else。

 we will print。This item is not for sale。

![](img/26574ae142fbb06f2cf03bdeb4f00980_53.png)

For sale is set to be true。This item is for sale。

![](img/26574ae142fbb06f2cf03bdeb4f00980_55.png)

If this variable were false。Well， then the item is not for sale。Let's try a different variable。

 How about online。If。Online。The user is online。Else。The user is。Offline。So the user is offline。

I'll change the Booleant to trueru。

![](img/26574ae142fbb06f2cf03bdeb4f00980_57.png)

The user is online。So with if statements， you can either write a condition or you could use a Boolean。



![](img/26574ae142fbb06f2cf03bdeb4f00980_59.png)

Al right， everybody。 So those are if statements。 Do some code only if some condition is true else you can do something else。

 It's a basic form of decision making。 And those are if statements in Python。



![](img/26574ae142fbb06f2cf03bdeb4f00980_61.png)