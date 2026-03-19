# 【精译⚡算法导论】AbdulBari p79 p78 Hashing Technique - Simplified -BV1hhPXeTEWM_p79-

Hi。This video is about hashing technique。

![](img/3b0307145021425596de0848036fcd4b_1.png)

Hsel technique is。Useful for searching purpose。Now， before going to Hahing。

Let us quickly look at some of the known searching techniques。



![](img/3b0307145021425596de0848036fcd4b_3.png)

Here is。

![](img/3b0307145021425596de0848036fcd4b_5.png)

Linear search。In this， the elements must be arranged。



![](img/3b0307145021425596de0848036fcd4b_7.png)

In and array。Randomly not in any order。

![](img/3b0307145021425596de0848036fcd4b_9.png)

And the time for searching is out of n。For searching any element。

 we start looking for the element from the left hand side of an array towards the right hand segments will start from the beginning index。



![](img/3b0307145021425596de0848036fcd4b_11.png)

And the time is sort of fun。Second search method is binary search。And this。

The elements must be in the ascending order， sorted order kept in a list kept in an array。

And we always look for an element in the middle of a list。And if the element is larger。

 we go on right side， if it is smaller， we go on left hand side。

 So the time for searching is order of login。

![](img/3b0307145021425596de0848036fcd4b_13.png)

So important thing is the arrangement of elements in a linear search。



![](img/3b0307145021425596de0848036fcd4b_15.png)

Can be random， but in binary search， it must be in the sorted order。



![](img/3b0307145021425596de0848036fcd4b_17.png)

And the time complexity for linear search is order of n。

And binding search improves the search method and makes it faster， and it is order of login。



![](img/3b0307145021425596de0848036fcd4b_19.png)

![](img/3b0307145021425596de0848036fcd4b_20.png)

But one the requisite here is that the elements must be sorted。

 so we have to spend some extra time in sorting the elements。

Okay now we want a search method which takes just constant time。

 so from n we have moved to log n and from log n we want to move on to order of 1。



![](img/3b0307145021425596de0848036fcd4b_22.png)

![](img/3b0307145021425596de0848036fcd4b_23.png)

So this is the requirement which。Introduces hashing technique。



![](img/3b0307145021425596de0848036fcd4b_25.png)

So， let' us see hashing。In hashing technique。If a。List of elements are given and the array space is given where we have to list store the list of elements。



![](img/3b0307145021425596de0848036fcd4b_27.png)

![](img/3b0307145021425596de0848036fcd4b_28.png)

Then we store the element upon its own index。 we take the value of an element itself as the index and we store it at same index。

 so 8 is stored at 8。

![](img/3b0307145021425596de0848036fcd4b_30.png)

And3， it is made as index， and it is stored at location 3， so on。



![](img/3b0307145021425596de0848036fcd4b_32.png)

Now， when you want to search for any key element， let us say 10。

 then we directly go to index 10 and see if the element is present or not。

If we want to search for key element  to2， then we directly go to index 22 and see element is present or not。

 so L is not found。So the search time is order of 1 directly we have to go to that index and look for the element。

But the problem is， if I have one more element that is 50， then we have to store it at index 50。

 which which may be far away。 So here for stor this 50 we should have an index 50 in the area。

So a lot of space is wasted in this method。

![](img/3b0307145021425596de0848036fcd4b_34.png)

If we want to reduce the time， then we may have to waste lot of memory。 just for few elements。

 we need a very large size array where most of the space are vacant。



![](img/3b0307145021425596de0848036fcd4b_36.png)

![](img/3b0307145021425596de0848036fcd4b_37.png)

To improve this technique or to improve this basic idea， we adopt a mathematical model。

 We design a mathematical model for hashing。

![](img/3b0307145021425596de0848036fcd4b_39.png)

Based on functions。 So let us see next。

![](img/3b0307145021425596de0848036fcd4b_41.png)

How it is modeled using mathematically。The list of elements what we have we call them as key space and the place where we have to store them。

 we call it as hash table。And we say that there is some function， say h of x equal to x。

 which is mapping these elements from key space to hash table， so h of8 is 8。

 so this 8 will be stored at index 8。And same way，3 is stored at 3。T。A of 13 is 13。

 so it is stored at 13 index 13。So， we say that。H of x equal to x is a hash function which is mapping these sc elements from key space to hash table。

 and this we take it as an ideal hash function， so this is the same case we have seen just now and we have just made it in the mathematical form。

Now in this， if I have an index 50 then if I have a key element 50。

 then I should have an index 50 in the array。So I should have a very lengthy hash table again the problem is same that lot of space is wasted。

 So if we see the properties of functions， there are two types of functions。



