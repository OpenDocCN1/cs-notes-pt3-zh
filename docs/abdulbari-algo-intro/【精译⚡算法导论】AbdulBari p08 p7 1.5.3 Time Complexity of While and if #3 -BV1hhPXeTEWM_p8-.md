# 【精译⚡算法导论】AbdulBari p08 p7 1.5.3 Time Complexity of While and if #3 -BV1hhPXeTEWM_p8-

はい。Al I have prepared a video how to find the time complexity if there is a follow loop。



![](img/f78805b8c2d8c5378bc5844b417756b6_1.png)

Now， the question is how to analyze a loop that is while loop or conditional statements。



![](img/f78805b8c2d8c5378bc5844b417756b6_3.png)

See basically in sea language， there are three loops。While and do while there is a difference。

Do while will execute minimum one time。But。Follow and vi loop， I say that they are same。

Whatever you can do using for loop， you can do using while loop and vice versa。



![](img/f78805b8c2d8c5378bc5844b417756b6_5.png)

But。Before sea language yes language is used to provide for loop in a different way。

 let us see that fall loop。

![](img/f78805b8c2d8c5378bc5844b417756b6_7.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_8.png)

4， I assign one。2 M。Do。Some statements in sight。And this is colon here。



![](img/f78805b8c2d8c5378bc5844b417756b6_10.png)

This was the syntax in Pascal language。Now， this loop says that I should take the values from1 n to n。



![](img/f78805b8c2d8c5378bc5844b417756b6_12.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_13.png)

RightSo always it will increase by one at a time。

![](img/f78805b8c2d8c5378bc5844b417756b6_15.png)

All right， so if you want to increase I by two times， then you should say。



![](img/f78805b8c2d8c5378bc5844b417756b6_17.png)

Step。Do。Now I will be changing by 2 every time， so I is one then it will become3 then5 and so on。

 so it will take y i as 1 then3 then5 and so on， but anyway I is incrementing linearly。

 it is increasing。

![](img/f78805b8c2d8c5378bc5844b417756b6_19.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_20.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_21.png)

Alright， so this was the only loops that were available in those days。

 So that time fall loop and vi loop were different。



![](img/f78805b8c2d8c5378bc5844b417756b6_23.png)

Then when you analyze this follow loop positive we have seen what is the time taken if I don't have this step steps let us say one only then this will execute for n time and this will execute for n plus one time。

 this is a common thing。

![](img/f78805b8c2d8c5378bc5844b417756b6_25.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_26.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_27.png)

And if you have while loop in this。Case， then in a language， if you have by loop。

 then don't know what the condition is。It will repeat as long as the condition is true and it will stop when the condition is false。

So we have to study this loop and find out when it is going to stop and how many times it is going to iterate based on that we have to do analysis。

And in this type of core syntax blindly for for loopments n。No other time， except N。

In this type of syntax。 And when the old languages were used。So mostly in algorithm。

 some books you will find dys luous use， So it is and blindly and。

 but while you cannot say n unless you study thoroughly。



![](img/f78805b8c2d8c5378bc5844b417756b6_29.png)

And in C language， we have do vi， which is same as this vial， except that it will execute。

 even if the condition is false， it will execute for one time because it is post tested loop。



![](img/f78805b8c2d8c5378bc5844b417756b6_31.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_32.png)

Post check the loop。 First， it will execute the statement inside。 then afterwards。

 it will check the condition。 So if all the condition is false in the beginning， only is false。

 So this time will execute one time。 and this will not execute at all。



![](img/f78805b8c2d8c5378bc5844b417756b6_34.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_35.png)

But in old languages， they used to be a loop called。



![](img/f78805b8c2d8c5378bc5844b417756b6_37.png)

Repeat。Some statement inside。And under。Some condition。



![](img/f78805b8c2d8c5378bc5844b417756b6_39.png)

Now， these loops were different。Repeat until loops are different。



![](img/f78805b8c2d8c5378bc5844b417756b6_41.png)

This will repeat as long as the condition is false。



![](img/f78805b8c2d8c5378bc5844b417756b6_43.png)

And once the condition is true， it will stop。 So it is similar to do while how。

