# 【精译⚡算法导论】AbdulBari p40 p39 3.1 Knapsack Problem - Greedy Method -BV1hhPXeTEWM_p40-

はい。A abstractack problem。Theres a well known problem first of all we will know about the problem。

 then we will see how it can be solved and then well also understand how Gry method is applicable here and it is following Gring method。



![](img/82b906812096c6448a649dfcc2837574_1.png)

Let us understand this problem。See here some objects are given， one，2， seven objects are given。

Every object is having some profit associated with it。And every object is having some weight。

So objects are there every object is having some profit and every object is having weight， okay。

 weight， we understand what is this profit。

![](img/82b906812096c6448a649dfcc2837574_3.png)

See， there is a bag given here that bag is called as knapsackack。 The bag capacities 15。

 These are7 objects。 bag capacities 15。

![](img/82b906812096c6448a649dfcc2837574_5.png)

There is a bag whose capacity is 15， let us say kg， okay。

 it can be kg is also pond also it can be anything， so Im assuming it as Kg。



![](img/82b906812096c6448a649dfcc2837574_7.png)

Now what we have to do is we have to fill this bag with these objectsics。

And we will carry this bag to a different place， and we will sal these objects。 We get that profit。

 So that profit is the gain that you get by transferring these objects to some location。

 So for transferring， you have to carry them in this container or bag。

 So I can also call this knapsackack as container。 This is a bag or knapsackack。

 I can also call it as container。 So the problem is a container loading problem。😊。

So we find this type of problems in daily life， a lot of goods are transported daily from one place to another place now the problem is about filling off that container with the objects。

When it becomes a problem。If you have the objects whose total weight is more than the capacity of the container or a bag。

If you have less all can fit in then no problem at all， if you have the objects more in number。

 their weight is greater than the capacity of a bag。Then it is a problem。

So already we have some objects here， so I have to fill this bag with these objects such that the profit is maximized。

Profit is maximized。So this is a optimization problem and it is a maximization problem。

Maximization problem。Can we follow greedy method， Yes。

 we can follow Gry method on optimization problem if it is suitable。Next thing。

What is the constraint here？The total objects included here in the bag。

 their total weight should be less than or equal to 15 kg。 This is a constraint。

So I can give various solution。 I can say that just put only one object and take it。

 It's not maximum。I'll say all， all cannot fiten。 It's not feasible， so it cannot be optimal。

 So there can be many solutions。 You can say take this that and all and fill this one。

 But we want maximum result。 That's it for a problem， there can be many solutions。

 but those solutions， which are giving the solution， which is giving maximum result。

 is an optimal solution。Let us see how to solve this one。

 See what I am going to do is for these objects。 I am going to include them。

 So I will write down whether the object is going to be included or not included or how much it is included。

 I will write down here。 X values。 So here I will be writing x 1 or x 2 or x 3， write X values。

 I will be writing。 So this x value can be either 0，2，1。



![](img/82b906812096c6448a649dfcc2837574_9.png)

![](img/82b906812096c6448a649dfcc2837574_10.png)

This x can be from 0 to 1。 So it means I can also take fractions， yes。



![](img/82b906812096c6448a649dfcc2837574_12.png)

So now listen one thing very carefully。Thisnapsack problem is for those objects， which are divisible。



![](img/82b906812096c6448a649dfcc2837574_14.png)

I have something of 5 kg min， I need not take all 5 kg。 I can just take2 kg also，1 kg also。



![](img/82b906812096c6448a649dfcc2837574_16.png)

So these objects can be divided， so what type of objects if I take an example。

 these may be vegetables。7 k G of potatoes，5 ks of tomatoes， something。 So instead of taking 5 K G。

 I can take 2 K G also means it can be divided， yes。

So this is not about those objects which are indivisible。 Let us say，5 K G。

grinder mixer  7 K G washing machine。 It cannot be divided。

 It cannot take half of that washing machine。 So I have to take the full one。

 So here I can take the fraction of an object also。

 So that's how whatever I am including that can be a fraction starting from 0 to 1。



![](img/82b906812096c6448a649dfcc2837574_18.png)

![](img/82b906812096c6448a649dfcc2837574_19.png)

Now let us see how to include these objects in the back。

 what should be my criteria method for including them in the back。



![](img/82b906812096c6448a649dfcc2837574_21.png)

You may be saying that this is giving highest profit， Take that one first。Yes。

 that is giving highest profit。 Take that one first。But。I can say that。



![](img/82b906812096c6448a649dfcc2837574_23.png)

First， fill the bag with the smaller things so that I can get more and more things in the bag。

 and I can make more profit。 More things you carry。 More will be the profit。

 So I prefer take these objects first with 1，1 K G weight or smaller weights。😊。

So your idea is also good。Take the maximum profit 1， and my dear is also good。

 Take the smaller weights，1 so that I can have more objects。 But what is the right method。

 I should select the objects， which is having highest profit by weight， is 18 is the profit。

 So I say that 18 bucks is the profit。 Then that profit is for 4 K G。😊。



