# 【精译⚡算法导论】AbdulBari p33 p32 2.7.1  Two Way MergeSort - Iterative method -BV1hhPXeTEWM_p33-

Hi， the topic is merge sort。 So for understanding merge sort， first of all。

 we should know what is merging。 So let us know about merge。That is merging。 See。

 merging is a process of combining two sorted list into a single sorted list。So if I have two lists。

 let us say a is one list。 B is one list with some set of elements like。



![](img/00439323bf427a94f2d908ac8358f4f8_1.png)

Now there are two list given and I have taken equal sizes they can be of different size also。But。

 they are sorted。Now， let us see how we can combine them such that the result is also sorted。

 So I will prepare a third list that is C。

![](img/00439323bf427a94f2d908ac8358f4f8_3.png)

These list can be in array also， or they can be in link list also。So irrespective of data structure。

 just we are looking at tool list。Now， let us understand how to combine them。So for each list。

 I need some index pointer， let us take I here and J here and K for this C list。

 which is in the beginning of empty list。

![](img/00439323bf427a94f2d908ac8358f4f8_5.png)

No， procedure starts。 The procedure for merging is like this。Compare a of I with B of J。

 If A of I is smaller， then copy that one here。

![](img/00439323bf427a94f2d908ac8358f4f8_7.png)

And the element which is copied there， you move index。



![](img/00439323bf427a94f2d908ac8358f4f8_9.png)

And this index also moves to next location。

![](img/00439323bf427a94f2d908ac8358f4f8_11.png)

Now， next， compare a of I with B of J。 This is a smaller than this one。

 So copy this element and move to next element here。



![](img/00439323bf427a94f2d908ac8358f4f8_13.png)

And here also， move to next free location。

![](img/00439323bf427a94f2d908ac8358f4f8_15.png)

跟着有。

![](img/00439323bf427a94f2d908ac8358f4f8_17.png)

A of I with B of J8 is smaller。 copy this one。

![](img/00439323bf427a94f2d908ac8358f4f8_19.png)

Then， move to next。And move K also to the next。In the same way， if I continue now，9 is a smaller。

9 is copied， then it will move to the next one。 Then 2 L and 15。2 L is a smaller。2 L is copied。

 Then it will move to next one here， and 15 and 17。 So 15 is a smaller。

 Then it will come to this one。 I will move here。 and this two are compared17 is smaller。

 And finally， K will be on the next three space。 and。😊，I is still here。 Jay has crossed the list。Now。

 we can see that one of the list has finished。Now， remaining elements are there in one of the list here in example。

 list is having some remaining elements， so simply copy those remaining elements。



![](img/00439323bf427a94f2d908ac8358f4f8_21.png)

So that's it。 I got a third list that is with the sorted elements。

 So we have combined two list by comparing the elements from one each list and whichever is smaller we have copied them and we got a sorted list。



![](img/00439323bf427a94f2d908ac8358f4f8_23.png)

This process is merging。The property of this process is that if tool list are already sorted。

 then the result is sorted， so the important thing is a result is sorted。



![](img/00439323bf427a94f2d908ac8358f4f8_25.png)

Now let us look at the time taken by this process。 if I say this list is having M number of elements and this list is having and the number of elements。

 then what is done here， M elements and elements are copied here。

 So this list is having m plus an element。 So what we did just we compare the elements and we have written the list here。

 So the amount of time taken for moving the data from here to there is theta of m plus n。



![](img/00439323bf427a94f2d908ac8358f4f8_27.png)

![](img/00439323bf427a94f2d908ac8358f4f8_28.png)

![](img/00439323bf427a94f2d908ac8358f4f8_29.png)

Though the time complexities are written just using variable N， but for merging。

 we use a the of m plus n。 So this resemble becomes a notation for merging。 m plus n means， okay。

 merging is being done there。 So this has become like a notation for merge。

Now we have understood merging。 I will write on the algorithm or a procedure for merging What the procedure I have shown you same thing I will write on the code there。



![](img/00439323bf427a94f2d908ac8358f4f8_31.png)