Minimum one time the statement is executed。But it is different compared to do while how do while will execute as long as condition is true。

 repeat until will execute as long as condition is false。

 it will stop when the become condition becomes true。Do this until this happens， so if it happens。

 you have to stop。So if you take an English sentence statement。Repeat until this happens。

 So if it happens， you have to stop。 if it is not happening， you have to go on continuing。

 So that's the difference between them。 Now， all these three loops， all these three loops。

 you have to study them。 then only you can give the time complexity。



![](img/f78805b8c2d8c5378bc5844b417756b6_45.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_46.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_47.png)

Datime complexityity can be n login a root， and it can be anything。



![](img/f78805b8c2d8c5378bc5844b417756b6_49.png)

But for loop， we can directly say sort of n。

![](img/f78805b8c2d8c5378bc5844b417756b6_51.png)

Now let me write few pieces of code or snippets where I will use while loop。



![](img/f78805b8c2d8c5378bc5844b417756b6_53.png)

I have written a piece of code using vi loop。 I have to analyze how many times this will execute。

 what is the time complexity of this one。 I want to know how many times this statement will execute。



![](img/f78805b8c2d8c5378bc5844b417756b6_55.png)

Initially I is0， this will take one of time。An I+ plus how many times this will repeat。

How many times this will repeat。 See， I plus plus， it is just incrementing every time。

 So simply without tracing this 1， I can say that this will repeat for n times。 How many times。



![](img/f78805b8c2d8c5378bc5844b417756b6_57.png)

This is statement well execute again， n times only how many times this will execute n plus one time。



![](img/f78805b8c2d8c5378bc5844b417756b6_59.png)

How n times the condition will be true and one time the condition is false。

 So if for example n is a 10， then this is going to repeat 4 total 10 times 0 to 10。

 It will stop when I becomes 10 and how long this will execute as long as I is from 0 to 9。

 So this is n time。Right， and that is one extra。 Then what is the time taken by this piece of code。

3 n plus 2 is3 n plus 2。 So the function F of n is 3 n plus 2， and it is theta of n or order of n。



![](img/f78805b8c2d8c5378bc5844b417756b6_61.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_62.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_63.png)

Now， the same piece of code in C line wage I can write like this for I S sign 0 here。



![](img/f78805b8c2d8c5378bc5844b417756b6_65.png)

Then I is less than it。

![](img/f78805b8c2d8c5378bc5844b417756b6_67.png)

Ies listening in。I plus， plus， I plus plus。

![](img/f78805b8c2d8c5378bc5844b417756b6_69.png)

Now， what is the analysis for this one， It will be same if I consider each and everything this will execute for one time。

 this will execute for n plus one time， this will execute for n time and this will execute for n time total how many。

3 n plus2。

![](img/f78805b8c2d8c5378bc5844b417756b6_71.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_72.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_73.png)

But when I was using for loop， I was saying that let us ignore these two and just take it as n plus 1。

 so I was saying that it was 2 n plus 1。

![](img/f78805b8c2d8c5378bc5844b417756b6_75.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_76.png)

Whatever the function may be， we are not interested in exact。Formula or exact function。

 we are interested in the degree of a function， So we say order of n。



![](img/f78805b8c2d8c5378bc5844b417756b6_78.png)

That's it now you can see whatever I can write using while loop I can write it using follow loop also。



![](img/f78805b8c2d8c5378bc5844b417756b6_80.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_81.png)

Now， next piece of code here。C， a assign 1 while a is less than B。

 some statement and a is multiplied by 2 every time。There is no end here。

Then how many times it will repeat， I don't know this depends on this condition as long as the condition is true。

 it will continue， so I don't know how many times it is going to run。Let us trace this one。

Is initially one。Right。

![](img/f78805b8c2d8c5378bc5844b417756b6_83.png)

The a is becoming a into 2， so that is 1 into2， so it is becoming 2。The next time again， this is2。

 so two into2 again， so this will become2 square。 the next time again this is two square into2 that is2 Q goes on。



![](img/f78805b8c2d8c5378bc5844b417756b6_85.png)

How many times this is going to happen， I don't know。



![](img/f78805b8c2d8c5378bc5844b417756b6_87.png)

