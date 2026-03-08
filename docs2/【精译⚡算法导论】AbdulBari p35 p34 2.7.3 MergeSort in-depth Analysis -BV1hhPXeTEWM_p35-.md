# 【精译⚡算法导论】AbdulBari p35 p34 2.7.3 MergeSort in-depth Analysis -BV1hhPXeTEWM_p35-

Hi， let us look at pros and cons of me sort。 first look at pros of meot。



![](img/e825c9a38332eea0600e180376d0844a_1.png)

![](img/e825c9a38332eea0600e180376d0844a_2.png)

Mo sort is suitable for very large size list。If you have millions of numbers。

 you can sort them using more sort。Or if you have millions of records， you can sort them using more。

 no other sort can support very large size list。I'll give you the reason afterwards。

So it is suitable for large size list， Mo sort is suitable for linked list。For example。



![](img/e825c9a38332eea0600e180376d0844a_4.png)

If I have two linked list， I'll explain how MerO is suitable for linkedist， see MerOt uses merging。

 so if we understand merging upon linked list then MerO also works similarly。See。

 if I have two list that are sorted， to link list。I can merge them without creating third linked list。



![](img/e825c9a38332eea0600e180376d0844a_6.png)

So I can just link these nodes and form a single link list so two link list can be merge by just changing the links without creating third link list。

 So if I start comparing the elements I start the merge process2。

32 is a smaller so two should be the first number next is three is a smaller so it should point on3 then 3 and8 right so 3 and 83 is smaller then8 and 98 is a smaller so this three should point on this one。



![](img/e825c9a38332eea0600e180376d0844a_8.png)

Then8 is over 99 to well， which one is smaller， 9 is smaller， so8 should point on 9。Then 10 and 11。

 sorry， look will and 11， which is smaller，11 is smaller。 So the same thing is there。

 Then next is this one。

![](img/e825c9a38332eea0600e180376d0844a_10.png)

So that's it we have a single sorted list if I start from here2 then three then 8。

9 11 and 12 so it is sorted without creating third link list I have sorted I have merged to linked list so I can also perform a sort over a link list without creating another link list merge sort supports external sorting。



![](img/e825c9a38332eea0600e180376d0844a_12.png)

![](img/e825c9a38332eea0600e180376d0844a_13.png)

![](img/e825c9a38332eea0600e180376d0844a_14.png)

Actually merging process supports external sorting so also merge sort。

 so what is this external sorting？

![](img/e825c9a38332eea0600e180376d0844a_16.png)

For explaining external sorting。

![](img/e825c9a38332eea0600e180376d0844a_18.png)

I have taken a hard disk here， there a hard disk。It is having two files。And this is。

 these are having some data。Imagine they are having millions of records or millions of numbers。

These two files are very big this is 5 Gb data and this is 10 Gb data is there in these two files。



![](img/e825c9a38332eea0600e180376d0844a_20.png)

![](img/e825c9a38332eea0600e180376d0844a_21.png)

![](img/e825c9a38332eea0600e180376d0844a_22.png)

These are very big files。I want to merge them。If I can merge them。

 then also I can perform merge sort because merge sort follows merging。



![](img/e825c9a38332eea0600e180376d0844a_24.png)

Let us see。These files are the data of those files has to be brought in the main memory。

 then only merging can be done， so let us say RA， I should bring this two files in the main memory。

 then only merge algorithm running here can merge those two and store the result in the third list。



![](img/e825c9a38332eea0600e180376d0844a_26.png)

![](img/e825c9a38332eea0600e180376d0844a_27.png)

![](img/e825c9a38332eea0600e180376d0844a_28.png)

But。

![](img/e825c9a38332eea0600e180376d0844a_30.png)

Size of my memory is just 4GB。Can I bring those two files， 5 GBB to 10 Gb， No。

 I cannot bring entire file in the main memory。

![](img/e825c9a38332eea0600e180376d0844a_32.png)

Then how merging can be done so I can bring the part of a file and merge and then store the result here。

 so I can bring that file in from in pieces in runs or chunks。Of file。

 the pieces of file I can bring。 So here to show you。

 I can show that just Ill bring number two and then number three from two files。

 first file and the second file。

![](img/e825c9a38332eea0600e180376d0844a_34.png)

So imagine that I have brought some group of numbers。



![](img/e825c9a38332eea0600e180376d0844a_36.png)

