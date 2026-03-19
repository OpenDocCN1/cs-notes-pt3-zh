# 【精译⚡算法导论】AbdulBari p47 p46 4.1 MultiStage Graph - Dynamic Programming -BV1hhPXeTEWM_p47-

The problem is multi stageage graph， this problem can be solved by applying dynamic programming strategy。

In this video， I will explain you what is the graph problem。 Second thing。

 how dynamic programming is applicable。 Third thing， I will solve it using forward method。

Let us stop。Let us talk about the graph。 a multistage graph is a directed weighted graph。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_1.png)

And the vertices are divided into stages。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_3.png)

Such that the word edges are connecting vertices from one stage to next stage only。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_5.png)

First the stage on the last stage will have just single vertex to represent the starting point that is source or ending point or sync of a graph。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_7.png)

This is usually useful for representing resource allocation。

 So here there are various path from source to sync。

 I have to select the path which is giving me minimum cost。 This is the objective of a problem。

 So it's a minim problem。 That is optimization problem。

 The problem can be solved using dynamic programming。

Let us understand whether the dynamic programming can be applied on this phone or not。

 so dynamic programming works on principle of optimality。

 principle of optimality says that a problem must be solved in sequence of decisions Let us see can you solve this by taking sequence of decision。

If I start from here from first stage， that is a stage2 here。 Okay， and this is stage。

 I have to select one of the vertex。If I select 5， then I should make sure that what I am selecting is optimal。

 going to give me optimal result。 Okay， once I selected this now， again， I have two options here。

 from 5， I can go to 8 and 7 out of this again， I have to decide and select anyone again， next。

 I have to decide and select anyone。 So every stage I can take a decision。 So， yes， here。

 the principle of optimality holds。Now applying dynamic programming procedure that is staization method to get the data filled in the table for each vtex I am going to find the cause and for finding the cost。

 I'll start from here。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_9.png)

Because if you see from here， the edges are going that side。

 So if I want to co find the cost of this one， then I should consider all the edges reaching till sink。

 if I find the cost of three， then I should consider all the path going till sink。If I consider 10。

 then the cost of path reaching there。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_11.png)

Now， if I say sync， then the cost is 0。 obviously。 So for the last vertex， the cost is 0。

And the vertex is too only。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_13.png)

For the last vertex， how I got the cost as 0。 I will write down like this cost of。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_15.png)

5 stage vertex 12。 So I will write here， stage number and here the vertex number。And the cost is 0。

This how I will use the formula cost of Phi comma 1 elements means，5 stage and the vertex number 12。

 and the cost is 0 let us find out the cost of all these vertices in this fourth stage。 So first。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_17.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_18.png)

Cost of what stage 4 vertex 9。 So what is the cost of reaching till sink， It is 4， this edge 4。

 just a single edge path that is。 So it is 4。And the cost of fourth stage，10th vertex。

 it is2 cost of。Fourth stage，11th vertex， this is5。But it says 42，5， right， So from reverse 5 to 4。

 So this is 5。 This is 2， and this is 4。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_20.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_21.png)

Now， by taking these vertices 9，10 and11， where I am reaching， I am reaching on2 the vertex only。

 So this is 2 L and 2 L and 2。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_23.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_24.png)

Explain you， what does it mean by D here。 Okay， very soon。 Now， let us take third stage。

 So I have the verses 6，7 and 8。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_26.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_27.png)

I will find out the cost of these three。 So first6。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_29.png)

Cal off。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_31.png)

Third stage 6 verortex。Now， from here， if I see， there are two edges coming out。 So this is 6 to 9。

 as well as 6 to 10。 So which 1 I should select， I should select the minimum cost。

 So let us consider both。 then select the minimum。 So I have to select minimum of what。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_33.png)

Cost of an edge，6 9。Plus， go off。For the stage 9 vertex。And also。

 cost of an edge 6 co 10 plus cost of。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_35.png)

Forourth the stage 10th vertex。I have to take the minimum of these two。

 So what is that6 plus cost of 9，5 plus cost of 10。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_37.png)

The6 is what this 62，9 is an h。 I am writing it like this， right sees。Cost of an H。

 cost is cost of an vertex。 This is C is weight of an H。 Okay。

 I'm writing it as weight of an H 6 plus 9。 So what is the sequel to minimum of。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_39.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_40.png)

C，6，2，9 is how much 6 plus cost of four common 9 is here 4。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_42.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_43.png)

Coma C of 6 comma M is how much5。Com plus。Cost of for comma 10，10 as this one，2。 So out of this。

Which one is a smaller。 This one is a smaller。 The vertex 10 has given me smaller value。

10 has given me smaller value。 What is that 7。 So6 is 7 and which vertex has given me minimum cost vertex 10。

 So the one which is giving minimum result。 we have to write on that one here。

 Co of 7 vertex that is stage 3 here。 cost of3 comm 7 from 7 vertex。

 If you see there are two are just going out。 So to know the cost of 7。

 I should know the cost of 9 and 10 plus the cost of this edge So4 plus cost of 9。

