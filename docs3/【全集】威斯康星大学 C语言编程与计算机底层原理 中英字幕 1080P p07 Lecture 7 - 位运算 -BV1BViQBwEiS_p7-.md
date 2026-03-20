# 【全集】威斯康星大学 C语言编程与计算机底层原理 中英字幕 1080P p07 Lecture 7 - 位运算 -BV1BViQBwEiS_p7-

![](img/feddeade64179ad0e66ecd303c94c392_0.png)

Hello， everyone， Welcome back to the second part of this week's lecture for machine organization and programming。

 Today， we're going to be looking at Biwise operators。 This is section 2。17 through 2。

110 of our textbook。 And again， some excellent example practice problems available at the end of that section。

 And again， what I want to do here is provide like a high level overview that makes the book accessible。

 The book goes very deep into these things practice problems sort of require that。

 But in order to make that accessible， that's sort of the goal of my lecture here is introduce these ideas。

😊。

![](img/feddeade64179ad0e66ecd303c94c392_2.png)

![](img/feddeade64179ad0e66ecd303c94c392_3.png)

![](img/feddeade64179ad0e66ecd303c94c392_4.png)

![](img/feddeade64179ad0e66ecd303c94c392_5.png)

![](img/feddeade64179ad0e66ecd303c94c392_6.png)

![](img/feddeade64179ad0e66ecd303c94c392_7.png)

![](img/feddeade64179ad0e66ecd303c94c392_8.png)

All right， and again， so bitwise operations are going to be you know math things we can do on an actual set of bits。

 you know， a binary number in the computer。 It gives us sort of a preview of the kinds of instructions that are available on the CPU。

 And it's also going to give us sort of a we'll talk about speed。 So as we write our own code。

 we can maybe take advantage of some of these things we learn to make our code run even faster。😊。



![](img/feddeade64179ad0e66ecd303c94c392_10.png)

![](img/feddeade64179ad0e66ecd303c94c392_11.png)

![](img/feddeade64179ad0e66ecd303c94c392_12.png)

![](img/feddeade64179ad0e66ecd303c94c392_13.png)

![](img/feddeade64179ad0e66ecd303c94c392_14.png)

All right， and I've got a couple of examples as to why we might ever care about looking at something at as low level as bitwise operations when we're writing code those examples are first bit masks where we may have you know a four byte integer I only care about one piece of it and so a bit mask is a way to extract that information in my example there is a packed integers from computer graphics。

 if we have red， green， blue and alpha channels for a number each of those are one byte Well rather than taking an integer to store each of them which is wasteful integers4 bytes。

 I only need one by for each of the color channels。

 I can pack them all together into one integer with all four pieces of data。😊。



![](img/feddeade64179ad0e66ecd303c94c392_16.png)

![](img/feddeade64179ad0e66ecd303c94c392_17.png)

![](img/feddeade64179ad0e66ecd303c94c392_18.png)

![](img/feddeade64179ad0e66ecd303c94c392_19.png)

![](img/feddeade64179ad0e66ecd303c94c392_20.png)

![](img/feddeade64179ad0e66ecd303c94c392_21.png)

![](img/feddeade64179ad0e66ecd303c94c392_22.png)

And very similarly， Boolean values can be represented as bit flags。

 If I have more than one boolean value for a particular piece of data， like a struct of some kind。

 each Boolean value only needs one bit。 And the smallest available data type in C is the1 by。

 a car care or a， a character。

![](img/feddeade64179ad0e66ecd303c94c392_24.png)

![](img/feddeade64179ad0e66ecd303c94c392_25.png)

![](img/feddeade64179ad0e66ecd303c94c392_26.png)

So， and that's going to waste 7 Bs worth of data。 So if I can pack more than one type of boolean operation a boolean true false value into one data structure。

 that's going to save memory。 All right， so without further ado， let's go ahead。

 jump in and begin talking about bidwise operations。



![](img/feddeade64179ad0e66ecd303c94c392_28.png)

