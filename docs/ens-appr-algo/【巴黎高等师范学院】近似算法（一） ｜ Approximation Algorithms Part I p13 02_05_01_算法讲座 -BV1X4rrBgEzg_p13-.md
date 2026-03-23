# 【巴黎高等师范学院】近似算法（一） ｜ Approximation Algorithms Part I p13 02_05_01_算法讲座 -BV1X4rrBgEzg_p13-

![](img/d4fa639fb7b099247d8b0e4c2b02ad85_0.png)

![](img/d4fa639fb7b099247d8b0e4c2b02ad85_1.png)

We have seen an algorithm for a special special case of the Napsack problem。

We have seen an algorithm for a special case of the Napsack problem。

Now has finally come the time to see what you have been waiting for impatiently。😊。

An algorithm for the general case of the Napsack problem。Why have we been wasting all this time。

 Because we can now leverage all the work we have done previously。

We know how to solve the problem when all values are small integers。

We have an algorithm for that case。So how do we solve the general case。 The idea is simple。

 We will just do a reduction。 We will take our general input。

 and we will modify it so that the values become small integers， integers between 0 and n。

And then once we are there， we cangeest。Leverage the algorithm we designed before and use it as a black box。

That's an algorithm， by reduction。How do we modify the input so that the values are small integers？😊。

We do the most natural thing you could imagine。First， we want them to be small。So， we scale。Second。

 we want them to be integers。So。We round。That's these are not big ideas。 and yet。

 that is going to suffice。So here is the general algorithm。Initially， some pre processingces step。

 let us discard the items that don't fit in annapsackack。

If an item has a size that is too big to fit in an knapsack， we just throw it away。

Consider the remaining items。Multiply each value by a scalar so that the resulting values are all less than or equal to n。

Then round all these scaled values down to the nearest integer。Nao。In this modified input。

 we can apply the dynamic program seen in the previous section。That's the general algorithm。Simple。

Pctorialally， you can see it this way。 This is the reduction。 Initially， we have a bunch of。Items。

 and here I plotted their values。We scale them so that the maximum item size becomes exactly equal to n。

And then we take all of these scale values and we discrete crisp them a little bit so that they become integers。

1，2， up 2。What is the effect of scaling？The maximum scale value is n。What does it mean？

That we must have multiplied by。N over the max value。

So we multiply every item by alpha defined to be capital n over max value。But。What is N？

How do we pick and， I did not say it yet。The answer is， we pick it small。En launch。

We pick it small enough that the runtime is polynomial。The smaller N is the smaller the runtime。

 We know the runtime is linear in terms of capital N。Lge enough。

That we will still have an accurate output。 The value of the output will be close to optimum。Now。

 is it possible to take capital N both small and large。

That's the object of this algorithm and analysis。 Cho and just write that the runtime is polynomial and the value is close to optimum。

So。Here's the algorithm。Dis card items not fitting。

 Let's define capital n equal to 100 times little N， let's say。

Define V prime I as the scaled rounded value。 the floor of V I times alpha。

Apply the dynamic program to the modified input where the Napsack capacity is still B。

 The sizes are still S I， but the values are V prime I。This gives us， as a result。

 a collection of items， and we output the corresponding items。😊，That's the general algorithm。Simple。

What is the runtime of this algorithm？Well， for that。

 we have to remember how the dynamic program worked。What dominates the runtime。

 What dominates the runtime are the two nested fall loops。1， ranging up to little end。

The other one ranging from 0 to V I-1， and then V I up to little n times capital n。In total。

 multiply。And we get。Little n squared times capital n for this our choice of value of capital n that gives 100 and cubed。

 We have a cubic time algorithm。😊，So we have seen an algorithm for the generalnapsack problem。

 It runs in cubic time。 It outputs something that is correct that fits in a Napsack。

 It only remains to analyze it to show that the value of the output is close to optimal。😊。



![](img/d4fa639fb7b099247d8b0e4c2b02ad85_3.png)