3 plus cost of 10 out of those two， whichever is minimum， I should take that one。

 So I'll write like this cost of an h from 7 to 9 plus cost of a vertex 9 in fourth stage。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_45.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_46.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_47.png)

高马。Cost of an H from 7 to 10 plus cost of a vertex 10 in stage 4。Out of these two。

 I should take minimum。Now， if I take minimum amount of these。Cost of 7 to9， x 7 to9 is4。Plus。

 cost of ninth vertex is there from the table， so you can see how the values from the table are useful。

So this 9， other we found out， No it is useful。 It was useful for 6 also， not for 7。 also。

 this value of 9 is useful。 So this is what overlapping sub problems are there in dynamic programming。

 So 4。Coma C of 7 to 10，7 to 10 is3。Plus， cost of 10。 cost of 10 is how much 2，2 out of these two。

 This is minimum。 That is 5。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_49.png)

So cost of a vertex 7 is 5。This we are getting due to which vertex 10。

 so in D I should write down 10， so in D I should write on the vertex which has given me the shortest part。

 the minimum cost。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_51.png)

Next is cost of8， so there are two edges going out from 8 to 10 and 11。

 so cost of an h from 8 to 10 and the cost of vertex。10 in fourth stage， comma theres no space。

 I write here， C of 8 to2 11 plustopho vertex 11 in stage 4。I have to take minimum of these。

 So this is minimum。 I know these values。 So I will replace them cost of 8 to 10。5ve。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_53.png)

Plus， cost of an H 10 whatex stem， sorry2。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_55.png)

Comma cost of an 8 to 11，6。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_57.png)

Plus， cost of a vertex 11，11。Ass5。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_59.png)

Mimium 7。 Who has given the 7， what extent1 has given the 7。 So here it is 7。

 and the vertex that has given that result is 10 only。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_61.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_62.png)

Now， let us find the cost of all those vertices， which are in stage 2， cost of vertex 2 in stage 2。

 see there are three edges going out from here，1，4，6，1，4，7， and 1，4，8。

So this is minimum of cost of an h from2 to6 plus cost of vertex 6 in stage 3 comma cost of an h from 2 to 7 plus cost of a vertex 7 in stage 3 comma cost of an h from 2 to 8。

Plus， cost of a vertex 8 in stage 3。 First， we are writing stage。 Okay， so I have operated the。

Cost function here itself out of these。 I have to take the minimum。 See。

 this one is how much cost of an edge 2 to 6，2 to 6 is。4 plus cost of 6 is 7。

Comma cost of for H2a 7 is how much2。Plus， cost of this 7 S 5。Comma C of the soil 1。Plus。

 cost of a verex 8 is 7 out of these three。 Which one is a smaller。This is 7， and this is 8。

 and this is 11。 So 7 is a smaller。 So this one has given us minimum result。

 So the answer of this cost of vertex 2 is 7。 and who has given us minimum result。

 The vertex 7 has given us minimum result。 So this is 7。Cost of second stage，4 verortex。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_64.png)

As minimum of。From 4， there is only one edge。 So cost of four comma 8 plus cost of vertex 8 in stage 3 out of this。

 There is only one value。 So this is。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_66.png)

11 plus cost of 8，11 plus cost of8 is 7。So this is 18。 who gave the answer。8 has given the answer。

 This verortex has given the answer。 So this is 18， and this is 8。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_68.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_69.png)

Cost of second stage 5 vertex is minimum of from 5。 there are two edgeges。1 is going to 7。

 and one is going to 8。 So C of5 comma 7 plus cost of7 vertex in stage 3 plus。高吗。

Cost of finites from 5 to 8 plus cost of vertex。8 in stage 3。Sort of this minimum of。C， or5。

 comma 7 S 11。Plus， cost of 7 is 5。Comma， this one is 8。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_71.png)

Plus， cost of 8 is 7。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_73.png)

So this is 16， and this is 15，15 is a smaller。 And who has given this result 8。 So this is 15。

 and this is 8。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_75.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_76.png)

Now almost the table is filled here。 only one value is remaining。

 now we are at the stage to find the minimum cause for this that is starting vertex so that will give us the minimum cost from here to there。

 so to sync。Cost of one comma1 from vertex 1 in a stage 1。 That is first the stage there in vertex。

 There are 4，1 to 2 and 3 and 4 and 5。 So I should consider all and take the minimum。

 Do I have the cost of vertex 2，3，4，5 years already They are filled here。

 So there is easy for solving now to find this cost。

 So this is cost of an edge from1 to 2 plus cost of。2，2， 2。

 cost of an H from1 to 3 plus cost of third vertex in stage 2 is what is minimum， Let us find out。

 See， the values are 9，7，3，2， right？ So this is 9 plus cost of2 comma2 is 7。

Coma cost of onea3 is how much 7 plus cost of what X 3 is 9。

Comma cost of this vertex 1 and comma 4 H is how much3 plus cost of4 is 18。

Comma cost of one comma 5 is2 plus cost of5 is 15。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_78.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_79.png)

