# 【精译⚡算法导论】AbdulBari p65 p64 6.2 Sum Of Subsets Problem - Backtracking -BV1hhPXeTEWM_p65-

The problem is， some of subsets。First of all， I'll explain the problem。

 then I'll show how to solve this problem using backtracking I have taken an example problem here。

Let us understand what the problem is。 See here， some weights are given n equal to6 total 6 weights are given。

 We have to take subset of those weights。Such that there sum total is exactly equal to M。 That is 30。

 If I add all of them， it will not be 30。 It will be much more than 30。

 We want subset of those such that their total is exactly 30。



![](img/49a4225c36cbb7e20b2683fefe9bc957_1.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_2.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_3.png)

Whiever the weights that I am going to include I will write them as solution here and this solution will be either in0 or run one form。

 means each X value can be either0 or1 means whether I am including it or not including。



![](img/49a4225c36cbb7e20b2683fefe9bc957_5.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_6.png)

Now， how to solve this problem？So selection of those weight can be done in various ways。

So let us try all possible ways of their selection and find out which of those a selection is giving us this exact way 30。

 I will draw a solution tree for this one that is state space tree for this one。

 little bit par part of a tree。 I will draw。 Then I will solve it。 See the idea is。

We will consider like this fuss of weight is included or decide first weight is not included。

But as we are following backtracking here， so we'll follow depth first search so we will generate this first。

 then afterwards will come to that side。 So but how it looks like I' am showing you So second object will be included or not included。

 So but we will consider this first and explore this one same way when we come to this side here also will consider second object is going to be included or not included。

 So second weight is included or not included same way next level will be for the third weight and third weight 0。

 So here also I will get all possibilities。 then this is for the fourth weight。



![](img/49a4225c36cbb7e20b2683fefe9bc957_8.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_9.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_10.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_11.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_12.png)

So like this， if I continue。If I continue like this， then。



![](img/49a4225c36cbb7e20b2683fefe9bc957_14.png)

Like there are six weights so I'll be getting7 level， including the root。

 seven level I'm be getting or the height will be6。



![](img/49a4225c36cbb7e20b2683fefe9bc957_16.png)

So total how many parts I am inviating。 So  two power 6。



![](img/49a4225c36cbb7e20b2683fefe9bc957_18.png)

Means to board N。If there are n weights， it's super M。So it's time consuming， right。

 so it's exponential。So depending on the path， it is2 n。

 so the amount of time taken for solving this one will be2 n because that many parts we will be generating。

But。When we apply backtracking， we try to kill the nodes if they are not satisfying bonding function。

 so we have to define the bonding function and we follow the bodying function。

 Now I will show you how to solve this one using backtracking and also I will define bonding function for this one。



![](img/49a4225c36cbb7e20b2683fefe9bc957_20.png)

Nowll generate the tree。Fussnd。Now every node I'll be putting the value two values0 and the total of this one。

 so total is how much 10， 20，30， 40， 50 and 60，73， so total is 73。



![](img/49a4225c36cbb7e20b2683fefe9bc957_22.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_23.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_24.png)

Why youll know shortly。

![](img/49a4225c36cbb7e20b2683fefe9bc957_26.png)

Now， I have to consider whether I am including this weight and the solution or not。

 so one by one I have to consider all。 so just now I have given you the idea how we will be doing it。

 so I will take this side。

![](img/49a4225c36cbb7e20b2683fefe9bc957_28.png)

So， this is。First weight included in the solution。 So what is first weight 5。5ve。Actually， initially。

 there was no weight， so it was 0， now it became 5。Now， total weights I was having was 73 now。

 five less， so that will be 68。

![](img/49a4225c36cbb7e20b2683fefe9bc957_30.png)

So remaining grade I having are 68。Continue， Second wait。Included。Second weight is 10。

 If I include it5 plus 10，15， then subtract 10 from this one， so 58。ARein weight Samm having a 58。

Next， third weight included， so third weight included， so third weight is 12。

 add 12 to this 27 subtract 12 from here， so 46 remaining weights I' am having are 46。



![](img/49a4225c36cbb7e20b2683fefe9bc957_32.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_33.png)

Next， include fourth weight。If I include fourth weight also that is 13 so 27 plus 13 it will be 40 and if I subtract 13 from here this is 33。

 see exact weight I want is a 30 but this has exceeded so if I go further I will not get any solution so I should stop here and kill this node with some bonding function so bonding function is nothing but a condition so what is the condition see if the total weight of so far objects。

 whatever you have included and add this one also then the total weight should be less than or equal to that one exactly right so。



![](img/49a4225c36cbb7e20b2683fefe9bc957_35.png)

Some of the weights included so far。Tilcate object plus weight of the next object should be less than equal to M。



![](img/49a4225c36cbb7e20b2683fefe9bc957_37.png)