Let us assume that somewhere it stops and at that time this is going to be2 parque。



![](img/f78805b8c2d8c5378bc5844b417756b6_89.png)

So it will repeat for K times， and that's what K I have to find out。I don't know how many times。

 So I am say king times。Now， I say that it has stopped here。 so you should know when it is stopping。

 it will terminate。

![](img/f78805b8c2d8c5378bc5844b417756b6_91.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_92.png)

When a is greater than or equal to B。It will terminate when a is greater than equal to B。

 So what I am saying I has reached till 2 power k。 So since I am saying that a is equal to2 power k now。

 So this is2 power k is greater than equal to B。 let us make it equal2 power k is equal to B。

 So what is k log B base 2。

![](img/f78805b8c2d8c5378bc5844b417756b6_94.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_95.png)

So how many times it's going to execute log B times？



![](img/f78805b8c2d8c5378bc5844b417756b6_97.png)

Log B times。Log B times。 we write the time complexity in the form of log n and we use term n。

 But we got the answer in B。 So let us call B itself as n。 So what is the time taken by the cell Go。

 It is order of log n。

![](img/f78805b8c2d8c5378bc5844b417756b6_99.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_100.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_101.png)

That's it。This is how I can analyze。Although you have shown this using for loop that time I was writing the same thing by using for loop like this。

4。A sign 1。A is less than B。A assign a into2， this portion as here。

That's all already we have seen this。In four loops， I have shown you this one。

Althoughread you know this one that time I was not taking a。

 I will take I and again here also I and this I will call it as n and this I will call it as I。

That's it。Basically， this is not proper based on fall loop because forments it should just go on incrementing or it should be decrementing。

 it should not multiply I， but in case of C language it is possible you write anything has initialization。

 any condition you write anything as a So these three pieces you can write whatever you like。



![](img/f78805b8c2d8c5378bc5844b417756b6_103.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_104.png)

Just make sure that the loop terminates after some finite number of steps。

So thats all what all you can do using while loop， you can also do it using for loop in C language and the examples what I have given in all the examples I have used for loop only but instead for loop just we can reframe them as while loop。

 let us take one more example again a loop is their while loop and in this while loop I is starting from n and I is getting divided by2 every time。

So again， the time will be log n I made it as a formula already in the previous video。

 so this will be log n and the same thing can also be done using follow loop。



![](img/f78805b8c2d8c5378bc5844b417756b6_106.png)

For I S N N。I is greater than one。

![](img/f78805b8c2d8c5378bc5844b417756b6_108.png)

IS SI9 by 2。

![](img/f78805b8c2d8c5378bc5844b417756b6_110.png)

Some statement in。 So this type of statement already we have analyzed in for loop。

 that same thing is using while loop。

![](img/f78805b8c2d8c5378bc5844b417756b6_112.png)

So the time will be seen。Now， here I have a loop。 Let us see how many times this will execute。

Condition is K is less than n。And here what is k k is1 and k is getting updated by adding I every time and I use inementing every time。

 so I don't know how many times it is going to execute so let us take。



![](img/f78805b8c2d8c5378bc5844b417756b6_114.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_115.png)

Trase this one。 I and K initially both are1。 So1 is less than n。 We don't know what n is。

 And what happens K assign K plus I。 So this becomes1 plus1 that is2 and I plus plus I becomes2。

Now assume K2，2 is less than then the next k sine k plus I， so 2 plus 2。



![](img/f78805b8c2d8c5378bc5844b417756b6_117.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_118.png)

RightAnd I becomes three。

![](img/f78805b8c2d8c5378bc5844b417756b6_120.png)

Then， next time。Again， k， let us say is less than I。 So then k assign K plus I。

 So this is 2 plus 2 plus 3， and I becomes4。 Next time， it will be 2 plus 2 plus3 plus 4。

 and I becomes5。 So this is going on continuing。 So how many times I don't know how many times。

 Let us call it as for M times。

![](img/f78805b8c2d8c5378bc5844b417756b6_122.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_123.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_124.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_125.png)

K， already， I'm using it here。 So  two plus 2 plus 3 plus 4 plus goes on to M。



