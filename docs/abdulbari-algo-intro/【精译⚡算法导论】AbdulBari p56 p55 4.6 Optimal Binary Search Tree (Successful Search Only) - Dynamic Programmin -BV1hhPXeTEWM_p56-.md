# 【精译⚡算法导论】AbdulBari p56 p55 4.6 Optimal Binary Search Tree (Successful Search Only) - Dynamic Programmin -BV1hhPXeTEWM_p56-

The problem is optimal binary search tree。In this video。

 I am going to talk about what is binary search tree？Then what does it mean by optimal binaryse。

 the problem？Then the dynamic programming approach for solving this problem。

 so Ill take an example and I will solve it。And I will also use the formula and show you how the formula is generated my focus will be on showing you how dynamic programming is working on this problem right instead of just showing you a shortcut how to fill up the table and get the answer。

Let us start with binary search tree。 See if the set of keys are given here。

 and the purpose is to search the keys。 If already I have the list of elements and I want to search some element。

So there are different search methods like linear search and binary search。

And also we have a data structure called binary tree Can we utilize binary tree for searching purpose Let us see。

 I will arrange these elements in the form of a binary tree。

 so I will create a binary tree out of these elements so Ill keep root as 40 and 20 as it left child and turn as it's left child and 30 here。

60。50。And 70。Now you can see that the elements are arranged such that for any node。

 all the elements on its left hand side are smaller。

 all the elements on its right hand side are larger for 4 T， all these elements are larger。

 And for this 60 this element is larger than this element is smaller Likewise here also So the benefit of arrange This type of binary tree is that it is useful for searching。

 S I want to search for a key element 50 then I can startnatch from here Is it 50 No 50 is greater than this one。

 So definitely it is on the right hand side， go here and check it is it 50。 No。

 the key value what I am searching is smaller than this one。

 so go on the left hand side Yes key is found。So that's how what is the time taken for searching a key element。

 the maximum time will be if the element is in the leaf。

 So what is the amount of time So this is height of a tree and the height of a binary tree is minimum login and this is minimum height only So the time taken for searching in a binary search tree is login。

 Now one more thing we have to consider here。 Well I am searching for the key like 50 I got the key。

 suppose I am searching for a key element that is 45 I it there。



![](img/99c6636cf37cf70017020f223bbede7a_1.png)

![](img/99c6636cf37cf70017020f223bbede7a_2.png)

No， if I search for it， 45 is greater and 45 is smaller than 60， 45 is less than 50。

 so my search will terminate here and the search is unsuccessful。

 so search may be successful or search may not be successful that is it may be unsuccessful when you are searching for the keys。

Now next I will show you for a given set of element how many different binary search are possible I have taken just three keys。

 let us see how many different binary search are possible so for these three keys。

10 as a root and 20 as its right child and 30 here。So，10。30 and 20 on the side。



![](img/99c6636cf37cf70017020f223bbede7a_4.png)

蹲啲。Then and。

![](img/99c6636cf37cf70017020f223bbede7a_6.png)

30 on this side。

![](img/99c6636cf37cf70017020f223bbede7a_8.png)

So for three keys， there are five different binary service trees possible。Right， so for n keys。

 how many different binary search key are possible2 and C and by n plus one binary searches are possible。

 So for three this will be2 into3 C 3 by 3 plus1 this will be5 so five different binary searches are possible for three keys for a number of keys these binies are possible。

 We will see what is the cost of searching it in each train。



![](img/99c6636cf37cf70017020f223bbede7a_10.png)

See the cost is dependent on the number of comparison required for searching for a key element。

 So in this tree， if I am searching for this key element， the cost is one。 if I search for this one。

 then I have to make two comparisons and if I have to search for this one I have to make three comparison。

 So what is the average number of comparison average number of comparisons are there are total three nodes so this is6 by3 that is2 Likewise。

 if I consider all of them， then this is one and this is2 and this is3 So this is one plus 2 plus 3 that is 6 by。

Three， that is true。And here it is one， and this is2 and this is 2。 So this is5 by3。

 So this is less than two， right， and this is one。 and this is two comparison and three comparisons。

 So this is6 by3， one comparison， two comparisons and three comparisons。 So this is also 6 by 3。



