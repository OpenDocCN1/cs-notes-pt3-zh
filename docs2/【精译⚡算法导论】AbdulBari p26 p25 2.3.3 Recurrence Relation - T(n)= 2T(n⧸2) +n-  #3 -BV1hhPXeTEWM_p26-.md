# 【精译⚡算法导论】AbdulBari p26 p25 2.3.3 Recurrence Relation - T(n)= 2T(n⧸2) +n-  #3 -BV1hhPXeTEWM_p26-

![](img/84d6714101144f5934c3b7f8f8a3ffad_0.png)

I have written an algorithm。 Let us find out recurrenulation for this one。

 and we will solve recurrennceulation。

![](img/84d6714101144f5934c3b7f8f8a3ffad_2.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_3.png)

This is PM。And inside this， there's a loop。

![](img/84d6714101144f5934c3b7f8f8a3ffad_5.png)

So the statement inside this loop takes n time。Test M and this is n by 2。 So test is T， N。

 So this is T， N by 2。 And this is also T， N by 2。What is the recurreation that T N is equals to sum of all these。

 So T N is equals to two times T N by two。 It is calling itself two times。

 Algom is calling itself two times。2 T， N by 2 plus this Anna。



![](img/84d6714101144f5934c3b7f8f8a3ffad_7.png)

う。Rferite recurreciation， T n equals 2。2 T N by 2 plus N。 When n is greater than one。

 When n is equals to one， it is some constant， or just take one。



![](img/84d6714101144f5934c3b7f8f8a3ffad_9.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_10.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_11.png)

See here， if you observe。

![](img/84d6714101144f5934c3b7f8f8a3ffad_13.png)

I have taken n greater than one， because this is dividing function。

 So the smallest value of the division is1。 We get1。 So that is the reason I am taking it as one。



![](img/84d6714101144f5934c3b7f8f8a3ffad_15.png)

In the decreasing functions， we were always taking it as0 here also， it can take 0。

 but solving recurrence solution will be difficult。



![](img/84d6714101144f5934c3b7f8f8a3ffad_17.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_18.png)

When we reach till 0， then everything may become 0。 Thats the reason we stop at  one。

 That is the reason we are taking it as one。 If it is not one also， if it is 0， also。

 we can make it as one and prepare a recurulation。 And this can be solved if this is made as one。



![](img/84d6714101144f5934c3b7f8f8a3ffad_20.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_21.png)

And of N is one。This recurrence solution is very important。

 Time complexity of some of the algorithms can be represented by using this recurrence solution。



![](img/84d6714101144f5934c3b7f8f8a3ffad_23.png)

This is very important。I will solve it using tree method， recursion tree method。BN。

This is calling itself two times。 And then N。 So O， N I will write it。 And this is two times。

 It is calling itself。 So this is T， N by 2， as well as T N by 2。To make it simple。

 what we do is see， this is T N T N 3 steps are there。 So what is the time of T， N， T N plus D。

So instead of writing T N， what we do is。

![](img/84d6714101144f5934c3b7f8f8a3ffad_25.png)

First step is n， then whatever the time we get in n by2 and the time taken in n by 2。

 So I am avoiding writing function T N completely just n then n by2 and n by 2。Then what this， again。

 it will call itself two times n by2 square and n by2 square。

 and this also n by2 square n by2 square。

![](img/84d6714101144f5934c3b7f8f8a3ffad_27.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_28.png)

Then this will call itself for n by2 cube and n by2 cube。 And this also n by2 cube， n by2 cube。



![](img/84d6714101144f5934c3b7f8f8a3ffad_30.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_31.png)

This is n by to Q， N by。送完了。

![](img/84d6714101144f5934c3b7f8f8a3ffad_33.png)

How long this will continue until they become one， they become one。 So how long we do this。

 We say that this we will do it for two power K times。给答。And by two power K times。

 So this we will repeat 4 k times。

![](img/84d6714101144f5934c3b7f8f8a3ffad_35.png)

This will repeat for。

![](img/84d6714101144f5934c3b7f8f8a3ffad_37.png)

And by two power K times。

![](img/84d6714101144f5934c3b7f8f8a3ffad_39.png)

So total harmony steps are there。 K steps are there。 K steps are there。



![](img/84d6714101144f5934c3b7f8f8a3ffad_41.png)

And in each step， how much time it is taking and， And this is how much and by doless and by do and only this is N。

 this is also an how much time this is taking。N by 4 n by 4 n by 4 n by four times。 it is n only。

N by8 n by8，8 times。 So there is also M。

![](img/84d6714101144f5934c3b7f8f8a3ffad_43.png)

And， so this is all N how many times。

![](img/84d6714101144f5934c3b7f8f8a3ffad_45.png)

And in K times。 So what is this K。

![](img/84d6714101144f5934c3b7f8f8a3ffad_47.png)

See， we assume that。

![](img/84d6714101144f5934c3b7f8f8a3ffad_49.png)

N by2 power k is equals to  one。 So n is equal to2 power K， and K is equals to log n。 Yes， therefore。

 this is N log N。

![](img/84d6714101144f5934c3b7f8f8a3ffad_51.png)

So， the time for this is。Audrov and log。

![](img/84d6714101144f5934c3b7f8f8a3ffad_53.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_54.png)

So the time taken by this algorithm is L log n。

![](img/84d6714101144f5934c3b7f8f8a3ffad_56.png)

So this is another way you can prove it using three methods is the first time I am writing it like this every time I was using TN。

 you can watch previous videos， other videos also I'm just writing the time。Instr function。

 I am just writing the time。 So this will be done for k times。 So every time the total in this level。

 total is n。 totalal is n。 So that will be K and time and K is log n。



