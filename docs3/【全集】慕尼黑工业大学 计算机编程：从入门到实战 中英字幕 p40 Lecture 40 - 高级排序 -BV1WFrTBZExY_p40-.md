# 【全集】慕尼黑工业大学 计算机编程：从入门到实战 中英字幕 p40 Lecture 40 - 高级排序 -BV1WFrTBZExY_p40-

![](img/23c7706dae5ae9b09d1964aac9be5be9_0.png)

Welcome back after the break， let's continue with our next unit on advanced sorting。

We've already discovered simple sorting algorithms such as insertion sort and you probably also have heard about others such as bubble sort。

 most of the ones that we discovered so far， however， are relatively slow。

 and today we would like you to introduce to you a more advanced and more performant sort algorithm。

 and this is called merch sort。Merch sort is compared to bubble sort much faster。

It's not necessarily the fastest one， and people consider Quickwordword as the fastest sorting algorithm。

 but Quickword is even more difficult to understand。

 we would like to have a middle ground here and on average if you do the complexity analysis。

 merge sort and Quickword are roughly the same in terms of performance。

Merch sort works like that from the general idea， you start with two sorted lists。As an input。

 and then as an output， you have one sorted list。And if。

You don't have a sorted list in the beginning。 In fact， you have the list as often as it's necessary。

Until you have a sorted list。 and what is the。Easest soest list。 Well。

 the list with only one element。So let's assume we have eight elements。

 and we haveal the list multiple times until we only have one element。😊。

And then we do the merge sort algorithms consecutively until we end up with the full list again。Now。

 because merge sort and especially the first two parts of it can be quite cumbersome to understand。

 we only focus on step three here， so we only talk about how can you merge two lists that are already sorted into a new list that is again sorted。

 that's the main algorithm that we would like to discover now and where we show you an implementation in Javava。

Next。First of all， try to understand how this works from a conceptual point of view。

 because you should also be able to program this in different programming languages later on。

Let's assume we have those two lists， you see they don't have to have the same length。

The first one has four elements and the second one has three elements。

 and both of them are clearly sorted from the smallest to the largest element。😊。

Now mech sort works like this， we compare the first two elements。

And then we would take the smallest one in the beginning of the new list， and if we would do that。

 then the end result would be like that。So that's our end result。

 so very quick transformation from the input to the end result and now let's try to understand how this works and then I have an animation where you can see it step by step。

😊，So the idea is， we have two sorted lists and we successively construct the output list from the arguments and to find the next element for the output list。

 we take the two smallest elements of the remaining input list。

 so the ones that are at the left side in that sense。And。Compare them。

 and then we take the smaller one and remove it from the input。Or if we use arrays。

 we shift the index1 to the right。 And now if the length。

Is of one of those input lists is basically one。So sorry， it's basically zero。

 we can take the remainder of the other list because this is already sorted and then we can basically stop the algorithm in order to be as performant as possible。

Now， if M and N are the lengths of the two argument lists。

 at most m plus n minus1 comparisons are necessary。

So this is the way of doing it as efficient as possible without any additional comparisons。

So let's see in detail how that works， here we would compare the smallest elements is0。

 this element smaller than minus3， no， so we take minus3 as an output of our new list。😊。

And as you see it's not part of the input in that sense anymore now again we compare the smallest elements is0 smaller than 7。

 yes， so we take0 as the second element in our output list now we again compare the smallest elements is 15 smaller7 no so we take seven。

Is 15 smaller than 13， no so we take 13， is 15 smaller than 42， yes， so we take 15。

 is 16 smaller than 42， yes， so we take 16 and then we are at the end because one list is empty。

 one input list is empty and then we can just take the remainder of the second input list。

So this is how it works conceptually。😊，And I guess this is relatively easy to understand yeah。

 so if I would give you now a few bricks or carts with numbers。

 you could probably do that on your own， on your table following the algorithm would actually be a nice exercise。

 we should probably consider this for next year。But if I ask you to program that。

 who are you thinks you would be able to program this immediately based on the。Given。Idea okay one。

 two persons maybe yeah so okay this is good you're very confident but of course we tell you how it works right of course ideally at the end of this course if you see such a conceptual visualization of an algorithm you are able to implement this on your own but we are still in the middle of the course so I help you out。