![](img/99c6636cf37cf70017020f223bbede7a_12.png)

![](img/99c6636cf37cf70017020f223bbede7a_13.png)

So you can see that out of these so five trees， one of the tree I got less number of。

Compars that average of comparison is less。 So that's what this is a balanced binary search tree。

 So why we got less is the height of this tree is less。

 So that's why this is balanced binary search tree。

So I have shown you what does it mean by hide balance binary search tree now let us come to the actual problem that is optimal binary search tree so in this problem we consider that if these are the keys available then we also consider what is the frequency of searching of those keys if the keys are having some frequency of search。

 let us say the frequency of searching 10 as a 3 and this is2 and this is5。



![](img/99c6636cf37cf70017020f223bbede7a_15.png)

So this means that all the keys will not search them with the same frequency。

 some keys are there that are more frequently used so we search them more frequently more oftenly and some are rarely used so like that who is having highest frequency that is having highest frequency then if the frequencies are defined for each key then what will be the cost so I want to know which a tree organization will be optimal or better。

So let us check them。See the number of comparisons required for this one is one。

 but its cost is three frequencies is 3 and this frequency is 2 and this frequency is 5。

 So how much this will be 15 plus 4 plus 3，18。

![](img/99c6636cf37cf70017020f223bbede7a_17.png)

And this is a3， and this is a2。 This is5， and this is a2。 So this is 10 plus 6 plus。3， so this is 19。

And here the frequencies are this is 2 and this is the number of comparisons are 2 and its frequencies is 3。

 so this will be3 into2 and the number of comparisons required that is the level is a 2 and its frequency is 5。

 so this is 10 plus 6 plus2， this is 18。And here it is a five， then 10， that is a three。

And this is two。So this is5 plus 6 plus 6。

![](img/99c6636cf37cf70017020f223bbede7a_19.png)

So， this is 17。And this is five into， this is2。And this is 3。 This 9 plus 4 plus 5，18。



![](img/99c6636cf37cf70017020f223bbede7a_21.png)

Now the cost of the trees are different， you can see that this tree organization has given us best resultsle so that is optimal binary search tree for these three keys。

 though it is not high balance， this was high balance now the height is more but based on the frequencies that cost of that binary search tree minimum。



![](img/99c6636cf37cf70017020f223bbede7a_23.png)

So that's what the problem is if the keys are given and the frequencies are given we have to find out which tree organization will be optimal based on the frequencies now I will take a problem and I will solve it using dynamic programming approach here I have keys 10 203040 and their frequencies are given here。



![](img/99c6636cf37cf70017020f223bbede7a_25.png)

![](img/99c6636cf37cf70017020f223bbede7a_26.png)

![](img/99c6636cf37cf70017020f223bbede7a_27.png)

For finding out optimal binary history for these set of keys I have created a table here。

 I will filling the values in this table， and then that will help me to generate a table。



![](img/99c6636cf37cf70017020f223bbede7a_29.png)

Here the keys are 1 to 4 Now the table you can see that it is starting from0 onwards right but the keys are starting from1 onwards I have taken from1 onwards this is from0 onward so that it is suitable for formula。



![](img/99c6636cf37cf70017020f223bbede7a_31.png)

Let us see how to solve this problem。 Let us call these rows as I and columns as J。



![](img/99c6636cf37cf70017020f223bbede7a_33.png)

Now， first of all， we'll find out those values which are。



![](img/99c6636cf37cf70017020f223bbede7a_35.png)

J minus I is equals to0。So for which values it will be J minus， I will be 0。 This is 0-0 is 0。

1-1 is also 0，2-23-3。4 minus-4。All these are0， so it means I'll find out the cost of0 comma 0 and1 comma 1 and all this。

 so it means I'll fill up the diagonal and for the diagonal I'll first fill up with all zeros。



![](img/99c6636cf37cf70017020f223bbede7a_37.png)

![](img/99c6636cf37cf70017020f223bbede7a_38.png)

![](img/99c6636cf37cf70017020f223bbede7a_39.png)

![](img/99c6636cf37cf70017020f223bbede7a_40.png)