Or a block of data。 Imagine that。 Now I have this data。 compareare which one is a smaller two。

 So two will go here。 Now， the data from this file is copied there。

 You bring the next data of that file 10。

![](img/e825c9a38332eea0600e180376d0844a_38.png)

![](img/e825c9a38332eea0600e180376d0844a_39.png)

Next heard。Now， compare this three goes here。

![](img/e825c9a38332eea0600e180376d0844a_41.png)

The next element from this comes here。So I am showing in terms of elements。

 but you imagine them in terms of some group of elements or group of records or blocks。

So I can bring few blocks here and merge them and store the result。 So I need very small space here。

 I don't need 5 Gb or 10 G B total 15 g B of space。 This is external merging。

 and external merge sort uses the same method， so merge sort can sort large size data using external merging。



![](img/e825c9a38332eea0600e180376d0844a_43.png)

![](img/e825c9a38332eea0600e180376d0844a_44.png)

Merch sword is stable。What does it mean by stable？If I have a list。

 I have a list in which I have some duplicates。8ight is duplicated。

 so it is appearing two times I have taken one in small size。

 one in large size to show that this is first aid and that is second8。After merging。

 how I want the result is then 4，5，6。

![](img/e825c9a38332eea0600e180376d0844a_46.png)

![](img/e825c9a38332eea0600e180376d0844a_47.png)

This is more eight than this eight than9。

![](img/e825c9a38332eea0600e180376d0844a_49.png)

So if you see here after sorting。The order of duplicate is maintained。

We did not get the area like this3，4，5，6 thats8 first then this eight and9。

 No we got them in the same order。 This was first aid that was second eight。

 so their order is maintained。So for the numbers we cannot figure out why what is the importance of that。

 imagine this is the record。This is students data。And these are the marks obtained by the students in。

Particular subject out of 10。Now all the data is having some arrangement based on their name or roll number somehow the arrangement is then now I want to sort them based on marks the previous arrangement should not be disturbed so this8 come first then that8 suppose this record belongs to Ravi and that records belong to Sil so Ans Ravi's records should come first and then Sil records should come。



![](img/e825c9a38332eea0600e180376d0844a_51.png)

![](img/e825c9a38332eea0600e180376d0844a_52.png)

That's it that' is the stability if already you have some arrangement of data and you want to sort it。

 then if there are duplicates， then they should preserve their order。



![](img/e825c9a38332eea0600e180376d0844a_54.png)

So moreert can do that better。

![](img/e825c9a38332eea0600e180376d0844a_56.png)

Most order is stable。Now cons of more sort， drawbacks of more sort。First is。

 it needs extra space for sorting。It is not in place sorting algorithm。



![](img/e825c9a38332eea0600e180376d0844a_58.png)

What does it mean by in place， See if I have a。

![](img/e825c9a38332eea0600e180376d0844a_60.png)

Aray of elements。I have to sort them，6，3，9，4，10，12。



![](img/e825c9a38332eea0600e180376d0844a_62.png)

And I want to sort them。 Now sorting algorithm should rearrange the elements within the same array only and sort them。



![](img/e825c9a38332eea0600e180376d0844a_64.png)

If it is rearranging within the same array， then we call it as in place sorting merge sort is not in place sorting for sorting this one。

 we have to merge the list， we'll break the list in two pieces and then we start merging。

 you know the algorithm。 So for merging the result has to be kept in a separate array。



![](img/e825c9a38332eea0600e180376d0844a_66.png)

![](img/e825c9a38332eea0600e180376d0844a_67.png)

![](img/e825c9a38332eea0600e180376d0844a_68.png)

![](img/e825c9a38332eea0600e180376d0844a_69.png)

Merge results cannot be within same array in place， merging cannot be done So in place。

 sorting cannot be done。 So we need some extra array。 It needs extra space and only in case of array。

 not in case of link list。

![](img/e825c9a38332eea0600e180376d0844a_71.png)

![](img/e825c9a38332eea0600e180376d0844a_72.png)

So mass soing is not much suitable for a races， it needs extra space。

 so in place soing is not possible。

![](img/e825c9a38332eea0600e180376d0844a_74.png)

![](img/e825c9a38332eea0600e180376d0844a_75.png)

You need extra space。Next one is no small problem。 We have seen the algorithm former thought that was no small problem defined。

 We say that the problem is large。 If it is large， we break it into small sub problemsble to half sub problemsble。

 And when it is small。 if there is single element， it is small and we don't do anything there。



