# LLVM入门教程-•-中英-p06-P06-Introduction-to-LLVM-Passes--BV1HtRUYnEji_p6-

![](img/27f843eae1d12afb53a9c3a75a77ab6a_0.png)

Hi， I'm August Snowy。 I'm a student in the Federal University of Negels。

 where I do research and compilers。

![](img/27f843eae1d12afb53a9c3a75a77ab6a_2.png)

Together with my colleague， Luigi Domenico， I will introduce you to L of Vamppais。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_4.png)

As previously discussed， a compiler is formed by three distinct modules， a front end， a middle end。

 and a backend。

![](img/27f843eae1d12afb53a9c3a75a77ab6a_6.png)

![](img/27f843eae1d12afb53a9c3a75a77ab6a_7.png)

All thepaes live in the Midland。 They are the primary two compilers used to optimize the code。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_9.png)

In Lov V M， the tool that drives the pass pipelines is called optt， which stands for optimizer。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_11.png)

There are two different types of passes。 The first is called the transformation Pass。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_13.png)

As the name implies， this kind of pass modifies the code somehow。

 and emits a new version of the code that has the same semantics as the original one。

 but makes it faster or smaller or has some other useful property。

The second kind of pass is called in analysis pass。 This kind of pass doesn't change the code at all。

 but emits analysis information， which is used by other passes to make their jobs easier。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_15.png)

There are many different types of passes。 Each deals with a different scope。

 The first is the loop Pass。 As the name implies， this passage analyzes or modifies lookss。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_17.png)

So in the example code to the right， the loop in the sum function could potentially be analyzed by a loop pass。

One level up， we have function passes。 These passes run on individual functions of the program。

After that， we have module passes。 These run on the whole module at a time。

There are other types of passeses， call graph S C pass， region pass， machine function pass。

 etc cetera。

![](img/27f843eae1d12afb53a9c3a75a77ab6a_19.png)

Now， I'd like to show you a couple of examples of existing passes to give you an idea of what they can do。

 Let's start with analysis passes。

![](img/27f843eae1d12afb53a9c3a75a77ab6a_21.png)

![](img/27f843eae1d12afb53a9c3a75a77ab6a_22.png)

Rang analysis collects information about the range of values a variable may。For example。

 in the code to the right， I has arranged from 1 to 100。A second analysis example is scar revolution。

 This is a very powerful analysis that can describe how variables evolve inside the loop。

This kind of analysis can be used to， for example， completely replace the code。

 the loop with code that will calculate the value of total。

 even if you don't know the loop bounds or compile time。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_24.png)

![](img/27f843eae1d12afb53a9c3a75a77ab6a_25.png)

A third example of analysis is a dominated tree analysis a dominateator tree is a very useful data structure for compilers。

 Basically this data structure tells you what part of their code will for sure run before some other part。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_27.png)

Let's look at an example to make things more concrete。We start with a node that functionary。

 this will always execute。

![](img/27f843eae1d12afb53a9c3a75a77ab6a_29.png)

Then we add a note for the if block。 Since they always follows the code entry。

 we add an edge from the node to this one。

![](img/27f843eae1d12afb53a9c3a75a77ab6a_31.png)

We do the same thing for the o block。Now， we add a note after the FL blocks。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_33.png)

Notice that neither the if or else box will for sure execute before the return statement。 However。

 the entry block will， so we add an edge from that node to this one。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_35.png)

![](img/27f843eae1d12afb53a9c3a75a77ab6a_36.png)

Now， let's look at some example of transformation passes。For these examples。

 I'd like you to imagine you are doing the Java compiler and how would you optimize the code examples yourself？



![](img/27f843eae1d12afb53a9c3a75a77ab6a_38.png)

The first transformation we will look at is called that code elimination。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_40.png)

So if you are a compiler， how would you optimize this code。Well， one is always less than2。

 so we could remove the comparison。 And while we are at it， remove the if block completely as well。

This is called dead code elimination。Code is called that if it's never going to be executed。Next。

 let's talk about constant propagation。Imagine we have Disc code secrets in our program。

How would you optimize this？Well， index， example， a has value 10。B is a added with 20。

 but we know that a is always 10， so that will always be 30。Similarly， C is B times 5。

 but we already know the result of the expression of compile time。

So we can replace it with the result， as well。Next， let's look at loopingvari code motion。

Take a look at the example code。 What can you do to optimize it。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_42.png)

Well， notice the calculation of x will always be the same every iteration of the loop。

So we can remove it from the inside the loop and move it to before the loop itself。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_44.png)

![](img/27f843eae1d12afb53a9c3a75a77ab6a_45.png)

So that was an introduction to All of the Paus。 Next time。

 we will show you how to write a very basic analysis pass。 till there。

 you are free to write us with questions and comments。 Thank you。



![](img/27f843eae1d12afb53a9c3a75a77ab6a_47.png)

![](img/27f843eae1d12afb53a9c3a75a77ab6a_48.png)