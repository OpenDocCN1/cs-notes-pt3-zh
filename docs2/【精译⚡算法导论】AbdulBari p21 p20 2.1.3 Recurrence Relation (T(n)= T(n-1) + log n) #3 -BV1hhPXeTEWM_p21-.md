# 【精译⚡算法导论】AbdulBari p21 p20 2.1.3 Recurrence Relation (T(n)= T(n-1) + log n) #3 -BV1hhPXeTEWM_p21-

Hi， already I have two videos on recurrennceation there I have shown the steps in detail。 Now。

 here I will do it little quickly。 right， So you also get the idea how we can do it quickly。 right。

 I'll just skip some steps。 That's it。

![](img/c414042cbdca40d4ff36015e72dd901a_1.png)

Not direct answer。Letteristic。

![](img/c414042cbdca40d4ff36015e72dd901a_3.png)

This is an algorithm or a function。 We have to find out how much time it is taking。

 so we know that this will take a T and the time。

![](img/c414042cbdca40d4ff36015e72dd901a_5.png)

![](img/c414042cbdca40d4ff36015e72dd901a_6.png)

Now， there is a loop。If you observe this is I starting from1 and I assign I into 2。

 so this is multiplied by 2 every time， so by looking at the loop you should know what is the time taken by this statement Al we have seen this in examples of time complexities。



![](img/c414042cbdca40d4ff36015e72dd901a_8.png)

![](img/c414042cbdca40d4ff36015e72dd901a_9.png)

![](img/c414042cbdca40d4ff36015e72dd901a_10.png)

![](img/c414042cbdca40d4ff36015e72dd901a_11.png)

One video is there you can watch that one I have shown how to find directly know what is the time taken by this one。

 So we know that this statement will execute for log and time。



![](img/c414042cbdca40d4ff36015e72dd901a_13.png)

Now， I will not consider this one and this one。 if I consider also again。

 I have to take the degree of expression and the degree will be lo in only。This will be log n plus1。

 this is one so2 log n plus2。 again， I have to write login only。

 so let us just concentrate on only this statement。



![](img/c414042cbdca40d4ff36015e72dd901a_15.png)

![](img/c414042cbdca40d4ff36015e72dd901a_16.png)

This will the main thing that is printing。 The algorithm is doing nothing just printing the value。

 So the job of printing， we are considering that one extralogan。



![](img/c414042cbdca40d4ff36015e72dd901a_18.png)

![](img/c414042cbdca40d4ff36015e72dd901a_19.png)

That how much is this one。As this is T N。 So this is T N -1。



![](img/c414042cbdca40d4ff36015e72dd901a_21.png)

Now， what is total for this one。 So this is T N is equals to。



![](img/c414042cbdca40d4ff36015e72dd901a_23.png)

T， N-1 plus log N。

![](img/c414042cbdca40d4ff36015e72dd901a_25.png)

T N -1 plus login that T N is equal to so and so。 This T N is some of these two。



![](img/c414042cbdca40d4ff36015e72dd901a_27.png)

Now， what is the recur solution？T， N is equals to1。 If n is 0， This is common。

 you have seen in previous algorithms。 Also， I will not explain now。 Then this is T， N-1 plus。

Log n for n greater than 0。Now， I will solve this one using three method。 So if I take T N。T N。

 what it is doing。 It is taking login time， and it is calling itself for T N -1。

Then what this will do， This will take log n -1 time and call itself for n -2。

 Then this will be log n-2 and call itself for n-3。 it goes on。 So at one point， it will be what T 2。

 So and it will look。

![](img/c414042cbdca40d4ff36015e72dd901a_29.png)

![](img/c414042cbdca40d4ff36015e72dd901a_30.png)

Log two times， and it will call itself for one， and this will be log 1。

 and this will call itself for T 0。

![](img/c414042cbdca40d4ff36015e72dd901a_32.png)

So this will stop at0 and then becomes 0，3 will stop there。Now， what is the time taken in each step。

 Lo n here， This is login time in this call， log n -1 time in this call like this。 So this total is。

 I will take few terms only log n。Plus， log n -1。Plus， goes on。2， log 2 plus log 1。



![](img/c414042cbdca40d4ff36015e72dd901a_34.png)

This is the summation of the time taken in each call。



![](img/c414042cbdca40d4ff36015e72dd901a_36.png)

What is this equal to， This is log。N into n-1 into goes on to 2 into1。