Okay， so and C， we've got six pit wide operators that I'm going to talk about right now。

 The first is the or operator。 And that's just going to be the vertical pipe， the and operator。

 the ampers， the knot is the tilde， the exclusive or is the carrot。



![](img/feddeade64179ad0e66ecd303c94c392_30.png)

Shift6。does not mean exponentiation in C。We also have the left shift and right shift operators。

 which are just the double greater than or double less than signs。



![](img/feddeade64179ad0e66ecd303c94c392_32.png)

Okay， let's take a look at how these work。And we're going to go through this with some examples。

 First， we need all of our numbers to be in binary， so ones in zeros。And then here's my example。

 So if I have x and y 1，0，1，0。 And I'm going to start with the top1。 I'm looking at the or operator。

 This is just going to take each of the pairs of bits in each position。 So over here。

 I've got the 0 in the B0 position and another0 and the B0 position and a perform an or operator on those bits and store that again in the resulting B0 position。

 So for an or if either one of these is a1， it'll have a one only if they're both0， will give me a 0。

 So in the B1 position， I've got two1s that's going be true。

 So we'll have a one there here we have a one in that position。 So we'll get a1 And here in B3。

 we have a1 in the x variable。 So that'll be 1 also。



![](img/feddeade64179ad0e66ecd303c94c392_34.png)

![](img/feddeade64179ad0e66ecd303c94c392_35.png)

![](img/feddeade64179ad0e66ecd303c94c392_36.png)

![](img/feddeade64179ad0e66ecd303c94c392_37.png)

And works exactly。The same way。So in this case， instead of。Yeah， if they're both 0。 and we get 0。

 They have to be able both be one in order for this to be 1。

 So both values must be true or one logical 1 in order to get a 1。 So 0，1 has a 0 right there。

 So that'll end up a 0。1，0 has a0 here。 So we're just looking at vertical columns in the same bit position。

 now I' how to just highlight here。 I putting in the numbers here。 This is number 10。

 This is number 6。 This resulting number really doesn't have a neat mathematical explanation at this point。

 to get their really doesn't make sense。 There's not a lot of connection。

 So here when we did and we get a two The other one we got a 14。



![](img/feddeade64179ad0e66ecd303c94c392_39.png)

![](img/feddeade64179ad0e66ecd303c94c392_40.png)

![](img/feddeade64179ad0e66ecd303c94c392_41.png)

14 right， yep， all right， yeah。 so not a lot of connection。So the next one is the not operator。

 So this is the only unary operator here。

![](img/feddeade64179ad0e66ecd303c94c392_43.png)

Wait， that's not true。 Shifting is also well。It only operates on one variable。

 so this is the only real unary operator。 So in this case， I've got my example 1，0，1，0。

 When I do the not operator， that's just going to flip all of the bit。

 It's going to take ones and turns them into zeros， zeros， turn them into ones。

 It's the same as the ones complement。 So in this case， I've gone from 10 to 5。 Again。

 no real connection here。

![](img/feddeade64179ad0e66ecd303c94c392_45.png)

嗯。If we were to add one to this， It' would be like negating the number and twos complement。

 because that's how the machines actually represent the numbers。



![](img/feddeade64179ad0e66ecd303c94c392_47.png)

![](img/feddeade64179ad0e66ecd303c94c392_48.png)

Okay， next up， the exclusive or what we're looking at here， again， I'm taking two numbers。

 if the values in the positions are the same that's going to return a0。

 and there they are the both one。 They're the same。 that's going to be a 0。 And if they're different。

 So if I have a 0 to1 or a 1 and a 0。 Those are going be return a1。

 So it's going to fill in with a one in those bit positions。



![](img/feddeade64179ad0e66ecd303c94c392_50.png)

![](img/feddeade64179ad0e66ecd303c94c392_51.png)

嗯。I'm trying to think of an example where that would be useful。 And I know I've used it in the past。

 but my mind is blank right now， sorry， guys。

![](img/feddeade64179ad0e66ecd303c94c392_53.png)

嗯。Let me just move on。 So the left shift operator is going to take a binary number and just move all of the bits over to the left。

