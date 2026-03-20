# 【精译⚡算法导论】AbdulBari p50 p49 4.3 Matrix Chain Multiplication - Dynamic Programming -BV1hhPXeTEWM_p50-

The problem is math exchange multiplication。In this video I'll explain you what ismatic multiplication problem then what does it mean by Ma chain multiplication then I'll show how to solve this by applying dynamic programming then we will come up with the formula that is used for solving this problem and also I will discuss the time complexity so let us start with matrix multiplication。

First of all， if you have a matrix， two mattresses and you want to multiply them and their dimensions are suppose phi crosss 4 and four crosss 3。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_1.png)

The condition for multiplying two mattic is the number of columns of the first matrix should be equal to number of rows of second matrix。

 then only multiplication can be done。If I write other way， B cross a。

 then their dimensions 4 cross 3 and phi cross 4 will be there。

 they cannot be multiplied because these are not same。 So A cross B if it is possible。

 then B cross A is also possible， iss not necessary。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_3.png)

When you multiply the resultant matrix will be C and the dimension of the resultant matrix will be phi cross 3 number of rows of first one。

 and number of columns of last one， phi cross 3。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_5.png)

So it means how many elements will be there。 So 15 elements will be there。

Then for getting each element what we are supposed to do， multiply fast row width first column。

So how many elements first row will have four elements， and this will also have four elements。

 that is four。 you can see。 So total four multiplications I have to do for getting this one single element。

 Then again， first row with second column I get this element。

 So it means for getting each element of the same matrix。 I have to make four multiplications。

 So this is into 4。 So finally， it is like this5 into 3 into 4。 This is 60。

 So it means for generating the same matrix。 I have to make 60 multiplications 5，4，3。

60 multiplications are required。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_7.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_8.png)

Bike。So this about the cost of multiplying two mattresses depends on the number of multiplications that you are performing。

 So how to obtain the number of multiplications this or we can find out the number of multiplications。

Now coming to the problem herere mates are given and the dimensions are given they are arranged such that they can be multiplied because these are same you see and the66 is same two two is same so they can be multiplied。

But the question is not to multiply and get the answer。 No， we don't want the answer for multiplying。

 I cannot multiply all of them together。 I have to take a pair at a time and multiply。

 So the question is which pair I should select such that the total cost of multiplying all of them is minimum。

 So the problem is not to multiply them， the problem is to know how to multiply them。

This is matrix multi chain multiplication problem。 It means how I should parenthesize them。

 Shall I do it like this， A1 is multiplied with A2， and that result is multiplied with A3。

 and that result is multiplied with a4 shall I do it like this or A1 and A2 are multiplied and separately a3 and A 4 are multiplied。

 Then their result are multiplied together。 Which method I should follow。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_10.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_11.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_12.png)

See， like this。 How many possibilities are there。 There are many ways I can parentheize them。

 So let me know total how many ways are there。 So if I show this in the form of a tree。

 a 1 is multiplied with a2 then a 3 is multiplied with a 4。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_14.png)

Then their results are multiplied， so it's forming like a tree。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_16.png)

Right，If you see this is formula like3 with how many nodes，3 nodes。

 because there are three multiplication out of foures。 So three nodes we are getting。

 So for this one， if I represent， then this is a 1 is multiplied with a 2。

 and that result is multiplied with a3。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_18.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_19.png)

And that result is multiplied with a4。See， this is representing that parent。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_21.png)

That tree is representing this parentheization。 So like this with three nodes。

 how many different trees are possible。 So it means how many different parentheizations are possible C4。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_23.png)

And nodes 2， N， C， N by N plus one binary trees are possible。 Now， for three nodes。

 how manyinate will be。 if I substitute 3 here， then I get answer 5。

 So it means these mattresses can be multiplied in five different ways。

5 different ways they can be parenthesized。 Which 1 I want， I want minimum。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_25.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_26.png)

So shall I try all five and calculate their total cost and pick up the best one。No。

 I don't have to do it like this。No doubt， I have to try all possible five。

 but I will follow easy method that is given by dynamic programming。😡。

