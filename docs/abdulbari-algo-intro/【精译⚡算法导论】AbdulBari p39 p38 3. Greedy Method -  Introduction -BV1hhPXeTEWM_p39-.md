# 【精译⚡算法导论】AbdulBari p39 p38 3. Greedy Method -  Introduction -BV1hhPXeTEWM_p39-

Hi， next topic is greedy method。This is one of the strategy for solving problems。

Just like divide and conquer and the other strategies。

 greedy method is also one of the approach for solving a problem。

Or a design which you can adopt for solving similar problems， the problems which fits into this one。

 you can solve all of them。

![](img/905736b502ba9ec7a2a515364c7bf218_1.png)

Let us understand what this method says， what is this method about。



![](img/905736b502ba9ec7a2a515364c7bf218_3.png)

This method is used for solving optimization problem。

What are optimization problems are problems which demands or which requires either minimum result or maximum result？

So for this， let us know few terms I'll explain it through an example， S there is a problem P。

 and the problem is I want to travel from one location A to location B。



![](img/905736b502ba9ec7a2a515364c7bf218_5.png)

![](img/905736b502ba9ec7a2a515364c7bf218_6.png)

![](img/905736b502ba9ec7a2a515364c7bf218_7.png)

I have to cover this journey。 That is my problem。For any problem， I am taking one example。

 it can be any problem similar type。No。For this problem， there may be more than one solutions。

 Let us say I can travel this by walk solution 1， or I can take a bike solution 2。

 I can take a car solution 3。 I can go by train solution 4， and I can go by flight solution 5。

 and there may be more solutions。

![](img/905736b502ba9ec7a2a515364c7bf218_9.png)

![](img/905736b502ba9ec7a2a515364c7bf218_10.png)

![](img/905736b502ba9ec7a2a515364c7bf218_11.png)

You can give me more solutions。So my problem is to travel from location A to location B。

 and there are many solutions you go like this or take this take the send go there。



![](img/905736b502ba9ec7a2a515364c7bf218_13.png)

But。There is a constraint in a problem。 I say that I have to cover this journey within2。

Does the condition constrain， So suppose I cannot cover it if I go by walk or by car。

 And so I can cover it only if I go by train or flight。



![](img/905736b502ba9ec7a2a515364c7bf218_15.png)

![](img/905736b502ba9ec7a2a515364c7bf218_16.png)

![](img/905736b502ba9ec7a2a515364c7bf218_17.png)

Now， for a problem， there are many solutions， but these solutions。

 which are satisfying the condition given in the problem then this type of solution becomes。



![](img/905736b502ba9ec7a2a515364c7bf218_19.png)

Feaible solutions。

![](img/905736b502ba9ec7a2a515364c7bf218_21.png)

Theres the meaning of feasible solution， a solution which is satisfying the condition given in the problem is feasible solution。

 though， for a given problem， there may be many solutions。

This is feasible solution satisfying the constraint commonly we use the term。

 is it feasible or not feasible in the sense what satisfying our constraints or not limitations or not。



![](img/905736b502ba9ec7a2a515364c7bf218_23.png)

![](img/905736b502ba9ec7a2a515364c7bf218_24.png)

Next， if I say that， I want to color this journey in minimum cost。



![](img/905736b502ba9ec7a2a515364c7bf218_26.png)

![](img/905736b502ba9ec7a2a515364c7bf218_27.png)

Minimum cost。

![](img/905736b502ba9ec7a2a515364c7bf218_29.png)

I want to spend as much as less possible。 Then this becomes a minimization problem。 So now。

 as the problem demands， a result should be minimum， then it is a minimization problem。



![](img/905736b502ba9ec7a2a515364c7bf218_31.png)

![](img/905736b502ba9ec7a2a515364c7bf218_32.png)

![](img/905736b502ba9ec7a2a515364c7bf218_33.png)

Right right。Then out of these two solution， one of the solution may be taking minimum cost。

 supposeupp by train。 if I go， this is minimum cost。 Then this is called as。