![](img/82b906812096c6448a649dfcc2837574_25.png)

![](img/82b906812096c6448a649dfcc2837574_26.png)

It's not for 1 K G。 It's for 4 K G。 So Parake G， how much。 So that's it。

 we should select the objects who are having highest profit by weight。 Parkegi。

 whoever is highest that I should take。 So I should calculate this one。

 So I will calculate profit by weight for all these objects。 So this is 5。 And this is 1。3。

 And this will be 3， This is 1， and this is 6， and 18 by 4 is  4。5， and this is 3。😊。



![](img/82b906812096c6448a649dfcc2837574_28.png)

![](img/82b906812096c6448a649dfcc2837574_29.png)

![](img/82b906812096c6448a649dfcc2837574_30.png)

![](img/82b906812096c6448a649dfcc2837574_31.png)

Now I have these profits and weights of all those objects。



![](img/82b906812096c6448a649dfcc2837574_33.png)

Yes， this is the right selection procedure for the object。

 so the object should be selected based on their profit by weight。

 So the one who is having highest profit by weight that I should put it in the back first。Allright。

 Now， this is the greedy method。 Let us see what the greedy method is doing。

 I was explaining you the problem so far。 Then I said on what basis I should select this。 Now。

 we decided that we will select the object based on their profit by weight。 This is our procedure。

 Now greedy method says that first， you decide how you are going to select the input。

 Then go on selecting the input，1 by one。 So we already selected the method。

 We are going to select them by profit by weight。 Now we will be going on， including them one by one。

 So which object I should include first in the bag。

 the highest profit by weight that is fifth object。 So I will include this whole thing。

 So now this is。

![](img/82b906812096c6448a649dfcc2837574_35.png)

![](img/82b906812096c6448a649dfcc2837574_36.png)

![](img/82b906812096c6448a649dfcc2837574_37.png)

![](img/82b906812096c6448a649dfcc2837574_38.png)

This is 15 Kg， right， So 15 minus how many kg this profit， this object is one。

 So now remaining 14 kgs I have。 So I have included that sixth fifth object in the bag。

 and I got the full profit 6。 Now， who is next， This one。 I will select this one。 Also this hole。

 All two ks I will take。 So this is 14-2 kgs。 Now I have 2 kgs remaining。



![](img/82b906812096c6448a649dfcc2837574_40.png)

![](img/82b906812096c6448a649dfcc2837574_41.png)

![](img/82b906812096c6448a649dfcc2837574_42.png)

In the back。 Now， this is the next objects。 I deserve the highest， then this is the next highest。

 This is the third highest。 I will select this object also completely full。

 So full means all four cages I will include。 This is weight，4 cages I will include。

 So this is 12-4 is 8 K G。😊。

![](img/82b906812096c6448a649dfcc2837574_44.png)

![](img/82b906812096c6448a649dfcc2837574_45.png)

8 Kg I have included， right， So 8 Kg。8 kgs are remaining。 Now， this is the next one。 So I have 3，3。

 These are two。 I can pick up anyone。 so I will select this object。 So this is how many cages。 Now。

 this is 5 ks。 Don't look at the weight。 Don't look at the weight。 I am selecting this one。

 This is giving profit by weight。 So this is 5 kg。 and I'll be getting 15 profits。

 So the profit is same only for both of them。 It is same。 So I'll select this。

 So how many ks are gone 5 ks。 So 8-5。 I am left with just  three kgs in the back。



![](img/82b906812096c6448a649dfcc2837574_47.png)

![](img/82b906812096c6448a649dfcc2837574_48.png)

![](img/82b906812096c6448a649dfcc2837574_49.png)

![](img/82b906812096c6448a649dfcc2837574_50.png)

Now， next is which one。 This one。 So I will take this whole thing。 So how many k G 1 K G。

 So 3 ks are there，-1， now Im left with 2 k G。 Now， it is the next one giving the profit。

 So this one， this one。 So I will include this。 But this is how many K G，3 K G。

 How much I have there。 I have only2 kgs remaining。 So can I include all these 3 ks there。 No。

 I will be including only 2 k G there。 So this is 2-20， it will become。 but from this one。

 I' am not taking the full object。 I'm just taking 2 kg out of 3。 So this is 2 by 3。



![](img/82b906812096c6448a649dfcc2837574_52.png)

![](img/82b906812096c6448a649dfcc2837574_53.png)

![](img/82b906812096c6448a649dfcc2837574_54.png)

![](img/82b906812096c6448a649dfcc2837574_55.png)

2 by 3。 So I am taking the fraction of this object。 You said already。

 I told you that these objects are divisible。 So I am taking two cages out of that。

 And what about this， This is not included。 So I have a solution for this problem。

 And this the solution。 This shows how I am going to include the objects。

 which objects I should include so that I get the maximum profit。 Now。

 I have to calculate the profit and find out how much it is。 I have just written here。

 the values from 0 to 1。

![](img/82b906812096c6448a649dfcc2837574_57.png)

![](img/82b906812096c6448a649dfcc2837574_58.png)