So if I'm doing a shift by4， it'll take all the numbers。

 shift them over four positions and give me the number。 So this 0 right here in B3 ended up in B7。

 the 0 here in B0 ended up in B4。 So 0，0，10 ended up 0，0，10。

 and it's just going to shift in 0s for the the bits that were vacated。By the shift to the left。

 the bits， the most significant bits here on the left， because there's not room to store them。

 They are just lost。 So we no longer have that data。Allright。

 so pretty straightforward it works the same for signed and unsigned numbers。 Oh。

 I should also mention that the left shift and right shift are not strictly defined by the guidelines for writing C。

 they're compiler dependent or system dependent and the guys who write the compilers can do whatever they want here。

 This is the most common way that we willll see this and this is the way that it's implemented on the CSL machines。



![](img/feddeade64179ad0e66ecd303c94c392_55.png)

![](img/feddeade64179ad0e66ecd303c94c392_56.png)

![](img/feddeade64179ad0e66ecd303c94c392_57.png)

![](img/feddeade64179ad0e66ecd303c94c392_58.png)

Okay， yeah。 so right shift。 This is going to depend on whether we have a signed number or an unsigned number。

 So， and whether when we look at sign numbers， whether it's positive or negative。

 So the first example here， I've got assigned signed X， this is going to be a negative number。

 I can see because I have a one right there in the first position。

 If I are to do my right shift to the four position。 that's going to take these four bits。

 the most significant bits。 and they're going to become the four least significant bits。

Because this is negative， it's going to shift in ones all the way across here。

I'll talk a little bit about this as in an example in just a second for a positive number。

 like this number right here， it's going to shift in zeros。 So the 0，1，1，0。

 the four most significant bits become the four least significant bits，0，1，1，0。

 and it's going to shift in zeros。AllrightThis is known as an arithmetic shift。

 It's just the name of it。 I can't for the life of you。 Remember that。

 I don't expect you guys to either just happens to be what it's called。



![](img/feddeade64179ad0e66ecd303c94c392_60.png)

🎼Al right， so one way to think about this is we're going to be shifting in whatever's in this most significant bit position。

 We're just going to copy it over。

![](img/feddeade64179ad0e66ecd303c94c392_62.png)

H， my phone's been ding all morning。 It's lot like sign extension。



![](img/feddeade64179ad0e66ecd303c94c392_64.png)

Okay， and then the for unsigned values， we'll be using a logical shift。 And again。

 I can't remember the name。 I have to look it up every time。 So I don't expect you guys to either。

 But here's the idea， because we're looking at unsigned values。

 were just always going to be shifting in zeros。 So I take my 10 or 1。

 These for most significant bits， become the least significant bits。

 I didn't get this lined up very well。 I'll fix that before I put them online。



![](img/feddeade64179ad0e66ecd303c94c392_66.png)

And we shift in zeros。

![](img/feddeade64179ad0e66ecd303c94c392_68.png)

Alright， guys， So all of these bitwise operations are widely used and can be implemented to write some very efficient code。

 I want to just give you a couple of examples where this is definitely possible。

 and places I've used them in the past。 All right， So first up。

 I need to introduce the idea of bit masks。 Bi masks are used to extract certain bits from a pattern。

 So in like I'm going just do an example here。 If I want to extract the 4 least significant bits from this number。

 If I've got x 1，0，0，1，0，0，1，0， I'm gonna get just these4 least significant bits，0，0，1，0。

 That's what I want。 So to do that。 actually， pause the video right here。

 go look at those6 operations and see if you can figure out a way to turn 1，0，0，1，0，0，1。

0 into just the four least significant bits。😊。

![](img/feddeade64179ad0e66ecd303c94c392_70.png)

![](img/feddeade64179ad0e66ecd303c94c392_71.png)

All right， pause video， see if we can figure out and then come right back。



![](img/feddeade64179ad0e66ecd303c94c392_73.png)

