# 【精译⚡算法导论】AbdulBari p37 p36 2.8.2 QuickSort Analysis -BV1hhPXeTEWM_p37-

Now， let us look at analysis of Quicks。 Let us analyze it。Find out its time complexity。See。

 one important thing is it's a recursive。And it is following divide and conquer strategy。

It is using partitioning procedure， partitioning algorithm。

 and the partitioning algorithm will find out the position of P vote。And it will divide the list。



![](img/b79f6c22c20685650129704198069443_1.png)

Suppose I have the list of elements。Let us say， one through 15。I have a list of 15 elements。



![](img/b79f6c22c20685650129704198069443_3.png)

Then if I call quicks by passing first index as1。And last index has 15。



![](img/b79f6c22c20685650129704198069443_5.png)

Suppose it is partitioning at the middle。

![](img/b79f6c22c20685650129704198069443_7.png)

Then I am getting elements from one to7 on this side。



![](img/b79f6c22c20685650129704198069443_9.png)

And。9 to 15 on this site。 So partitioning was done at index 8 that is at the middle of a list。

 So elements 12，7 here and 9 to 15 on this site。

![](img/b79f6c22c20685650129704198069443_11.png)

![](img/b79f6c22c20685650129704198069443_12.png)

Suppose the partitioning is done in the middle。 assume this。



![](img/b79f6c22c20685650129704198069443_14.png)

Then what about this left hand side， this part and this part。

 assume always partitioning is in the middle。

![](img/b79f6c22c20685650129704198069443_16.png)

![](img/b79f6c22c20685650129704198069443_17.png)

Then here the middle element will be four and this side we get a list from one to three and in this side five to seven。



![](img/b79f6c22c20685650129704198069443_19.png)

Similarly， if it is happening here， then the partitioning will be at 2 well middle of a list。

 then we get the elements 9 to 11 here and 13 to 15。



![](img/b79f6c22c20685650129704198069443_21.png)

Suppose partitioning is again in the middle and I get one element on this side that is one to1 and3 to 3 here the partitioning is on4 so then five to five。

And7 to 7。

![](img/b79f6c22c20685650129704198069443_23.png)

Personing is at 10。Here，9 to9。He 11 to11。And here， 13 to 13。14 partitioning is done， 15 to 15。



![](img/b79f6c22c20685650129704198069443_25.png)

If partitioning is always done in the middle I have given 15 elements and suppose the partitioning was at8 and thats all for every node I have written partitioning so the working of the quickword will be like this。



![](img/b79f6c22c20685650129704198069443_27.png)

![](img/b79f6c22c20685650129704198069443_28.png)

![](img/b79f6c22c20685650129704198069443_29.png)

Then if I analyze this one based it on the tree。

![](img/b79f6c22c20685650129704198069443_31.png)

What the partitioning algorithm is doing。 It is comparing the element and exchanging them。

 So what is the time taken by this algorithm， It is n。 It will go through entire list。



![](img/b79f6c22c20685650129704198069443_33.png)

![](img/b79f6c22c20685650129704198069443_34.png)

So the time taken for this is n。And the time taken at this level。

 this left side and right side together is almost n， no doubt one element is reduced。

 but let us say it is n。

![](img/b79f6c22c20685650129704198069443_36.png)

Then at this level also， it is M。

![](img/b79f6c22c20685650129704198069443_38.png)

And that's all。 that is the end of the level。Then what is the height of a tree？See。

 it was 15 divided by 2 at as the partitioning is always in the middle， half half the site。

 divided by two by two by  two。 when something is getting divided by 2 every time。

 How many times it will divide such that it reaches one。 So if you say n by2 then by  two then by 2。

 So how many times so that it becomes1，11 element。 So this n by2 per k is equals to 1 and n is equals to2 per k。

 So K is log n base 2。 So， yes， how many levels are there， log n levels are there。 And in each level。

 what is the time taken， I am assuming that partitioning algorithm will compare the elements for n times。

 So it's n。

![](img/b79f6c22c20685650129704198069443_40.png)

![](img/b79f6c22c20685650129704198069443_41.png)

![](img/b79f6c22c20685650129704198069443_42.png)

![](img/b79f6c22c20685650129704198069443_43.png)

![](img/b79f6c22c20685650129704198069443_44.png)

![](img/b79f6c22c20685650129704198069443_45.png)

So the time complexity of quick sort will be。

![](img/b79f6c22c20685650129704198069443_47.png)

Aoff and login， assume that always partitioning is done in the middle of a list。



![](img/b79f6c22c20685650129704198069443_49.png)

So that assumptionsump has given us this time。 So this will be best case of an algorithm。



![](img/b79f6c22c20685650129704198069443_51.png)

![](img/b79f6c22c20685650129704198069443_52.png)

What is the case if the partitioning is always in the middle and what is the time in best case。

 its order of N log n。

![](img/b79f6c22c20685650129704198069443_54.png)

So the best case time of quick sort and log in and this will going to achieve only if the partitioning is done in the middle。



![](img/b79f6c22c20685650129704198069443_56.png)

Let us see whether this best case is possible or not。For that。



![](img/b79f6c22c20685650129704198069443_58.png)

Let us know about media。What is median。If I have the numbers， one，2，3，4，5，6，7。

The numbers are sorted and this is the middle element of the sorted list。

 and this is called as median。

![](img/b79f6c22c20685650129704198069443_60.png)

So mediumn is the middle element of sorted list。Then。

Best case of quick sort is always the partitioning should be in the middle。



![](img/b79f6c22c20685650129704198069443_62.png)

So if partitioning is in the middle means， the element that is selected as P vote。