I'll write this in square packets。So what is this。N into n -1 into so on into2 into 1。

 So it is just like one into 2 into 3 into 2。 N。 So this is nothing but log。N factorial。

 So here write， log n factorial。

![](img/c414042cbdca40d4ff36015e72dd901a_38.png)

Loin factorial。 already， we know this。

![](img/c414042cbdca40d4ff36015e72dd901a_40.png)

There is no tide bond for this one， but theres an upper bound for log n factorial。 for n factorial。

 upper bond is Npar N。 So for log n factorial log of Npar N， that will be equal to biggo of。



![](img/c414042cbdca40d4ff36015e72dd901a_42.png)

![](img/c414042cbdca40d4ff36015e72dd901a_43.png)

And log again。So that's it。 This is the time we got。So the time taken by this algorithm is en log n。

And login。Right， so this is with the three method I have shown you。

 So we got the time complexity as analog login。 Now， by using induction method。

 I will solve this recurnceulation。 I'll remove this and I will solve that one directly。

 Let us solve this recurrenulation by induction or substitution method。

 So I'll write this recurrenulation P N。

![](img/c414042cbdca40d4ff36015e72dd901a_45.png)

![](img/c414042cbdca40d4ff36015e72dd901a_46.png)

Is equals to T N-1 plus。Login。Then directly， I'll write down。 This will be what。

TN is equal to in place of this what it will be Tn minus2 plus log of n minus1。Plus。

 this login as it is。

![](img/c414042cbdca40d4ff36015e72dd901a_48.png)

This was the first equation。Now， if I simplify this one， open the brackets， T N-2 plus。



![](img/c414042cbdca40d4ff36015e72dd901a_50.png)

Log of， and -1 plus。

![](img/c414042cbdca40d4ff36015e72dd901a_52.png)

Loin。Then。This is the second 1 I got。Then I will substitute1。

 So this will be T n is equals  to in bracket。 T N-2 will be T N-3 plus。



![](img/c414042cbdca40d4ff36015e72dd901a_54.png)

Log and minus-2。

![](img/c414042cbdca40d4ff36015e72dd901a_56.png)

Plus。

![](img/c414042cbdca40d4ff36015e72dd901a_58.png)

These termss， as it is， log n -1 plus log n。

![](img/c414042cbdca40d4ff36015e72dd901a_60.png)

This is in brackets。 I'll open this one。 So T， N is。T， N-3 plus log of。



![](img/c414042cbdca40d4ff36015e72dd901a_62.png)

And-2。

![](img/c414042cbdca40d4ff36015e72dd901a_64.png)

Log of， and  -1。

![](img/c414042cbdca40d4ff36015e72dd901a_66.png)

Let's log。This is the third one。

![](img/c414042cbdca40d4ff36015e72dd901a_68.png)

If I continue for k times。Then what will happen？ See， this was n then n-1 then N -2。

 So it will be go on using up to one。

![](img/c414042cbdca40d4ff36015e72dd901a_70.png)

![](img/c414042cbdca40d4ff36015e72dd901a_71.png)

So directly， I will write on。 So here I continue。 So T N will be equal to。



![](img/c414042cbdca40d4ff36015e72dd901a_73.png)

T N minus K plus log 1 plus log 2 plus。

![](img/c414042cbdca40d4ff36015e72dd901a_75.png)

Goes on to log n -1 plus log N。

![](img/c414042cbdca40d4ff36015e72dd901a_77.png)

Now， we know that。N the minus k is equals to 0， therefore n is equals to k。

 Now if I substitute there T n is equals to this becomes t0 and all these terms if I add I am getting same terms。

 so this is log n factorial。Now， Im not sure how to get that Al。 We have seen this。

In the previous method。This is one plus。

![](img/c414042cbdca40d4ff36015e72dd901a_79.png)

Log and fatalto。What is time taken in this one， This is big of。



![](img/c414042cbdca40d4ff36015e72dd901a_81.png)

And log and。Ex it， we got the same answer。

![](img/c414042cbdca40d4ff36015e72dd901a_83.png)

That is big off and login， that is login factorial。



![](img/c414042cbdca40d4ff36015e72dd901a_85.png)

Now， if you have already seen first and the second video for recurrent solution with the decreasing functions。

 This is the third video。 If you have already seen those two， then you can understand this。 Now。

 I'm going to show you how we can directly get the answer for a recurrent solution of decreasing functions。

 See I'll take the examples of first two videos。 Then also this one， then let us see。