😊，What do we need to do let's plan our implementation。

 it's always good to plan implementationer and not just get started because if you have a good plan it's typically much more structured and you come to a better result more quickly so we start with two input lists and the first thing that we have to do is to create the output list。

😊，And then we basically transverse or iterate over the two input lists A and B。

 we always compare the two current nodes with the smallest elements。

 the one that is smaller is basically used and is appended into our output or result list and if the end is reached in either A or B。

 we append the rest of the other list to the output as well。

 if you write that down before we had a visual，Implementation of the algorithm or of the concept and now we've write it written it down into steps。

 yeah textual steps then you can use those steps and actually write code for it and this is how it looks like in the end so we first create the result or output list then we traverse over the input lists using a while loop。

😊，And we always take the smaller elements and edit。And by doing that。

 we always increase the index I using for input A and J using as index for input B。😊。

And now if we are at the end， if we've done that as often as we want。

 if one of those two conditions is false， then it means that one list is empty we don't know exactly which list is empty because we don't remove them from the input lists here。

 we just increase the index or we have to check again if index is smaller。

 if the index is smaller it means we are not at the end of this particular input list and we can just iterate again through all the elements and add them to the result。

 or if it's not input a that has remaining elements but it's input B， we do this for list B。

And that's basically what we do here。And this is just one example implementation。

 you can also use this do this with Lada expressions with four loops。

 we decided to use Y loops here because it makes the most sense。😊，So let's quickly do this again。

 and now we also explain you that this is a generic algorithm。😊，And in order to do that。

 we have to state a few requirements so that we don't have to implement it for in string。

Double and so on。 What are the requirements， Well， we have a generic type T。

 and in order to compare two elements， you remember， we already discovered a comparable interface。😊。

And the comparable interface makes sure that any class that we use here。😊。

Implement the Comp two method， so if you want to use this with your own point class， for example。

 or if a student class student or point have to implement a Comp two method。

 so this is our upper bound if you remember right。😊，Every type that we want to use for this。

Algorithm or function， in this case， it's a static method。

 it's what we can call it function has to implement a comparable interface。😊。

And the list input A has to use this type。Or a potential subtype， of course。

 and input B also has to use this type， very important。And of course。

 our result also uses this type in the end。And then we basically go through it。With collections。

 we will see an exercise in a few minutes where you have to do this with arrays。

But here we use collection data types， and here we just say if I is or while I is smaller than the length or the size of the input and J is smaller than the size or length of the input B of list B。

We go through it， so we iterate until we are at the end of one of the two input lists。

And then we compare the current element， like you've seen it in the visualization of the first one with the current element of the second one。

😊，And smaller zero， remember， compared two has a very specific。Signature and definition。 and if it's。

The result is smaller， zero and it means the element of the first one here is smaller。

 so we add this element。😊，Into our result。And additionally， we increase the index I by one。Otherwise。

 if they are having the same value or if the value in B is larger。The value in b is smaller， sorry。

Then we add the one from B and increase the index J by 1。

And we do that until we are at the end of one of those two genericists。

 And then depending on which case。And which condition is true， We basically add the remainder of the。

List it still has elements。Any questions regarding this algorithm？

Yeah so the question is about this post fixed increment here and why do we not just get the value at I and then incremented by one。

 this is basically what we're doing with the post increment which it's just a shorter way of writing it down so this code here is identical to let me just。

Make this a bit larger。Yeah， so I could get rid of this。

 but then I would need to do it in the next line。I would need to write I plus plus or I equals i plus1。

Yeah， so this is basically the same。 It's just a shorthand of it。

 and you can do a separate line if you want， but I decided to keep this slide small to do this in one。

Line。Yeah， so the question is， can we yeah？Can we leave out compare2 and simply say A at position I is smaller than B at position J？

If you know that you have integers or doubles， yes， but we have implemented this in a generic way。

 so the result of this a dot get I could be a point。😊，And for a point。

 you don't know the smaller operator is not defined right。

 The smaller operator is only defined for primitive data types or for the rappers of primitive data types。

 and this is why we can't use it here。 So that's basically the。