![](img/f78805b8c2d8c5378bc5844b417756b6_127.png)

If I make this as1， then you can see that is some of a natural numbers。

 so this will be m into m plus1 by 2 roughly plus1 extra。



![](img/f78805b8c2d8c5378bc5844b417756b6_129.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_130.png)

Roughly， it is this much。Now， this is K value will be this much but it has gone till M。

And K value this much。 And let us assume it has stopped。 So what is the condition。 K is less than n。

 it will continue when K becomes greater than n or equal to n， it will stop。

 So I assume that K became greater than or equal to n。

 So what is k I am saying I have stopped K at M in to m plus1 by 2。 that is greater than equal to n。

 This is roughly equal to what M square is greater than n。 So M is what root n。



![](img/f78805b8c2d8c5378bc5844b417756b6_132.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_133.png)

Approximately it is root n。 So it will repeat for M time。 So what is M root n。

 So the time complexity of this one is order of root n。Same thing I can write using for loop， also。



![](img/f78805b8c2d8c5378bc5844b417756b6_135.png)

4。K assign 1， comma， I assign assign 1， two initializations。



![](img/f78805b8c2d8c5378bc5844b417756b6_137.png)

Condition is what K less than n。

![](img/f78805b8c2d8c5378bc5844b417756b6_139.png)

Abdation is what I plus plus。And one more update is there that I will do in。

The statement and K sign K plus I。

![](img/f78805b8c2d8c5378bc5844b417756b6_141.png)

There's the same thing。

![](img/f78805b8c2d8c5378bc5844b417756b6_143.png)

How long this is executing routine and， How long routine again。1，2，1，2， condition， condition。



![](img/f78805b8c2d8c5378bc5844b417756b6_145.png)

Abdation， a， this a and this a。

![](img/f78805b8c2d8c5378bc5844b417756b6_147.png)

Everything is， as it is。So what I wrote using while can also be written using for。



![](img/f78805b8c2d8c5378bc5844b417756b6_149.png)

This is little difficult to read。 That is clear and easy to understand。



![](img/f78805b8c2d8c5378bc5844b417756b6_151.png)

Alright， so already we have seen this type of loopbe。 now I have written it using while loop。Next。

 this piece of code is for finding GCD of two numbers， M and N。



![](img/f78805b8c2d8c5378bc5844b417756b6_153.png)

Now how many times it will repeat this will repeat for some time until M and N becomes equal。

 it will be repeating when they become equal it will stop so when they are equal so that is a G CD value either you say M or you say n。



![](img/f78805b8c2d8c5378bc5844b417756b6_155.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_156.png)

How many times you can execute I don't know， so let me trace if m is equals to 6 and n is equals to 3 initially。



![](img/f78805b8c2d8c5378bc5844b417756b6_158.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_159.png)

Then what happens， M is greater than n。 Yes， so M minus n。 So this becomes 6 minus-3 that is 3。

 and is also 3。

![](img/f78805b8c2d8c5378bc5844b417756b6_161.png)

That all， now， they became equal。So it has executed only one time。



![](img/f78805b8c2d8c5378bc5844b417756b6_163.png)

If I take M and N， both as 5，5。

![](img/f78805b8c2d8c5378bc5844b417756b6_165.png)

Then how many times they are equal it will not enter inside， so it will execute zero times。

 So it is minimum executing0 or1 times。

![](img/f78805b8c2d8c5378bc5844b417756b6_167.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_168.png)

Lets say M is 16 and n is 2。

![](img/f78805b8c2d8c5378bc5844b417756b6_170.png)

Now how many times this will execute。

![](img/f78805b8c2d8c5378bc5844b417756b6_172.png)

M and N are not equal M is greater than n yes， 16 is greater than2 enter inside m assign sign m minus n。

 so M becomes how much 14 and this will be2 only。

![](img/f78805b8c2d8c5378bc5844b417756b6_174.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_175.png)

Then again M is greater than n only， so again2 is subtracted， so this becomes too and this is2 only。

Again，2 is greater than 2， so this becomes1 and this is2 only。



![](img/f78805b8c2d8c5378bc5844b417756b6_177.png)

