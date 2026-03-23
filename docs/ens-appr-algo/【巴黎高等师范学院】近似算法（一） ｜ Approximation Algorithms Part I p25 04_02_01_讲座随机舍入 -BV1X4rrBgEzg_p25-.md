# 【巴黎高等师范学院】近似算法（一） ｜ Approximation Algorithms Part I p25 04_02_01_讲座随机舍入 -BV1X4rrBgEzg_p25-

![](img/a5c0a2db7f65db1427914c90fbe63294_0.png)

![](img/a5c0a2db7f65db1427914c90fbe63294_1.png)

We have defined a set cover problem。 We have seen that it was a generalization of the vertex cover problem。

 We have tried to extend the algorithm we had for vertex cover and we failed。

 Now we need to make another attempt at getting a set cover algorithm。

Here was our linear programming relaxation。 This， we will keep。 The big question is。

 how do we round the solution of the linear program。

Now we are going to see an algorithm using randomized rounding。

If you think about a variable that equals 0。9， when the variable is between 0 and 1 and you want to make it an integer。

Po。int9 probably should be arounded to one。On the other hand， if it's equal to 01。

 then probably it should go to 0， be rounded down to 0。But as we have seen。

 we cannot fix a particular threshold and say that everything above that threshold goes to 1 and everything below that threshold goes to0。

So we need to be smarter， and the idea here is to do it using randomization， using probability。

How do we do this， Let's say that a variable equals 0。8。😊，Thenen。😊，We're going to run it to one。

 not always， but with some probability。We flip some coins。

And then we round the variable to one with probability。Point8，80%。This is how we will use the value。

 the fractional value and transform it into an integer value。😊。

So the new rounding algorithm is very simple。😊，Forever set us。

We look at the variable XS in the solution of the linear program。With probability ex S。

 we put S in the set cover。With probability 1 minus x of S， we do not put S in a cover。

 And so when we do this for every set S， we take a decision and then we output the resulting collection of sets。

That's a very simple， rounding algorithm。As always， for this kind of algorithms。

 we have three questions to answer。😊，First question。Is it efficient？Second question。

 is the output a natural set cover， is it correct？Third question， how good is it。

 What is the cost of the output cover。These are the three questions that we always need to answer for approximation algorithms。

The first question is easy。Is it efficient。Yes。Why。😊。

Because the time it takes is just the time to solve the linear program。

 which we know is polynommal time， plus for each variable， make one random choice。

 draw one random variable between 0 and1 and make one decision。

So this overall takes polyinmal time assuming， of course， that we have access to random numbers。😊。

Which is true in practice。Second is the output of cover。It dependss。

It could be that it's not a cover because for every set， we make some random choice。

 It could be that for every set we decide not to put it in the cover and that we'll have no set in the output and the elements will not be covered。

So maybe it a cover， maybe not。And how good is it， Well， it depends。 You know。

 maybe we'll choose some expensive sets or maybe not。



![](img/a5c0a2db7f65db1427914c90fbe63294_3.png)

So these are the two things we need to analyze for this algorithm。

 we need to analyze the probability that the output is a cover。

 and we need to analyze the cost of the output collection of sets。😊。

