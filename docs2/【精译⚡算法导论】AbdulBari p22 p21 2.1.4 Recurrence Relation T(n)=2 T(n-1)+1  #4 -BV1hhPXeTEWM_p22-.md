# 【精译⚡算法导论】AbdulBari p22 p21 2.1.4 Recurrence Relation T(n)=2 T(n-1)+1  #4 -BV1hhPXeTEWM_p22-

はい。Now， next recurnce， I have an example algorithm here。 I prepare a recurnce， and I will solve it。

 Now， this time I may not be explaining each and everything。

 although I have explained previous recurrennce， the approach is same。So if you want explanation。

 you can watch at least one of the previous recur numbersumbers are given beside the video so you can check that。

This  one， I'll just solve it with a little bit of explanation。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_1.png)

Let us find out a recurrent solution for this function。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_3.png)

If I say this is taking tea and time。Then inside this， these are the three main statements。

 This is taking one unit of time。 Then how much time this takes T。As this test is taking N。 So T N。

 So test of n -1 will be T N-1 also will be。P，N，-1。Then， this is。T N is equals to all these。 So T。

 N is equals to 2 T， N-1 plus 1。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_5.png)

Now， the recurrent solution will be。DM。Is equal2。2 T N-1 plus 14 n greater than 0。

 And when n equal to 0， it is constant。 I'll take 1。Now let all this using recursionary method。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_7.png)

Right。DN。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_9.png)

Now， from the algorithm also I can see it is printing and calling itself two times。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_11.png)

Printing and calling itself two times。 So for printing， it takes one unit of time。

 and then it calls itself for L -1 and again， call itself for L -1。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_13.png)

Then what about this， this again，1 and call itself for n-2。 call itself for n -2。

 And this also1 and T n-2 and。T N -2。what about this again，1， T and -3。T and-3，1， T and  -3。

T and  -3。Then here， also，1， T and  -3。T and -3。 This one is 1， T and -3。T and -3。

If I go on doing it until when。Until they are reaching till t 0 or T 0， because here。N is 0。

 That is the smallest value。 you know。 So I want to keep on reducing it up to 0。Now。

 let us find out time for this one。 See， in this step， what is the time taken。

 just it is taking one unit of time， And then I have to find out the time for this one and this one and add them。

So I don't know how much time this is taking so if I look at this one then this is taking one unit of time and further this one and this one is also taking one unit of time and further this one So let us add these two so this is two。

So each is taking  one，1 unit of time so that I have taken to further， these are also there。 Now。

 if I take these。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_15.png)

1，1，1，1，4。Then in the next step， if I expand these also，1，2，3，4，5，6，7，8， so 8 steps。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_17.png)

This will go on。 So if I write this， this is one，2 part 1，2 part 2。And this is two part 3。

 So how many times it will proceed。 So as we have been doing for K times。

 So let us say they still go for K times，2 part K times。 Then it will become 0。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_19.png)

At 2 per K， this will become 0。 Not total time。 How much is the time。

1 plus 2 plus 2 square plus 2 Q plus so on。 Now， let me add all these。

 Then I get the total time of this one。 So I'll remove this and add them。 Not this。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_21.png)

1 plus 2 plus 2 squared plus 2 cube plus goes on to2 power K。

 This is some of the terms of G P series， and this will be。2 power K plus1，-1。How I got this。

 I will show you。 This is the first time I am using it， so Ill show you。If there is a G P series。

 A plus A R plus A R square plus A R Q plus goes on to A R power K。R is a common ratio。

 A is a first term， and these are the sum of the terms of G series。 This is G series。

 What is the answer for this one。A R to the power of k plus 1-1 by R-1。 This the formula。

In this series， what is a A is equals to1。 What is R R is equals to2。

 It is getting multiplied by 2 every time。 So if I put this in this formula。

 then one into2 par k plus11 by 2-1。 So this is1 only。 So finally it is2 par k plus 11。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_23.png)

So thiss why I got the answer。So directly， I have written this one。Now。

 as per the assumption already we were doing， assume。N minus k is equals to 0。 So therefore。

 we were assuming it has n equal to K。 So what is K here， N。 So the answer is 2 power n plus 1-1。

 And this is order of2 power N。 So it is。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_25.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_26.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_27.png)

2 par N or theta or biggo。 This belongs to class，2 par N。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_29.png)

Now I'll show you another method by using subs back substitution method。 we will solve it。

 so I'll remove everything， and I will simply solve this recurulation。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_31.png)

Now， that is all this using back substitution method。If I take a recurrencelation。

 T N is equals to 2 T N-1 plus 1。 This is the first one。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_33.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_34.png)

Now， what is this one， I'll directly substitute this。 So T N is equals to2 as it is。 Now。

 this can be written as 2 T N-2 plus1。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_36.png)

And this plus one， as it is。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_38.png)

If I open this。2 square T and-2 plus1。So以 do。And plus one。That's it。

 So this is the second equation I got。After first substitution。Again， if I substitute T N -2。

 this is 2 square 2 T， N-3 plus 1。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_40.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_41.png)

And outside this， two and one are there。If I open this to Q T， N- 3 plus2 squared into1。

2 square plus 2 plus 1。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_43.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_44.png)

So this is the third equation I got。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_46.png)

How this is happening， you should know already。Right， I am not elaborating these steps。

 If I continue this 4 k time。 So this T N will be 2 power K， T， N minus K plus 2 power C。

 when this is 3， this is 3。 So this is 2。 So K-1。 when this is k， this is K。

 O K-1 plus 2 power K -2 plus goes on to 2 power 2 plus 2 plus 1。

 And this is the fourth equation I have。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_48.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_49.png)

Now， this equation， I'll write here and continue fourth equation。 I'll write Tm is equals to2 bar K。

 T N minus k。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_51.png)

![](img/fe53d4ef7e0c0164b6b991107806a4e8_52.png)

Plus 2 power k-1 plus2 power K -2。Plus goes on to two square plus 2 plus one。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_54.png)

We assume， always。N minus k is 0。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_56.png)

See， all these are decreasing functions and is reducing subtracting functions。Right。

 decreasing or decreasing function。So in this one always we are taking n is equals to0 and this we are getting it as 1。

 we are taking it as 1。 so when n is equals to0 that is the smallest value。

 So we assume that this n minus s k has become 0。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_58.png)

So when this is0， n is equal to k， right， now this is2 power N。T of0 plus what is this。

 I'll write it from that site，1 plus 2 plus2 square plus goes on to2 power k minus1。

This will be two pour and into 1。 T 0 is1。Then plus this is equal to what2 power k-1。

 So this will be2 power n plus2 power ks，2 power n-1。 So this is。2 power n plus 1-1。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_60.png)

This is。Big go of to pour N or T of to pour N。

![](img/fe53d4ef7e0c0164b6b991107806a4e8_62.png)

Yeah。That's it。 It is too boring Now I'll show you masters theorem for decreasing function。

 So in next video you can watch master's theorem for decreasing function。



![](img/fe53d4ef7e0c0164b6b991107806a4e8_64.png)