Okay， I'm back with the answer。 It's pretty straightforward。

 We can use the and operator to create a mask that'll clear some of the bits and retain others。

 So if I just look at this sort of bit pattern as a window。 If I've got zeros here。

 it's going to block these。 because anything ended with zero is going to give me 0。

 So that's just going to cancel out all of these bits and turn them into zeros。



![](img/feddeade64179ad0e66ecd303c94c392_75.png)

![](img/feddeade64179ad0e66ecd303c94c392_76.png)

![](img/feddeade64179ad0e66ecd303c94c392_77.png)

![](img/feddeade64179ad0e66ecd303c94c392_78.png)

And then if I look at the ones as if a window that I can see through anything ended with one just stays what it is。

 So 0 and1， when I ended together is going to give me the0 again and 0。 and this will retain the1。

 So I'm going to end up with 0，0，10。

![](img/feddeade64179ad0e66ecd303c94c392_80.png)

Just like that。 So that's all there is to it。 pretty straightforward。 let's do another example。

So suppose instead of the four least significant bits， we want to get the four most significant bits。

 So I want to return。 if I've got this number 1，0，0，1，0，0，1，0， I want to return these for1，0，0，1。

 but I want them to be in the least significant position here。 So I just want to grab these。

 I want to know that my number is 9 in this case。

![](img/feddeade64179ad0e66ecd303c94c392_82.png)

All right， so pause the video， think about how you might do this。

 and I'll be right back with the answer。

![](img/feddeade64179ad0e66ecd303c94c392_84.png)

Alright， guys， I'm back。 Take a look at this。 We're going to do this in two steps。

 The first thing we're going to do is shove all of these bits。 the 1，0，0。

1 over into the least significant bit position。 So they're in the right spot， at least。

So if we do this， this number happens to be a negative number and there's a one here。 if it's signed。

 that is。 So it will fill in the first for most significant bits with ones。 when we do that， the 00。

1，0 is going to be lost because it's going to get shoved out of a place where there's no bit to store that data and we'll get the 1001 in the correct position。



![](img/feddeade64179ad0e66ecd303c94c392_86.png)

![](img/feddeade64179ad0e66ecd303c94c392_87.png)

The next thing we're going to do。 step 2 is to use the and operator to create that mask that's going to cancel out all these ones I just shifted in and retain。

The 1，0，0，1。All right。Pretty straightforward， I just had to do it in two steps。

I'm going to Trump down。Oh yeah， yeah， there's the answer one or0 one。Jump down。

 I want to talk about packed integers for a second。 And here's my example。

 This is where it's very common。 In computer graphics。

 we're going to represent colors by four numbers， red， green， blue。

 and then an alpha channel to represent transparency。



![](img/feddeade64179ad0e66ecd303c94c392_89.png)

Each one of these is going to be one byte， so it's got values between 0 and 255。

Or0 to FF and alpha is going to represent the transparency。

 So0 alpha would be completely transparent255 or FF is going to be completely opaque。

 That means we can see it。 This is used for compositing。

 If I want to layer images on top of one another。 I can do the with alpha masking。



![](img/feddeade64179ad0e66ecd303c94c392_91.png)

Okay， so here's the idea。 I'm going to store all four of these bys because there's just one by into a 4 B integer and it's going to save me a bunch of space。

 That way I don't have to waste a full in for each one of these numbers。 Allright。

 so the challenge then is how do I get out a particular value。 So if I want to grab blue。

 So it's going to be red will be the 8 most significant bits。 Then green will be the next8。

 Then blue will be the next8。 Al will be the least significant。 So what I really need。

 So alpha is going to be B0 through B7。 blue will be 8 through whoops。

8 through 15 green will be what is that 16 to 23 and 24 to 31 red。

 So if I want to grab a particular color。 if I'm on blue， I need to be8 through 15。😊。



![](img/feddeade64179ad0e66ecd303c94c392_93.png)

![](img/feddeade64179ad0e66ecd303c94c392_94.png)

Over here， I was thinking while I'm using green text。

 I shouldn't do blue as an example when I've got green text。

And sorry to those of you guys who are colorblind， but here's the idea。



![](img/feddeade64179ad0e66ecd303c94c392_96.png)