![](img/84d6714101144f5934c3b7f8f8a3ffad_58.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_59.png)

Next， I will solve it using the back substitution method。 I will remove everything。

 and I will solve this recurnceulation using back substitution method。



![](img/84d6714101144f5934c3b7f8f8a3ffad_61.png)

Now， let us solve this recur in And by substitution in a third。I take this reconciliation。

 T N is equals to 2 T N by2 plus n。

![](img/84d6714101144f5934c3b7f8f8a3ffad_63.png)

Then I can know answer。 if I know T N by 2。

![](img/84d6714101144f5934c3b7f8f8a3ffad_65.png)

What is the D N by2。Since we know， T N is。2 T N by 2 plus n。

 then n by 2 in place of thecipher right n by 2 T， This will be n by2。 So n by 2 and again by 2。

 So this becomes square plus n by 2。

![](img/84d6714101144f5934c3b7f8f8a3ffad_67.png)

So that's it。 This visual substitute here。

![](img/84d6714101144f5934c3b7f8f8a3ffad_69.png)

So this becomes what2， what is this2 T N by 2 square plus n by 2。



![](img/84d6714101144f5934c3b7f8f8a3ffad_71.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_72.png)

So two， as it is at this place， we have substituted this one purse and as it is。



![](img/84d6714101144f5934c3b7f8f8a3ffad_74.png)

This was our very first equation。 Remember this。

![](img/84d6714101144f5934c3b7f8f8a3ffad_76.png)

If I open this2 square E N by 2 square plus2，2 gets cancelled and N plus M。

So this is the second equation。Here， even I can write to an。 So， and I have written done it。



![](img/84d6714101144f5934c3b7f8f8a3ffad_78.png)

This is Ten。

![](img/84d6714101144f5934c3b7f8f8a3ffad_80.png)

Now， I have to find out this one and substitute here。 Let us see what is t n by two square。

 So here I write T N by two square。 So in place of n n by two square。

 So two as it is T N by two square。 So N by two square。 But one more2 is there。

 So2 Q plus us N by two square。😊。

![](img/84d6714101144f5934c3b7f8f8a3ffad_82.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_83.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_84.png)

This one has to be substituted here。 So what this still be，2 square。And that part。

2 T N by 2 cube plus N by two square。

![](img/84d6714101144f5934c3b7f8f8a3ffad_86.png)

After this2 and，2 win。 So only this portion have substituted。 So this became the same bracketcade。

Open is fun。 So this will be2 squared into 2，2 cube T N by2 cube plus2 square2 squared cancel So N all2 is there。

 So this will be 3 N。

![](img/84d6714101144f5934c3b7f8f8a3ffad_88.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_89.png)

Tolib。

![](img/84d6714101144f5934c3b7f8f8a3ffad_91.png)

That said two times I have substituted each。 Now， if I continue this4 k times。

 I say that Ill repeat this 4 k times。 I'll continue writing here。



![](img/84d6714101144f5934c3b7f8f8a3ffad_93.png)

![](img/84d6714101144f5934c3b7f8f8a3ffad_94.png)

If this is continued for K times， then this will be TM。



![](img/84d6714101144f5934c3b7f8f8a3ffad_96.png)

2 part K。2 part K。

![](img/84d6714101144f5934c3b7f8f8a3ffad_98.png)

P， NY 2，4， K， NY 2，4 K。

![](img/84d6714101144f5934c3b7f8f8a3ffad_100.png)

This is cube。 This is cube but this is3。 And so plus K， N。



![](img/84d6714101144f5934c3b7f8f8a3ffad_102.png)

And we assume that this has become P of NY2 equal K has became P1。



![](img/84d6714101144f5934c3b7f8f8a3ffad_104.png)

So therefore n2 board k is equals to 1 and n is equal to2 k and k is equal to log n。



![](img/84d6714101144f5934c3b7f8f8a3ffad_106.png)

This is a。

![](img/84d6714101144f5934c3b7f8f8a3ffad_108.png)

No， what is equal to T A N。

![](img/84d6714101144f5934c3b7f8f8a3ffad_110.png)

🎼2 part K。 What is K，2 part K。 O， let it be2 part K only。 Then what is this T 1 plus K N。 Now。

 you know what is the two K。2 port K is and T or T of one is what one。那。And as it is。

 what a skate login。

![](img/84d6714101144f5934c3b7f8f8a3ffad_112.png)

。Now， T N is n plus n log n。 the highest term is this one。

 So it is to go off and log n or tee off and login。 so you can say。



![](img/84d6714101144f5934c3b7f8f8a3ffad_114.png)

That's it。This is the recurrennce solution， solution of recurrennceulation is N log n。



![](img/84d6714101144f5934c3b7f8f8a3ffad_116.png)

There is a very important recurrennce solution again， I'm telling you。



![](img/84d6714101144f5934c3b7f8f8a3ffad_118.png)

You should know2 Tn by 2 plus and if you have， then this will be a result。



![](img/84d6714101144f5934c3b7f8f8a3ffad_120.png)

That's all。 we will end recurrences here。 Next， I will show you masters theorem。



![](img/84d6714101144f5934c3b7f8f8a3ffad_122.png)

For dividing functions， the functions in which this is getting divided。



![](img/84d6714101144f5934c3b7f8f8a3ffad_124.png)

And let us see how we can directly give the answer by looking at a recurrent solution。 So for that。

 we will look at masters theorem。

![](img/84d6714101144f5934c3b7f8f8a3ffad_126.png)

So next video is one master just here。