This is the fastest step。Now I will find out this a diagonal， so in this one。

 J minus i value should be 1。

![](img/99c6636cf37cf70017020f223bbede7a_42.png)

J minus r equal to1 then what it should be。 So this is 1 minus-0 is 1，2-1 is 1，3-2 is also1。

4 minus-3 is also1。 so this is0 comma 11 comma 2 and2 comma 3，3 comma 4。

 So I'll find out the cost of all those cost of0 comma 1 cost of1 comma 2。



![](img/99c6636cf37cf70017020f223bbede7a_44.png)

Cost of2 comma 3 and cost of 3 comma 4。Now we will start filling the values now see0 comma1 means I'll be considering just1 k that is key1。

10。 What is frequency4， so the cost is4。And C of1 to 2 just ignore this first value and take this one so this is the key second key。

 second key is 2 and the cost is 2 so yes this is 2 and this is third key。

 third key is 30 and its cost is c that is frequency is C so the cost is6。

And this is 4 T and its frequency is 3， so the cost is 3。 So 4，2，6，3。 So I got the answer as 4，2，6，3。

 So I have considered just one node where J minus I equal to1。



![](img/99c6636cf37cf70017020f223bbede7a_46.png)

![](img/99c6636cf37cf70017020f223bbede7a_47.png)

Now， next we' will go for J minus I equal to 2。Now， when this J minus I will be equal to 2。

 So this will be 4 2-0。 This is 0 comma 2 and 3-1。 This is 1 comma 3 and J will be 4 and I will be 2。

 So this is 2 comma 4。 So for these things。J minus I value will be2。

 so it means I'll be considering two keys， so I will consider first key and second key first so that means I will take this one first cost of0 comma 2 I will find out this is0 comm 2 right I'm considering two keys So what are those two keys just ignore 0 start from1 So key 10 and key 20。

 What are their frequencies4 and2。

![](img/99c6636cf37cf70017020f223bbede7a_49.png)

![](img/99c6636cf37cf70017020f223bbede7a_50.png)

![](img/99c6636cf37cf70017020f223bbede7a_51.png)

Let us see using these two keys only what is the minimum cost binary search tree or the optimal binary search tree I can generate just by using two keys so for two keys what are the possible binary search trees 10 and this is 20。

That is first is the root and this is second one is the root， so 10 will be on this side。

So what is the cost of this。 So directly I will calculate， see the frequencies4 and this is one time。

 and this is frequencies2 and the number of comparisons are 2。

 So how much this is 4 plus 4 it is 8 and this is2 into one and this is 4 into 2。

 So one comparisons required for this and two comparisons required for this So this is how much 8 plus 2。

 So this is giving 10 and this is giving 8。 So which one is minimum this one is minimum minimum costs is 8 and which key is forming a root to1。

 So I will fill up this value 8 and the root is 1。

![](img/99c6636cf37cf70017020f223bbede7a_53.png)

![](img/99c6636cf37cf70017020f223bbede7a_54.png)

Now， I will show you how I can apply the formula here。 Now， before showing in the formula。

 I will use one value that is weight of。

![](img/99c6636cf37cf70017020f223bbede7a_56.png)

0，2，4， for example。Then this means some of all the frequencies from。1 to4。 actually。

 we have frequencies from one to4， but we'll write from0 to 4 right we are starting from 0 so that we can make a formula So c of0 to 4。

 once all some of all the frequencies from one to4。 So let us see the formula。

 See this is the cost is 8 I got Now here I was taking root as1。

 So this is C of0 comma 0 on the left hand side then C of1 comma2 on the right hand side。

 plus weight of。

![](img/99c6636cf37cf70017020f223bbede7a_58.png)

0 to 2， right。 So this is0 to，2。Let us check from the table what we got。

 will we get this value as 8 or not， let us check c of0 comma 0， how much0。



![](img/99c6636cf37cf70017020f223bbede7a_60.png)

Plus。C of1 comma 2。 C of1 commma 2 is how much2。2。Plus weight of0 to2 minutes I should add all the frequencies from  one to 21 and2。

 So already I have this  four plus2， so 4 plus 2。 so answer is8。

