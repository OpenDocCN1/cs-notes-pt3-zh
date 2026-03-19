# 【精译⚡算法导论】AbdulBari p54 p53 4.5 0⧸1 Knapsack - Two Methods - Dynamic Programming -BV1hhPXeTEWM_p54-

The problem is0， and abstractpsack problem。In this video， I will explain what is zeronapsack problem。

And how it can be solved using dynamic programming。We will understand its approach。Next。

 I will show you a tabular method for solving this one。

Then also I will show you a sets method for solving this one。

 So there are two methods we will see both the methods。First of all。

 let us understand what the problem is。Here I have some four objects for each object。

 there is some profit， and there is some weight。And there is a bag of capacity M that is 8 is given。

The objective is to fill this bag with these objects。So can I put them all？See the capacity a is 8。

 but the total weight of all these objects is 14。 So all objects cannot be filled in the bag。

 So I have to carry few of those some of those objects。 that is subset of those objects。

And I have to carry them and sell them at other place。So once I sell， I get this profit。

So I have to fill the objects such that the total profit is maximized。

And I have to give the solution in the form of a set。For each object， like， for example。

 this is included and this is not included or not included like this。

 I have to write on which one is included and not included。

 So it means I can write down each X either0 or one means the values can be 0 or1， but not fraction。



![](img/66a98f3f17a0b9caab806c8632760dc9_1.png)

So it means that the object that I am going to carry are not divisible。



![](img/66a98f3f17a0b9caab806c8632760dc9_3.png)

Breakable， so I cannot take the fraction of that object。So this means these are some solid objects。

Maybe a mixer or microwave ovenov or a router， it can be something like this。

 so which I cannot take a half of a mixer in the back。So these are indivisible objects。

 so either I should carry the whole object or don't carry it at all。

So I have to carry the objects such that the sum of their。



![](img/66a98f3f17a0b9caab806c8632760dc9_5.png)

Profits should be maximized。And some of their。Wes should be less than or equal to the capacity of the back。



![](img/66a98f3f17a0b9caab806c8632760dc9_7.png)

Now let us know the approach of dynamic programming for solving this one。Now。

 a few important things about dynamic programming。 dynamic programming is useful for solving optimization problem。

 Yes， this demands maximum results。 So it's optimization problem。 Second thing。

Dynamic programming says that a problem should be solved in sequence of decisions。 So， yes。

 we can take the sequence of decisions for every object we can take。

 Sha I include or not include or not， include or not， so I can take decisions。

 I can even start taking the decision from the last object also include or not include or not。

 So usually in this one， we take the decision from last object towards first object。

So we can take sequence of decision Next thing， one more point that dynamic programming says that you should try all possible solutions and pick up the best one。

Now how many possible solutions are there， See when I am writing the solution in the form of zeros and ones。

 then it can be0，0，0 min no object is included or 1，1，1，1 min all objects are included or 0，00。

1 min only fourth object is included our first object is included。

Our first two objects are included like this。 There are many possible solutions。

 and some of them may be feasible。 Some may not be feasible。 like all objects I cannot include。

 So anyway， I should try all of them and pick up the best one。

 So total how many solutions will be there。 So like 4，0s in ones form。 if I continue。

 So I'll be getting to power 4 solutions。

![](img/66a98f3f17a0b9caab806c8632760dc9_9.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_10.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_11.png)

So I should try to pour4 solution for n objects， it will be2 power n solutions， so if I try out all。

 then the time complexity will be 2 pour n。

![](img/66a98f3f17a0b9caab806c8632760dc9_13.png)

This is too much time consuming。So dynamic programming shows an easy method for doing the same thing。

We will not we will be indirectly trying all to power in， right， but not directly。

 so we will not spend that much time Let us solve this problem using tabulation method。

 tabulation method， let us see how to fill this values and how to get the solution for this problem。

So for solving， as the capacity of the bag is 8， so I have taken the columns starting from 0 to8。