![](img/82b906812096c6448a649dfcc2837574_59.png)

Now， I will see total how much profit I get， and I will also verify the weight that I am getting 15 k G only or not。

 You right。These values， one with the weight。1 into 2 plus 2 by 3 into this weight，3 plus。1 into 5。

Plus，0 into 7。

![](img/82b906812096c6448a649dfcc2837574_61.png)

Plus。1 into one。Plus，1 into 4 k G。Plus，1 into1 Kg。

![](img/82b906812096c6448a649dfcc2837574_63.png)

If I take this， this is。

![](img/82b906812096c6448a649dfcc2837574_65.png)

Do plus。This is 2 plus 5 plus0 plus 1 plus 4 plus 1。So this is 9，1014 plus 1，15。 So， yes。

 the total weight is 15。 only see these x， these are the x values。 This is 0 from 0 to 1。

 so that I am multiplying with weights。 So what is this sum of the X I into weight I。

 And that is less than equal to 15。 So I have found out the total weight。 I was just subtracting。

 now I'm just verifying it。 So， let me know the profit。 So for profit also， what Ill do is。



![](img/82b906812096c6448a649dfcc2837574_67.png)

![](img/82b906812096c6448a649dfcc2837574_68.png)

1 into 10，1 into 10 plus。2 by 3 into 5，2 by 3 into5 plus。1 into of 15。



![](img/82b906812096c6448a649dfcc2837574_70.png)

Plus，0 into 7。 I will avoid writing it。 Then  one into 6，1 into 6。



![](img/82b906812096c6448a649dfcc2837574_72.png)

Plus 1 into 18，1 into 18。

![](img/82b906812096c6448a649dfcc2837574_74.png)

Plus one input3。

![](img/82b906812096c6448a649dfcc2837574_76.png)

1 and3。This is the profit。 So this is nothing but summation of X I into P。

 Every x value is multiplied with profit。 So this is showing how much quantity I' am taking x。



![](img/82b906812096c6448a649dfcc2837574_78.png)

Now， what is this total equal to This is 10 plus 2 into1。3 plus 15 plus 6 plus 18 plus3。

 So this is 54。6。

![](img/82b906812096c6448a649dfcc2837574_80.png)

![](img/82b906812096c6448a649dfcc2837574_81.png)

So that's it。 Our total profit is 54。6， and the total weight is 15。



![](img/82b906812096c6448a649dfcc2837574_83.png)

Once again， I'll show you something here。 See these objects are given。

 Then what is the constraint given in the problem， The constraint is what。



![](img/82b906812096c6448a649dfcc2837574_85.png)

Some of the weights of the objects included in the batch should be less than equal to capacity of the back。



![](img/82b906812096c6448a649dfcc2837574_87.png)

Yes， we have done it。 See， total weight should be less than equal to 15， and this is satisfied。

 This is the constraint given in the problem。 So we have taken that solution。

 which is satisfying the constraint。 Yes， the solution is satisfying， so this is feasible。😊。



![](img/82b906812096c6448a649dfcc2837574_89.png)

![](img/82b906812096c6448a649dfcc2837574_90.png)

![](img/82b906812096c6448a649dfcc2837574_91.png)

And objective is what。

![](img/82b906812096c6448a649dfcc2837574_93.png)

。Objectiveists。Some of the weights， profits of the objects that are included should be maximum。

This is the objective of a problem。

![](img/82b906812096c6448a649dfcc2837574_95.png)

And we have achieved both。Now， quickly， I will explain you how we have followed the3 method。

 once again， I am explaining you， see the objects are given， and the bag is given。

 We have to include these objects in the bag such that the profit is maximum。

 but the total weight should not exceed that one。 So we have to select some objects such that we guarantee that we are getting maximum profit。

 So we have decided the criteria of selection。

![](img/82b906812096c6448a649dfcc2837574_97.png)

![](img/82b906812096c6448a649dfcc2837574_98.png)

Have we tried this object， No， without trying how you can say that that is the best one。

 because the method we followed is best one。

![](img/82b906812096c6448a649dfcc2837574_100.png)

![](img/82b906812096c6448a649dfcc2837574_101.png)

The method we followed is best one that we selected those objects whose profit by weight is higher and definitely whose whoever par G values is greater that will give you the maximum profit。



![](img/82b906812096c6448a649dfcc2837574_103.png)

So that's all aboutnapsack problem。 There is one more problem called 0，1napsack problem。

 That is different from this one。 How it is different here。

 fraction of an object is allowed but there indivisible objects。 Fions are not allowed。

 So this is container loading with Ve or fruits like this， which are divisible things。

 Anything that is divisible and 0，1napsack problem will be container loading with indivisible thing。

 Either you include that holdinging or it don't include at all。 So you cannot take the part of it。

So that's all So I'll be making videos for all the topics that are there in greedy and then I'll move on to dynamic programming and so on。

So I'll be covering the entire syllabus what all the topics are there in the syllabus。



![](img/82b906812096c6448a649dfcc2837574_105.png)

Okay， thank you for watching。