Now how the same formula is applicable on this site， see this one is I am taking two as a root。

 so one on the sides， so c of0 comma 1 plus c of2 to2 plus weight of0 to 2 so from the table let us see 01 01 is how much4。



![](img/99c6636cf37cf70017020f223bbede7a_62.png)

![](img/99c6636cf37cf70017020f223bbede7a_63.png)

Plus C of2 comma2 is 0 weight of all these that is 4 plus 2 S 6。 So how much this is 10。 Yes。

 we got the same answer。 So either I just checked them with the height。

 I am getting the same answer or else I am using the formula。

 So I'm not showing the complete formula just I am applying it here。

 so which has given us the minimum result 8 so that I have written there。



![](img/99c6636cf37cf70017020f223bbede7a_65.png)

Now I have to find out one comma 3。C of1 comma 3。 Just ignore 1。 So start from 2。 So2 to 3。

 So I will be taking keys 2 and 3。 other1 and all finish。 So 2 and 3。

 because every time will be taking just two keys。 So keys are 20 and 30。

 and then frequencies are2 and 6。 Now what are the different race possible from this one。

 I can make this second one as a key root。 So this side will be 30。

 or I can make third one as a root。 So this side will be 20。



![](img/99c6636cf37cf70017020f223bbede7a_67.png)

![](img/99c6636cf37cf70017020f223bbede7a_68.png)

Now， what are the costs for this one， This is two into one。

 and the number of comparison for this one will be 2。 So this is 6 into2。 So how much this is。

 So 2 plus 2 L is。14 and this is one into six。And this is two into two。 So this is 4 plus 6。

That is 10。 Who became root here。 Third key。 This is the second key， and this is the third key。

 So third key became a root here。 So this is 1 and third key became root。



![](img/99c6636cf37cf70017020f223bbede7a_70.png)

![](img/99c6636cf37cf70017020f223bbede7a_71.png)

I will not use the formulala。 although we have shown you。 Now， let me finish another value Also。

 Now next key is this one。

![](img/99c6636cf37cf70017020f223bbede7a_73.png)

![](img/99c6636cf37cf70017020f223bbede7a_74.png)

This is2 comma 4， so2 comma 4 C of2 comma 4， so ignore2 will be taking third key and fourth key。

 So third key is how much 30 and its frequency is 6， fourth key is 40 and its frequency is 3。

Now what are the trees possible So if I make 30 as a root。

 then 40 will be on the right hand side or else 40 as a root， then 30 will be on the left hand side。

 So two different trees are possible out of this right let me put the course directly So the frequency of this one is 6 and the number of comparison require 1 and this is a 3 and the number of comparisons are 2 so this is 6 plus2。

6 and that is 22。This is 3 into 1， and this is 6 into 2。 It cost is 6。 So this is 2 plus 3。

 That is 15。 So who has given us the minimum result。2 has given us the minimum result。

 And what is the key here， Third， Third one is the key here。 So answer is 2 well。



![](img/99c6636cf37cf70017020f223bbede7a_76.png)

And3 is the key。

![](img/99c6636cf37cf70017020f223bbede7a_78.png)

So three will become a root， third key will become a root。



![](img/99c6636cf37cf70017020f223bbede7a_80.png)

So that's it。 We have filled up this diagonal where every time we were considering two keys。

 Now we have to fill up this diagonal and we have to consider three keys at a time。

 Now J minus I equal to 3。 So what are the possibilities。 J is a3 and I is 0。 So this is0 comma 3。

 and J is4 and I is 1。 So this is one comma 4。 So these are the two possibilities。

 So I should consider first three keys。 and then what that is 1 to 3 and then2 to 4。 So 3，3。

 I should select So let us see if I select this first1， that is 0 to 3。

 So just ignore 0 and take the keys。 So the keys are 1020 and 30 first， second key and third key。



![](img/99c6636cf37cf70017020f223bbede7a_82.png)

And the frequencies are 4，2，6。Now， what are the trees possible。With these three。