So this means that though the capacity is 8 but will not consider that 8 at once。

 so we add weight 1 by1 so starting from0 then let us assume weight is 1 weight is 2 and so on。Then。

 throw。Four objects I have taken 5，01，23，4， so starting from 0。

 so it means one by one we will consider the object。

 so initially we will not consider any object will not include any object in the back。

So for filling this， we have a formula， so I' will show you formula after some time after filling some values。



![](img/66a98f3f17a0b9caab806c8632760dc9_15.png)

So let us see first row， as a0 object， no object is included。 then what will the profit。

 So in these boxes， I'll be writing the profit。 So there is no profit gained when no object is included。

And even when the capacity of the bag is 0， these are the， this is the capacity。

 These are the weights， right， and these are weights and the profits of the objects。

 So these are the weights。 And that is then 0 weight is there。 Then all these are 0，0，0。Next。

Now I will start filling， so for that Ill consider first object when I consider first object I'll take this row and I will ignore all other objects。

And similarly， when I go to second row， I will ignore the remaining and I will take the second object。

As well as the first object， I'll consider the first object also。So it means whenever I am in eyerow。

 I will consider all the objects in the previous rows also。So for the first row， directly。

 I can fill it， let us see。First row， what is the weight of the first object two。

 so it can be filled only when the bag capacity is a two。 So here， so what will be the profit one。

 so fill one here。That this means this is same value， previous value。



![](img/66a98f3f17a0b9caab806c8632760dc9_17.png)

Usually we write previous value only if required then。Rest of the cells。

 the capacity of the bag is increasing but how many objects I am considering only one so I don't have anything more to fill in the bag so only that object I can fill and it will be getting profit as one。

1， one only。

![](img/66a98f3f17a0b9caab806c8632760dc9_19.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_20.png)

I'll fill the second row also， right third row also in the same way。

 then I will write on the formula。 Let us go to second row。I am going to consider second object。

 So as I said， when I consider second object， I should also include the first object。So first。

 let us look at the second object。 See the weight of the second object is 3。

 It can be filled in the bag only if the capacity is a 3。 So in this cell only it can be filled。

 So what is the profit that I'll get to。 So put to two here。 What about this site。

 It will be same value， same value as the previous row。



![](img/66a98f3f17a0b9caab806c8632760dc9_22.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_23.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_24.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_25.png)

Then beyond this， what should come here。 So as I said that when you are taking second object。

 you should also consider first object。 So if I fill the second object also in the back。

 total weight requires how much。

![](img/66a98f3f17a0b9caab806c8632760dc9_27.png)

5， so this is 5， and total profit will be 3。 So both the objects can be filled when the capacity is 5 and the total profit will be 3。

 So here， both of them can be filled。Right， both of them， I'm considering both of them。

 So now I have only two objects， and this is giving for both objects are filled。

 So rest of the values will be 3，3，3。 Then what will be the value here。 So as this is 2。

 So this will also be 2。 So I can take the previous value or this value， whichever is maximum。

 I can take the same thing。

![](img/66a98f3f17a0b9caab806c8632760dc9_29.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_30.png)

N filter third object also， then for the fourth object I will show you the formula。Third object。

When I consider third object， if you look at these。

 the maximum weight is this one and as they are arrangeding the increasing order of the weight。

 So this weight is 4。 so this object can be filled in the bag only if the capacity of the bag is 4。

 so this will be included in the bag when the capacity is 4 so the total profit that will be getting is 5。

 so this is 5。Then before that， whatever the previous row values are， so 2，1 and 0。



![](img/66a98f3f17a0b9caab806c8632760dc9_32.png)

Now， beyond this， let us see， see， when I am on the third object。

 I should also consider first and the second object also。So if I just check them， this is four。

And if I take these two objects， it will be total6 weight weight is 6。

 so these two objects I can fill if the weight is6。Right， if I want to fill these two。

 then these two I can fill when the weight is 7。This way can fill if the weight is5 and what will do the profit 3。

 This object itself is 5。Right now I will consider these two6 and the total weight will be 6。 so at6。

 it will be 6 only。

![](img/66a98f3f17a0b9caab806c8632760dc9_34.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_35.png)

