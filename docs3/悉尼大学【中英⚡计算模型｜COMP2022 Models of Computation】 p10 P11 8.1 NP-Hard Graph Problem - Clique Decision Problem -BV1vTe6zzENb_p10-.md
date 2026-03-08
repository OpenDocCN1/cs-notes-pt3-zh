# 悉尼大学【中英⚡计算模型｜COMP2022 Models of Computation】 p10 P11 8.1 NP-Hard Graph Problem - Clique Decision Problem -BV1vTe6zzENb_p10-

Hi， the topic is clear decision problem。 This is a N hard graph problem。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_1.png)

So in this video， I'll be discussing about these things。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_3.png)

First of all well learn what is a click then we will understand what are the differences between decision problem and optimization problems then we will see what does it mean by NP hard graph problem how this comes under NPhar graph problem then Ill show you the procedure how to prove any problem as NP hard then finally we will prove this CDP that is click decision problem as a NP hard problem。

So let us start let us understand what does it mean by click so for that I have taken some example graphs here see if you look at this graph there are four vertices and from every vertex there is an edge connecting to all other vertices so this graph is called as complete graph。

Complete graph。And one of the property of a complete graph is if you take the number of verrtices n。

 then the number of edges will be n into n minus1 by 2。This is one of the property of complete graph。

 If there are n vertices， then there will be n into n minus-1 by2 number of edges。 So yes。

 this is a complete graph of four vertices。 This is a complete graph of three vertices and this is a complete graph of just two vertices。

 So we have understood what does it mean by complete graph。 Now let us know what is a click。

 So for showing that what I do is。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_5.png)

I'll add one more vertex here，5。And I will connect a few edges。 Okay，1。2， that's it。

Is it a complete graph with five vertices No，5 is connected to only4 and3。

 What about one and2 it is not connected， So this is not a complete graph。

 but what about the subgraph of this graph， Yes， this is a subgraph of this graph now。

 and the subgraph of a graph which is actually a complete graph， this is called as click。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_7.png)

So click is a subgraph of a graph， which is complete。Let us take this in this。

 I will add two more vers，4 and5。And I will connect this now。There are five vertices in a graph。

 Is it a complete graph。 No， is it having a complete graph with four vertices。 No。

 if these edges are there， then it will become four。

 Is it having a complete graph with three vertices。 Yes， this is a complete graph。 So actually。

 this is not a complete whole graph， is a part of a graph。 So that is a subgraph of a graph。

 So a subgraph of a graph， which is complete， is called as click。 This is a clickique of this graph。

😊。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_9.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_10.png)

The same way there can be click of just two vertices also three vertices。

 also four or a number of vertices。 Now， let me draw one graph and we will identify。

 is there any cl in that graph or not。Now， I have an example graph。

 Let us find out what are the clickiques present in this one。

 So a graph G is given that is having total 6 vertices。 Then let us find out。

 is there any subgraph which is forming a complete graph， Yes。

 these are four vertices This are forming a complete graph。 So there is a clickique of size 4。

And there are three vertices which are forming a click。 There is a click of size， 3。

And even if I take this also， it is forming a click of size3， right？So if I take just5 and 6，1"， yes。

 there is a click of size2 also。Right， so this is the minimum1。

 So what is the maximum click I am having of size 4。

Now we have identified clicks from this graph Now let us understand what does it mean by decision problem and what does it mean by optimization problem。

From this example problem well understand this， let us look at this。

Is there a c of size the3 in this graph answer is yes。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_12.png)

Is there a c of size a two in this graph？ Yes， answer is yes。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_14.png)

So problem， which requires answer as yes or no， is a decision problem。

So decision problem is to just find out， is it true or false。 So what is the question here。

 I there any click of size of4 in the graph， Yes or no， Find out， and the answer is yes。

 So finding out whether the answer question is true or false， that is called as decision problem。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_16.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_17.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_18.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_19.png)

The next optimization。What is the maximum click size in the graph。 So we found 2，3 and 4 beyond 4。

 There is nothing。 So4 is the answer。 So this is。Optimization problem。

 So when you want to find out something maximum or minimum， then it is optimization problem。

 Finding a maximum click is optimization problem。 Finding a click of size a K present in the graph or not is a decision problem。

 So decision problem。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_21.png)

Decision problem is find out if a graph is having a click of size K or not K means any number。