![](img/00439323bf427a94f2d908ac8358f4f8_32.png)

![](img/00439323bf427a94f2d908ac8358f4f8_33.png)

Algorithm。March。

![](img/00439323bf427a94f2d908ac8358f4f8_35.png)

Which it takes list a， and。B under their sizes M and N。



![](img/00439323bf427a94f2d908ac8358f4f8_37.png)

Algo the mergege is taking tool list AB， and let us say M&N。

 it depends whatever you like you can pass the parameters， it depends on you。



![](img/00439323bf427a94f2d908ac8358f4f8_39.png)

![](img/00439323bf427a94f2d908ac8358f4f8_40.png)

Now， what we are doing here， we have taken I that is at beginning place and J also at beginning place and K also at beginning place。

 Initially， if you remember， that means I is1。

![](img/00439323bf427a94f2d908ac8358f4f8_42.png)

![](img/00439323bf427a94f2d908ac8358f4f8_43.png)

J is also1 and K is also1。 So I' am starting the indices from1 onwards。

 not like C plus plus where we start from0 onwards。 So for making it simple。

 I'm starting from one onwards。

![](img/00439323bf427a94f2d908ac8358f4f8_45.png)

![](img/00439323bf427a94f2d908ac8358f4f8_46.png)

What is the procedure， We compare A of I with B of J。 So if。



![](img/00439323bf427a94f2d908ac8358f4f8_48.png)

A of I is less than B of J then in C of K I should copy a of I。



![](img/00439323bf427a94f2d908ac8358f4f8_50.png)

If this is smaller， copy this one and move I and K also， So K plus plus and I plus plus。



![](img/00439323bf427a94f2d908ac8358f4f8_52.png)

If this is not smaller， this is smaller else。And sea of Cap plus， plus。Copy B of J plus plus。



![](img/00439323bf427a94f2d908ac8358f4f8_54.png)

![](img/00439323bf427a94f2d908ac8358f4f8_55.png)

This process will continue。 That's what we have seen。 Compare them and copy whichever is smaller。

 So this process will continue。 How long as long as I is less than or equal to M and J is less than or equal to N。



![](img/00439323bf427a94f2d908ac8358f4f8_57.png)

![](img/00439323bf427a94f2d908ac8358f4f8_58.png)

![](img/00439323bf427a94f2d908ac8358f4f8_59.png)

The size of the list is M and the size of this list is N。 This process will continue。



![](img/00439323bf427a94f2d908ac8358f4f8_61.png)

And once this process complete， this loop completes。

 We know that any one of the list will have some remaining elements。 Like in our example。

18 was remaining in the first list。

![](img/00439323bf427a94f2d908ac8358f4f8_63.png)

![](img/00439323bf427a94f2d908ac8358f4f8_64.png)

So I should copy the remaining elements， so we don't know in which list the elements shall be remaining。

 maybe in a or maybe in B。

![](img/00439323bf427a94f2d908ac8358f4f8_66.png)

C。😊，If suppose here I have few more elements，181925。 So there are three elements。

 So I is pointing here from here onward， I should copy all the elements。Means wherever I is pointing。

 I should copy all the elements。Or else here I may be having some elements。1925，30。 So J may be here。

 So wherever J is， I should copy rest of the elements。好 here啦你。4。

Wherever I may be don't initialize it， Let it be at the same place， wherever it is。

 and I is less than equal to M。

![](img/00439323bf427a94f2d908ac8358f4f8_68.png)

I plus plus And in C of K plus plus copy a of I。

![](img/00439323bf427a94f2d908ac8358f4f8_70.png)

5 plus this is already there。 So just I'm seeing copy the remaining elements from list A to list C。



![](img/00439323bf427a94f2d908ac8358f4f8_72.png)

![](img/00439323bf427a94f2d908ac8358f4f8_73.png)

Otherwise， if there are some remaining elements in second list。Then copy the remaining elements。

From second list。

![](img/00439323bf427a94f2d908ac8358f4f8_75.png)