So dynamic programming says that you try out all possibilities and pick up the best one。

 So how to try all possibilities， it is difficult for every problem。

 even they may be missing some possibility also so without missing anything how to get the perfect answer by trying all possibilities。

 Now we will see how to solve this problem。Let us solve this problem using dynamic programming as dynamic programming uses tabulation methods。

 So these are the tables I have。 I will call this with the name M。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_28.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_29.png)

And this withname S。Any name you can give M is the name I have taken。Now。

 we will fill up the table and intulation method will follow bottom of approach。

We should take the smaller values and fill the table first。 So actually。

 we are talking about multiplication。 So let us take just a1。Not multiplied with anything。 Just a 1。

 So what is the cost of multiplication It' not multiplied with anything。 So the cost is 0。

 So when I say a1。 So let me call it as M of1 comm of1。 So M of one comm of1 is。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_31.png)

0， then。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_33.png)

If I take a2， just a2， then this will be M of2 comma 2。 And there is nothing multiplied。

 So there's also 0 same way M of 3 commma 3 is 0，4， commma 4 is 0。 So this is small problem。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_35.png)

Let us find out M of1 comma 2。M of1 comma 2 means I'm multiplying two mates that is 1 to 2。

 So a 1 with a2。Then what are the dimensions of a1，54 and dimensions of a2，4，6？

So what will be the total cost of myplication，5 into4 into6。This is 1，20。

So A M of1 comma 2 that is multiplying this pair of matrixes 120。

 So here I write 120 first value and for this。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_37.png)

1 with the two， I multiply， so I take it as1。 So at same one comma 2， I will write it as one。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_39.png)

Why I am writing that I will explain after some time。Now， next， I will try。A 122 is over， not2 to3。

 I'll select this pair first I selected this next I'm selecting this after that I'll be selecting this so2 to 3 I will select so M of2 to3 that is a2 with a3 what are the dimensions4 comma 6 and 6 comma 24 into 6 and 6 into2。

So， this will be 48。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_41.png)

Right， so2 come 3 M of2 co 3 is 48。 So Im filling this diagonal。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_43.png)

Next， I'll be selecting a 3，4。 So here I will write on M of3 comma 4 will be multiplying these two mates。

 so their dimensions are 6，2 and 2，7。Right， so6 into 2 into 7 is。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_45.png)

84， so 3 comma 4，3 comm 4 is filled with 84。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_47.png)

So now I have the cost of multiplying pair of mat and there are different pair possible I have taken all possible pairs。

Now two two mat were selected now we'll select3 matrix so that is I will find out a of 1 comma 3 M1 comma 3 means a1 a2 and a3。

 so when I consider all three。Then there are two possibilities。

1 is this is multiplied the result of this or first A1 and A2 are multiplied and their result is multiplied by a3 there are two possibilities。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_49.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_50.png)

Now， what is the cost of what are the name？What are the dimensions of this p cross4 and this is four cross 6。

62 and544，662。Now， what is the cost of a of1， This is nothing but M1 comma 1。Plus。

 what is the cost of this M22 3，22 3。 Then what is the cost of this multiplication。 See。

 this is already done。 We know the cost， right，2coma 3， I have written。

 I want to know only this multiplication， just one multiplication。 So this depends on the dimensions。

 So what are the dimensions，5 and 4。2， so 5，4，2。 So the result of this will be  four cross 2。

 So 5 into 4 into 2。 So this will be 5 into 4 into2。 Then what about the site， this is。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_52.png)

M of one comma 2 plus M of this is just 3。 So write the three comma 3。

 Then plus what are the dimensions。 See， the final dimensions of this one will be these two。

 So5 into 6 into 25 into 6 into 2。 Now， M of one comma 1 is how much 0。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_54.png)

Plus M of 2，3，2，3 is 48。Plus， how much this is。40。Then M of 1 comm 2，1 comm 2 is 120。Plusus。M of 3，3。