So find if a graph is having a click of size K or not as a decision problem。

 then what is optimization problem？Optimization problem is find what is the maximum click a graph is having。

Finding Max click in a graph is a optimization problem。A click decision problem is this one。

 So click decision problem is a graph problem。 And also， we have to prove that it is N hard。

 See if a decision problem is N hard， then optimization problem is also N hard。

 Both our N hard problem， But we have to prove that click decision graph problem。

 Click is from graph only。 So graph problem is N hard。 Now。

 let us look at the procedure for proving a graph problem as N hard。 What is the procedure。 Now。

 let us see what is the general method for proving a problem as N hard。

 then we will come to CP problem。 So if we call our problem。 Any problem as L2。

 then we have to prove that problem， L2 is N hard。😊，So for proving it。

 we have to select any problem L1， which is already known as NPhad。

 and we have to show that L1 reduces to L select a presently known NPhard problem from that。

 we can prove the other problem also as NPhad。Then how we do that。

 we take the example of this problem。 And from the example of this problem。

 we will prepare an example of second problem。 This one。

 we have to take this example such that if this can be solved in polynomial time。

 then this should also be solved in polynomial time。 Or in other words。

 if this problem can be solved， then this should also be solved。

 And the conversion that is conversion from this one to this one， we will do it in polynomial time。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_23.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_24.png)

Now， let us put our problem and see here。 what problem we want to show as NP hard CP problem。

 Then what is the known problem we have， which is already NP hard satisfiability problem。

 So we have to prove that satisfiability reduces to CP。 So for that。

 we have to take an example of satisfiability。 that is conjective normal form formula。

 we have to take。 And from that formula， we should prepare a graph that is having some clickique。

So let us see how to prove that satisfiability reduces to CP and hence prove that CP is also NP hard。

 C Saisfiability is the known NP hard。 Now， we are proving that CP is also NP hard。

Now let us prove satisfiability reduces to CDP， So for this first of all I'll take an example and show you。

 then I'll show you the general formula for it， how to prove this one。

 so I'll take an example so here and I will take a satisfiability formula。

 I'll take the formula with three variables x1， x2 and x3。Let us say F is a formula。

 I will use very few variables here， X 1。R x 2。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_26.png)

And。X 1 bar or X 2 bar。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_28.png)

And X 1 or x 3。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_30.png)

There are three variables， and I have not taken all three variables in every clause。

 These are the three clauses。 C 1 is a clause。 C2 is a clause。 C3 is a clause。

 So there are three clauses。 So if you look at the formula。

 The formula is made up of clauses C I and all clauses are added right。

 and I take the values from1 to K。 So how many clauses are there K clauses are there from this formula。

 I have to prepare a graph such that which is having a clickique。

 and that clickique should be of size a K。 So K is how much here 3， it should have a click of size 3。

 Let me show you how we will prepare a graph for this one。

 Take these variables and make them as vertices， x1， This is a vertex x2， this is also vertex。

 Then I take the variables of second clause， but I will not mix with these。

 I will make them separately。 This is x1 bar as a vertex。 Then x2 bar as a vertex。😊。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_32.png)

Then this also， I will keep them separate。 X 1 is a vertex， and x 3 is also an vertex。 Now， actually。

 this belongs to clause 1。 So I will try them like this。 This belongs to clause 1。

 Just I want to differentiate them。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_34.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_35.png)

So this belongs to clause 2。 so this belongs to clause 2。And this belongs to clause 3。So。

 these are the vertices。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_37.png)

I don't want to mix them。 So I have kept them separately。 So what are vertices in a graph in a graph。

 the vertexes of this form。 Let us say it is a comma I。So such that this a belongs to some claw C。

So whichever clauses belongs that I will write on here。

 and should be a variable in that one or a literal in that one。

 So we have taken all the variables or the litals and form the vertices。 vertices are over。 Now。

 let us see how to form edges。 See the first rule is， I should not connect the vertices of same claw。

 This belongs to clause 1。 So I should not connect these two。 This belongs to clause 2。

 I should not connect these two。Then I scan connect the vertices of one claw with the vertices of another claw this is allowed。

Okay， let us draw it。I will draw an  edge from this one to this one。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_39.png)