![](img/3b0307145021425596de0848036fcd4b_43.png)

![](img/3b0307145021425596de0848036fcd4b_44.png)

1 to one function。And。Many do one function。These are the two types of cardinalities followed by functions and h of x equal to x as a 1 to1 function。

 If you take any other function other than h of x equal to x， it may be many to one function。



![](img/3b0307145021425596de0848036fcd4b_46.png)

![](img/3b0307145021425596de0848036fcd4b_47.png)

![](img/3b0307145021425596de0848036fcd4b_48.png)

But also it depends on the keys or the hash table size。

 so but mostly it will be many to one function。Now we say that here this function is responsible for mapping the elements to their indices。

 so we should modify the function to efficiently utilize the space in hash table。



![](img/3b0307145021425596de0848036fcd4b_50.png)

![](img/3b0307145021425596de0848036fcd4b_51.png)

So， leaveve。We will try to modify the function。 So here it we take， here we take。



![](img/3b0307145021425596de0848036fcd4b_53.png)

Hash function H of x equal to x mod。 This is the size of hash table。10 is the side of the hash table。



![](img/3b0307145021425596de0848036fcd4b_55.png)

So， now。We will take a。Hh table size S 10 as an example。

 I am taking the size S 10 here size can be we can take a hash table of any size。

 So hash function I am taking it as h of x equal to x mod size， and the size is 10。



![](img/3b0307145021425596de0848036fcd4b_57.png)

![](img/3b0307145021425596de0848036fcd4b_58.png)

![](img/3b0307145021425596de0848036fcd4b_59.png)

Now， let us map the elements 8。8 mode 10 gives me 8。So8 is stored here。Three mode to 10 is a3。

 so it is stored here。13 more to 10 is also3。 So， theres a collision。So， this is causing。

Glusionlusion。

![](img/3b0307145021425596de0848036fcd4b_61.png)

Now， the problem is when you change the hash function。

 then there is a possibility that two or more elements are mapped at the same index。

 and that is call collision。 Now we have to resolve this collision。 We have to solve this problem。



![](img/3b0307145021425596de0848036fcd4b_63.png)

![](img/3b0307145021425596de0848036fcd4b_64.png)

![](img/3b0307145021425596de0848036fcd4b_65.png)

There are different methods for a avoiding collusion。

For avoiding collusion or for removing collusion， we have different methods that is。

Open hashing under that is chaining， and next is close hashing under that。

 we have linear probing and quadratic probing。Let us look at them one by one。



![](img/3b0307145021425596de0848036fcd4b_67.png)

First method her for resolving collusionists chaining。



![](img/3b0307145021425596de0848036fcd4b_69.png)

In this method。Then we map any key using same hash function。



![](img/3b0307145021425596de0848036fcd4b_71.png)

Hash function is same。 When we map it， it will be mapped at 8。

 So we will not store the element in the hash table itself。 But added this index， we will。

Add a new chain， and in that we will insert the element。Chain is nothing but a linguist。

3 is mapped here， so we will。Add a nod to a chain， and insert 3。



![](img/3b0307145021425596de0848036fcd4b_73.png)

3uring is also mapped here， so we'll add a new node。



![](img/3b0307145021425596de0848036fcd4b_75.png)

And there we will insert 13。So when there is a collusion。

 we will insert a key element at the same index in a chain。Right。

 so all these elements are inserted into there。Indices。Inside the chain。Now。

 when I want to search for any key element， let us say 13。



![](img/3b0307145021425596de0848036fcd4b_77.png)

Then。I should use hash function。Each of 13 is 13 more size。 That is 3。3 mo。10 gives me3。

 so go to index 3 and search for that element key element in the chain at that particular index。

 So there may be more than one element， so we have to search that entire chain entire linked list。

So that sound the time complexity of hashing will not be order of one， it will be more than one。

 but it will be better when login， it will be faster than login。Now let us look at other methods。



![](img/3b0307145021425596de0848036fcd4b_79.png)

Let us look at next method， linear probing in this hash function is h of x equals x mod size。

 same hash function I am taking。8 is mapped at 8。3 is mapped at 3。13 is also mapped at same location。

 but there is a collusion so we store it at next location 13。



![](img/3b0307145021425596de0848036fcd4b_81.png)

![](img/3b0307145021425596de0848036fcd4b_82.png)

So in this method， we simply find the next free space and store the element in next free space。

 So what is this approach we should give the reasoning in mathematically so here。



![](img/3b0307145021425596de0848036fcd4b_84.png)

Thats explanation。Our actual hash function is。X mode size。



![](img/3b0307145021425596de0848036fcd4b_86.png)

