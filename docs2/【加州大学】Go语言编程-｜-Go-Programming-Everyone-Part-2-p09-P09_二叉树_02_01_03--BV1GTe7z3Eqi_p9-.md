# 【加州大学】Go语言编程-｜-Go-Programming-Everyone-Part-2-p09-P09_二叉树_02_01_03--BV1GTe7z3Eqi_p9-

![](img/03a8fd7e38688f23064eb05687c5661d_0.png)

So a binary tree is a slightly more complicated self referential data structure。

And it has many uses in computing。So recall， we've already done a linear list， again。

 a very important data structure。 and in a linear list。

You have a pointer that points with the next element。What makes the binary tree more complicated is。

There are two elements that the next element points to， so the binary tree grows exponentially。

And that's very important to some of its usess， which we will talk about。

Now the tree has a root node。And then it has a left and right off springring。

 So that's going to be represented by two pointers。And then a typical binary tree。I。

It can hold n items where。The length that you have to traverse。

Unlike a linear list where you'd have to traverse an items to get through the n element would only be log base2 of n。

 so that's considerably shorter if you have 1000 elements， log base two of 100， approximately 10。

 So in a fairly well balanced binary tree。You can store a thousand elements。And the search。

May involve。At most。Going through10 links。So this allows the tree to be a very efficient data structure for maintaining and accessing and updating a large amount of data。

 and therefore it's extremely useful throughout computer science and。Algorithms use。Okay。

 so visually， this is what a binary tree looks like， there's a root。

There's a left and right offspring and then。呃。依据。Tree element can have at most two offsprings。

 There are， of course， generalizations。 You can have a ternary tree。

 You can have a tree with any number of offsprings。But。

The binary tree is most useful because it already has a characteristic that its depth is going to be largely about log n。

Now it is possible to have a skewed binary tree where you just have， for example。

 left offsps and then the elements。It ends up looking like。A linear list that goes off to the left。

With all the other， with all the right elements being no pointers。 But that would be very skewed。

And that wouldn't be very useful。Okay， so let's see how we actually build that and go。

 we have a node， and now the node， unlike the linear list node。Has a place where theres data。

 and that could of course the key could be way more than just an integer。

 could be a whole bunch of data。And then there's the left offspring and the right offspring。

And that's self referential。And then the head of the tree of， a course。Also， a pointer to node。

 so a pointer to node is the head， and then each internal node has the left and right offspring。Okay。

 let's move on。Now。We want to see how you insert a node into a binary tree。 And in effect。

 how you would build。A node。 and this is going to be。A binary tree that has an order to it。

 a sordid order。So we're going to。Push smaller keys to the left and larger keys to the right。

And that'll enable us to later search effectively for a key in our binary tree。 so in doing that。

We first see is the binary tree empty。A empty binary tree would have its root as nil so we can check the special value nil。

 remember nil is the universal value for a null pointer。And if it's still。

 then we have to create the binary tree in effect creating the root node of the binary tree。

 and that means we return。An address of。Noode where the key is the key element。

And then there's the left element。Is nil， and the right element is nil。 So it has no offsprings。

 It's just a single node created with a key。 And that's because。The binary tree initially was empty。

If the binary tree is not empty， then we do a search on the key value。

If the key is less than the root of the key。Then we do an insertion。On。

And we assigned that to the left。呃。The left pointer value。Otherwise。

 we do it and we assert to the right。So very simple routine， three cases。Tre is empty。

 create the tree by creating the root node。Tree isn't empty。

Go and see if you're off to the right or off to the left。And if you're off to the right。

 do an insert on the right， otherwise do an insert on the left。Okay。Now let's move on。呃。

And now we're going to try and search。For an existing key that sits in the binary tree。

And here we're going to use recursion and recursion is going to be just like recursion was useful in the linear list case。

 recursion is very useful。In。Any of these self referential data structures。

 recursion is a very natural form。A flow of control。

 It's not like you couldn't convert this to something using loops， but。The logic。

 and you should get used to that， the logic is much better suited to a recursion。So again。

 we're going to try and look up a key inside the tree。

 one of the possibilities as the key isn't there。If the root is nil。

 then we can't have the key and there's nothing to search。 So a base case is to return。