![](img/c414042cbdca40d4ff36015e72dd901a_87.png)

![](img/c414042cbdca40d4ff36015e72dd901a_88.png)

See there， I just write a simple expression。 T N was T， N-1 plus1。And the time taken in this one was。



![](img/c414042cbdca40d4ff36015e72dd901a_90.png)

I'll just say order of， not biggo Theta， anything。 This order of me， just the degree I am writing。

 This answer was N。

![](img/c414042cbdca40d4ff36015e72dd901a_92.png)

![](img/c414042cbdca40d4ff36015e72dd901a_93.png)

On the second video， we have seen this Pn-1 plus n。 So this was n square。



![](img/c414042cbdca40d4ff36015e72dd901a_95.png)

![](img/c414042cbdca40d4ff36015e72dd901a_96.png)

And in the third video， this one in this video， just now， we have seen this T N-1 plus log n。

 and this is。

![](img/c414042cbdca40d4ff36015e72dd901a_98.png)

And the login。

![](img/c414042cbdca40d4ff36015e72dd901a_100.png)

So what do you understand from this one。 So when this is t of n -1 means n is decreasing。

 n is decreasing every time。 So if it is1 multiplied by n。

 it is then multiplied by n n square log n multiplied by n n log n。

 So it means we can make out that if reconciliationconciation is T n -1 plus n square。

 then it will be definitely。

![](img/c414042cbdca40d4ff36015e72dd901a_102.png)

![](img/c414042cbdca40d4ff36015e72dd901a_103.png)

![](img/c414042cbdca40d4ff36015e72dd901a_104.png)

![](img/c414042cbdca40d4ff36015e72dd901a_105.png)

![](img/c414042cbdca40d4ff36015e72dd901a_106.png)

Into N。 So this is N Q。 Yes， this is true。Right， so whatever the term you are having here just multiplied by n。



![](img/c414042cbdca40d4ff36015e72dd901a_108.png)

Because this is going to repeat for any time。 So that's why this whole thing into end。



![](img/c414042cbdca40d4ff36015e72dd901a_110.png)

If。🤢，From the first one， I'm just making some change。 T and-2 plus 1。 Instead of n-1 plus 1。

 it is -2 plus 1。 So the exact answer you may be getting as n by 2， because it is taking 2。

2 steps every time。 instead of 1，1 step，1，1 value decre at 22 values decre。



![](img/c414042cbdca40d4ff36015e72dd901a_112.png)

So it will n by two。 That is， again， order of and only。



![](img/c414042cbdca40d4ff36015e72dd901a_114.png)

Means that even if you have T n is equals to T N minus00 plus n。 then what will be the answer。

 as this is n just multiplied by n fits order of n square。



![](img/c414042cbdca40d4ff36015e72dd901a_116.png)

This is n not1。 n-1。 It's n-0。 whatever it may be。 So it is taking hundred step every time plus 00。

 So imagine n value as in 1000 or millions a bigger value， very big value of for small values。

 you can say that。 no， it will not take that much time。



![](img/c414042cbdca40d4ff36015e72dd901a_118.png)

![](img/c414042cbdca40d4ff36015e72dd901a_119.png)

![](img/c414042cbdca40d4ff36015e72dd901a_120.png)

Big values of end。 So we say that whatever the value of n may be from some value to infinity will go。

 So， yes， this is true。

![](img/c414042cbdca40d4ff36015e72dd901a_122.png)

So whatever is subtracted， you get the same answer。



![](img/c414042cbdca40d4ff36015e72dd901a_124.png)

But if you have a recurnceulation like this。

![](img/c414042cbdca40d4ff36015e72dd901a_126.png)

2 into T of n-1 plus 1。 If there is some coefficient here， then it's not directly one into n。

 So we'll see what will happen in this one。 right， See， there was no coefficients here。

 There were no coefficients。 Only these values were changing1 n log n n square n cube and log n anything。

 So whatever you have here just multiplied by。

![](img/c414042cbdca40d4ff36015e72dd901a_128.png)

![](img/c414042cbdca40d4ff36015e72dd901a_129.png)

![](img/c414042cbdca40d4ff36015e72dd901a_130.png)

En。Right。But now， if there is a coefficient， then what should be the answer。

 you will see this in next video， next to this one。



![](img/c414042cbdca40d4ff36015e72dd901a_132.png)

![](img/c414042cbdca40d4ff36015e72dd901a_133.png)

喂。