![](img/b79f6c22c20685650129704198069443_64.png)

Should be a medium。So how can you know median unless the list is sorted， we cannot know the medium。

So， is it possible that always the element selected is a mediumn and it is sitting in the middle of a list partition in the middle of a list？

It is not possible randomly it may happen， but we cannot control it。



![](img/b79f6c22c20685650129704198069443_66.png)

So achieving best case is not possible in quick sort。

 you cannot achieve It may randomly happen that always the element is。A medium。



![](img/b79f6c22c20685650129704198069443_68.png)

What is the worst case of Quick sort？Suppose I have a list 2，4，8，10，16，1817。



![](img/b79f6c22c20685650129704198069443_70.png)

Suppose I have a list which is already sorted。

![](img/b79f6c22c20685650129704198069443_72.png)

Then if it perform quick sort how it works Partitional algorithm we saw it will select the first element as by vote and it will start I here and J here。

 I will continue until it finds a greater number so here and J will continue until it finds a smaller or equal number so its not small not small it will come and stop here。



![](img/b79f6c22c20685650129704198069443_74.png)

![](img/b79f6c22c20685650129704198069443_75.png)

![](img/b79f6c22c20685650129704198069443_76.png)

Then where the partitioning will be done at the same place。 Now， this is sorted。

 So rest of the elements we have to sort。

![](img/b79f6c22c20685650129704198069443_78.png)

So you can see that partitioning will be done in the beginning of a list。

Because the list was already sorted Now from this list， if I select4 where it will be partition。

 where it will be position finally at the same place again。



![](img/b79f6c22c20685650129704198069443_80.png)

![](img/b79f6c22c20685650129704198069443_81.png)

So always the partitioning will be happening in the beginning of a list that is the worst case of quick sort。



![](img/b79f6c22c20685650129704198069443_83.png)

If I give the numbers from 1 to7， then one will be sorted and on this side I get2 to 7。

 then two will be sorted and this side Ill get the number from 3 to 7， then 4 to 7。



![](img/b79f6c22c20685650129704198069443_85.png)

Then，5 to 7。6，2，7。

![](img/b79f6c22c20685650129704198069443_87.png)

And 7 to 7。

![](img/b79f6c22c20685650129704198069443_89.png)

Now you can see that always the partitioning is happening on the beginning of a list or it may happen at the end of the list also it depends here it is sorted in ascending order if it is in descending order always will be at the end。

Now， what is the time taken here， First partitioning algorithm takes makes n comparisons then n minus-1 comparisons n -2 and so on so 2 then1。

 So what is this equal to this is equal to n into n plus 1 by 2 that is order of n square。



![](img/b79f6c22c20685650129704198069443_91.png)

That's it。The worst case time of quickword is in square。



![](img/b79f6c22c20685650129704198069443_93.png)

B case time is order of N square。

![](img/b79f6c22c20685650129704198069443_95.png)

Best case time of quicks is N login， which is not possible for us to achieve it。

 but worst case time is n square and when it will happen if the list is already sorted。

So this is the problem with quick sort that its worst cases in square if you compare this with the merge sort merge sort was not having any best or worst cases。

 it was just average time in login but here the average time is in login。

 but the worst cases in square。

![](img/b79f6c22c20685650129704198069443_97.png)

![](img/b79f6c22c20685650129704198069443_98.png)

Now we need to solve this one。How can we reduce this problem See the probability that if the list is already sorted。

 we are again sorting it， the chances are high because you want to keep the list in the sorted order we may be sorting it again and again。

 So if it is already sorted and you are sorting it， then the time is going to be n square。



![](img/b79f6c22c20685650129704198069443_100.png)

So this is the problem with Quicks。 So what we do is we say that。



![](img/b79f6c22c20685650129704198069443_102.png)

Don't always select the first element， as by vote。You can select the middle element as per vote if you select middle element。

 then what happens。If you select this one way it will come， it will come here only。

 so the partitioning will be done here。If partitioning is happening here。

 then the list gets divided into two equal halves。

![](img/b79f6c22c20685650129704198069443_104.png)

Thats it if always we select the middle element as by vote then the partitioning will be done always in the middle of a list because the list is already sorted and that is how it will convert from n square to n log n the worst case will become best case。



![](img/b79f6c22c20685650129704198069443_106.png)

![](img/b79f6c22c20685650129704198069443_107.png)

![](img/b79f6c22c20685650129704198069443_108.png)

There are two suggestions for improving the worst case of quick thought。

 removing worst case of quick thought。Always select middle element as by vote。So。

If the list is already sorted， it will become best case that is in login。

But still the maximum time will be n square for some elements， some arrangement of elements。

Other suggestion is randomly select some limit as per vote。

If you randomly select some element as per vote again。

 it may be possible that it may take a login time or maximum again in square time。



![](img/b79f6c22c20685650129704198069443_110.png)

So always the worst time taken by quick saws。

![](img/b79f6c22c20685650129704198069443_112.png)

And square。About the space complexity， Quicksortt is a recursive algorithm and it doesn not need any extra space。

 but it will use a stack。So what could be the maximum size of the stack inverse case。

 it may be n What is the minimum size of the stack in best case， the height maybe be log n。

 So the quickaw takes stock size that is log n to n。

 So how you can know this just now have shown trees in best case， the height of a tree was log n。

 So the size of the stack depends on the height of a tree tracing tree and in worst case it was n。

 So maximum size of the stack maybe n。

![](img/b79f6c22c20685650129704198069443_114.png)

![](img/b79f6c22c20685650129704198069443_115.png)

So that's all about the quick thought。

![](img/b79f6c22c20685650129704198069443_117.png)