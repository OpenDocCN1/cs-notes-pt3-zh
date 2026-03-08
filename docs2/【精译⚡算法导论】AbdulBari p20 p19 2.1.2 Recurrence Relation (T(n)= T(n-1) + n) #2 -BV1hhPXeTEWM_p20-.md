# 【精译⚡算法导论】AbdulBari p20 p19 2.1.2 Recurrence Relation (T(n)= T(n-1) + n) #2 -BV1hhPXeTEWM_p20-

![](img/d892a936ded25618014062851286dcb3_0.png)

Hello， friends。 This is the next video on recurrent solution。

 and the type of recurrent solution is a decreasing function。

So other I have made one video on recurrenret or this the second video see the title I have given us recurrennce decreasing function。

 So 1，2，3， so you can see all those functions So each functions is each function is covered in a separate video。



![](img/d892a936ded25618014062851286dcb3_2.png)

Now， here I have a function as a recursive function。 When N is passed， it is calling itself for n -1。



![](img/d892a936ded25618014062851286dcb3_4.png)

![](img/d892a936ded25618014062851286dcb3_5.png)

Then inside this， there is a loop follow loop is there。



![](img/d892a936ded25618014062851286dcb3_7.png)

Let us find out what's the time。 So for this， I will say。



![](img/d892a936ded25618014062851286dcb3_9.png)

This takes TN time。

![](img/d892a936ded25618014062851286dcb3_11.png)

Then how much time this loop takes， so I will try to take details。



![](img/d892a936ded25618014062851286dcb3_13.png)

This condition takes one unit of time。 And this far， we have been writing n plus one。

 and whatever is there in sight will execute for end times。



![](img/d892a936ded25618014062851286dcb3_15.png)

![](img/d892a936ded25618014062851286dcb3_16.png)

Then what about this statement this will execute for Tn minus1 time？



![](img/d892a936ded25618014062851286dcb3_18.png)

Then what is the recurrennce solution？

![](img/d892a936ded25618014062851286dcb3_20.png)

If I write this one， then T N is equals to some of all these。 So T N is equals to T N-1 plus。



![](img/d892a936ded25618014062851286dcb3_22.png)

2 n plus 2。

![](img/d892a936ded25618014062851286dcb3_24.png)

This is what the recurrence solution I got。

![](img/d892a936ded25618014062851286dcb3_26.png)

But。If I take it in this form， it will not be easy for me to solve it。



![](img/d892a936ded25618014062851286dcb3_28.png)

So this part of a relation， we have to take aytotic notation of that one。



![](img/d892a936ded25618014062851286dcb3_30.png)

Once I should round round it up， I should not take2 n plus 2。

 So what is the notation for that it is big of n or the of n Also I can say it belongs to a linear class degree1。

 so that I can frame it as T N is equals to T n minus1 plus n。



![](img/d892a936ded25618014062851286dcb3_32.png)

And stop writing2， n plus 2， I can simply write N。Now， this is the good installation network。Alright。

 so let us prepare this recurrerent solution。 C T N is equals to。T， N-1 plus n for n greater than 0。

 If it is greater than 0。

![](img/d892a936ded25618014062851286dcb3_34.png)

And when n is equals to 0， what it is doing。 It is doing nothing。 So I can say some constant。

 or I will call it as one。

![](img/d892a936ded25618014062851286dcb3_36.png)

For instead of constant， I am writing it as one。Right， or you can take C or anything there。



![](img/d892a936ded25618014062851286dcb3_38.png)

So that's it。 So here we have learned how to prepare a recurreulation from a given algorithm or a function。



![](img/d892a936ded25618014062851286dcb3_40.png)

![](img/d892a936ded25618014062851286dcb3_41.png)

Now this recurnceulation， I will solve it using recursion tree。D n。BN。It is taking an amount of time。

This one， loop is taking an amount of time， and also， it is calling itself T M-1。