This procedure for merging。Here， this procedure， this while lu。

 is for comparing and copying the elements。 Then the first follow loop is。

 if there are any remaining elements in list take， copy them to list C can follow loops。

 if there are any remaining elements in list B， copy them into list C。



![](img/00439323bf427a94f2d908ac8358f4f8_77.png)

This is merging。Now， let us see if there are more than two lists then how merging is done。

Let me take two more than two list。Now here I have multiple lists。

 Let us see how I can merge them so I can compare first elements of all these list and copy the one。

 which is very smaller。 So as a two is the smaller so I can copy in the final list as a two。

 Then as this is taken now I should go on to the next element of this list。

Now a smaller one is three。 copy this 3。 Now as I have already taken this one。

 then I should go to next element of this list。So I should compare 4，5，8。

4 and this four is smaller two are there so I can copy the first one。

 So now this is completed so I should go to next element here， so I should compare 6，5。

8 and 4 and whichever is minimum I should take that。

 So in this way I can compare all the elements plus one1 element from each list and take the minimum one。



![](img/00439323bf427a94f2d908ac8358f4f8_79.png)

So at a time I am merging multiple list together howmin list， four list， Im merging together。

 So this method， if I take example 4， then this will be called as four way merging。



![](img/00439323bf427a94f2d908ac8358f4f8_81.png)

It will be called as four wave margin。So as four lists， So for emerging。 So as many list you have。

 And if you're following this procedure， then it is called as。



![](img/00439323bf427a94f2d908ac8358f4f8_83.png)

MV margin。

![](img/00439323bf427a94f2d908ac8358f4f8_85.png)

It is M margin。If Im merging just two lists at a time。

 see here I was trying to merge all four lists together at a time。

 If I merge just two list at a time， then it is called as two way merging。



![](img/00439323bf427a94f2d908ac8358f4f8_87.png)

![](img/00439323bf427a94f2d908ac8358f4f8_88.png)

![](img/00439323bf427a94f2d908ac8358f4f8_89.png)

And mostly， we follow this method two way merging。 So let us see if I have these four list。

 how I can merge them by following two way merging， not two emerging。

 I can take two list and get one list。 So that will be 3，4，5，6，9， and and 21。



![](img/00439323bf427a94f2d908ac8358f4f8_91.png)

And I will take these two list and get one list。 That is 2，4，8，10，16 and 18。

Now I have tool list and I can merge these two into a single list。



![](img/00439323bf427a94f2d908ac8358f4f8_93.png)

So one merge， then second merge， then third merge， so four list are there。

 so I have to take pair of two list at a time pay of list at a time and merge them。

 so I have to perform merge three times。

![](img/00439323bf427a94f2d908ac8358f4f8_95.png)

This is one way the other way is suppose I just take this one A B D full list are there。

 I can merge these two and get one list， list one， then I can merge these two。

 then I can get second list then I can merge these three these two and I can get a third list or else if ABC D are list given they can merge these two and get first list and merge these two and get second list then I can merge these two and get third list。



![](img/00439323bf427a94f2d908ac8358f4f8_97.png)

![](img/00439323bf427a94f2d908ac8358f4f8_98.png)

![](img/00439323bf427a94f2d908ac8358f4f8_99.png)

So I have various options available here。

![](img/00439323bf427a94f2d908ac8358f4f8_101.png)

I can first merge A with the D or A with the C also。More than one possible。

Patterns of merging are there。 So when you follow two will merging and you have multiple lists。

 then you can merge them in various patterns。So we have learned that multiple list can be merge in various patterns。



![](img/00439323bf427a94f2d908ac8358f4f8_103.png)

Now， let us look at two wayers thought。There are two me method， one is two way meard。

 other one is just a maard。

![](img/00439323bf427a94f2d908ac8358f4f8_105.png)

Mostly people get confused with the2 m salt and mass salt。



![](img/00439323bf427a94f2d908ac8358f4f8_107.png)

Actually， there is a minor difference between them。



![](img/00439323bf427a94f2d908ac8358f4f8_109.png)

To v our sort is a iterative process， repeating procedure that is using loop。

And monar is a recursive procedure， a recurcial garden。



