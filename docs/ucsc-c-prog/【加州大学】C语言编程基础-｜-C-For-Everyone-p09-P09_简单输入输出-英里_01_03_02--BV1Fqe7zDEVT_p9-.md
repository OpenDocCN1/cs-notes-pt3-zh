# 【加州大学】C语言编程基础-｜-C-For-Everyone-p09-P09_简单输入输出-英里_01_03_02--BV1Fqe7zDEVT_p9-

🎼TheYeah。Our next program is to compute the distance of a marathon in yards。

 so it's again a conversion program。

![](img/ffa60fbd8d460ac3e213c25d702ea6c1_1.png)

Very similar to the program。We did where we converted from Fahrenheit to Celsius。

But we're going to see a few extra differences and it's very worthwhile to practice on these programs。

Some of the very basic things you have to get down and they easily trip you up later on if you try to do something more complicated。

So the idea is we're going to take in miles and yards， a marathon distance。

 you can see it to be 26 miles in 385 yards。And there's a formula it's kilometers times roughly 1。

6 times the miles plus the yards， and the yards are divided by 1760。

 And that's just a conversion formula we have to get you to kilometers。And they more printed。

So indeed， if we run this program。呃。I think I precompiled it already。And you see a marathon is 42。

185969 kilometers。Now the program we had just seen。With Fahrenheit。And Celsius。

 we kept all an integer。 That's a rougher。Consideration in this case we wanted。A more。

Accurate answer for the marathon。Otherwise， if he had done it all in integer。

 we would get something like 42 kilometers。And that might be an interesting exercise to check。

 see what you would do if you did it all as an interest program。 see if you would get 42。Now。

 let's explain some of the ideas we find in this program。

This marathon program is taken from a book on sea by myself and my co- authorthor Al Kelly。

 one of the early programs just like the Fahrenheit Celsius program is an early program in Cninggan Richie and again。

If you want to follow this course and you want a lot more detail and lots more exercises。

A book on sea is one place that you can get a lot more exposure。

So there are some differences with the Fahrenheit to Celsius program。

 let's look at what they might be。In that program we had a declaration int miles equals 26 yards equals 35。

That's a declaration with what's called an initializer。

So each of those integer variables is given a value。26 for miles， 385 for yards。Again。That。

Type of statement is a declaration in the program we declare the variables we're going to use。

 we must name them， We want to pick names that are meaningful because that's good for the documentation of the program。

 it makes it easier to read and maintain and easier for other people to use and modify for their own purposes。

So miles and yards were identifiers。It means that that was the data type those identifiers are allowed to use。

And。Recall that on a normal machine， which is typically a four byte machine。

Where an integer is four bytes， you can get roughly plus and minus 2 billion。

So if you go outside that range， something's going to go wrong。

 but if your program only needs the integers and plus and minus 2 billion。You'll be okay。

Now in some machines， you're allowed to go to long endt， which might even be much larger。

 and there's even cases where you can go to long law。But if you need a very large interteger range。

 you have to use special packages。The other key thing to look at in this program is。An expression。

 And that expression。They get this as full screen。That expression。呃。Was kilometers is 1。

609 times miles plus yards divided by 1760。0。 and it's very important that we used。

Po0 rather than 1760。And this is one of the key things that can easily trip。

A non C programmer up and certainly a novice。So I didn't write out miles， I didn't write out yards。

But I'm condensing this expression and adding parentheses。 and those parentheses indicate。The order。

In which。The expressions are done。So the first thing that gets done。Is。7even。Divided by 1760。

And the reason that we were careful about this。To be a double is that if we had this as 1760。

 it would have been an integer divide， but when we make it 1760。0， it's a floating point divide。Now。

235 divided by 1760。 If 1760 was an integer， the answer would be 0。But since it's a double， you get。

And appropriate to something like six significant figures， expression for that value a fraction。

And we didn't want at zero。Now， once this expression is double。And we do this divide。

 and we get whatever we get。 and then we add in miles。

The second thing we've done is now add miles to that。And then finally， we multiply it by。1。609。

And that's the third thing that gets done， and that gives us that answer of。42 kilometers in change。

So it's very important in your expressions to know what domain you're in by domain。

 I mean things like integer and double。Because that's going to tell you what the arithmetic is being done。

And at arithmetic。Can affect the meaning of an operator， like。Divide。

Divide can be an divide if everything is integer or it can be。

A floating point divide if one of the arguments is floating point。

 and then this answer ends up a double。Okay。So this example gives you a number of other ideas。

To go with the ideas from the。Fahrenheit example。And。Let me。Give you a suggested。Exercise。

Modify the program。To input。Input miles and yards。And then it could be a general。Conversion。

 much like the Fahrenheit to Celsiusius。kilometers。

You should be able to readily manage that having looked。At those two programs。



![](img/ffa60fbd8d460ac3e213c25d702ea6c1_3.png)

🎼あ。

![](img/ffa60fbd8d460ac3e213c25d702ea6c1_5.png)

🎼Yeah。