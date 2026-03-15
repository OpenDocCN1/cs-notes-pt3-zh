# 【加州大学】C语言编程基础-｜-C-For-Everyone-p08-P08_简单输入输出-华氏度_01_03_01--BV1Fqe7zDEVT_p8-

🎼TheYeah。🎼Okay。The next program we're going to look at。Is a program that converts。From Fahrenheit。

To Celsius， thats degrees。So remember the Fahrenheit scale， for example， for ice， that's 32 degrees。

 but Celsius， which is a little more logical， it's in the meter system and we go from zero。

 which is ice， the boiling water， which is 100， which in Fahrenheit would be 212。And it's。

A little hard to do that in your head。 So we're going to just write a little program。

 And the reason we're going to do that program is。That。



![](img/e086835cc4a94c96ce96fdd6d94c0d73_1.png)

It illustrates。A number of principles。That we find in the C language and indeed it's one of the early programs。

A form of it is an early program in the great classic。啊。

TheC programming language by Carnegan and Richie， and of course。

 remember Rie is the inventor of the language。And there's a lot to learn。

If you're going to get serious about the see language。

 it's definitely a book you want to consider on your bookshelf。嗯。Now。

As before we're going to do input output and the character of the program is we're going to ask you to type in a Fahrenheit。

Temperature， and then the conversion will be to a Celsius temperature。It main void， of course。

 Maine by convention is where we always start our programs。

 So a C program should always have a main and technically。It's tight， its return type is integer。

We're going to use， though， if we wanted more scientific precision， we might use double。

 but in this case， we're going to use。Int as the basic type for Fahrenheit No Celsius。And then。

We're going to be polite on asking for data entry。Please enter your Fahrenheit as an integer。

And notice again for the moment， if you don't fully understand it。The scanf， which gets us input。

We have a format。That。Of percent D， which is a format for integer。

 And then we use this fancy symbol called empersand。 And the empersand means shove it in the address。

A Fahrenheit。We can't say Fahrenheit without the empersent because Fahrenheit is a variable。

 And if we said Fahrenheit， we would look for the value in that variable。 In this case。

 we want to look for the address of that variable。 an address is location and memory。

And then here we do the computation Celsius， it's Fahrenheit minus 32， and's divided by1。8。

Or equivalently we could have multiplied by five9s。And that's。

A conversion when I say note conversion， that little comment。

Means that this expression is actually going to be done as a double because。Constant 1。

8 is a literal double。Even though this is an integer。

And then this all gets done as a double and then gets reconverted to an integer。

So there are what are called silent conversions going on， and we will have to understand them。

 They're often confusing for the beginner。Finally， we use a print f。And we have again。In that printf。

We have。Two places where we're going to output。Integers。So we're going to output an inture。

Percent T of Fahrenheit and percent the of Celsius。 Both will be integers and return 0 is just。

The clear way， even though it could be omitted， that says。We finished。

With Maine and everything is okay。Let's actually do a conversion。I think I already compiled it。

So a do out。Now let me just clear the screen。No。For example， 32。

And that would be 32 Fahrenheit is zero Celsius。see it a little better。

 I'm going to clear the entire screen， I will run my executable again。

 let's see what happens if we do boiling Fahrenheit， boiling water， so that's a0。And if we。

Were to do some random thing in the middle。Currently where I'm sitting。

 it's about 92 degrees Fahrenheit， so Celsius， that would be 3。Okay。

That program shows us how to use simple variables， how to compute simple expressions。

And how to do input and output， and while it's not exactly the Carnegie and Richie program。

It is very close。And if you go to Kernning and Rie。

 what would be added in their version of the program is a little more sophisticated。

 and we're not ready for that， they do a while loop and print a whole table。



![](img/e086835cc4a94c96ce96fdd6d94c0d73_3.png)

🎼Yeah。

![](img/e086835cc4a94c96ce96fdd6d94c0d73_5.png)