# Python超全入门教程-p67-P67-Python-SORTING-is...-quite-something--BV1fcdLYXEw9_p67-

All right， people。 So today， I got to explain sorting in Python。

 There's two ways to accomplish sorting in Python， the sort method or the sorted function。

 It depends on what type of data structure we're trying to sort。 Today will'll cover lists， Tuples。

 dictionaries and objects。 This is just my opinion。

 But dictionaries are probably the most complicated to sort。 Even more so than objects。

 Let's begin with lists。 Let's create a list of fruits。Think of some fruit。I will add a banana。

An orange。Apple。Then coconut。I will print my list of fruits。Which gives me banana， orange， apple。

 coconut。Sorting a list is really easy。

![](img/4819c5f43593a74f62af660809ee2da6_1.png)

All we got to do is take our list。Use the built in sort method， and call it。



![](img/4819c5f43593a74f62af660809ee2da6_3.png)

That will arrange the elements in alphabetical order， starting with a for Apple， followed by Ban。

 coconut， then orange。

![](img/4819c5f43593a74f62af660809ee2da6_5.png)

If the elements of a list were numbers， for example。Three， one， five， two， four。

The numbers will be in ascending order。

![](img/4819c5f43593a74f62af660809ee2da6_7.png)

For reverse order within the sort method， we will pass in a keyword argument of reverse and set that to be true。



![](img/4819c5f43593a74f62af660809ee2da6_9.png)

The elements of my list are now in reverse alphabetical order， beginning with orange， Coconut。

 banana， then apple。 That's how to sort a list。 I would say it's the easiest。



![](img/4819c5f43593a74f62af660809ee2da6_11.png)

![](img/4819c5f43593a74f62af660809ee2da6_12.png)

Now we'll move on to Tuples。

![](img/4819c5f43593a74f62af660809ee2da6_14.png)

The elements of a tuple are surrounded with a set of parentheses。

So let's convert our list into a tuple， then I will print our tuple of fruits。



![](img/4819c5f43593a74f62af660809ee2da6_16.png)

To sort a tuple， we'll use the sorted function rather than the sort method， You know what。

 let's attempt to use the sort method and see what happens。I will take my tuple of fruits。

 use the sort method。

![](img/4819c5f43593a74f62af660809ee2da6_18.png)

That's going to give us an attribute error Tple object has no attribute sort。



![](img/4819c5f43593a74f62af660809ee2da6_20.png)

That's why we need to use the sorted function rather than the sort method。

 because tuples don't have a sort method。I'm going to take fruits， equals， use the sorted function。

Then pass in my tuple of fruits。

![](img/4819c5f43593a74f62af660809ee2da6_22.png)

Let's output the result。Apple， banana coconut orange。 They're all in alphabetical order。

 The sodid function will convert our tuple into a list。

 The elements are surrounded with a set of straight brackets。



![](img/4819c5f43593a74f62af660809ee2da6_24.png)

If you would like to keep your tuple as a tuple after sorting it。

 we're going to enclose the sorted function within a Tuple function。



![](img/4819c5f43593a74f62af660809ee2da6_26.png)

To type cast it into a tuple。We have taken our tuple， sorted it。

 all the elements are in alphabetical order， then we have converted it into a tuple。

Now for reverse order。Within the sortded function， after passing in our tuple of fruits。

 we will pass in a keyword argument of reverse and set that to be true。

The elements are now in reverse alphabetical order。Orange， coconut， banana， apple。

 So that's how to sort a tuple。 We use the sorted function。



![](img/4819c5f43593a74f62af660809ee2da6_28.png)

![](img/4819c5f43593a74f62af660809ee2da6_29.png)

Now， we're going to cover dictionaries， which are probably the most complicated。

 Let's change this tuppple of fruits into a dictionary。

We enclose all the key value pairs with a set of curly braces。We have a key and a value。

 The name of each fruit will be the key。 The value， let's say， is the calories per serving。Bananas。

 they'll have 105 calories per serving。Oranges will be 73。Apples will be 72。

Coconanuts are very calorie dense。 They have 354 calories per serving。



![](img/4819c5f43593a74f62af660809ee2da6_31.png)

Here's my dictionary。 A dictionary consists of key value pairs。The name of each fruit is the key。

 the calories per serving is the value to sort this dictionary will use the sorted function。



![](img/4819c5f43593a74f62af660809ee2da6_33.png)

We're going to reassign our dictionary equals call the sorted function。

Then pass in our dictionary of fruits。 However， there's one more step。

The keys are sorted in alphabetical order， but we lose the values， they're truncated。

 we have converted our dictionary into a list。The elements are surrounded with a set of straight brackets。

 We're going to take our fruits， call the items method。

The It method will return a tuple for each key value pair in my dictionary。

 the items method returns each pair as a tuple。Then we are going to type cast it into a dictionary by surrounding the sortded function with the dictionary function。



![](img/4819c5f43593a74f62af660809ee2da6_35.png)

And now all the keys are sorted alphabetically， apple， banana， coconut， orange。

Each key has its value of calories per serving。

![](img/4819c5f43593a74f62af660809ee2da6_37.png)

For River alphabetical order， let's copy what we have。

This is where it gets complex within the sorted function。After we call the items method of fruits。

 we're going to pass in another argument。A keyword argument， we will set the key equal to。

A Lambda function， the It method is going to return a tuple during each iteration。

So for the Lambda function， we're going to take each tuple， which will be named item。

 that's the parameter。Co， what would we like to return？

We're going to return our tu of item at index of zero。For the first pair in our dictionary。

We're returning the value at index 0。 that would be the key。

 indexex 1 would be the value for every pair of items in our dictionary， take each pair。

 return the first element， return the element at index 0， which means the key。

