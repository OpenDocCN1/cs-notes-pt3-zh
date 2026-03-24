# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p21 06-04-02-视频 -BV1DEFDzGEZW_p21-

![](img/cf9dced2ab23b50ac299d84a857e6204_0.png)

For some problem， too。But this is only， I mean， after step one， we， we obtain only C I， right。

 So then we just define with CI， as I have said， we can define G G very easily。



![](img/cf9dced2ab23b50ac299d84a857e6204_2.png)

![](img/cf9dced2ab23b50ac299d84a857e6204_3.png)

![](img/cf9dced2ab23b50ac299d84a857e6204_4.png)

With C， I can define GI in this way， GJ in this way。



![](img/cf9dced2ab23b50ac299d84a857e6204_6.png)

Very easily。 So then we， once we obtain C I， then。We define。Now i def gj。

GJ to be or I such that C I equals to J。This J is from one to k。Now I get。

 get the the partition of the 12 N。Once we obtain that， then we can solve sub problemblem too。



![](img/cf9dced2ab23b50ac299d84a857e6204_8.png)

![](img/cf9dced2ab23b50ac299d84a857e6204_9.png)

In sub problem 2。Here。

![](img/cf9dced2ab23b50ac299d84a857e6204_11.png)

We needed to。And solve of this with respect to Z， right。

 now G is given G is obtained from step one from sub problem one。



![](img/cf9dced2ab23b50ac299d84a857e6204_13.png)

Now I would like again to rewrse this objective function here。



![](img/cf9dced2ab23b50ac299d84a857e6204_15.png)

What I'm going to do is expand this。 So it is。Again， it is just them。I in G1。

 because I want to expand this in in in J。X， I minus Z1。That two enormous squared of plus。

Sigma I in G2。This X minus Z2。2 normal squared plus。Plus， sigma I in G K。X， I minus Z K。

The two norm squared。So then for two action E。We want to minimize。



![](img/cf9dced2ab23b50ac299d84a857e6204_17.png)

We want to minimize this objective function with respect to。To Z。 Now Z is the unknown。

 We G is known。 Z is the unknown。 So then we just split this summation in J。 So we get K terms here。

Now， again， you can check that。In the first term， it involves only K Z1。Involves。Only the1 and。인지펜든트。

Of all the variables， Z2 to the。To Zk。So it involves only z1， similarly for the second term。

 it involves only z2， and it is independent of other terms。And for the last term。

 it involves only Z K。 It is independent of Z1 to Z K-1。So that each term。

involves exactly only one unknown。So which means that now these two。Originally， in2。

 we need to do a joint minimization of this function jointly on Z1 to ZK， maybe we go back。



![](img/cf9dced2ab23b50ac299d84a857e6204_19.png)

I want to minimize this objective function jointly in Z12 Z K。

 but because this objective function has this very nice property。



![](img/cf9dced2ab23b50ac299d84a857e6204_21.png)

So minimizing in Z1 will not。We are not change the。The function value， the value of these terms。



![](img/cf9dced2ab23b50ac299d84a857e6204_23.png)

Right？So。

![](img/cf9dced2ab23b50ac299d84a857e6204_25.png)

Because of the special form of this function。Minimizing this objective function in Z 12 Z K jointly is the same as minimizing this objective function。

 minimizing each term。Separated。So this we call actually we call this kind of special property separable。

This objective function is separable in Z 12 Z K。 So it is equivalent to we minimize。Z J。

Sigma of this I in Gj。This X， I minus Z G， the two norms squared。And we have only this term。

J is from。But now， we have。K sample problems， sample problems to to minimize， to solve。

We just obtained this one。 This is。

![](img/cf9dced2ab23b50ac299d84a857e6204_27.png)

So then what is the solution of this one？For a fix J。So actually this one has a closed form。

 the solution of this one has a closed form I just give you it is exactly the average of all XI in this GJ。

 we can get this the solution exactly it is just let me first write down the formula and then give you a very short proof。



![](img/cf9dced2ab23b50ac299d84a857e6204_29.png)

So it is just the sigma of I in GJ。Of all vectors， the X I。And then， do the。主住。Where。主者。Is the。

Number of elements。Number。Of ans。现视绝。So this。Is for all J。 J is from one to K。

So this formula just tells us Zj is。You know that this is a summation and then divided by the number in in this number of terms in this summation。

 right， So this is exactly an average I mean。A mean of the vectors in Jji。

So this is the mean of the vectors in Jji。Why， why this is this。

 let me have you give you a short proof。I mean， why the solution of this minimization is given by this？

Right， I only give you a proof when n equals to， to1 to see this。Consider for simplicity， Of course。

 for general and。

![](img/cf9dced2ab23b50ac299d84a857e6204_31.png)

You can， you can show it similarly， but of course， more teachers calculation。



![](img/cf9dced2ab23b50ac299d84a857e6204_33.png)

So then in this case， minimization if if n equals to one。If n equals to one in one dimensional case。

 now this is Z J。So all the vectors are just。In R， right， so that ZJ is just a real number。

And this sigma， I in Jji。Now， this。Two Nor squared。In R， its。To norm in R is just the absolute value。

This will be X I minus Z J squared。I just this then。We know that we just now Zj is the variable。

 I want to minimize this function with respect to Z。Then。

What we do is that we take the derivative and set the derivative to 0。 right。

 So then I take the derivative for each term。

![](img/cf9dced2ab23b50ac299d84a857e6204_35.png)

With respect to ZJ very easily， you see it's just two sigma， maybe。It is just a sigma， I in Gj。

Two times。Z J minus X I。I just two because Z is the variable。 So it's two by using that。Chain rule。

 two times this， one times this。Derivative with respect to Zj。 So it's minus of this。

 So we just get this。 Then we set the derivative to0。So here， this is step just。Set。Dere with you。

To zero。Then。We have this。Then this is an equation。 So then we saw this。

 You can see that this is exactly Z J equals to maybe just。



![](img/cf9dced2ab23b50ac299d84a857e6204_37.png)

This is exactly the same as Sigma， I， N G， J。Z J equals to sigma I in G j。Xon。 but just this one。

 but。This， ZJ is independent of I， right， So just the。

 the left hand side just means ZJ is repeated for absolute value of GJ so many times。 So this。

 this is just。

![](img/cf9dced2ab23b50ac299d84a857e6204_39.png)

This one， it is just GJ times Z J。Right， so then。By solving this， we just。Otain。

Z J equals to this sigma I in G， J X， I divided by this G， J number of G J。So this is a short。

 a simple argument。

![](img/cf9dced2ab23b50ac299d84a857e6204_41.png)

On the formula here。

![](img/cf9dced2ab23b50ac299d84a857e6204_43.png)

When n equals to one。For general， and， you can。You just need to calculate n numbers。 So basically。

 it's， it's， it's the same。You just need to consider the entries of ZJ1 by one。



![](img/cf9dced2ab23b50ac299d84a857e6204_45.png)

You works still at this formula。

![](img/cf9dced2ab23b50ac299d84a857e6204_47.png)

So anyway， so this is。

![](img/cf9dced2ab23b50ac299d84a857e6204_49.png)

This sub problem， too。The minimization。With respect to Z1 to Z。

 K has a closed cast an explicit solution given like this。 Z J is just the mean of vectors in G J。



![](img/cf9dced2ab23b50ac299d84a857e6204_51.png)

![](img/cf9dced2ab23b50ac299d84a857e6204_52.png)

行。Let me write down。TheIn words， Z J is the mean。Of vectors。愿知者。



![](img/cf9dced2ab23b50ac299d84a857e6204_54.png)