![](img/e825c9a38332eea0600e180376d0844a_77.png)

So it's not having a small problem。So， because it is divide and conquer and it is recursive。

 it is observed that for small size list it is slower。For small size list。

 it is much slower compared to other sorts。

![](img/e825c9a38332eea0600e180376d0844a_79.png)

So， example。Insertion sought。Actually insertion sort takes order of n square time and merge sort takes order of analog n time。



![](img/e825c9a38332eea0600e180376d0844a_81.png)

Incion sort is n square and mese sort is n log n so merge sword is much faster than insertion sort。

 but it was observed that if the size of a list is very small then the me sort weighs a lot of time in recursion and it is becoming slower compared to insertion sort when you really run two algorithms on a machine on a computer we find that the me sword is slower if the list is small So it is observed that for the list is less than or equal to 15 number of elements me sword is slower after that the list is larger than me sword is slowly better than insertion sort。

 So what we do is for small problem if the list is small we assign it to insertion sort So we use insertion sort as a part of mese sort。



![](img/e825c9a38332eea0600e180376d0844a_83.png)

![](img/e825c9a38332eea0600e180376d0844a_84.png)

![](img/e825c9a38332eea0600e180376d0844a_85.png)

So merge sort will not sort smallest， it will take the help of insertion sort and the results it will merge。

Now， next， Y insertium sort。

![](img/e825c9a38332eea0600e180376d0844a_87.png)

Because insertion salt is also stable。That is the reason we use insertion sort， along with mass salt。



![](img/e825c9a38332eea0600e180376d0844a_89.png)

Is there any other algorithm that is a stable， yes， bubble sword？



![](img/e825c9a38332eea0600e180376d0844a_91.png)

![](img/e825c9a38332eea0600e180376d0844a_92.png)

嗯。Bubble salt is also in square and it is also stable in place of insertion we can use bubble also。

But。MerO is suitable for linkless and insertion sort is also suitable for linked list。

RightSo actually I am discussing about me sort and the problem with the me sort and I have not discussed about insertion and bubble so you can find it in another video where I will be analyzing all the algorithms while comparing all the algorithms。



![](img/e825c9a38332eea0600e180376d0844a_94.png)

On various criteria。So here for solving me sort， for small problems。

 we take the help of insertion sort。

![](img/e825c9a38332eea0600e180376d0844a_96.png)

The last thing is insertcion sort is recursive。And all recursive algorithms use stack。

 they use stack that is stack in the memory。Then meO also uses a stack。

 so what could be the maximum size of the stack， the maximum size of the stack depends on the tracing height of a tracing tree of me sort。



![](img/e825c9a38332eea0600e180376d0844a_98.png)

![](img/e825c9a38332eea0600e180376d0844a_99.png)

![](img/e825c9a38332eea0600e180376d0844a_100.png)

Right so in the previous video you can find a tree of me salt and it depends on the height of that tracing tree of me salt so if you remember if the eight elements are given then it will call itself for14 and then here5 to8 then here one2。



![](img/e825c9a38332eea0600e180376d0844a_102.png)

![](img/e825c9a38332eea0600e180376d0844a_103.png)

2， then here  one to one。 So what is the height， It is log n。



![](img/e825c9a38332eea0600e180376d0844a_105.png)

So the height of mergech sort or the working， if you see， the height is login。

 So how much stack space it needs， login stack space at a time it needs。



![](img/e825c9a38332eea0600e180376d0844a_107.png)

It may be creating many activation records， but the maximum activation records will be login。

 So it needs space in the stack。 and also it takes extra space for auxiliary extra space。

 extratra space size should be n n plus that stack space is login so。😊。



![](img/e825c9a38332eea0600e180376d0844a_109.png)

Mescer takes N plus login space。And asymptically， when you take。

 you can take it as the of n or we go of n N plus log n is the total space taken。 What is n。

 this extra space and log n is the stack space。

![](img/e825c9a38332eea0600e180376d0844a_111.png)

![](img/e825c9a38332eea0600e180376d0844a_112.png)

![](img/e825c9a38332eea0600e180376d0844a_113.png)

So that's all the pros and cons of ma sort so you can watch my previous video。

 and one more thing is if you are watching video for ma， first of all， you watch a video on。2 way ma。

 Then you can follow my。 I have split the video into so that it should not become a very big size video。

 So you should watch first two way ma sort， then merge sort， then the analysis of mass sort。



![](img/e825c9a38332eea0600e180376d0844a_115.png)