![](img/905736b502ba9ec7a2a515364c7bf218_35.png)

![](img/905736b502ba9ec7a2a515364c7bf218_36.png)

![](img/905736b502ba9ec7a2a515364c7bf218_37.png)

![](img/905736b502ba9ec7a2a515364c7bf218_38.png)

Optimal solution。A solution which is already feasible and also giving me minimum cost that is best reserve that is best for me。

 minimum is best for me。

![](img/905736b502ba9ec7a2a515364c7bf218_40.png)

Then that solution is called as optimal solution， and definitely for any problem。

 there can be only one optimal solution。 There cannot be multiple optimal solutions。



![](img/905736b502ba9ec7a2a515364c7bf218_42.png)

That means there can be only one minimum cost。 Minimum can be only one。

There can be more than one solution。 There can be more than one feasible solution。

 but there will be definitely only one optimal solution。 This problem requires minimum result。

 Some other problems may require maximum result。So if a problem requires either minimum or maximum results。

 then we call that type of problem as。

![](img/905736b502ba9ec7a2a515364c7bf218_44.png)

![](img/905736b502ba9ec7a2a515364c7bf218_45.png)

Optimization problem。

![](img/905736b502ba9ec7a2a515364c7bf218_47.png)

Optimization problem is one which requires either minimum result or maximum result。



![](img/905736b502ba9ec7a2a515364c7bf218_49.png)

So let us briefly look at the terms once again， feasible solution means a solution which is satisfying some constraint Opim solution means which is achieving the objective of a problem。

 satisfying the objective of a problem that is either minimum result or maximum result。

 a problem which requires a minimum or maximum result is a optim problem。



![](img/905736b502ba9ec7a2a515364c7bf218_51.png)

![](img/905736b502ba9ec7a2a515364c7bf218_52.png)

![](img/905736b502ba9ec7a2a515364c7bf218_53.png)

So greedy method is used for solving optimization problems。

These are the strategies used for solving optimization problems。



![](img/905736b502ba9ec7a2a515364c7bf218_55.png)

![](img/905736b502ba9ec7a2a515364c7bf218_56.png)

![](img/905736b502ba9ec7a2a515364c7bf218_57.png)

These three methods are for solving optimization problem， the approach is different。

And every problem， whichever requires optimal results， some may be suitable here。

 some may be suitable here。 this strategy can apply on it or some this strategy can be applied or some for some problems。

 all three strategies can be applied on them。So we will learn all these strategies through problems 1 by one。

 Now， we are going to cover this greedy method。 we will start with greedy method。

 We will understand what greedy method says， What is the approach。 So next。

 I will tell you about greedy method。 What is this approach。



![](img/905736b502ba9ec7a2a515364c7bf218_59.png)

![](img/905736b502ba9ec7a2a515364c7bf218_60.png)

Here is the general method of Gry。 I have written an algorithm。Now。

 see greedy method says that a problem should be solved in stages。In each stage。

 we will consider one input from a given problem and if that input is feasible then we will include it in the solution。

 so by including all those feasible in inputs we will get an optimal solution。

So in stages we will each time we take up our input and we consider it and we its feasible。

 we will include it and like this if we follow this procedure we will get the optimal solution。



![](img/905736b502ba9ec7a2a515364c7bf218_62.png)

So here a general method is given if a problem is given and that problem is having a input of some size and and is the size。

 and it is having some data， some values， input values。



![](img/905736b502ba9ec7a2a515364c7bf218_64.png)

![](img/905736b502ba9ec7a2a515364c7bf218_65.png)

Now it will go through all those input values from one to n and each time it will select something from a and call it as x。

 if that x is feasible， that is one input， one by one it will pick up the input and that input if it is feasible。

 it will include in the solution。

![](img/905736b502ba9ec7a2a515364c7bf218_67.png)

![](img/905736b502ba9ec7a2a515364c7bf218_68.png)

![](img/905736b502ba9ec7a2a515364c7bf218_69.png)

If it is feasible， it is included in a solution。 So this comes under if。This is the general method。

 Now， I will explain you through example， the approach of Gry method。