We define a new hash function， H dash of x。That is。Atrox plus。F of I。Moud size。



![](img/3b0307145021425596de0848036fcd4b_88.png)

And therefore for5。Is equals to I。Where I takes values。0 or1 or2， or so on。



![](img/3b0307145021425596de0848036fcd4b_90.png)

No。When we use。13， and we have to insert 13。 Then we say h of 13 plus f of0。Mod1。



![](img/3b0307145021425596de0848036fcd4b_92.png)

This gives us three， but there is a collusion。 So next， we use the same。Hh function。

For a different value of I。And find F of1。Mo than 10。 So we got the answer as 4。

 so that's how the value is stored at location 4 index 4。So we use this S dashx as a hash function。

And we store the element。If there is a collisionlusion， then we take the next value of I。

 even if there is a collision again， then we take the next value of I and so on。Now。

 let us insert the rest of the elements，6 as is stored at 6。And 4。There is a collision。

 already some element is there， so we store it at next place。And 10 is stored here。

Now when I have to search for any key element， let us say Im searching for。4our。

Then I should use this hash function h of x equal to x more size， go to that place4。

 but di is not present there。 Then I should look at the next location that is 4。

 Yes it is found here， so it is found at index x5。

![](img/3b0307145021425596de0848036fcd4b_94.png)

So it means by using the hash function， I should go to the index and start looking for the element。



![](img/3b0307145021425596de0848036fcd4b_96.png)

And the consecutive locations。If I have a key element， if I have to search for key element 24。

Then 24， more 10 gives me。Index 4， when I go to index 4，24 is not present。

 Then I should move to next location。 It is not present。 Next location， not present。

 Next location is empty， so I should stop and say that 24 is not found。

So I can say that for searching any key element， we should use H function。

 go to that particular index。

![](img/3b0307145021425596de0848036fcd4b_98.png)

And start searching for the element。Until the element is found， are empty spaces reached。

 this is the method for searching。

![](img/3b0307145021425596de0848036fcd4b_100.png)

And again， the time complexity will not be order of one。 It will be more than one。

 but it will be better than login。

![](img/3b0307145021425596de0848036fcd4b_102.png)

Now， the problem in linear probing is it causes clustering of element。

 A bunch of elements will be at one single place at consecutive location。

 they will be allocated continuously。 So this may cause a lot of time for searching in the element。



![](img/3b0307145021425596de0848036fcd4b_104.png)

![](img/3b0307145021425596de0848036fcd4b_105.png)

![](img/3b0307145021425596de0848036fcd4b_106.png)

So to avoid the clustering of elements we introduce。



![](img/3b0307145021425596de0848036fcd4b_108.png)

Godraatic probing。Cdratic probing。So this is same as linear probing。There。

If I take the hash function。Then for this also， we define a new function as dash of x。

It is h of x plus。F of i。Moud size。But f of5 is。I square。I takes the value 0，1，2， and so on。

So it' is not f of5 is not equal to I f of5 is equals to i squared。

 so the difference between linear probing is and linear probing。



![](img/3b0307145021425596de0848036fcd4b_110.png)

A linear probing f of i is equals to I we take。

![](img/3b0307145021425596de0848036fcd4b_112.png)

Here， but in cordratic probing。F of I is equals to i squared we take。

That is the difference Now when we try to map the key element， a is stored here。



![](img/3b0307145021425596de0848036fcd4b_114.png)

3。Same place。3。For IS 0， there is a collision， so for IS 1。It will be stored at next location。

An X is 23。So let us find out for 23。Ege of 23。Plus f of0。Mo 10。This gives three。

 There is a collusion。At location 3， there is a collision。The nature of 23。H of 23 plus。F of one。

Mod 10。So， this is 3 plus 1。Moud 10。Is4 at 4 also there is a collision。



![](img/3b0307145021425596de0848036fcd4b_116.png)

Then， we find。23。A of 23。Plus， F of 2。Mod 1。So this is 3 plus F of2 is 4。Mo 10 is a 7。



![](img/3b0307145021425596de0848036fcd4b_118.png)

So this 23， there is a collision here， so it is stored at index 7。



![](img/3b0307145021425596de0848036fcd4b_120.png)

Now you can see that the element is kept few locations away。

 it is not very close to the elements which are getting collusion with 23。

 so there is a gap in between the elements so this will take this will avoid clustering of elements and improve the searching time。



![](img/3b0307145021425596de0848036fcd4b_122.png)

![](img/3b0307145021425596de0848036fcd4b_123.png)

![](img/3b0307145021425596de0848036fcd4b_124.png)

Hope you have understood Hahing。 Thank you for watching this video。



![](img/3b0307145021425596de0848036fcd4b_126.png)