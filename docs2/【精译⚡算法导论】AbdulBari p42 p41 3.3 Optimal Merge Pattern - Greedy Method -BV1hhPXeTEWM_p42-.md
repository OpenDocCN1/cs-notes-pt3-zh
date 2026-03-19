# 【精译⚡算法导论】AbdulBari p42 p41 3.3 Optimal Merge Pattern - Greedy Method -BV1hhPXeTEWM_p42-

Yeah， the problem is optimal merge pattern。Again， this problem can be solved using greedy method。

 and if we know how to solve this problem， we can also understand half man coding。

So let us talk about this one before knowing what is optimal merge pattern。 First of all。

 we should understand merging。

![](img/e7eadf1ca1a87342254ee976138aaaa8_1.png)

Let us quickly understand merging。See if I have a list A and B with some set of elements。

If I have two sorted list， then I have to combine them and get a third sorted list。



![](img/e7eadf1ca1a87342254ee976138aaaa8_3.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_4.png)

2 sorted lists are there。 I have to combine them。 So the process simple。

 What we do is we compare the first element of each， whichever is smaller。 We write on that。

 and then we'll move to the next element and compare these two。 and 5 is smaller。 We write that。



![](img/e7eadf1ca1a87342254ee976138aaaa8_6.png)

8 is a smaller。9ine is a smaller。11。Nella is a smaller。Then，16。



![](img/e7eadf1ca1a87342254ee976138aaaa8_8.png)

能本题。So quickly， I have shown you the elements are compared one by one。Right。

 so one one element from each side is compared， whichever is model that is written here。

 and we get a single sorted list。 So margin can be done only on sorted list。

How much time it has taken for merging if I say this is M and this is n。

 then the total time is m plus n。

![](img/e7eadf1ca1a87342254ee976138aaaa8_10.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_11.png)

If I count in terms of elements， four elements， four elements， and how many I got eight elements。

So the total time taken depends on the size of the list。Now， let is extend the problem。

 What happens if I have more than two list。

![](img/e7eadf1ca1a87342254ee976138aaaa8_13.png)

Let us look at it。Now， here I have four list given and their sizes are given。

 I have not taken the elements。 I am saying that this list is having six elements and is having five elements and so on。

 I have to merge these four list。 I can merge them together also。

 that will be called as four merg or M merg。 No， I want to follow two way merg。

 So at a time I want to merge only two list。 So let us see how merging can be done。



![](img/e7eadf1ca1a87342254ee976138aaaa8_15.png)

I'll take the list6，5，2，3， I'll merge these two first。

 so the new list what I get will be having 11 elements then this one with this one so 11 plus2 I'll be having 13 elements in this list then 13 and 3 I'll be having 16 elements so final list altogether comping will be giving a 16 element list Now you can see that at a time I'm emergingrg tool list。



![](img/e7eadf1ca1a87342254ee976138aaaa8_17.png)

But what is the total time spent in merging total cost。 See， first I have merge 11 elements。

 So this is 11 plus then I have 11 merge 11 plus 2 So 13 elements， then 16。

 So I did not get this 16 element at once。 It was in stages。

 So total amount of merging done as this one。So this is how much fat。Now。

 is there any other way I can merge， Let us try。

![](img/e7eadf1ca1a87342254ee976138aaaa8_19.png)

A， B， C， and D。 So this is 6，5，2，3。

![](img/e7eadf1ca1a87342254ee976138aaaa8_21.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_22.png)

I' merge these two，11， I'll merge these two，5。 Then I merge these two，16。



![](img/e7eadf1ca1a87342254ee976138aaaa8_24.png)

Yeah， I have selected a different pair every time。 So what is the answer。

 Total cost is how much 11 plus 5 plus 162。

![](img/e7eadf1ca1a87342254ee976138aaaa8_26.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_27.png)

Total cost is 32。

![](img/e7eadf1ca1a87342254ee976138aaaa8_29.png)

Is there any other way， let me try。There may be many possibilities of merging， but I'll try one more。



![](img/e7eadf1ca1a87342254ee976138aaaa8_31.png)

Now merge from that site。 Fo merge these two。 So I got 5。 Then he merge these two，10。

 Then I merge these two，16。 So total cost is how much 16 plus a 10 plus 5。



![](img/e7eadf1ca1a87342254ee976138aaaa8_33.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_34.png)