![](img/905736b502ba9ec7a2a515364c7bf218_71.png)

![](img/905736b502ba9ec7a2a515364c7bf218_72.png)

As a that。Suppose if you have to buy a best car。Best god。Best car in the sense， in terms of features。

 you want a best car Op， optimal。 Okay， the cost will be maximum definitely。

 so but you want optimal optimal in the sense for in terms of features。



![](img/905736b502ba9ec7a2a515364c7bf218_74.png)

![](img/905736b502ba9ec7a2a515364c7bf218_75.png)

Now， how do you choose a best car， How do you choose a best car？

 So one method is you should look at all the brands and all the models of cards available in the world。

 or at least in your city。 Then you can say that I have checked all the cars。

 Then I have selected the best car。

![](img/905736b502ba9ec7a2a515364c7bf218_77.png)

This is one approach for solving a problem。 The problem is to buy a car。



![](img/905736b502ba9ec7a2a515364c7bf218_79.png)

This one method。 This will be very much time consuming。

 You have to check each and every brand and every model。 See， the cost may not be a thing。

 Sometimes Earl car may be better than costliier car。

So checking with the featuress and you are deciding that this is the best car so but actually what is the method we follow we first of all sort out the brands and we say that we don't want in this this we want let us say you are selecting a brand at Toyota or Hyundai。

Right okay， you are saying that these are the best brands for you。And in these brands， then again。

 you will select the top models。Righte。So you are， you are not looking at the lower models。 So again。

 you have sort out。Then again， you say that in this top model。

 the latest release car are the well known car， well tested car。 We are picking up that one。

 and you are saying that is the best one。 Is it really the best one out of all the cars in the market。

For you， it is the best one。 So what is the approach you adopted。 You have adopted a greedy approach。

 So you have your own method of selection。 And based on that selection method。

 you got some result and you are saying that this is the best result。 That's how it is a greedy。

 And definitely when you do this， you will be become up a best car。

 So you don't have to waste time in checking all the cards in the available in the city available in the market。

 So that's it。 So without checking all of them， you say that you select fewer and say this is the best car。



![](img/905736b502ba9ec7a2a515364c7bf218_81.png)

![](img/905736b502ba9ec7a2a515364c7bf218_82.png)

No doubt that is the best car， but the approach you adopted is greedy。I'll give you one more example。

 Suppose you are running a company and you want to hire some people。 So when you have given an ad。

 some thousand people came to you for the interview。 Now you will conduct some type of test。

 like if first， you conduct written test， and then you have a technical test or group discussion like that。

 You will have various phases of test。 and you will filter the people。 And finally。

 you select one person。 And you say that this the best person out of those thousand。

 Is he really a best person is according to your procedure， is the best person。

 What was your selection procedure based on the selection procedure。 He is the best person。



![](img/905736b502ba9ec7a2a515364c7bf218_84.png)

And yes， you have got the optimal solution。So the approach is greedy。

 Many student complain that I was better than him and he got selected。 They think like that。

 but really the person who got selected is the best one definitely。

So the approach that you are adopting now I'll tell you。

 if you are selecting one person out of thousand， then for all。

 you should give a chance for return test for all， you should give a chance for group discussion for all you should you should give a chance for technical interview and HR interview。

 then pick up the best one。 This will be very time consuming and costly process。 we don't do that。

 we simply filter the people and select the best one。 This approach is called as greedy approach。

 So we have our own methods of selection and we follow blindly。

 we follow those methods because those are the known methods when you follow known methods of solving a problem and you quickly solve it that approach is called as greedy。



![](img/905736b502ba9ec7a2a515364c7bf218_86.png)

So I have given you enough idea about the greedy method now you will come across through the problems one by one I will pick up and I will solve them so while discussing the problem also Ill show you what the approach gridy is following so that if you type find any similar type of problem you can follow the same approach and solve it。

That's it。 The introduction for bleeding matter。

![](img/905736b502ba9ec7a2a515364c7bf218_88.png)