![](img/00439323bf427a94f2d908ac8358f4f8_111.png)

Let us talk about two women thought。

![](img/00439323bf427a94f2d908ac8358f4f8_113.png)

All we have explained you M way merging or2 way merg merg means you can merge more than two list that is M list at a time。



![](img/00439323bf427a94f2d908ac8358f4f8_115.png)

![](img/00439323bf427a94f2d908ac8358f4f8_116.png)

But two will merge as two lists are taken at a time and they are merged。



![](img/00439323bf427a94f2d908ac8358f4f8_118.png)

So we will follow that one for sorting the numbers。Here a list is given， array is given。

Aray is having eight elements， and I have to sort the array。

But I have to sort this using merge process。 So how I can merge。

 I need at least two arrays for merging， and that must be sorted。



![](img/00439323bf427a94f2d908ac8358f4f8_120.png)

But this single array is given and even that is not sorted。

 So what I can do is I will assume that each element in the array is a list。



![](img/00439323bf427a94f2d908ac8358f4f8_122.png)

So there are eight lists。

![](img/00439323bf427a94f2d908ac8358f4f8_124.png)

Containing one element in each list。Each list is having just a single element。

 so if there is a single element， then it means it is already sorted。So yes， can I merge them， Yes。

 I have to merge eight lists into a single sorted list。So that's how I will merge all of them。

Shall I merge all of them together？ No， I will follow two way merge method。So using two way merge。

 I will merge them into a single list that will be a sorted list。



![](img/00439323bf427a94f2d908ac8358f4f8_126.png)

So， lets do。

![](img/00439323bf427a94f2d908ac8358f4f8_128.png)

I'll select first tool list。 Actually， these are two elements， but I am calling them as tool list。

 merge them。 So what I get。3 is smaller than 9。 So I got one list。



![](img/00439323bf427a94f2d908ac8358f4f8_130.png)

That is merging of those two is done， I got a single list with two elements。



![](img/00439323bf427a94f2d908ac8358f4f8_132.png)

Then I merge these two。5 and 7。

![](img/00439323bf427a94f2d908ac8358f4f8_134.png)

Now， I got one more list with two elements。

![](img/00439323bf427a94f2d908ac8358f4f8_136.png)

Next， I'll merge these two。 So I get 4 and 6 and same way，2 and 8。2 is smaller than8。

 so I have merged these two and I got a sorted list of two elements， so I got such soded list of2。

2 elements each。

![](img/00439323bf427a94f2d908ac8358f4f8_138.png)

![](img/00439323bf427a94f2d908ac8358f4f8_139.png)

Now， there were8 lists。 Now I have four list。

![](img/00439323bf427a94f2d908ac8358f4f8_141.png)

I have completed all the elements， so this is first pass。



![](img/00439323bf427a94f2d908ac8358f4f8_143.png)

One pass is complicated。I have gone through all an elements。Now one more thing。

 if there were nine elements， then9 elements will not have pairing with anybody so that will come directly。



![](img/00439323bf427a94f2d908ac8358f4f8_145.png)

![](img/00439323bf427a94f2d908ac8358f4f8_146.png)

Right，So don't worry if there are odd number of elements。

 then that will simply come here and that may go to merge some time later。



![](img/00439323bf427a94f2d908ac8358f4f8_148.png)

And one more thing。When I am merging them where I am keeping the elements。

 they are not kept in the same array A。Definitely when you merge tool list。

 you need to store it in a third list that is third array。

 So here I have tool list in a single array。 So after merging。

 I need one more array B where I will be keeping this result。So remember that when you merge。

 the result has to be kept in a separate array。But I want the result in a only okay copy but copy it back from B to a。

 So if there is array list。 if there is an array A。

 then the elements are merged and we get the result in B。

 then all these elements will copy them back to a So again the list are in a only this what we do。

 So I' am not showing it here programmatically it can be done。

 Now I have four list I have to merge them。 So four list I'll pick up two。 So two list each with two。

2 elements merge these two。 So the smaller is three。 the next is5。 the next is 7 the next is9。

 So I have done mergerging I got one list of four elements。

 then merge these two So two is the smallest and then four then six then8。