Right， and when I consider these two。 So total is 7，7。 and the profit is also 7。 So at 7。

 the profit is 7。 Can I include all three， It will be 10。 But the capacity of the bag is only 8。

 so I cannot or include all three。 Then beyond this， the value will be 7 only。 And before this one。

 the value will be same as this 5。

![](img/66a98f3f17a0b9caab806c8632760dc9_37.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_38.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_39.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_40.png)

I liked。Now I will show you the formula and I will fill fourth row with that formula。

 the formula is like this。

![](img/66a98f3f17a0b9caab806c8632760dc9_42.png)

If I call the stable as V， the table as V， then V of I comm W I is the row number。

 W is the column number。Is maximum of。V of I -1 that is from the previous row I should take same value means previous row value I should take。

 This is the meaning or maximum of this one or what。



![](img/66a98f3f17a0b9caab806c8632760dc9_44.png)

V of I-1 comma weight minus weight of an object。WI。Yes。Profit of an object that you are considering。



![](img/66a98f3f17a0b9caab806c8632760dc9_46.png)

Now， let us follow the formula and fill all these。

![](img/66a98f3f17a0b9caab806c8632760dc9_48.png)

First 1，4 comma 1。 I will fill 4 comma 1。 So V of4 comma 1。It's Magim off。V of3 comma 1。

 like this is 4。 So this will be 3 comma V of。3 comma weight is almost much 1 minus weight of an object。

 weight of an object is 5，1-5。Plus。Profit of that object is 6，6。Now， this becomes 3 comma minus-4。

 There is no such location， So that value becomes undefined。 So only this value will be defined。

 V of three comma 1 will be defined。 So v of three comma 1 is what 0。 So I should take 0 only。



![](img/66a98f3f17a0b9caab806c8632760dc9_50.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_51.png)

There will not be any such index v of 3 comma minus4 Yes for that I have to take 0 only。

 so it means up to what I'll be getting negative numbers up to fifth weight up to fifth weight。

 So till here I should fill these values as it is only。



![](img/66a98f3f17a0b9caab806c8632760dc9_53.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_54.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_55.png)

So that's what I was saying that this can be considered or this can be considered in fourth。

 So write on its value and all previous values as it is。 So the same thing here。

 because there will be getting negative。 So till fifth weight， till fifth weight before that。

 till before that， I have filled as it is。 Now， this fifth weight， how to fill， I will show you。



![](img/66a98f3f17a0b9caab806c8632760dc9_57.png)

For this value，4 comma 5。V of for four comma 5 S maximum of。V of。3 comma，5， comma， V of three comma。

 weight is how much 5。

![](img/66a98f3f17a0b9caab806c8632760dc9_59.png)

Minus weight of this subject is how much5。Plus， profit of this subject is how much 6，6。

Let us see V of 3 comma 5，3 comma 5 is how much 5。告吗？V of 3 comma 51，5-5，0， v of 3 comma 0。

3 comma 0 is 0 plus 6， So which is greater。6 is greater。 So fill this value with 6。

 So that means this object is included here。Now，4 comm 6， I will find out V of。

4 comm 6 as maximum of。

![](img/66a98f3f17a0b9caab806c8632760dc9_61.png)

V of3 comma 6， comma， v of3 comma weight is 6， right， and the weight of the object is 5 plus。

Profit of the object is 6。 So how much this is v of three comm 6 is， how much3 comm 6 is6，6 comma。

V of 3 commma 6-1。6-5。 That is 1，3 comma 1，3 comma 1 is how much0，0 plus 6。

 So the answer is both are same only。 So take6 only。Next1， full comma 7。 V off full comma 7。

Magazim ofmo。V of three comma 7， commma。 V of three comma。Weight is how is 7。

 So weight of the object is 5，7-5 plus profit is 6。 So this is 3 comm 7 is how much 7。

 This is3 of 3 comm 7-5 is a 2，3 comm 2。 So 3 commma 2 is how much 1 plus 6。 So this is 1 plus 6。

 So this is 7。 only both I am getting 7 or 7。 So they are seemingly take 7。V of4 comma 8。