20 thirty1。Oh， I'm getting still less than that。So is there any other method by which I can get less than 31。

 I don't think so。 See if you see the different patterns， these are the patterns， one pattern。

 second and third pattern out of these three patterns。 And this 1。

 I am always selecting two smaller list for merging。



![](img/e7eadf1ca1a87342254ee976138aaaa8_36.png)

That's why I got the minimum result。 So now from this observation。

 we can say that the greedy method that we should follow is always we should merge a pair of small size list to get the best result。



![](img/e7eadf1ca1a87342254ee976138aaaa8_38.png)

Yes， so we have the greedy method。 Now。 We got the approach for solving this problem。

 We understood that always you select two small size lists， combine them。

 Then total merging time will be reduced。 If you follow like this， then the time was 40。

 and this was 32， and there is 31。 So that is best one。Alright。

 so we'll take one problem and solve that one。Here is an example problem for optimal mergech pattern。

I have five files， x1 x 2 x，32 x 5 R files， file names， and these are the sizes。

The numberumb of each5。Now we'll follow greedy approach for solving this one。

We have to find out a pattern in which the total cost of merging is minimized。

So let us follow Gring method。 Grding method says that you should always select a smaller pair of files for merging。

 so they are not arranged in the increasing order of their sizes。

 I will take them in increasing order of their sizes。



![](img/e7eadf1ca1a87342254ee976138aaaa8_40.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_41.png)

I have taken those files in the increasing order of their sizes。



![](img/e7eadf1ca1a87342254ee976138aaaa8_43.png)

Now， let us follow optimal merge pattern so we should select a smaller pair of files and merge then 5 and 10。

 So I'll merge these two。 I'll get a new file of size 15。



![](img/e7eadf1ca1a87342254ee976138aaaa8_45.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_46.png)

Then what are the files I have， I have a new file of size 15，20，30，30。



![](img/e7eadf1ca1a87342254ee976138aaaa8_48.png)

Now， which one is a smaller。 I should select the pair 15 and 20。 These two are smaller。

 so I should select these two and merge them。So， this is 35。15 plus 2035。 So after merging these two。

 Ill be getting 35 elements here。Now what are the list I have， 35， 30，30。

 so I should select a pay of minimum size list or least size list these two。Mge these two， it is 60。

Now what are the list remaining 35 and 60 combine these two and form a list that is 95。 Now。

 let us find out what is the total cost of merging。 See first， these two files are merged。

 the cost was 15。 And when these are merged 35。 So I should take the sizes in these circular nodes。

 So the sizes are 15 plus 35 plus。

![](img/e7eadf1ca1a87342254ee976138aaaa8_50.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_51.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_52.png)

95。Plus，60。Theres two not 5。

![](img/e7eadf1ca1a87342254ee976138aaaa8_54.png)

So the total cost of merging these files by following a optimal pattern is2 not5。



![](img/e7eadf1ca1a87342254ee976138aaaa8_56.png)

I have added all these internal loans， and I got that present。

Even what I can do is how I can know the cost is this 5， how many times it is merged1 time，2 time。

3 time。 So the number of time it is merged with the file says depends on the distance。

 So let us call this as a distance。 So distance how much 1，2，3。



![](img/e7eadf1ca1a87342254ee976138aaaa8_58.png)

So three times， what5 plus。1，2，3，3 times 10， three times 10 plus。1，2。Two times，20 plus。1，2。



![](img/e7eadf1ca1a87342254ee976138aaaa8_60.png)

Two times，30 plus。1，2， so two times 30。

![](img/e7eadf1ca1a87342254ee976138aaaa8_62.png)

So I have taken their distances and their sizes。 Even this total will also be2 not 5。

 If you multiply and add all these things， it will be 2 not5。

 So how I can know the total cost of merging either by adding the sizes of internal nodes or these nodes。

 external nodes， I can say external nodes with their distances。

 So here I can say it' like a formula distance of each node D。



![](img/e7eadf1ca1a87342254ee976138aaaa8_64.png)

![](img/e7eadf1ca1a87342254ee976138aaaa8_65.png)

，The size of each node X I。 so this gives the total cost of merging for all these files by using optimal merge pattern。

That's all about optimal Mosh pattern。 The problem is very simple， but。

This is used by Huffman coding。 So the next video will be about Huffman coding。



![](img/e7eadf1ca1a87342254ee976138aaaa8_67.png)