3 comm3 is0 plus how much this is。60。Right， which one is minimum， this is 88， and this is 1，80。

 This is minimum。So M of1 comma 3 is 88， M of1 comma 3 is 88。Now， here， there were two possibilities。

 We have tried this one versus this one and took minimum out of these two， right。

 we have taken minimum of these two。 So who has given minimum， This one was this side and 2，3，4， 2。

3 was that side。 So one has given us the result。 So for this value。 I should write one here。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_56.png)

I should find out M of2 comma 4 means I should select these three。

 So M of2 comma 4 in this there are two possibilities a2 multiplied with the result of this one or a2 multiplied with a3 and the result with a4。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_58.png)

See this way， I am trying all possibilities， but easy method because the result I can get it from the table from the table。

 I am getting the values， and I am filling the table。Let us check this，4，6，6，2，2，7，4，6，6，2，2，7，4，6，6。

2，2，7。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_60.png)

Now， what is this one。 This is M of 2，2 plus this side is M of 3，4 plus。

What will be the product of this one。 See， we will get this as a dimension， right。

 And these two are same。 So they are multiplied 4 into 6 into 7，4 into 6 into 7。

Then what about this side， This is M of 2 to 3 plus M of4 to 4。Plus。

The result of this one will be this one。 And as these two are same。

 then final will be 4 into 2 into 7。 So 4 into 2 into 7。Let us see how much this is M of2 co 2。

2 co 2 is 0。Plus， M of 3，4。 M of 3 comma 4 is 84。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_62.png)

Then this is 168。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_64.png)

Then M of 2，3，2，3 is how much 48。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_66.png)

48 plus M4，4 is 0， plus 56。So which one is smaller。This is 252 and this is one not4。

So which one is minimum，1， not 4 is minimum。 So the answer for this one is1 not 4。 That is2 co of 4。

2 co of 4 is 1 not 4。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_68.png)

And who gave this value， See this side is 2，3， and that side is 4。 So answer is 3。

 So 3 has given us minimum re。 I have to find out this final value。 that is all four。

 So we tried two then 3 at a time， No 4 at a time。 Now M of one come of 4。

 So now I will use the formula and show you。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_70.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_71.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_72.png)

Use the formula。M of。1 comm 4 S minimum of。M of one comma1 plus M of。2 co of 4， see 1。

 come of one decide， then 2 to 4 remaining。 plus what will be the cost of multiplying them from here。

 I will see this is  one， And these are together 2 to 4。 So this is 5 into 4 into 7。

 So 5 into 4 into 7。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_74.png)

Comma， I have to take the minimum。 This is one possibility。1， A1 is the side and all three that side。

 So I wrote here1。 then again， M of。1 comma。 See that time I wrote one here。

 Now I will write two here。 So then plus M of this will be 3，4。

 So this means 1 to 2 this side and 3 to 4 that side。

 So 2 separate plus what will be the cost of this  one，5，4 and 7， sorry，5，6 and 7。

 So 5 into 6 into 7。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_76.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_77.png)

Then there are two more possibilities。Here， right。 M of one。 See first time1。 So decide2。

 Then next is2。 Now it is 3。1 comma 3 plus M of 4 comma 4。 So 1，2，3 decide and for that side。

 So this is 5 into 2 into 7。 So 5 into2 into 7。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_79.png)

That's it。 So what are the possibilities。 I have only one this side，3。

 that side or two this side to that side or three， this side and one that side。

 So all possibilities I have taken here， I have to find out what is the cost of this one。 See。

 this is 0 and 2 comma 4 is how much，1 not 4，1， not 4， And this is for p。

And this is M of1 comm2 is how much 120。Plus，3 comma 4 is 84。Plus。Doden。

M1 comma 3 is how much1 comma 3 is 88。 This is 88。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_81.png)

Plus，4 comma 4 is 0， and this one is 7 and0。Not of this， which seems to be smaller。 This is 200。

 and this is 3，400 above。 and this is。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_83.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_84.png)

1，58， Yes， this has given us a smaller result。 So the result is 1，58。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_86.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_87.png)

Then on what value I got this answer 3。 So this is 3。That said， I have filled the table。