![](img/00439323bf427a94f2d908ac8358f4f8_150.png)

![](img/00439323bf427a94f2d908ac8358f4f8_151.png)

![](img/00439323bf427a94f2d908ac8358f4f8_152.png)

![](img/00439323bf427a94f2d908ac8358f4f8_153.png)

Now I have two lists of four element each， and I have completed one more pass means I have gone through all the elements。

 so this is second pass。

![](img/00439323bf427a94f2d908ac8358f4f8_155.png)

Now， I have just two lists。 I have to merge them， and I get a single list now， with two the smallest。

 then 3， then 4，5，6，7，8，9。

![](img/00439323bf427a94f2d908ac8358f4f8_157.png)

![](img/00439323bf427a94f2d908ac8358f4f8_158.png)

![](img/00439323bf427a94f2d908ac8358f4f8_159.png)

That's it。 Now， I got a single sorted list。This was the third bus。That's it。

 Now the elements are sorted。 Finally you can keep these elements back in array A So single array of8 elements is sorted by using merge process and that we are using two way merg that is we are merg tool list at a time。



![](img/00439323bf427a94f2d908ac8358f4f8_161.png)

Now， let us do some analysis。

![](img/00439323bf427a94f2d908ac8358f4f8_163.png)

How much work is done in each pass， So I emergingrg an elements in this pass。



![](img/00439323bf427a94f2d908ac8358f4f8_165.png)

And again， merging n elements in this pass。 So together， total n elements are merged here。

 So actually，8 element 8 is n here。

![](img/00439323bf427a94f2d908ac8358f4f8_167.png)

![](img/00439323bf427a94f2d908ac8358f4f8_168.png)

How many times this is done。How many times it is done， three times，8 elements， three times。



![](img/00439323bf427a94f2d908ac8358f4f8_170.png)

So if you see this one， eight elements were there， eight lists were there。

 they are divided and we got four， so they are divided by2 and we got four list。



![](img/00439323bf427a94f2d908ac8358f4f8_172.png)

![](img/00439323bf427a94f2d908ac8358f4f8_173.png)

Again， they are divided by two。 Then we got two list。 again， that two is divided by two。

 So we got one list。 So finally， this is one。 So how much this is8 is。



![](img/00439323bf427a94f2d908ac8358f4f8_175.png)

![](img/00439323bf427a94f2d908ac8358f4f8_176.png)

![](img/00439323bf427a94f2d908ac8358f4f8_177.png)

Divided by two raiseds to3， that is becoming one list。 Finally， we have stopped。

 and it became one last。 So this is 8 is equals to 2 per3。 So harmoning passes three passes。

 three passes。 So this is log8 base 2。 That is 3。 So it means log of8 gives me 3。



![](img/00439323bf427a94f2d908ac8358f4f8_179.png)

![](img/00439323bf427a94f2d908ac8358f4f8_180.png)

![](img/00439323bf427a94f2d908ac8358f4f8_181.png)

So I can know the number of passes by taking log of that。



![](img/00439323bf427a94f2d908ac8358f4f8_183.png)

Number of elements。So it means how many passes are required。 numberumber of passes are。



![](img/00439323bf427a94f2d908ac8358f4f8_185.png)

![](img/00439323bf427a94f2d908ac8358f4f8_186.png)

Number of passes。Log n， whatever the number of elements are。



![](img/00439323bf427a94f2d908ac8358f4f8_188.png)

Now in each pass， n merges are there and likewise login passes are there。

 So total time is n into log n。

![](img/00439323bf427a94f2d908ac8358f4f8_190.png)

![](img/00439323bf427a94f2d908ac8358f4f8_191.png)

Yes， I can take it as theta because there is a class available for this function。



![](img/00439323bf427a94f2d908ac8358f4f8_193.png)

And login。So， the time complexity for。

![](img/00439323bf427a94f2d908ac8358f4f8_195.png)

2 way Mar far is and login。 This is the working of two way mass thought。



![](img/00439323bf427a94f2d908ac8358f4f8_197.png)