I'm going to go ahead and grab bits 16 through 23。To extract the green color。

 And if my in my green text here， I've got 0 red。

![](img/feddeade64179ad0e66ecd303c94c392_98.png)

There's full green。0 blue。 and it's fully opaque。 I can totally see it。 It's not transparent。

 So this is going to be my bit pattern for the packed integer， for the full color。

 What I really want to do is extract just the green。 It should be F F 1。 I'm all done， or 2，55。So。

Pause for a second。 See if you can figure this one out on your own。And then come back for the answer。



![](img/feddeade64179ad0e66ecd303c94c392_100.png)

Alright， We back。 Here's the idea。 We're going to do this in two steps。 Also。

 the first thing we're going to do is shift this by 16 B， and we're going to go to the right。

 So in this case， we're going to move。

![](img/feddeade64179ad0e66ecd303c94c392_102.png)

Yeah， this is going be 4 bits，4 bits，4 bits，4 bits。 And that's 16。

 So that will move this F F all the way over into the rightmost position。 In this case。

 I'm starting with a leading0 bit。 So it's going to fill in with zeros。 If this had been a one。

 it would fill in with ones。So once I get the FF over here in the rightmost position。

 the bottom 8 bits， I need to do a mask again， and I'm going to end with 0，0，0，0，0。

0 FF to just retain those bottom 8 bits。 In this case。

 I didn't need to do that because it would shift in zeros， but I didn't know that。

 So I'm going to go ahead and do that anyway。

![](img/feddeade64179ad0e66ecd303c94c392_104.png)

![](img/feddeade64179ad0e66ecd303c94c392_105.png)

Alright， so there's the idea behind packed ins Next up， I'm going to talk about bid flags a second。

 but I need to go make a slide for that one second。



![](img/feddeade64179ad0e66ecd303c94c392_107.png)

All right， I'm back。 I made some slides for this。 I'm pretty happy with them。

 So bit flags or bit fields are just a way that we can store Boolean data very efficiently。

 Boolean data is just a one or a0 and see true or false。 I only need one bit for it。😊。



![](img/feddeade64179ad0e66ecd303c94c392_109.png)

![](img/feddeade64179ad0e66ecd303c94c392_110.png)

But C is going to use integers for that。 So that's 4 B worth of data。 I'm wasting all that space。

 If I wanted to， I could use a care and just only waste 7 B。 But here's the idea。

 if I have a lot of boolean data to store。 I can just use one bit for each piece and store that in an integer where I've got a whole bunch of these all lined up ready to go。

 So let's take a look at an example。 Maybe this will make more sense。

 So here I'm just going to declare a bunch of variables to use as my flags。

 So these are data that would， you know， maybe represent a typical person。

 So they could be old young。 And I'm just going store one shifted 0 positions into old。

 So that's going to be number one。😊。

![](img/feddeade64179ad0e66ecd303c94c392_112.png)

![](img/feddeade64179ad0e66ecd303c94c392_113.png)

![](img/feddeade64179ad0e66ecd303c94c392_114.png)

![](img/feddeade64179ad0e66ecd303c94c392_115.png)

![](img/feddeade64179ad0e66ecd303c94c392_116.png)

![](img/feddeade64179ad0e66ecd303c94c392_117.png)

And then I'm going to shift， I'm going keep track of whether they're employed or not。 So again。

 I'm using Boolean data， true or false。 So I'm going to take one and shifted by one position。

 and now I'll get 0，0，0，1，0 or two。 And then for the rest of these， I'm a parent。 I'm not married。

 I do not drive a Ferrari。 sorry guys， this job does not pay that well。

 But then I'm just going shift a one into whatever position。

 So this is my mask for each one of these different variables。 So again。

 parent is going to be shifted by two positions into that spot married will be over here into that one。

 drives Ferrari into the that position。 Now here's the idea。

 Now I can create a variable that represents all of the data about me with just one statement， so。



![](img/feddeade64179ad0e66ecd303c94c392_119.png)

![](img/feddeade64179ad0e66ecd303c94c392_120.png)