Then what about this step。See， that is printing n times。 So I have not written print here。

 I am saying that that statement made is taking n time。 So I wrote just time。 Im not tracing it。

 I am preparing a tray。

![](img/d892a936ded25618014062851286dcb3_43.png)

Now， this will be n minus-1 and again it will call itself n minus-2。

Then this will be n -2 times this loop will repeat because now the value pass is n -2。

 and this will be T N-3。

![](img/d892a936ded25618014062851286dcb3_45.png)

Continue if I continue like this then where it will stop， this n will reduce by 1 every time。

 and it reach till 0。 Why， because we know the value of n is equals to 0。

 When n n equals to 0 answer is1。 So there is the smallest value that we know。

 So we say that it is reducing up to t to that time， it will print two times and t 1， and for t1。

 it will print that loop it will print for one time， and this is t 0。 for t 0， it does nothing。



![](img/d892a936ded25618014062851286dcb3_47.png)

![](img/d892a936ded25618014062851286dcb3_48.png)

![](img/d892a936ded25618014062851286dcb3_49.png)

That's it。So what is the amount of time taken here see？

If you compare this one with the previous example in the previous video。

 you can find that Prif was there， so I was printing the value， but now I am not printing the value。

 I am saying that this statement will take an amount of time because it is printing n values instead of writing all n values。

 I am just writing time。

![](img/d892a936ded25618014062851286dcb3_51.png)

Now， let us find out the time how much time it is taking in this is step。

 N then the word about this is step and the -1 time and then call。 So n-1 time。

 And this call is there。 So this call is taking how much time and-2。And then and -3。

 So this will take how much time and -3 goes on。 This will take how much time，2 and 1， then 0。



![](img/d892a936ded25618014062851286dcb3_53.png)

If I sum up all these things， then it will be。0 plus 1 plus 2 plus from here I am adding。

 then goes on to n-1 plus n。 What is this。

![](img/d892a936ded25618014062851286dcb3_55.png)

N into n plus one by 2。

![](img/d892a936ded25618014062851286dcb3_57.png)

So the total time here。 See the time for this one is n plus this time。

 How much is this time n-1 plus this time。 So I have added all of them。

 So the total time is n into N plus one might do。 So T N， we got the answer as。



![](img/d892a936ded25618014062851286dcb3_59.png)

![](img/d892a936ded25618014062851286dcb3_60.png)

![](img/d892a936ded25618014062851286dcb3_61.png)

N into n plus one by 2。 And this is。

![](img/d892a936ded25618014062851286dcb3_63.png)

And square。Now you write theta， bego， whatever it is， it is n square。



![](img/d892a936ded25618014062851286dcb3_65.png)

So the time taken by this algorithm is。

![](img/d892a936ded25618014062851286dcb3_67.png)

And square。

![](img/d892a936ded25618014062851286dcb3_69.png)

This is using dream method。 I have saw this。

![](img/d892a936ded25618014062851286dcb3_71.png)

Al。So see by practicing you get the idea， you don't have to elaborate it thiswatch quickly you can get the jump onto the answer。

 so just you need to practice few functions and recurnces and get the answer。

 then you can directly give the answer。You don't have to solve all these。

 When you are writing a theory examination where you have to write essay type cushions there you may have to write on all these steps and then prove that it is n square。



![](img/d892a936ded25618014062851286dcb3_73.png)

If it is objective type cushion， direct answer you need。

 so there is a method to know the direct answer also， we will be looking at this in coming videos。

Now I will show you another method that is back substitution or induction method。

 so that is back substitution by substitution， we will solve this one。



![](img/d892a936ded25618014062851286dcb3_75.png)

![](img/d892a936ded25618014062851286dcb3_76.png)

So I'll remove this， and I will solve just recurnceulation。Now let us solve this one。

T N is equals to T， N-1 plus n。

![](img/d892a936ded25618014062851286dcb3_78.png)

I can own this one if I can find out this。 So what is this since T N is equals to T N-1 plus N。

 Therefore， what a T N-1 will be T N-2 plus N-1。