4 comma 8 is maximum of。V off。3 comm， comma， v of3 comma weight is 8 minus the weight of an object is 5 plus profit is 6。



![](img/66a98f3f17a0b9caab806c8632760dc9_63.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_64.png)

3 co my 8， How much，3 co my 8 is 7。Coma v of 3 comma 8-5 is 3，3a 3。 How much 2。 So this is 2 plus 6。

 So how much this is， this is 7， and this is 8。 So answer is 8。



![](img/66a98f3f17a0b9caab806c8632760dc9_66.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_67.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_68.png)

So this is how the table is filled。 So I have used the formula for few cells in the last row。

And this can also be filled directly also without the formula。

 Let me show you how to fill this last row directly。

I am considering fourth object whose weight is 5 and the profit is 6， so in fifth column。

 just write 6 its profit。

![](img/66a98f3f17a0b9caab806c8632760dc9_70.png)

And what to write on the cells before that same value as the previous rule。



![](img/66a98f3f17a0b9caab806c8632760dc9_72.png)

This is what you do first。

![](img/66a98f3f17a0b9caab806c8632760dc9_74.png)

Then。Beyond this now the weight is5 beyond this the capacity of the bag is increasing so I can include other objects also。

 so let us check other objects what I can include in the sixth column this object is definitely because its profit is maximum。

 right。

![](img/66a98f3f17a0b9caab806c8632760dc9_76.png)

5 plus 2，7 at 6。 nothing will happen。 So take 6 only at 7， I can consider these two， these two。

 So this is 6 plus 1，7，7。

![](img/66a98f3f17a0b9caab806c8632760dc9_78.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_79.png)

Then at8 when the back capacity is， which of the objects I can consider5 plus 38， so6 and28。

 so this is8。So whichever objects that you can consider。

 you just add them and in that capacity if they are fitting in， you write on the max total profit。



![](img/66a98f3f17a0b9caab806c8632760dc9_81.png)

So this is a simple method for filling the cells。 Instead of following this complex formula。

 you can follow that method。 So I have shown you both。



![](img/66a98f3f17a0b9caab806c8632760dc9_83.png)

Solution。

![](img/66a98f3f17a0b9caab806c8632760dc9_85.png)

I have to write down x 1， x 2， x 3， x 4 values。

![](img/66a98f3f17a0b9caab806c8632760dc9_87.png)

Now， this。对。Now for finding these answers， actually I'll be taking sequence of decision now。

 see the decisions can be taken only if you have the data。 Yes， we have kept the data ready。

 the formula was used for filling this data。 Now I have to take the sequence of decision So how to solve。

 So actually I have to know which object should be included and which should not be included in the bag。

 So let us come with a maximum profit that is 8 the last cell。This8 is generated only in fourth row。

 and in that previous row you don't find8 anywhere。

 so it means we got the shade because of including fourth object only， so include the fourth object。

Right，Pro is 8， fourth object is included because8 is not just in previous row。 Now。

 what is the profit of the A V A fourth object，8 minus profit is 6，6。 So this is 2。



![](img/66a98f3f17a0b9caab806c8632760dc9_89.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_90.png)

Now， remaining profit is2。 not check whether two is there in the third row have to check for the third object。

 fourth， then third， then second and then one。 So third object，2 is there。 Yes。

 at' the same value 2 is there in the previous or also。 Yes， it is there。

 So it means it is not because of third object。 So don't include third object。Now。

 let us consider second object。 Is it two there here in the second row， Yes，2 is there here。

 Is it there in the first row Also no， So it means this regard because of inclusion of this second object。

 So take this as 1。 So now remaining is 2-2。 so 0。

![](img/66a98f3f17a0b9caab806c8632760dc9_92.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_93.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_94.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_95.png)

Now， zero was it there in the first object， so I have to consider the first object， Yes。

  zero was there in the first object row。Was it there in the0th Also。

 Yes it was there in the0th Also this row also。 So it means don't include the object。

 So this is the solution。 So it means which objects are included in the bag X 2 and x 4。

