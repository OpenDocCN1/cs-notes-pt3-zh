# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p03 P3 Video Part03 -BV1iwMpzfEDc_p3-

To not have to worry about end the file marker and J likes end the file is not a character and therefore this wouldn't fully work so it says if I hit the end the file stop break because I can't read anymore and what I'll do is I'll go down to the bottom three lines otherwise I look up the next state so look up T of state and current character and a blank is considered an error so if the next state is a blank that is error I break。

 go to the bottom three lines otherwise I update my state to be next state read another character and go back in the loop and keep reading and this is an infinite loop until I hit an end the file and then I break out。



![](img/24cfe53575deea24309d149fcda39915_1.png)

![](img/24cfe53575deea24309d149fcda39915_2.png)

![](img/24cfe53575deea24309d149fcda39915_3.png)

![](img/24cfe53575deea24309d149fcda39915_4.png)

![](img/24cfe53575deea24309d149fcda39915_5.png)

![](img/24cfe53575deea24309d149fcda39915_6.png)

![](img/24cfe53575deea24309d149fcda39915_7.png)

If I'm at the bottom it says well let's look at state。

 is it in a list or a table of accepting states， if so I know what it is and I can process it。

 otherwise I signal that I had an electrical error。

 my scanner would not scan that particular sequence under the logic diagram I had。



![](img/24cfe53575deea24309d149fcda39915_9.png)

![](img/24cfe53575deea24309d149fcda39915_10.png)

![](img/24cfe53575deea24309d149fcda39915_11.png)

![](img/24cfe53575deea24309d149fcda39915_12.png)

It's possible if I wanted to eliminate the table and fill this in actually in terms of logic that you might program。

 the advantage here is you don't program this， the scanner generates it。

 so would say this is explicit control。 The advantage of this is that it's easier for a human to read。



![](img/24cfe53575deea24309d149fcda39915_14.png)

![](img/24cfe53575deea24309d149fcda39915_15.png)

![](img/24cfe53575deea24309d149fcda39915_16.png)

And by the way， is that necessarily a great advantage？Say， oh， hey， that's cool。

 I've got the code in front of me， I can change it if necessary。



![](img/24cfe53575deea24309d149fcda39915_18.png)

Again， how many people here are in quality assurance？



![](img/24cfe53575deea24309d149fcda39915_20.png)

Gotta be some。And quality assurance people quality assurance is actually one of the most important departments in any organization。

 including this one， so when you're up for review and possible raises， you can quote me on that。



![](img/24cfe53575deea24309d149fcda39915_22.png)

![](img/24cfe53575deea24309d149fcda39915_23.png)

And the reason for that is you only get one chance to make a bad first impression。



![](img/24cfe53575deea24309d149fcda39915_25.png)

What that means is if the quality assurance people， these are the people who says this product works。

 it works well， it's high quality， if you mess up and something goes out the door and a user finds an error。

 that's not so good， the user finds many errors， it's really not so good because Epic has a reputation of selling really high quality products。



![](img/24cfe53575deea24309d149fcda39915_27.png)

![](img/24cfe53575deea24309d149fcda39915_28.png)

![](img/24cfe53575deea24309d149fcda39915_29.png)

![](img/24cfe53575deea24309d149fcda39915_30.png)

So the trouble with something like this is， oh， I can just go in there and program it。



![](img/24cfe53575deea24309d149fcda39915_32.png)

But one of the problems with fixing bugs and again， QA people know this is something。



![](img/24cfe53575deea24309d149fcda39915_34.png)

Sometimes when you fix a bug， you unintentionally introduce a new bug。



![](img/24cfe53575deea24309d149fcda39915_36.png)

So what QA people do is not just see is this error fixed。

 but typically taking the revised program that has to quote， F， they run a whole suite of tests。



![](img/24cfe53575deea24309d149fcda39915_38.png)

![](img/24cfe53575deea24309d149fcda39915_39.png)

Very much like we're going to do when we test your program in grading and say。

 do all these things still work？

![](img/24cfe53575deea24309d149fcda39915_41.png)

![](img/24cfe53575deea24309d149fcda39915_42.png)

It's certainly possible you may have fixed this one， but had another problem。



![](img/24cfe53575deea24309d149fcda39915_44.png)

If you've ever seen something where somebody tries to nail down a warped ward。

 you're down there and the board is warped on one an。

 you go over there and start naling nailling nailling and the other side pops back up so it's kind of like that in programming you fix one thing and by fixing one thing another thing may go wrong。



![](img/24cfe53575deea24309d149fcda39915_46.png)

![](img/24cfe53575deea24309d149fcda39915_47.png)

Say to yourself， mom，'m not so stupid， I'd never do something like that。

But it turns out you're unlikely to have been the person who wrote the program。

 and a lot of times there's some subtle assumptions built in that you don't know about。

 and unless they're very well documented， you may break that rule and of a sudden something that relies upon it fails。



![](img/24cfe53575deea24309d149fcda39915_49.png)

![](img/24cfe53575deea24309d149fcda39915_50.png)

![](img/24cfe53575deea24309d149fcda39915_51.png)

So having this thing looking like it's code is good。But remember， if I have a generator。

 what I could do is even better is fix it up at the token level and a regular expression level。

 regenerate this thing， maybe it looks a lot like this， or maybe it looks changed。