Out of this， Which one is a smaller， This is 16。 This is also 16。 This is 21， and this is 17。

 So I got two answers that are same。 So the answer is 16 only。

 but that is going via what first was vertex 2 and second was vertex 3。

 Both are giving same residual。 So I'll write two or three here。😊，I can take only one also。

 but I am writing both to see how the difference will be just like first filling the smaller values。

 then getting the answer for the larger value so we started from the back side that is from the backside of our multit graph last stage onwards we started。

But still this is called as forward method， how we will see that next。Let us frame the formula now。

 I did not show you the formula， but now， but the procedure already have shown you。

 let me frame the formula。 We were finding it like this cost of。I the stage J the vertex。

 this I is a stage number， right？And this jer。Vex number。So， this was minimum of。

I was taking minimum off what？😡，This was cost of a match from vertex J to some vertex L。Plus。

 cost off。Cost of that next vertex L。 if I say J and L， J is supposed to then L is supposed 6。

 So J cost of 2 to 6， then the cost of 6， third stage 6 vertex。

 So we were writing the stage number here。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_81.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_82.png)

I plus 1 and L。This for the formula we are finding whatever the edges are available for two there are three edges。

 so we wrote the same thing three times。You can see that for finding cost cost of second stage。

 third vertex was minimum of one of the value write down third vertex 2，6 vertex plus cost of。

Third stage6 vertex。 If I say this is stage number2 and vertex， this is J。

 then minimum of cost of an h J to some L some vertex L。

 then cost of that L and that L 6 is definitely in the next stage。 So this is i plus 1。 If I is a 2。

 then this is2 plus 1。 So this is i plus1。This is how we were using the formula for finding discourse in multi stage graph。

 So this is the formula Form stage graph。 And we say that。I am sorry J and L belongs to set of edges。

And， and。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_84.png)

L belongs to next stage。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_86.png)

So this is the formula that you can find in the textbooks Now the actual dynamic programming stars right Al we have the formula and up the table based on the dynamic programming only dynamic programming approach to get the result actually the method of dynamic programming is to solve a problem by taking sequence of sessions we have not taken any decision so far。

 but now we are going to take the sequence of decision based on the data available。

So already I was writing the Dvalue， whichever the vertex was giving us minimum result。

 I was writing the Dvalue there using that we take a decision。

 What decisions we take from here where we should go to which vertex。

 then from there where we should go。 then from there So decisions are taken only have this complete data with you。

 So already we have the data。 Now we are going to solve it by taking sequence of decision and we will start from vertex1 on words towards sync。

 So this is forward。 the decisions will be taking in forward direction。 So the base decisions。

 this is forward method。 let me do that。 first of all， distance of D D Dvalue you have for 1，2，3。

4 all I have。 So first I will write stage number， this is a stage number right and then I will write on vertex。

 This is vertex。D of1 co of1。 So actually， we are concerned about this。

 I'm writing it like a formula。 Okay， so this is stage number and this is verex number。

 So we will consider this verex number。 What is the answer to， So let us take2。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_88.png)

![](img/a0af762bf50cf1fe863f779e0c63a7c2_89.png)

Now， in the second stage， already we have taken two D of two coa 2。 So is all the first stage。

 we selected first vertex and second stage， second vertex vertex 2。

 Now from there where we should go。 So two who has given the minimum result for 2，7。

 So this is 7 in D， we have 7。Now， we are on the  seventh vertex on。7th vertex in stage 3。 Now。

 being on stage 3， where we should go next from 9 or 10。 Which one。 So 7 has given us a 10。 So 10。

 Now we are on the vertex 10 in stage 4。 Then from fourth stage10th vertex， where we should go next。

 So table will tell us everything。 So we should go on 12。 So that's it to2。

 So our part is what we started from vertex 1 to 2， then 7， then 10 and 2。 So this one to 22 to 7。😊。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_91.png)

7even to 10。10 to together。

![](img/a0af762bf50cf1fe863f779e0c63a7c2_93.png)

This is the shortest part from source to sync that this Dvalue has given us the result。

So now we have taken sequence of decisions。Let me show you once more，4，3。

 I said that for both 2 and 3， we got the answer as 16。 So let is 3。 What does it give。

 I start from vertex 1。 That is stage 1。 So one1 gives us what 3， then。I'm on stage 2 on vertex 3。

 then third vertex。What is the one which has given minimum result 6。 So this says goes to 6。

 Then in the third stage， I'm on verex 6 now。 So， okay， I'll do it here。 Also， I have gone to 3。

 then 3 has sent me to 6。Now， being on third stage 6 vertex， where I should go next。

 So 6 was the answer，10。 So go to 10。 So it says that I should move to this one。

 So this is the decision I have taken。Then。10 is in fourth stage。 So from 10th vertex。

 where I should go10th vertex， we already have seen this answer that is 12，12。 So from 10。

 I should go to 12。 So this is another route。 you see。 This is another route。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_95.png)

Which is giving us the minimum result。 So this is one。Right5 2，7，10， then 1，3，6， and 10 and 2。

 So I have two parts of same cost。 So the optimal result is only one。 but in by chance。

 we are having two parts which are giving us the same result。

 that's all about multis stage graph problem。 and I have explained you how dynamic programming is followed here。



![](img/a0af762bf50cf1fe863f779e0c63a7c2_97.png)