2 objects are included in the bag。 So that is x 2 is this one。 X 4 is this one。

 So total profit will be 8。 So this is the maximum profit of 0 andnapsack problem。Next。

 I will solve it using sets method， same problem。 I will solve it using set method。 Now。

 let us solve it using set method。 set method will try to find all possibilities and pick up the best solution。

 So let us see how sets are generated。We will prepare a set of order pay That is profit and weight。

So we'll start with the set0。Set0 and this we say no profit。

 no weight means nothing is included in the back。

![](img/66a98f3f17a0b9caab806c8632760dc9_97.png)

Then we will consider the first object。 That is one comma 2 whose profit is1 and the weight is 2。

 So consider the first object。 So prepare as 0 of1 and include this first object in the bag。

 So it will be one comma 2。

![](img/66a98f3f17a0b9caab806c8632760dc9_99.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_100.png)

So actually I add one comma to this order pair so we get this one。No prepares set one。

Then merge these two order pairs and prepare this one。So， this means that。

We have considered first object， so two other pairs are showing that first object is not included。

 first object is included。Now， let us prepare。Next set by considering second object。

 So that is 2 plus 3。 So prepare next set that is S 11。 So add 2，3 to these order base 2 plus 3。

 So this is2 comma 3。Then two plus3 is added， so this will become 3 plus。Three， gaa five。

Then this is second set for the second object。 So when you consider second object total four order pairs。

 all these are merged， So this is1，2 and 2，3， and this is 3，5。This means that no object is included。

 first object is included， second object is included。

 Both objects are included four possibilities are there， so all the other pairs we got。



![](img/66a98f3f17a0b9caab806c8632760dc9_102.png)

Then prepare as two of one by considering third object Phi comma 4， Add Phi comma 4 to all。

 So this 5 plus 4。 So this is 5 plus 4 is。

![](img/66a98f3f17a0b9caab806c8632760dc9_104.png)

5 comma 4 only。 So 5 plus 4。 So this will become 6 and 6。 So this is 6 comma 6。5 plus 4。

 So this is 7， comma 7。So5 is added to this and4 is added to this， so this become  eight comm9。



![](img/66a98f3f17a0b9caab806c8632760dc9_106.png)

8 common9。Now merge all these anti take order pairs。 So set 3 we get as 0，0。1，2， then 2，3。Then three。

5。Then，5，4。Then 6，6。7，7。Now， here。8ight common 9， profit is 8 and the weight is 9。

 so that is exceeding the capacity of the bag don't include that one。



![](img/66a98f3f17a0b9caab806c8632760dc9_108.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_109.png)

So， we have discarded that。

![](img/66a98f3f17a0b9caab806c8632760dc9_111.png)

Right。Now， this is set 3。 and this one， if you observe。



![](img/66a98f3f17a0b9caab806c8632760dc9_113.png)

This is profit。 This is weight， profit increase weight increase。 Then from this profit increase。

 weight also increase， profit increased and the weight also increase， but here， profit increase。

 weight is decreased from 5 to 4。

![](img/66a98f3f17a0b9caab806c8632760dc9_115.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_116.png)

This is not possible。 Profit is increasing， so the weight is also increasing。

 but weight is decreased。 How is possible。 So that's why this order pay are wrong。

 So we have to discard anyone。 so we will discard the one with the lesser profit， smaller profit。



![](img/66a98f3f17a0b9caab806c8632760dc9_118.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_119.png)

So1，2，3，4，5，6。 Now， we have only six order pairs because two were invalid。

 One was this was giving wrong values， and this was exceeding the capacity of the back。



![](img/66a98f3f17a0b9caab806c8632760dc9_121.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_122.png)

So cutting off this one we call it as a dominance rule。

 so with the dominance rule the value is other pair discarded。Now。

 I will consider fourth object 6 comma 5。 I will include， so I will prepare。Set3。