False if there's nothing left to search。Otherwise。We have to compare the key we're searching for to the root。

K。And if it's found， we can stop。And we could say， a， we found it returned true。Now， by the way。

 you could also， if you needed to， you could also do a return where not only would you return true。

 but you might return the location。Of that value， the node that's holding that key。

 because maybe you want to do some update or some further operation on it。嗯。And then the other case。

 of course， is。诶。We didn't find the key。So we can't stop。

 so then we use the property that tree has been ordered。

And we go to the left if the key is less than the root key and we go to the right。

 If the key is not less than the root key。 So we then do the recursion， the general recursive step。

 which is search root left key or search root right key。 and that's the recursion， ultimately。

 it's going to stop with either return of true， if it finds a key， or return of false。 if everything。

Ends up。As what might be called the leaf node where the leaf nodes are nil okay。

 so that's our search routine again， the logic is recursive now let's just look at how we're going to use this and show it。

So we're going to start with a root。Which is just again， a pointer to node。

And here are the keys that we want to insert we're going to have a slice。

 an integer slice and we'll have。Eight keys。That'll show up in that。In that tree。And then。

Over that slice。We'll do the insert and the insert is how we build the tree。

We've seen the insert before and then once we've built a tree。

 we're going to search and look for search key equals6 and of course we saw that six was placed in the tree in the build part。

 so we're going to say that it's found。Otherwise， we wouldn't find it， but in this case。

 we're going to find it。All right， so that's a simple。Use of the binary tree。

Establish how to create it， establish how to search it。So now let's turn to running the code。

We'll run the code showing how to build this ordered tree。

 remember it's ordered because we can compare the key and go left or right and we can recursively search it。

Later。We might look at how to build something which is called a balance tree。

 which is more efficient for。Searching and updating， okay？

So let's look at code on my terminal for the binaryary tree program。Again。

Self referential data structure。So a node has just got node embedded in it。

It's got a left and a right part。Which are both pointers and then the key information。

 which in our simple case is just an int， but obviously if you wanted to build a huge database。

 that could be。Itself， a very complicated struck。So here's insert again。The first part of insert is。

 oh， we don't have a tree yet。 So we have to create the tree。 So that's why we're returning。

A percent node， and we're building a key with the information nil， nil as the left and right node。

Otherwise。We have the look。To the left or the right。 And depending on which。Where the key is。

 we go to the left or the right， and we point。We perform the insertion at the appropriate spot。呃。

In the tree so that that tree is sorted。By this left and right process。Finally。We're showing again。

 a recursion in which。We can return。Whether we could find a key inside the tree。

So this is a very simple search。 We're not looking factually returning the node。

 We're just saying true or false。 The key sits somewhere in the tree。 and we have to find it。

 and we find it by first seeing if the tree。If where we are is empty， no， nll。

 then we're we haven't found it。 So we return false otherwise。We do our left and right search。

 excuse me we first see if we found the key。So the equals equals is a test on whether root do key is equal to the key。

 and then we return true， we're founded。Otherwise， we have to go either to the left or the right。

And in each case， we call the routine recursively。So ultimately。

 we're going to end up with either false or true。And here's our main function。

We're building a tree out of a slice。The slice has， I think， nine values。

 so there'll be a binary tree with nine nodes。We do a four。On the keys range。Inserting the keys。

 the individual keys。Into the intoto the binary tree。And then we try to see if。We can find 6。

 So if everything is worked right，6 is going to yield true。It'll say printf。

 the printf says he has been found in the binary tree。 Otherwise， it's not been found。

And in this go code it's really a very simple implementation of a binary tree with insertion and search functionality。

 so let's just try and run the code。And。What you see is indeed。

The key has been found in the binary tree。So very simple。

Easily done and you should play with that example。Okay。



![](img/03a8fd7e38688f23064eb05687c5661d_2.png)

![](img/03a8fd7e38688f23064eb05687c5661d_3.png)