And this becomes 8 and 2，6 and 2，4，2，2，2。 Now it will stop。 Now they both became equal。

 so it will stop。

![](img/f78805b8c2d8c5378bc5844b417756b6_179.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_180.png)

How many times it has executed。

![](img/f78805b8c2d8c5378bc5844b417756b6_182.png)

1，2，3，4，5，6，7。

![](img/f78805b8c2d8c5378bc5844b417756b6_184.png)

7 times。So almost 16 by two times。 So it means it will execute for n by two times。



![](img/f78805b8c2d8c5378bc5844b417756b6_186.png)

So， I can say it is。Ader of and。So the maximum time taken by this algorithm is or of n。

 And what is the minimum time taken by this algorithm， It is one means one time it is executing。

 So minimum time is。

![](img/f78805b8c2d8c5378bc5844b417756b6_188.png)

A of1 maximum time is order of n。

![](img/f78805b8c2d8c5378bc5844b417756b6_190.png)

I can write the same thing even using for loop， I'll just convert it into for loop。



![](img/f78805b8c2d8c5378bc5844b417756b6_192.png)

For nothing initialized。 and only the condition， then。



![](img/f78805b8c2d8c5378bc5844b417756b6_194.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_195.png)

No obligation。I can use for loop， also。Anyway， this is the GCD， one of the procedure。

 there are other procedures also you can find out that and in this procedure the time I am getting it as n by2 so I wrote it as order of n。

So if it is a while loop， then I have to study it and find out now same thing in C language can also be written using fall loop。

 so even it is fall loop in C language you must treat as while only and study it。

Unless an until it is obviously order of n， you have to study it。Yes。

 I am taking one example here which will show what happens if is there。



![](img/f78805b8c2d8c5378bc5844b417756b6_197.png)

Just a random code I have written here。 it is not meaningful。 it's not doing anything。



![](img/f78805b8c2d8c5378bc5844b417756b6_199.png)

Algothm test is taking some parameter， and。

![](img/f78805b8c2d8c5378bc5844b417756b6_201.png)

If n is less than 5， just print n。

![](img/f78805b8c2d8c5378bc5844b417756b6_203.png)

If n is greater than or equal to 5， then enter in the L part and。



![](img/f78805b8c2d8c5378bc5844b417756b6_205.png)

Repeat this loop。 So how many times this loop is going to execute， This will execute for n times。



![](img/f78805b8c2d8c5378bc5844b417756b6_207.png)

And what about this， this will execute for one time。



![](img/f78805b8c2d8c5378bc5844b417756b6_209.png)

That's it。If a algorithm is using some conditional statements。

 then the conditional statements may decide different amount of time and depending on the condition。

 If the condition is true， then it's going to execute just one statement so the time is order of one。



![](img/f78805b8c2d8c5378bc5844b417756b6_211.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_212.png)

And if the condition is false means it' is greater than 5， then it is going to repeat for n time。

 so it is order of n。

![](img/f78805b8c2d8c5378bc5844b417756b6_214.png)

So this is best case time， and this is worst case time。So I can say that if there are。

So I can say that if there is a conditional statement in an algorithm。

 then it can decide or give different amount of time depending on the condition。

 so maybe it may become worst case or best case or of an algorithm， it's not necessary。

 it is not necessary， it may doesn't mean that if if its there is not a legal formula rule。

 it if is there then definitely it will take that much time， it is not necessary。



![](img/f78805b8c2d8c5378bc5844b417756b6_216.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_217.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_218.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_219.png)

Now I feel Ill make some change here。 in the condition now。

 now this will execute4 n times n greater than5。Right， now there is no minimum or maximum。

 There is no best case or worst case。 If n is greater than5， it will execute。 That's all。

So as I said that you cannot take it as a rule that if。



![](img/f78805b8c2d8c5378bc5844b417756b6_221.png)

Conditional statement， if it's there， then the time will be different。Iect。

So that's all about the loop and the conditional statements。

 while loop and the conditional statements， this is how they have analyzed。



![](img/f78805b8c2d8c5378bc5844b417756b6_223.png)

![](img/f78805b8c2d8c5378bc5844b417756b6_224.png)