If I take 10 as a route。Then on this side， I can get。20 and 30。

 This is one possibility or 10 as a root， then 30 and 20。 This is another possibility。

 Just 10 as a root。 So 10 is one as a root， right， one as a root。 Then if I take two as a root。

 then what are the possibilities，20 is here。 And on the left hand side is 10。

 and the right hand side is 30。 If I make 30 as a key that is root here，3 as a root， third value。

 then 30 on this side， then left side， it can be 2010。Or 30 years root。10 on the right side 20。

So with the three keys by selecting any one of the key as a root。

 there are total five different trees possible。 Now out of this， which one is minimum。

 which one is minimum。 So for this， I will use the formula directly， right。

 I will not calculate them。 So formula if you remember this one， some of the frequency。

 So we have to take from 0 to 3。 So if I find out weight of 0 to 3 directly。

 I will find out how much it is 4 plus 2 plus 6。 So this is 12。 So let us use this tool every time。

Alright， so what is the cost of this side and this side and this side see here who is root。

 one is root， so if one is root， then this will be c of0 comma0 plus c of1 comma。3。And plus weight。

 weight is how much to L， I'll directly write on this one。Then for this when two is there as a root。

 so this is0 comma 1 plus C of2 comma 3 plus22。And on this side。

 C of0 comma 2 plus C of 3 comma 3 plus 2 L out of this。

 I have to select any one of them that is giving me minimum， so that will the cost of C of0 comma 3。

So you have0 comma 3。 So0 comma 0。 That is 0 plus one comma 3。 How much 10。Plus 12，22。0 comma 1。

 how much4 plus2 coa 3， how much2 coa 3 is 6。Plus21。 So this is 22。



![](img/99c6636cf37cf70017020f223bbede7a_84.png)

Then zero comma2， how much？8 plus 3 comma 3，0 plus 2 well。 This is 20。 So 22， and this is also 22。

 Which one has given minimum result this is 20。 So0 comma 3，0 comma 3 is 20。



![](img/99c6636cf37cf70017020f223bbede7a_86.png)

![](img/99c6636cf37cf70017020f223bbede7a_87.png)

![](img/99c6636cf37cf70017020f223bbede7a_88.png)

And which route has given us answer 3， Third route has given us the answer。

 So this is third route has given us the answer。 So third key should be a root。

 I have to find out next。

![](img/99c6636cf37cf70017020f223bbede7a_90.png)

![](img/99c6636cf37cf70017020f223bbede7a_91.png)

Value this one for three keys。 And that is one comma 4。 C of1 comma 4。 So what are the keys。

 Just ignore one and start taking the key from two onwards。Second key。

 so that is 20 and the third key that is 30，4 key， 40， and the frequencies are 2，6 and3。

Right so I will not draw all possible trees now directly I will use the formal and solve it。

 So for that I will find out the weight So w of1 comma 4 So in this is skip1 and remaining we have to find out。

 So it' is nothing but some of all these frequenciesancies So2 plus 6 plus 3 So this is 11。Now。

 let me use the formula。 C of one comm of four is minimum of。See off。Second is the root。

 so1 comma1 plus C of2 comma 4。Our C of third key is a root， so1 comma 2 plus c of3 comma 4。

 fourth key is a root C of1 comma 3 plus c of4 comma 4。And at last。

 I have to add that weight that is 11。 So let me write on these values。

1 comma 1 is 0 plus how much this is2 comma 4，2 comma 4 is 12。0 plus 12，1 comm2 is 10，1 comm2 is 2。

Plus，3 comma 4 is。

![](img/99c6636cf37cf70017020f223bbede7a_93.png)

3。这个意。1 co 3 is a 10。Plus，4 comm of 4 is 0。 So which one of this is minimum， this is minimum。

 So this is 5 plus 11 is 16。 So cost of this one is 16。

Right so answer is 16 and who gave this which was the root here here the root was2 and here the root was 3。

 this was the root， so3 is a root again。

![](img/99c6636cf37cf70017020f223bbede7a_95.png)

Now next J minus I equal to 4 then I should consider four keys so for this possibility is 04 minus 0 that is 0 comma 4 so finally I have to find out this value last value so for that all possible binary search trees from that I have to pick up the best one that' is going to give me a optimal cost。



![](img/99c6636cf37cf70017020f223bbede7a_97.png)