1 by considering fourth object 6 comma 5。 So first order pair is 6 comma 5。

 Next order pair is 6 and 5 are added。 So this is 7 comma 7。 Then 6 and 5 are added。

 So this is 8 comma 8， and then 6 and 5 when they are added。 it will become 11 comma 9。6 and 5 added。

 So this become2 wella 11。And 6，5 when added to 7 and 7， so this becomes 13 in comm to  well。Now。

 I have to prepare set 4。 This is the final set。 Most， these order pairs。 So 0，0 is taken from here。

1 comma 2 and 2 comma 3 and 5 comma 4，6 comma 6 and 7 comma 7， they are coming as it is。 Now。

 in this one，6 comma 5 is there。 So6 comma 5 should come before 7 comma 7。 So 6 comma 5。Now。

 here again， you see the profit is remaining same， but the weight is reducing。

 so this should be removed。 Then 7 comma 7 is there。 then 8 comma 8 is there。

 Then remaining 11 comma 9， exceeding the capacity of the back 9，11 and 22。

 So all three order pairs are gone。

![](img/66a98f3f17a0b9caab806c8632760dc9_124.png)

So these are the other pairs I have。 So if you observe the method is generating all possibilities。

 So this is one easy method of finding all possibilities。

 So the time taken by this one is almost too power。



![](img/66a98f3f17a0b9caab806c8632760dc9_126.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_127.png)

Now， what is the solution， So we have already sets。

 Now we take the sequence of decisions to solve this one。 Now。

 what is the maximum order fair 8 comma 8。

![](img/66a98f3f17a0b9caab806c8632760dc9_129.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_130.png)

So，8 comma 8。Now， using that， I will solve this one。 So the approach is similar。

 like what we saw in the tabular method，8 command8 belongs to set 4。But。8 comma 8。

 Check whether it belonged to set 3 in the set 3，8 comma 8 was not there。

 so it doesn't belong to set 3。 Therefore fourth object is included because of that only we got for comma 4。

Now I should take an order pair8 comma 8 from this I should subtract the profit and weight of the fourth object。

 so this is profit is 6 and the weight is a5， so the order pair is how much2 comma3。

 So now I should consider two comma 3。 So now this was the first one， now second one。2 comma 3。 Now。

 I have to consider third object。 So check whether it belongs to S 3。To commentary。 Yes。

 it belongs to S3 and。2 comma 3 belongs to S 2。 Check whether it belongs to S 2。

 S 2 comma 3 is there here。 Also， it means this is not because of the third object。 So therefore。

 third object is not included in the back。Then now， next step is， I will consider second object。

2 coa 3 belongs to set 2 for second object 2 coa 3。 Now， does it belong to set 1。



![](img/66a98f3f17a0b9caab806c8632760dc9_132.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_133.png)

But。2a3。Doesnt belong to set1， so2 comma 3 was belonging to set 2 and2 comma 3 doesn't belong to set1。

 so therefore this is because of the second object that is included。Now。

 what is the profit and weight of the second object to comma 3。

 So when you subtract2 comma 3 from this one，2 minus-2 S 0 and 3 minus-3 S 0。

 So this gives 0 comma 0。 Now first object I will consider now the step is4。

 So0 comma 0 belongs to set 1 and also0 comma 0 belongs to set 0。 therefore。

 first object is also not included。0 comm 0 belongs to S 1 also as 0。

 Also it means this is obtained not because of the first object。

 So fast objects is also not included。 Then the solution is from bottom。 If you see 0，1，0，1。

 So the answer is。

![](img/66a98f3f17a0b9caab806c8632760dc9_135.png)

0，1，0，1。So these two objects are included， C the profit is 8。

So weve got the same solution with the help of sets also。 So this is one more method。

That's all about0 abstractack problem。Leave a comment and let me know whether it was easy for you to understand。

 so I have shown you both the steps for solving zero1 appsps are problem right in some places we find tabition method and some places we find the sets method。



![](img/66a98f3f17a0b9caab806c8632760dc9_137.png)

![](img/66a98f3f17a0b9caab806c8632760dc9_138.png)