Small disadvantage when you use generics， you can't use the simple operators anymore。

 you have to use the more object oriented ones right there are other ways how to compare two things yeah you don't have to use comparable。

 you can also use a compator this code could also be implemented with compators and Lambda expressions probably also with streams but we left this out for now to not over blow it。

Okay， it might take a little bit of time， but if you read it again。

 if you tried it out with an example， you might better understand it， one more question。Yeah。

 this is Z the question is where do we have this， this is out of scope， we only look at number three。

 step three of the whole algorithm， we only merge two lists。

 the half in process that has to be done beforehand。It's not included in here。

 we will show it to you later on you have to you know it's like a serious or Netflix。

 you have to watch the next episode to see how it works and it's probably not in the next episode it's after Christmas at some point then we also show you how the halfing algorithms could be implemented。

This is to keep you engaged。Okay， great。嗯。Here's an example use。 We can create two lists of intes。

 for example， and then call mergech， and then you'll see that they actually merge it like that。

 And if you don't believe it， copy and paste the code into your playground try it out， debug it。

 and then you will see how it works。 And also how the data structures during the algorithm actually are。

Excessed， we it's important that we do not change list 1 and 2。 Yeah， this is an important。

Invariant or assumption or requirement for this particular method。

Those initial lists are not changed。 we only get elements from them。

 We do not remove elements from them。So theoretically。

 you could also implement it in a way that you get a copy and then you can remove elements。

 but this is not what we do here， and this would also be less performant in the end。Great。

 and then we'll have a little exercise for you and this is now a bit more difficult。

 so you also get a bit more time， the idea is that you implement this function now with generic arrays instead of generic lists。

😊，And we ask you to give it a try， it's not super easy， we did some preparation for you already。

 we define how the message should be called， and how signature actually works。

 we still use the generic type that extends comparable， but we return an array instead。

 and we have inputs as arrays。😊，And we also help you to get the result。

 the result is simply a copy of RAA with a specific length， you don't really know how this works。

 but this makes sure that you can use generics here。

Because generics and arrays are sometimes not so easy to mix。And we give you a hint。

 youll still need index I for the input array， index， for the second input array。

 and additionally because you're now manipulating arrays where you can't just append elements to the end of it for a list this is possible。

 I can just add elements here we would need to insert them at a specific positioner so we need to keep track of the index for the output array。

And you can basically for this exercise， just copy the previous implementation。😊，Paste it in here。

 and then adapt all the。Elements， yeah， instead of saying， get。

The element at a specific position you use to array syntax how to access elements at a specific implementation right so from the main structure yeah you still need three y loops and the conditions in the y loops are semantically the same。

 it's just a different syntax okay。😊，That's basically the exercise tutors will go around and help you again this is not easy。

 this is a medium one but we also would like to increase the complexity now a little bit and we help you out in case you have issues you can also debug this and we also provide it some code for you how to test your implementation again with intes so have fun with this exercise and let us know if you need help。

😊，Okay then I guess we can continue well done， I thought it's a bit more difficult and tricky for you to come up with a solution。

 but apparently this has worked out much better than I assumed。

We have an example solution here and I'll quickly explain it to you， most of the code stays the same。

 we take a while loop first in order to find out which element of A or B is smaller。

 but you see that the syntax slightly changes instead of using the size method we use the length attribute of the array。

Instead of accessing the element with get I， we used the square braces with I and the square braces with j。

 and what is also important is that we have to maintain the index k。

 so we have to post increment both k and I in the first branch of the if statement or K and in the second branch of the if statement。

And similar in the second while and in the third while loop， the main idea stays the same， but again。

 instead of appending elements， we set the element here maintaining the index and access the element。

 not using the get but。Square operator， so to speak， any questions regarding this example solutioner。

 anything that is unclear？Okay， great， then we'll do a break and continue at 4 pm。



![](img/23c7706dae5ae9b09d1964aac9be5be9_2.png)

With the remainder of today's session。So see you in around 30 minutes。

