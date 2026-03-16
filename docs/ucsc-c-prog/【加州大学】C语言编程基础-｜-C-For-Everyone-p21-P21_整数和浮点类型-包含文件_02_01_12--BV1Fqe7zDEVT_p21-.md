# 【加州大学】C语言编程基础-｜-C-For-Everyone-p21-P21_整数和浮点类型-包含文件_02_01_12--BV1Fqe7zDEVT_p21-

🎼2。🎼。

![](img/e3f9c54339cac416a5a3d9856bd701ab_1.png)

The next data type we're going to talk about are the floating point numbers。

As you can see with the little sea turtle。He's really happy when he's floating in the sea。

So here are the float types in C。Float。Double。And long double。And these are three types that are。

Usually。Ordered and shortest to longest。AndWe'll see there is a catch here。That's not guaranteed。So。

 the shortest。Is float and its range is typically from 10 to the-38。

 a pretty small number to 10 to the positive 38， pretty large number。For example。

 scientists think that the universe is something like。10 to the 88th。あ。Adams。So。

That's an even larger number， but this is still pretty significant。For example， on earth。

 there's something like。Seven times 10 to the ninth people or seven billion people。

And then that can be expressed with six significant figures， as in 0。123456。

 And then there's an exponent part， which is 10 to the 12th and showing the exponent part of the float。

We use an E。 So this is a general way to write the integer part。The fractional part。

The exponent and then a plus or minus integer here。And you can consider that there's a sign。

 a sign of the entire floating point number of fraction and the exponent。Now if we go to。

On most machines， the longer type。 And typically， again， if you use the size of operator on a float。

 you'd find。Mostly that it was 4 Bs and double you'd find is twice as large or 8 Bs。

 And that lets us express more stuff。So one of the things that gets increased is the range。

 the range becomes from this extremely small number，10 to the -38 up to a very large number。

10 to the 38。 Then we would have。No problem representing the number of atoms in the universe。

 and instead of six or seven significant figures we typically get 15 significant figures。Finally。

We have long double。And long double， when it's implemented。And is larger than double。

Stays with the same。Exponent range。 but has a great deal， more significant figures。

 So there's an IBM implementation where there are 31 significant。Digits， but again。

 this can be system dependent。So we have。In the sea system。These three types float， double， long。

 double。You can declare a variable of any one of these types。

The notion is float conserves the most space。Double is typical。

 so frequently I just use double for most of my things。And long double。

Get you all this extra significant figure， but the only thing guaranteed by the C compiler is。

If there's。Double it will be at least as large as float。

And at le is significant and if there's a long double， it will be at least as large as double。

And they're significant。So it could， conceivably on some。Especially early sea system。

All three of these could really mean the same thing， but then on some modern supercomputer。

 they may also be。Clearly distinguished in the way we just talked about。Finally。

 we have to know how to write literals or constants。

And here's three ways to write the constant one notice。One is not of that way。

 so it's not possible if you write down one without a decimal point。

That's going to be the integer literal。And we're going to see later when mixing types。

 this can be very important。So if we want， we can write 1。0， which is quite clear。

Or one point and not have the。Fraactctional part， or we could write 0。1 E of1。

 which is another way of saying。That's a power of 10， so that would just shift it to one。

And this would be the least confusing， but all of these would lead to the same。Literal。

That's a floatat。Now。It's important to understand that significance。It's critical。In a computation。

So when you're dealing with these numbers， they are not like real numbers。From mathematics。

In the world of mathematics。There ostensibly is a place on the real line where you could show pie in Wall its glory。

 3。14159， cea， et cea， et cea。With as much precision as you want。In。

A standard representation like a double for pie。You could only get。Your。6 or 15。Significant digits。

Represented as a double。So you're going to lose some precision。

And think about where this could show up， you might have a computation which looks okay like you've added。

A tense， the real number， a tense to the real number 1，2，3， by real number， I mean。

 double 1123 raised to the 10th of the 12th power。It turns out this number is so large that when that's added in。

 the result is no change on this number。 It's dwarfed by the larger part of the number。

So that means this computation if you put it。In some expression。Would。Not have an effect。

And in more advanced courses on numerical analysis。

People who are specialists in this have to keep track of precision。

 loss of precision and some of the precision that may come about because a number that looks like it's precise and decimal might not translate to it being precise under the kind of binary representation that's used for a floating point number。

 so something like，1 and a third，1。33333 might not have the same kind of。

Precision when it's translated to the internal number。Okay， finally。

 we also want to know how to do input and output with these float。

So that means we want to know about conversion characters and we have a selection of conversion characters available we can use percent lower KC or percent upper KC。

And then it prints as。A。Number with a fraction and an exponent part。Where we can have。

A percent F and it prints as。A number written out， but without the exponent。Finally。

 we can have a more。Flexible。Format， which is percent G or percent uppercase G。And they。

Pick from E or F and decide on which one to use based on what gives you the shortest representation。

 So this is more flexible， which you might end up with one or the other。

Depending on which is shortest on printing to the screen。Okay， in the next segment。

 I'm going to use some of those ideas and actually write a little piece of code to show some of those ideas。

🎼And。Get you used to printing。Doubles and also to using。

The math library which has functions like square root and sign， so you might look online too。

Do a little。Work on how the math library can be used。



![](img/e3f9c54339cac416a5a3d9856bd701ab_3.png)