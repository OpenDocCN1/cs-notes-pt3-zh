# 【精译⚡算法导论】AbdulBari p24 p23 2.3.1 Recurrence Relation Dividing Function T(n)=T(n⧸2)+1 #1 -BV1hhPXeTEWM_p24-

Hi， next， these are dividing functions。 We will look at a dividing function already I have few videos on a decreasing functions。

 Now， this is called as dividing function reason， If you see in the algorithm or a function。

 it is calling itself for n by  two。 If n is passed， then it is dividing n。

 See if an algorithm is taking any parameter， Let us say n。



![](img/7611969e089f9ccfb4ca89aa5925cda3_1.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_2.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_3.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_4.png)

Then it can reduce the value of n by either n-1 that is subtracting or decreasing or n by 2。

 That is a dividing or root n。 That is root function。Right，So for all these。

 we can have different type of functions where the algorithm or a recursive function is calling itself again by root value of n or divided value of n or decreased value of n。

 So already we have decreased value of n functions。 Now， this is dividing value of the function。

 If you have not seen those videos， we can watch them。



![](img/7611969e089f9ccfb4ca89aa5925cda3_6.png)

Now， let us solve this one。Let us prepare a recurrennce solution。

 We will say this algorithm takes T and time。And there are two statements inside this one。

 So this takes one unit of time。 And when this is a T， N， what is this， T， N by 2。

Then what is the equation， T N is equals to these two。 So this is T N by 2 plus1。



![](img/7611969e089f9ccfb4ca89aa5925cda3_8.png)

There's the conenceulation。 Now， let us write that in consulation here。 T， N is equals2 T。

 N by 2 plus 1。Then， Ennes。

![](img/7611969e089f9ccfb4ca89aa5925cda3_10.png)

See if you observe here， I have written one。I have written one。 So if n is greater than one。

 this is happening。

![](img/7611969e089f9ccfb4ca89aa5925cda3_12.png)

If n is equal to one， then nothing。 So I can take constant， or I will just write one。Constant。

This is the recurrenulation。 Now， let us solve this one by using3 method， recursion3 method。T。

 N is called。 What are the steps，1 and T N by 2。 So this is one， and this is T N by 2。

How much time T N takes1 plus whatever the time taken by this， we don't know the time for this one。

 So what is this， this is 1 plus T N by2 squared。 So that is n by 2 by 2 again。



![](img/7611969e089f9ccfb4ca89aa5925cda3_14.png)

So this one is1， T， N by2 cube。How long will continue， We say that will continue for K times。

 So if we continue for K times， then this will be。T off and by two power K。



![](img/7611969e089f9ccfb4ca89aa5925cda3_16.png)

See， when this is getting divided and divided and divided， at last， what we will get。

The unity value or the unit value for division and multiplication is one。So it should stop at one。

And we know when n is equals to one answer is one。So the purpose of going dividing is to reach that one。

 So we assume that we have reach till and y2 power k， that is equal to1。

So now let us see what is the time。 See in this， it is one step， then one step in each。

 there is only one step， one step。 How many times this will take one one step。

 Total how many steps are there。 So we are doing it for K times。 So these are K steps。



![](img/7611969e089f9ccfb4ca89aa5925cda3_18.png)

So it means time is k， so it depends on the number of steps or the number of levels that this tree is having。

 So that is equal to k。 see this is one time then two times， then three times up to k times。



![](img/7611969e089f9ccfb4ca89aa5925cda3_20.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_21.png)

Right， and we know that n by 2 power k is equals to1 since n by 2 power k is equals to1。

 then this is n is equal to2 power k。 Then what is k K is equals to log n base 2。



![](img/7611969e089f9ccfb4ca89aa5925cda3_23.png)

You send this power base to the side。 So it becomes login base，2。



![](img/7611969e089f9ccfb4ca89aa5925cda3_25.png)

See， I'll right here。 If 2 power5 is。32， then5 is equals to log 32 base 2。Loob 32 base 2。



![](img/7611969e089f9ccfb4ca89aa5925cda3_27.png)

Right， so it means if you have a power B is equals to C， then B is equals to log C base a。



![](img/7611969e089f9ccfb4ca89aa5925cda3_29.png)

So same way，2 power k is equals to n。2 port k is equals to n。

 Then K is equals to log n base to log n base 2。 So that's it。 How many steps it is taking， K steps。

 So what is the time taken， log n， K， K is log n。 So the answer for this is order of log n or say biggo of log n。



![](img/7611969e089f9ccfb4ca89aa5925cda3_31.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_32.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_33.png)

So that's it。 This is using three method。 Now， it is all the same thing using substitution method。



![](img/7611969e089f9ccfb4ca89aa5925cda3_35.png)

Let us solve this by substitution。PM is equals to。T N by 2 plus1。 this is the first equation。



![](img/7611969e089f9ccfb4ca89aa5925cda3_37.png)

Then what is t N by 2， C， Since T N is equals to T n by 2 plus 1。

 then T n by 2 will be what T N by 2 by 2 So n by2 square plus 1。



![](img/7611969e089f9ccfb4ca89aa5925cda3_39.png)

So we can substitute this one here。So this becomes what T N is equals to T N by2 square plus1。

This one， then plus one as it is。T N is equals to T N by2 squared plus 1 plus 1，2。

 I'm adding them because these are just constant values 1，1。 So I'm adding them。



![](img/7611969e089f9ccfb4ca89aa5925cda3_41.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_42.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_43.png)

So it means in the next step， what I get。

![](img/7611969e089f9ccfb4ca89aa5925cda3_45.png)

This is second one。 So it means in next sister， what I get T n is equals to T N by2  Q。Plus，3。

If we continue doing this， then what I get。Pm is equals to T and by 2 power k。



![](img/7611969e089f9ccfb4ca89aa5925cda3_47.png)

Plus gay。40 equation。

![](img/7611969e089f9ccfb4ca89aa5925cda3_49.png)

Tn is equal to T n by2 per K plus k。

![](img/7611969e089f9ccfb4ca89aa5925cda3_51.png)

T， N is equals to T， N by 24 k plus k。

![](img/7611969e089f9ccfb4ca89aa5925cda3_53.png)

Now， we assume that n by two power k has became one。 That is n equal to one。 So we assume this one。



![](img/7611969e089f9ccfb4ca89aa5925cda3_55.png)

And by2 per k is equals to1 because we are reducing it I result reducing it up to1。

 So this has became1。 So therefore， n is equals to2 per k and K is equals to log n。



![](img/7611969e089f9ccfb4ca89aa5925cda3_57.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_58.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_59.png)

![](img/7611969e089f9ccfb4ca89aa5925cda3_60.png)

Now， take that one。 T N is equals to T。1 plus， what is K login。



![](img/7611969e089f9ccfb4ca89aa5925cda3_62.png)

T N is equals to what is the T1。 T1 is 1，1 plus log n。



![](img/7611969e089f9ccfb4ca89aa5925cda3_64.png)

That's it。 This is theta or big of n。

![](img/7611969e089f9ccfb4ca89aa5925cda3_66.png)

So we got the same answer。So that's it this form of equation recurrent solution。

 we are getting the answer as log again， So we have saw using three method as well as substitution or induction method。

 and we also have master theorem for this one。 So we will see few recurrent solutions。

 then we will see master theorem for this one。

![](img/7611969e089f9ccfb4ca89aa5925cda3_68.png)