Then we have one more argument。 So after the key for reverse alphabetical order。

We will pass in a keyword argument， we will pass in a keyword argument of reverse and set that to be true。



![](img/4819c5f43593a74f62af660809ee2da6_39.png)

Yes， it's very complicated。So now our dictionary is sorted in reverse alphabetical order by key。

 We have orange， coconut， banana， apple。

![](img/4819c5f43593a74f62af660809ee2da6_41.png)

To sort the dictionary by value， here's what we'll do。



![](img/4819c5f43593a74f62af660809ee2da6_43.png)

Again， we'll take our fruits。Equals， call the sorted function。Take our dictionary of fruits。

 call the items method to return each key value pair as a tuple。

 then type cast it back into a dictionary。After we call the items method。

We will pass in a keyword argument where the key equals a lambda function。

For every tuple of our dictionary， take that tuple of item。Colon。

 return the value at item index of one。Zero refers to the key， an index of1 applies to the value。



![](img/4819c5f43593a74f62af660809ee2da6_45.png)

So now， our dictionary is sorted by the values in ascending order。

Apples have the least amount of calories per serving， then oranges， bananas， then coconuts。



![](img/4819c5f43593a74f62af660809ee2da6_47.png)

That's how to sort a dictionary by value。 To sort the values in reverse order。

 Let's copy what we have。After our keyword argument of key。

We will pass in a keyword argument of reverse。Then set that to be true。



![](img/4819c5f43593a74f62af660809ee2da6_49.png)

The values in my dictionary are sorted in reverse。The first key value pair has the most amount of calories。

 which would be cocos。 then banana， orange， apple。 Those are a few different techniques to sorting dictionaries。



![](img/4819c5f43593a74f62af660809ee2da6_51.png)

We can sort by key or by value。

![](img/4819c5f43593a74f62af660809ee2da6_53.png)

All right， now we're going to move on to objects in this example， we will create a class of fruit。

Within this class， we will need a constructor。When we create a fruit object， we will need a name。

And calories for calories per serving。Self dot name equals name。Self dot calories。Equals calories。

I'm also going to use a magic method。It's REPR， meaning represent。

When we attempt to print one of these objects， we can create a string representation of that object。

 so if I was to print a fruit that we create， we will call Dunder represent to represent that object。

So we will return enough string。I'll add two placeholders。We will display self Don name。

 What's the name of this fruit。And self dot calories。 What are the calories per serving。

We will create a list of fruit objects。Fruits equals a list。I will call the fruit Conor。

For the first fruit。The name will be banana， calories will be 105。For the second fruit。

 we'll call the fruit constructor。Pass an apple。Calories 72。For the third fruit。

 called the fruit constructor。The name will be orange。Caallories，73。

I'm going to put each of these on a new line for readability。Then for our last fruit。We have coconut。

Calories， 354。

![](img/4819c5f43593a74f62af660809ee2da6_55.png)

Just to test everything， I'm going to print my list of objects。



![](img/4819c5f43593a74f62af660809ee2da6_57.png)

Behind the scenes when we print each of these objects。



![](img/4819c5f43593a74f62af660809ee2da6_59.png)

We'recaling the method of Dunder represent。Were displaying the fruit's name， colon。

 then the calories per serving。

![](img/4819c5f43593a74f62af660809ee2da6_61.png)

I'm going to collapse this class just so it's easier to see everything。



![](img/4819c5f43593a74f62af660809ee2da6_63.png)

To sort this list of objects， I will reassign it to fruits。

 fruits equals we will use the sorted function。We'll pass in our list of objects。

Pass in a keyword argument of key。Key equals a lambda function。 During each iteration。

 the lambda function is going to be provided with one of these objects， beginning with the first。

That's going to be the parameter， each fruit。For every fruit that we iterate over。

 we will return the fruit's name attribute。And sort by that， using the keyword argument of key。



![](img/4819c5f43593a74f62af660809ee2da6_65.png)

These objects should be sorted by their name。

![](img/4819c5f43593a74f62af660809ee2da6_67.png)

We have apple， banana， coconut， orange。

![](img/4819c5f43593a74f62af660809ee2da6_69.png)

For reverse alphabetical order。All we got to do is pass in that keyword argument of reverse。

 Se that to be true。

![](img/4819c5f43593a74f62af660809ee2da6_71.png)

These objects are now in reverse alphabetical order by their name， O， coconut banana， apple。



![](img/4819c5f43593a74f62af660809ee2da6_73.png)

![](img/4819c5f43593a74f62af660809ee2da6_74.png)

Then let's do calories。Within our lambda function， sort by the fruits， calories。



![](img/4819c5f43593a74f62af660809ee2da6_76.png)

We have apples with the least amount of calories， 72， then oranges， banana， coconut。



![](img/4819c5f43593a74f62af660809ee2da6_78.png)

Than to sort by calories in reverse order。We will add one additional keyword argument of reverse。

 Se that to be true。

![](img/4819c5f43593a74f62af660809ee2da6_80.png)

All right， so now we are sorting these objects by what has the most amount of calories。

Which would be coconuts， bananas， oranges， then apples。



![](img/4819c5f43593a74f62af660809ee2da6_82.png)

All right everybody， so those are a few different sorting techniques。 We've discussed lists。

 tuples and dictionaries which are in my opinion， the most complicated than objects with dictionaries and objects。

 we set the key as a lambmbda function and well everybody。

 those are a few different sorting techniques in Python。



![](img/4819c5f43593a74f62af660809ee2da6_84.png)

![](img/4819c5f43593a74f62af660809ee2da6_85.png)