![](img/feddeade64179ad0e66ecd303c94c392_121.png)

Id capitalized it， Er。Alright， never mind。 Here's the idea。 I'm gonna create a variable， mic。

 Im 45 years old， so I'm older than a typical student。 So so we'll go it old here。 I am employed。

 I've got a job where I teach this awesome class to you guys。😊。



![](img/feddeade64179ad0e66ecd303c94c392_123.png)

![](img/feddeade64179ad0e66ecd303c94c392_124.png)

And I am a parent。 However， I'm not married， and I do not drive a Ferrari。

 So I'm just going to list the things that are true for me。 and that's going to shift a one into。

 I'm sorry， I'm using the or operator。 So it's going take these top three and or them all together。

 So if I look at this， there's a one there。

![](img/feddeade64179ad0e66ecd303c94c392_126.png)

![](img/feddeade64179ad0e66ecd303c94c392_127.png)

So that will be the B0 position。 We'll have a1 in it。 This will have a1 in it。

 So the B1 position will have a1。 The top 3， there's a1 there。 So B2 will have a1 in it。

 And then for the first two bits， B4 and B5。0，1，2， I mean， three and four。嗯。They are all 0。

 So I'm going to get 00。 So 0，0，1，1，1 is a field that has all of this Boolean data talking about me。

Now， if I want to use that， if I want to extract just one of these Boolean values from that。

 it's very straightforward。 a single operation on the CPU。 So if Mike and this is a bit wise old。

 this will give me So the old field is right here 0001， I'm going end with that0，0，01。

 So all of those zeros， I'm going to cancel it all the rest of these bits。 And then when I do old。

 that's going have a one here， So this will return to one。

 and anything that's positive is going to be true。 So Mike and old says wow。

 you're old that will be true。

![](img/feddeade64179ad0e66ecd303c94c392_129.png)

![](img/feddeade64179ad0e66ecd303c94c392_130.png)

![](img/feddeade64179ad0e66ecd303c94c392_131.png)

![](img/feddeade64179ad0e66ecd303c94c392_132.png)

![](img/feddeade64179ad0e66ecd303c94c392_133.png)

If I use the drives Ferrari， I'm going to be ending with the 1，0，0，0，0。

 So the one here is going to extract that 0。 and I get 0。

 and the rest of the zeros mask out all of those。 So in the end， that will result in a complete 0。



![](img/feddeade64179ad0e66ecd303c94c392_135.png)

![](img/feddeade64179ad0e66ecd303c94c392_136.png)

![](img/feddeade64179ad0e66ecd303c94c392_137.png)

For whatever is in my conditional， when I use the bidwise and， and that'll be false。All right。

 so last up， I want to talk about multiplication and division。



![](img/feddeade64179ad0e66ecd303c94c392_139.png)

Al right， now to wrap this up today。 I just want to talk a little bit about a trick we can use to make multiplication and division go faster。

 So first a little bit about speed。 if I'm adding or subtracting， this happens very quickly on a CPU。

 one to two CPU cycles， depending on the architecture I saw different measurements out there as I was looking at some data for you guys。

 However， multiplication is significantly slower。 We're looking at 6 CPU cycles。 So basically。

 multiplication is going to happen a lot like you learned back in elementary school doing the long multiplication。

 So I've got 32 B multiplied by 32 B。 It's going take each one of those rows， shifted over。

 I'm going to get。😊。

![](img/feddeade64179ad0e66ecd303c94c392_141.png)

![](img/feddeade64179ad0e66ecd303c94c392_142.png)

![](img/feddeade64179ad0e66ecd303c94c392_143.png)

![](img/feddeade64179ad0e66ecd303c94c392_144.png)

![](img/feddeade64179ad0e66ecd303c94c392_145.png)

![](img/feddeade64179ad0e66ecd303c94c392_146.png)

Basically， 32 additions that I've got to do。 They can do those in pairs， so。



![](img/feddeade64179ad0e66ecd303c94c392_148.png)

It only ends up taking six CPU cycles to do that。