Now， I will directly use the formula and solve that one。 So cost of。0，2，4。So ignore0。

 I have to take key 1，2，3，4 that are 10，20，30 and 40 and their frequencies are 4，2，6，3。

 then weight of0 to 4 will be how much add all these So this is 15。

And the cost of 0 comma 4 will be minimum of。If I consider first key as a root。

 then this is0 comma 0 plus C of1 comma 4。Then if I consider this second as a root。

 then this is C of。0 comma 1 plus C of second as the roots are 2 to 4。Then third one has a root。

 So C of0 comma。2 plus C of3 comma 4。The last one is c of0 comma 3 plus c of4 comma4。

 and then in all these I should add this weight that is 15。Right。

 so I will write down their values here， so this is0 plus1 comm of4 is how much one comm of4 is 16。

Plus，0 commma 1 is 4。

![](img/99c6636cf37cf70017020f223bbede7a_99.png)

Plus。2 comma 4，2 comma 4 is 12，4 plus 12。 This is0 comma 2。 that is 8。



![](img/99c6636cf37cf70017020f223bbede7a_101.png)

![](img/99c6636cf37cf70017020f223bbede7a_102.png)

And 8 plus 3 comma 4 is 3。注意。0 comma 3，0 comma 3 is 20。Plus4 comm of4 is0 only So of this。

 which is giving minimum result。 This is 16 and this also 16， and this is 11 and this is 20。

 So minimum answer is 11 plus 15。 and who is a root here，3 is a root here。

So answer is cost is  26 and3 is0 root。 So this is。



![](img/99c6636cf37cf70017020f223bbede7a_104.png)

26 and three is a road。

![](img/99c6636cf37cf70017020f223bbede7a_106.png)

So the cost of optimal binary search is 26 and root is 3。 Now， I have to generate a3。

 Let us generate a3 from this data。 This is 0 comma 4， and the root is 3， so for。



![](img/99c6636cf37cf70017020f223bbede7a_108.png)

![](img/99c6636cf37cf70017020f223bbede7a_109.png)

Root of 0， comma 4。Is 3 so if I take third key as a root， this is a key number。

 not a key that is 30 is a key is a key number then on this side what we will get root of0 to 2 and this is root of3 to4。

Now，0 to 2，0 to 2 is this one。 So who is a root here，1。 So for this， root is one。Then on this side。

 what I get root of when one is the root0 to0 and on this side root of one to2。



![](img/99c6636cf37cf70017020f223bbede7a_111.png)

Then who is root of 1 to 2，1 to 2 as this one，2。 This is the second key， right。

 This is the second key。 first key and the second key。 So that is second key is the root。

 So here is the second key is the root。

![](img/99c6636cf37cf70017020f223bbede7a_113.png)

Then on this side what it will be root of one to1 and this side root of2 to 2 so for this answers are0 only now three to4 so what is3 to43 to4 is this one this is fourth key so this is fourth key and on this side root of three to3 and root of four to4。



![](img/99c6636cf37cf70017020f223bbede7a_115.png)

![](img/99c6636cf37cf70017020f223bbede7a_116.png)

So for this， all the values are0 only。So this is a three， so who should be a root。

 30 should be a root and the left hand side should be 10 right side of this one should be 20 and the right side of this is 40。



![](img/99c6636cf37cf70017020f223bbede7a_118.png)

That's it， this is the optimal by the research tree for this。

 the cost of searching will be minimum based on their frequency of search。



![](img/99c6636cf37cf70017020f223bbede7a_120.png)

Now finally， I will write on the formula that I was using。Cost of I comma J is equals to minimum of。

Goov。I comma K -1 plus cost of K2 J。

![](img/99c6636cf37cf70017020f223bbede7a_122.png)

Plus， weight of Ia J。

![](img/99c6636cf37cf70017020f223bbede7a_124.png)

Where K takes the values greater than I less than equal to J。So the route was not starting from I。

Afterwards， so if this is0 comm of4， so youll start from1 onward ignore0。 that is the meaning。

 So this is the formula for optimal binary searchty and the same formula I was using it for filling the table。

 So that's all about optimal binary search problem。



![](img/99c6636cf37cf70017020f223bbede7a_126.png)