![](img/d892a936ded25618014062851286dcb3_80.png)

![](img/d892a936ded25618014062851286dcb3_81.png)

![](img/d892a936ded25618014062851286dcb3_82.png)

sentered see n in case of n in place of n n -1。 So in place of n n-1， Al -1 is there。 So n -2。

 then plus in place of n n minus-1。

![](img/d892a936ded25618014062851286dcb3_84.png)

![](img/d892a936ded25618014062851286dcb3_85.png)

![](img/d892a936ded25618014062851286dcb3_86.png)

Now， I know this one。 So instead of n -1， I can take this and substitute it here。

 Now this becomes T N is equals to。

![](img/d892a936ded25618014062851286dcb3_88.png)

![](img/d892a936ded25618014062851286dcb3_89.png)

What is this， T， N-2 plus n-1。

![](img/d892a936ded25618014062851286dcb3_91.png)

Plus， and， as it is。

![](img/d892a936ded25618014062851286dcb3_93.png)

If I open the brackets。T N is equals to T， N-2 plus。And  -1。嗯嗯。



![](img/d892a936ded25618014062851286dcb3_95.png)

Remember one thing， whenever you are solving this one， don't add。

 it becomes 2 n minus1 if it becomes2 n minus-1， it will be difficult for you to find out a formula of for this one or a single expression for this sequence。

Actually， we will be getting a sequence。 So based on that sequence， we have to prepare a formula。

If you add， you'll be getting just a single one or two terms。 So from that。

 we cannot figure out the formula。So better avoid adding these terms。



![](img/d892a936ded25618014062851286dcb3_97.png)

So if this was the starting equation， now after first substitution。

 this is the second equation I got。

![](img/d892a936ded25618014062851286dcb3_99.png)

![](img/d892a936ded25618014062851286dcb3_100.png)

Now， further， I will substitute。 I need to know the value of this。



![](img/d892a936ded25618014062851286dcb3_102.png)

So here only I will continue so what if I write n as n minus2 instead and if I write n minus2。

 then this will be n minus3 plus n minus2。

![](img/d892a936ded25618014062851286dcb3_104.png)

Intro of n， it is n-2， in n -2。 Sorry， n -1 and-2-1。 So n -3 and the n -2 directly。

 So in place of in this equation only the first one only， I have just kept n -1 in place of n。

 So I got this one。

![](img/d892a936ded25618014062851286dcb3_106.png)

![](img/d892a936ded25618014062851286dcb3_107.png)

So， this part。I will substitute it here。

![](img/d892a936ded25618014062851286dcb3_109.png)

So what I get。T N is equals 2 in brackets。 T n-3 plus n-2。



![](img/d892a936ded25618014062851286dcb3_111.png)

![](img/d892a936ded25618014062851286dcb3_112.png)

Plus， outside and  -1。

![](img/d892a936ded25618014062851286dcb3_114.png)

Plus n。Open this one。PN is equals to。T， N-3 plus n-2 plus n-1。



![](img/d892a936ded25618014062851286dcb3_116.png)

![](img/d892a936ded25618014062851286dcb3_117.png)

Plus M。That's the third equation。

![](img/d892a936ded25618014062851286dcb3_119.png)

See， after doing it for two times then you can come on go to k steps and then you can get the formula。

 this is the method followed in induction right so we are substituting the value so index or substitution whatever you call it。



![](img/d892a936ded25618014062851286dcb3_121.png)

So。I have done it for two times。Now， from this， I can observe and say if I do it for k times。

 what will happen。

![](img/d892a936ded25618014062851286dcb3_123.png)

See， when first equation， it was n -1 and n。This was second equation n -2 and then n -1 and n2 terms。

Now n-3， n-2， then one， then n。If I do it for k times， what happens？



![](img/d892a936ded25618014062851286dcb3_125.png)

I'll use this part。

![](img/d892a936ded25618014062851286dcb3_127.png)