![](img/feddeade64179ad0e66ecd303c94c392_150.png)

And there's some other technicalities here that can make this go much faster。

 Modern CPUs are pipeline， which means they can work on more than one multiplication problem at a time。

 and they can come up with an average through pit。 if I've got lots of multiplications。

 like if I'm doing like a matrix multiplication or something。

 or I've got lots of numbers or I'm doing it at a loop。

 It can do those more than one at a time and bring down this6 on average to know， one on average。

 So this is a。

![](img/feddeade64179ad0e66ecd303c94c392_152.png)

![](img/feddeade64179ad0e66ecd303c94c392_153.png)

![](img/feddeade64179ad0e66ecd303c94c392_154.png)

![](img/feddeade64179ad0e66ecd303c94c392_155.png)

A little bit of a trick。 However， division tends to be very slow at 30 to 60 cycles。

 So this is a little trick we can use for multiplication and division by powers of 2， like 2，4，8，16。



![](img/feddeade64179ad0e66ecd303c94c392_157.png)

![](img/feddeade64179ad0e66ecd303c94c392_158.png)

Here's the idea if I'm looking at multiplying 14 times 2， it's going to give me 28 in the end。

 14 represented in binary 1110。Okay， if I want to multiply that by 2，28 in the end is going be 0，0，0。

1，1，1，0，0。 Okay， so the idea is， I'm just shifting these bits 1 position over to multiply by 2。

 And here's how this works。 So if I rubbed out14 as the like what is this。



![](img/feddeade64179ad0e66ecd303c94c392_160.png)

![](img/feddeade64179ad0e66ecd303c94c392_161.png)

Powers of two expansion。 So I've got two race to the one， two raiseds to the two。

 two raised to the three。 I'm adding all those together。So this will be 8 plus 4 plus 1。Plus2， sorry。

 I misspoke plus 2。 it's gonna be 14。 and 28， when I write this out to the fourth through the third2。

 the second， I add those up。 I get 28。Hold on once I open。 Let me make another slide。Okay， here。

 I think this one maybe a little more clear。 So I've got 14 times2。 Here's my。

Binary or powers of two expansion of 14。 When I multiply by2。

 I can distribute this two into this summation here。 So it's2 to third times 2，2 square times 2。

2 times 2。 And when I multiply something by 22 times 2。

 That's just going to increase that the power here from 3 to 4。

 So that's going take that three to that four right there when I multiply by2。

 And this is the exact same thing is shifting all of these bits to the left by1。



![](img/feddeade64179ad0e66ecd303c94c392_163.png)

嗯。And it's going to be the same if I want to multiply by4， I'm going to shift by two positions。

 I want to multiply by8， I'm going to shift by three positions。 So just knowing this little trick。

 I can use this in my code anywhere I'm going to be dividing by 2 or multiplying by two like if I'm doing a binary search or something I'm going to be cutting my data set in half。

 I can use a bit shift operator there and that's going to happen in one CPU cycle instead of this 30 to 60 Now in modern computers they're very fast you might never notice unless you're doing lots and lots and lots of division by  two that I can get away from。



![](img/feddeade64179ad0e66ecd303c94c392_165.png)

![](img/feddeade64179ad0e66ecd303c94c392_166.png)

![](img/feddeade64179ad0e66ecd303c94c392_167.png)

![](img/feddeade64179ad0e66ecd303c94c392_168.png)

But during the 70s， computers were not quite as quick as they are now。

 And this was an important trick。 So you'll see this throughout older code When you guys go get real jobs and you're looking at legacy code。

 you'll see this bit shift used for division all the time。All right。

 I think this is going to wrap it up for me。Yep， that was the last slide。 Okay。

 so I'm gonna to go edit the video， put it together。

 and hopefully it'll be up before I have office hours I running way behind schedule。

 So apologize for that。Hope everyone has a great day。

 Def stay safe and keep our stick classmates in your back of your mind right。



![](img/feddeade64179ad0e66ecd303c94c392_170.png)

![](img/feddeade64179ad0e66ecd303c94c392_171.png)

Have a great day。