Right so finally I have used the formula slowly I have built a formula。Right， so finally。

 I have built a table。 the two tables already。 Now。

 we need to know the answer before knowing the answer， I will write on the formula。 say here。

 if I say M of I comma J。Minimum of。What is this？I'm off。I to some K。

 So you can see that this was one or two， then  two， then  three， then 3 and 4。

 So M of I comm my K plus M of。K plus 1 comma J。 This is the formula I use。 This one commma 1。

 So 2 to 4，1，2，2，3，2，4。 So 1，2，3，4，2，4， I to K， K plus 1，2 J。Then plus this was getting multiplied。

 This are getting multiplied。 So how I should represent them。 Now， from the example， I'll show you。

 So if I say this is a dimension 1。 then this is a dimension 2， then this is a dimension 3。

 then this is a dimension 4， then this I have to score it as a dimension 0。

 like there are four matrixes So total 5 dimension。 So I should start from 0。 So otherwise。

 if I start from1， I will end up at 5。 but the last matrix is 4。 So let us start from 0， dimension 0。

12，3，4。 So when I am multiplying any matrix。 C when I am multiplying the matrix that is I J2 k plus12 J。

 So I should take I。 So if I is this matrix， then I should take this one， I -1。

 So this is D of I-1 into D of k。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_89.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_90.png)

Into D of。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_92.png)

G。

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_94.png)

This is the foreign law。Now， let me follow this table， the one which was giving minimum。

 I was writing them here。 So the first topmost one， what it says3。 So it means this site。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_96.png)

Then this is separate。 So this is one parent This is at a3 This a split。 K is 3。 So 1。

2 3 is this site and for that site。 right， Now， what about 1，2，3。 So if I check 1，2，3， it is 1。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_98.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_99.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_100.png)

1 to3 is giving one。 So one this side， So a 1， this side。

 then what that side is remaining a 2 and a 3。Then already this outer bracket was there， then a4。

That's it。2， to 3。 So 22 3 gives us what2 only。 So there are only two。 So let them be as it is。

 So how it looks like。See， a2 and a3 are multiplied first and we get this result。

 then a1 is multiplied with their result， right， then a4 is multiplied with their result。

This is how the multiplication will be done。This is a tray we got or this ship we got。Right。So。

 there is a solution。Now let us check what is the time complexity So actually we are preparing a table but we are not preparing entire table we are preparing half of the table so also you can say n into n plus one by two number of elements we are generating。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_102.png)

![](img/5f79e634b4fc3da4b20cd9dae262e4f9_103.png)

Right， see， this is one， then2， then 3， so on。 So N in n plus1 or n minus-1 else you can say because this diagonal is all 0。

 So whether you want to consider or not。 So anyway， this is going to be n square。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_105.png)

Approximately n square， right， if you want to write notation， it is n square。

But each element how we are getting， we are calculating all and finding the minimum。

 So how much time it takes at the most N。 So this is into N。

 So the time complexity of this one is N Q。 So this is K of N Q。

So the time complexity for mat chain multiplication is N cube。

 multiplying the mattices is also in cube and solving the parentitization problem of mattices is also N cube。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_107.png)

Then lastly， I'll show one more thing。This table， I'll draw it like this。Right。

 because we are not using this portion。 So fast row， I will write like this。 This is fast row。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_109.png)

Right， then this is second row。Then this is third row and this is4 row。So these are rows 1，2，3。

 So this is 1，2，3，4。 So if I say I is for rh and J is for column。 So these are I。

 So I'll write I here， right that side from that side if I see。Then these are columns。

 So these are columns。 So this is 1，2，3，4。 So these are J。Then what is the value here 158。

 and this is 88 and1 not 4 and 120，48 and 84，0，0，0，0。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_111.png)

This is how a table is prepared。 Instead of drawing it like this and half unfilled。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_113.png)

Are empty。 We can also draw it like this。 So just turn is that side。 you get the table。



![](img/5f79e634b4fc3da4b20cd9dae262e4f9_115.png)