No， this is also wrong。 Second rule。 What is the second rule。 See。

 you cannot connect a claw with its negation。 So this is x 1。 So that is x1 bar。

 So you should connect to another claw。 And also， it should not be a negation。

 So this edge is not allowed。 Then can I form an edge from here to here。 Yes， x1 to x2 bar。 Yes。

 allowed。 Then x2 to x1 bar。 Yes， allowed。 Then x2 to x2 bar。 No， it's a negation， not allowed。😊。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_41.png)

So let us see before completing that， Let us see how to form edge。 So for an edge。

 if you are forming an edge from a to I of first claw 1 claw to B of J。Of another claw。

 then the edge should be such that。This I should not be equal to J means they should not belong to same clause and。

 and second condition is B should not be equal to a bar。 So if you have taken a here。

 then they should not be a bar。 So these are the two conditions that we have to take care while drawing edges。

 Let us complete this。 from here， I have connected to this。 Now。

 from this verticus let us connect to this X1 with X1。 Yes， okay， no problem。X 1 with x 3， Yes。

 no problem。 X 2 with X 1， Yes， no problem。 X 2 with x 3。 Yes， no problem。 I can correct。

Now I have to connect these two claws。X 1， bar it， X 1， no personalation。Then X1 bar with x 3， yes。

X2 bar with x1。 Yes， it can be connected。X2 bar with X 3。 Yes， it can be connected。

So I got a graph which is an example from this formula， this formula is satisfiability。

 this graph is for this problem。Now， such that if this is all in polynomial time， this is also Sa。

And one more。What are the number of clauses here， the size of this formula K K is 3 here？

Then find out。 Do you have a click here。Do you have a click here， We have to find out click。 Yes。

 there is a click of just two vertices， single edge。There is a cl of three whates also。

 So this is a cl of size，3。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_43.png)

Check， do you have a click of size 4 in this one。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_45.png)

No， no， this is the clique we have。 This is the cl。 See， there are more triangles。

 but this is the 1 I have selected。 This is the one。 Okay， there is one more triangle。

 There is one more triangle。 You can form different triangles。

 but I am picking up this one of the triangle。 You can take all of them check all of them。

 but we want only one。 We have one clickique of size 3 because this formula is having three clauses。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_47.png)

That's it see thisprove that if you take a formula of satisfiability with the K clauses。

 then definitely a K size a click will be there in the graph。 Yes。

 there is a K size click in the graph。😊，Now， if this is solved， that will also be solved。

 how let us see how many variables we have， X1， x 2 and x 3， See the ver is what I have selected。

 Let us mark them as a true。 I'll make this X 2 as a true。 X 2 is true。 So for two， I will write one。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_49.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_50.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_51.png)

Then x1 bar as a true。 So what is x1 falses， Then x 3 as a true。 So this is1。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_53.png)

![](img/48ab6c5c8f71e4ce96667354dc2cef82_54.png)

So I made all these as true。 This I made as true。 So this became false。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_56.png)

Now， let us fill these values，0，1，1 here。 This is what 0。 And this is1。 So 0 or1。

 the result will be one。 So the first floor result will be one。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_58.png)

Excell1 bar。See x1 is 0。 X 1 bar is true。 and x2 bar。 X1 is what true。 So X 1 bar will be false。

1 or0 is 1 only or dision。 So1 or 0 is1 only。 then x 1， x1 is 0。 but x 3 is1。 So0 or1 is1。

 Now C clause is 1 and1 and1 result of this formula is 1。 Yes， for this click。

 If you select these vertices and mark them as a true。 put the same values in the formula。

 formula is a true。😊。

![](img/48ab6c5c8f71e4ce96667354dc2cef82_60.png)

From this graph， if you pick up another click， if you take this one， this one。😡，And similarly。

 if you do the same thing， then also the formula will be true。 So finally。

 we have proved that if this can be solved， then that solution will help in solving this one also。

 So as this is NP hard。 this is also NP hard。 So we have proved that click decision problem is NP hard。

 not NP complete。 remember it's NP hard。 Now how to prove this as NP complete。

 you have to write a nondeterministic polynommal time algorithm for click decision problem。

 then it can be proved as N complete。 So it's already known as NP complete。

 if you want you can browse and find out what is the algorithm for it or you can write by yourself。



![](img/48ab6c5c8f71e4ce96667354dc2cef82_62.png)

That's all。