![](img/24cfe53575deea24309d149fcda39915_53.png)

![](img/24cfe53575deea24309d149fcda39915_54.png)

![](img/24cfe53575deea24309d149fcda39915_55.png)

But it's automatically generated and therefore， if something messes ups not my fault。

 I define the tokens correctly。 it's Mr。 JLx， go back and sue him。 Unfortunately。

 Jlex is distributed for free， So usually when you get something for free。

 proving damages is kind of hard so you get what you pay for but JL has been around a while and it's pretty reliableli。



![](img/24cfe53575deea24309d149fcda39915_57.png)

![](img/24cfe53575deea24309d149fcda39915_58.png)

![](img/24cfe53575deea24309d149fcda39915_59.png)

![](img/24cfe53575deea24309d149fcda39915_60.png)

So this thing said， okay， it's going to do exactly what the previous program did。

 but there's no tables now， so you can in fact read the logicing and again，'s somewhat positive。

 I like to be able to read code， so it says if the current character is a slash。

 read another character， if the current character is a slash， repeat reading the other character。

 until I hit an end the file or an end of line。

![](img/24cfe53575deea24309d149fcda39915_62.png)

I then folded at the bottom and it says if the current characters end the line， fine。

 I've got a valid token， otherwise it must have been an end the file I hit。

 and I'm going to signal an lexical error。So this thing is reasonably readable。

And automatically generate it。 So that's cool。 We're going to use Jx which generates the table。

 but you're never going to have to look at the table。 So that's a big plus。



![](img/24cfe53575deea24309d149fcda39915_64.png)

![](img/24cfe53575deea24309d149fcda39915_65.png)

![](img/24cfe53575deea24309d149fcda39915_66.png)

Let's look at a few more examples。 And then， yeah，'ll be time for a break。

 and then we'll actually start getting into JLx， and you can start actually thinking about doing scanning。



![](img/24cfe53575deea24309d149fcda39915_68.png)

![](img/24cfe53575deea24309d149fcda39915_69.png)

So， here's a case where。

![](img/24cfe53575deea24309d149fcda39915_71.png)

I want to show both the finitetmain and the expression， and it turns out there's a rule， or not rule。

 but algorithms that says if I have a regular expression like real lit。

 I can generate a diagram like that。And this is actually internally what Jx does。

 You program in something that looks like the real lit definition。

 It translates it into the logic diagram that corresponds to that particular automaton。



![](img/24cfe53575deea24309d149fcda39915_73.png)

![](img/24cfe53575deea24309d149fcda39915_74.png)

![](img/24cfe53575deea24309d149fcda39915_75.png)

Turns out I probably won't go into it， but if somebody wants it。

 I can show you where it is in the textbook， you can actually go backwards if I have an automain here。

 I can go back to a regular expression that represents it。



![](img/24cfe53575deea24309d149fcda39915_77.png)

![](img/24cfe53575deea24309d149fcda39915_78.png)

Sometimes it's， it's clean。 Sometimes it's not。

![](img/24cfe53575deea24309d149fcda39915_80.png)

But what this thing is saying is that let's see what it is in English。

 so I want a real literal and I require digits on one or both sides。

 but I'm not going to allow digits on neither side， so it means like I only have one point。



![](img/24cfe53575deea24309d149fcda39915_82.png)

![](img/24cfe53575deea24309d149fcda39915_83.png)

3。14 is fine。1。00。01， but I can't have just a decimal point。



![](img/24cfe53575deea24309d149fcda39915_85.png)

Because that's another a number。 got to have some digits。



![](img/24cfe53575deea24309d149fcda39915_87.png)

So that thing represents it， but notice it looks kind of funny because I've got a D star， a D plus。

 a lambda， and a worse sign and looking at that and you say， what in the world is this guy doing？

If I look at the diagram the blow， it's a Ted more readable。



![](img/24cfe53575deea24309d149fcda39915_89.png)

Let me go it says， okay， if I read a dot knows there， I've reached a state that's not final。

 So it's saying for sure， I don't want a dot。

![](img/24cfe53575deea24309d149fcda39915_91.png)

![](img/24cfe53575deea24309d149fcda39915_92.png)

If I take a digit， says if I see a digit fine， that's a final state。 So an integer like 1，2。

3 is fine。 I can read additional digits。 I can read a trailing decimal。

 and that would take me to something like one point。 That's fine。 I could read another digit， like 1。

2。

![](img/24cfe53575deea24309d149fcda39915_94.png)

Up top， I could read a dot， which is not acceptable， but I could read a dot followed by a dig like 0。

1 or 0。11， and that's acceptable。

![](img/24cfe53575deea24309d149fcda39915_96.png)

![](img/24cfe53575deea24309d149fcda39915_97.png)

So I would argue that the bottom diagram is easier to read。

 but we just had the signal to stop talking， so when I start up again we'll go back to that one and kind of read our way through that one。

 which is equivalent， but I would argue less readable。



![](img/24cfe53575deea24309d149fcda39915_99.png)

![](img/24cfe53575deea24309d149fcda39915_100.png)

So we'll let you kind of ponder on that again， it's quarter of。

 so let's pick up again about 8pm and we'll have our final half hour session。



![](img/24cfe53575deea24309d149fcda39915_102.png)