If it is greater， it is useless to continue。 So kill this one。

 If I add more that I will be crossing 30， so I may not get 30 again。So okay。

 I cannot include fourth， so okay try without including fourth object fourth object is not included。

 so if fourth object is not included weight remains same only total weight and in this 46 remaining weights so fourth object is gone right 13 is gone so remaining will be 33 only。



![](img/49a4225c36cbb7e20b2683fefe9bc957_39.png)

33。These two weights are remaining， 56， those are the remaining weights I have。



![](img/49a4225c36cbb7e20b2683fefe9bc957_41.png)

Now， try including fifth object。Right。Now fifth object is 15 if I add 15 to this one this will be 43 and subtract 15 from this one。

 this will be 18。Again， this is exceeding， so kill this node with bonding function。

 now try without fifth object。Without5 object means。

 total weight will be 27 only and the exact object is not taken so take 18。

Right see we are not trying this further because that is not giving us the result。

 So that part will not give the result。 So that's for the benefit we are reducing our work with the help of this bond function。

Otherwise， well be generating two power and nodes。Now， next， in this one。Let us include sixth object。

 So if I include6 object， it is 18 and this， if I include 18。

 this will be 45 and this remaining is 0。 Again， this is exceeding。 kill this one。

Now shall I try without a sixth object？See if I try without6 object。

 this will be 0 and this is 27 only this is meaningless you don't have enough weight to make the weight 30 so this node should not be tried。

So we should have remaining weights enough to become exact value M， right。

 So one more morning function is that so far， what all you have included。



![](img/49a4225c36cbb7e20b2683fefe9bc957_43.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_44.png)

And。Remaining weights， I takes values from k plus 1，2。N should be greater than M。



![](img/49a4225c36cbb7e20b2683fefe9bc957_46.png)

So total weights you have and the remaining weights of what you have should be greater than M， see。

27 plus 0 is not greater than 30， so it is fruitless to generate this node。

 so we will not try this node at all。Now without six， we tried， without five without four over。

 now without three， we should try now without three， third object not included。

Then the weights will be 15 only and discarding third object， we will have a 46 as a weight with us。

Now try fourth object， so include fourth object。This is1 and 0 here again for1 and0。

 both we will try。 So fourth object is how much 13。 If I include 13， this is 28 and 13 is subtracted。

 so this is 33。Now， this is okay，28， we can go further Now， fifth object， if I include。

 then fifth object is how much 15， and this will be 4 3。This is exceeding and 15。

 if I subtract this will be 18。 So again， bonding function。

 this should not be taken because that weight is exceeding 30。 So without fifth object， we will try。

Without fifth object， total weight will be 8，28 only， and this is 18。 Now include6 object。

6 object if I include， then this will be 46。And this is 0，46 exceeding again。 Now， without6 object。

 we should not try because this will be 0 only and 28。 so this will not give the result。

Now without six， we tried， without five， we tried。 now without four， we will try now here。

 without four。So fourth object is not included， so the total weight will be 15 only。

 and this will be 33 without fourth object。 We are not considering it。

 So fourth object will remove 13。 So this is 33。Now fourth is not included。

 Next level is what fifth is included， fifth object is included， so include fifth object，15。

 fifth object is 15，15 plus 1530。Remaining is 18， we got the answer。We got one of the answer。

 I'll stop here if I continue further and I go on this side also without taking first object。

 without taking second object the tree expands like anything。



![](img/49a4225c36cbb7e20b2683fefe9bc957_48.png)

If you are go on doing it， then I am be getting more results。

 So one of the result is what first object included， second included， third， not included。

 fourth not included， fifth included。 This path has given the result。 So first and second included。



![](img/49a4225c36cbb7e20b2683fefe9bc957_50.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_51.png)

Third and fourth are not included。 Fth is included。 So definitely6 is not included。

 This is giving us the solution。 First object， Second object 15， then  fifth object 130。



![](img/49a4225c36cbb7e20b2683fefe9bc957_53.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_54.png)

There are more possibilities you see。

![](img/49a4225c36cbb7e20b2683fefe9bc957_56.png)

18 plus 2 12 plus 18 also gives 30 then 12 and 13 gives 25 right and this 5。

30 this also gives the result。

![](img/49a4225c36cbb7e20b2683fefe9bc957_58.png)

These three together gives the result。So like that there are more than one solution is possible。

 but we have seen just one solution。 The purpose was to see how backtracking work and what are the bonding function。

 what is a bonding function， what are the conditions of bonding function used in backtracking that was important and this will be a recursive algorithm again So backtracking algorithms or recursive because it's like defer search。

 This one then left and then left then left then like a preororators。



![](img/49a4225c36cbb7e20b2683fefe9bc957_60.png)

![](img/49a4225c36cbb7e20b2683fefe9bc957_61.png)

So if you say binary tree， then it's pre order or else it's a defafer search。

 so we follow defer search for solving。

![](img/49a4225c36cbb7e20b2683fefe9bc957_63.png)

Problems under backtracking。That's all about this problem。