Yes， if I continue this four K times， let us see what I'll get。



![](img/d892a936ded25618014062851286dcb3_129.png)

DN。equals to T， N minus k。

![](img/d892a936ded25618014062851286dcb3_131.png)

Instead of n-3， I am writing n minus k。

![](img/d892a936ded25618014062851286dcb3_133.png)

Plus。And-2， if was 3， So it will be 2，1 less than this one。



![](img/d892a936ded25618014062851286dcb3_135.png)

So if this is K， then this will be n minus。

![](img/d892a936ded25618014062851286dcb3_137.png)

K-1。

![](img/d892a936ded25618014062851286dcb3_139.png)

![](img/d892a936ded25618014062851286dcb3_140.png)

This was three。 So that is2。 The next will be。N minus k-2。And goes on to。And -1 and n。

So this is the fourth1 I got， right， This is the fourth one。



![](img/d892a936ded25618014062851286dcb3_142.png)

This is up 2 k。Now， I assume that I have reached till n minus case。

 So I assume that I have reached till 0 and is 0。 So assume。



![](img/d892a936ded25618014062851286dcb3_144.png)

![](img/d892a936ded25618014062851286dcb3_145.png)

N minus K， this one。Has become 0， therefore， n is equal to k。



![](img/d892a936ded25618014062851286dcb3_147.png)

Now， in place of K， if I substitute n in this one， Let us see what I get。



![](img/d892a936ded25618014062851286dcb3_149.png)

T， N is equal to this one， T， N minus N plus。

![](img/d892a936ded25618014062851286dcb3_151.png)

N minus， I' open this。 So this becomes minus n plus 1。



![](img/d892a936ded25618014062851286dcb3_153.png)

So instead of K， Im writing N， and then I am opening the bracket。



![](img/d892a936ded25618014062851286dcb3_155.png)

Plus。N minus。And plus 2。Then， goes on。Last term will be n-1 plus n。



![](img/d892a936ded25618014062851286dcb3_157.png)

These two last terms， as it is， There is no K here。Now， simplify it further。

 T N is equals to t 0 plus。

![](img/d892a936ded25618014062851286dcb3_159.png)

![](img/d892a936ded25618014062851286dcb3_160.png)

This N N gets cancelled 1 plus N N gets cancelled 2。

 So it means I can figure out the next term is a3。 Yes， it is a3。

 then goes on up to what and -1 plus N。

![](img/d892a936ded25618014062851286dcb3_162.png)

That's it。So what is this I got， What is this I got， This is some of first and natural numbers。



![](img/d892a936ded25618014062851286dcb3_164.png)

Then T N is equals to T0 is what1。Plus， this is N name blue n plus1。バ2。



![](img/d892a936ded25618014062851286dcb3_166.png)

That's it。If you compare the three method， there Also， I got an in plus  one by 2。

 But here I got one extra because this is giving me calls numberumb of calls actually。

 So plus one call extra。

![](img/d892a936ded25618014062851286dcb3_168.png)

![](img/d892a936ded25618014062851286dcb3_169.png)

![](img/d892a936ded25618014062851286dcb3_170.png)

Anyway， almost at the same thing。 So what is this， This is the of n square。



![](img/d892a936ded25618014062851286dcb3_172.png)

Take off and square at。That's it。 I have solved this second one by using recursive tree method。

 as well as by substitution method。 And we got the same answer。 It this order of n square。

 So in this video， we have learned how to write a recurrenulation for any algorithm or a function。

 than how to solve that recurrennceulation to get the answer。

 So we saw two different methods for solving it。

![](img/d892a936ded25618014062851286dcb3_174.png)

![](img/d892a936ded25618014062851286dcb3_175.png)

This useful for understanding the procedure， how to solve it。

 and also useful for that is theory exams。RightBut for objective type questions。

 you should know directly how to get the answer that will be learning in next videos。



![](img/d892a936ded25618014062851286dcb3_177.png)