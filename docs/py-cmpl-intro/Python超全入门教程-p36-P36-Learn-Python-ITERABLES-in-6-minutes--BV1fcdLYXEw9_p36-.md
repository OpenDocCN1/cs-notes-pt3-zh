# Python超全入门教程-p36-P36-Learn-Python-ITERABLES-in-6-minutes--BV1fcdLYXEw9_p36-

Hey， everybody。 So today， I got to talk about iterables in Python。 and iterable。 It's a category。

 Any object or collection that can return its elements when at a time is considered an iterable。

 If an object or a collection is considered an iterable， then it can be iterated over in a loop。

 For example， let's create a list of numbers。

![](img/6e8c40c8113edca802f95e776a7965eb_1.png)

![](img/6e8c40c8113edca802f95e776a7965eb_2.png)

Numbers equals a list。 I'll add the numbers 1 through 5， to keep it simple。

Listists are considered iterable。 We can use them within a for loop。In the context of a four loop。

 we're going to be given each element one at a time。Each element that we're working with。

 we can give a temporary nickname。 Let's say number for every number in my iterable of numbers。

Let's just print each number。

![](img/6e8c40c8113edca802f95e776a7965eb_4.png)

This will give us one through five。

![](img/6e8c40c8113edca802f95e776a7965eb_6.png)

The name of the current element in our iterable should be descriptive of what we're iterating over。

 For example， I don't want to rename the current number that we're working with as something like blah。

 blah， blah。

![](img/6e8c40c8113edca802f95e776a7965eb_8.png)

![](img/6e8c40c8113edca802f95e776a7965eb_9.png)

You know this would work， but other people looking over your code might not understand what a blah。

 blah， blah is， and I don't blame them。Each element that we given from our iterable。

 the name should be descriptive of what were given。Or you might see item。For every item in numbers。

 print each item。That's also a good choice。

![](img/6e8c40c8113edca802f95e776a7965eb_11.png)

Now， you could even iterate backwards by enclosing or iterable within the reversed function。



![](img/6e8c40c8113edca802f95e776a7965eb_13.png)

So take our iterable of numbers and reverse it。Then we get the numbers， 5，4，3，2，1。

If you would rather not print each element on a new line。

 we can replace the new line character at the end of print statements with something else。

 Print is a function。 We can pass in a keyword argument of end。

 rather than end each line with a new line character。 Let's end with a space。

This will space out each of the elements， or we could replace it with something else。

Or what about a dash。After each element， a Pedaadeash character。



![](img/6e8c40c8113edca802f95e776a7965eb_15.png)

We could even add multiple characters such as a space， a dash， and a space if we so choose。



![](img/6e8c40c8113edca802f95e776a7965eb_17.png)

It's up to you。Tuples are also iterable。Let's convert our list to a tuple by enclosing our numbers within a set of parentheses。

And I no longer want this reversed。For every number in my iterable of numbers， print each number。



![](img/6e8c40c8113edca802f95e776a7965eb_19.png)

Then again， we get the numbers one through5。

![](img/6e8c40c8113edca802f95e776a7965eb_21.png)

Let's cover sets。I will create a set of fruit， which I will name fruits。For a set。

 enclose any values within a set of curly braces。 Let's add a string of apple。



![](img/6e8c40c8113edca802f95e776a7965eb_23.png)

A string of orange。A string of banana。And a string of coconut。



![](img/6e8c40c8113edca802f95e776a7965eb_25.png)

So with our for loop， let's say for every fruit。

![](img/6e8c40c8113edca802f95e776a7965eb_27.png)

In my iterable of fruits。I will print each fruit。

![](img/6e8c40c8113edca802f95e776a7965eb_29.png)

That would give me apple banana， orange coconut。Now， sets， they're actually not reversible。

 I will attempt to enclose our iterable of fruits within the reversed function。Here's what happens。

We have a type error set object is not reversible。

![](img/6e8c40c8113edca802f95e776a7965eb_31.png)

Setets， you can't reverse。

![](img/6e8c40c8113edca802f95e776a7965eb_33.png)

Let's cover strings。I will create a string of name。 type in your full name。



![](img/6e8c40c8113edca802f95e776a7965eb_35.png)

I'll use my YouTube channel name。For every character。In my iterable of name。

 I would like to print each character。

![](img/6e8c40c8113edca802f95e776a7965eb_37.png)

Maybe I would rather not have each character end with a new line。

I will set the keyword argument of end to be a space。



![](img/6e8c40c8113edca802f95e776a7965eb_39.png)

Last， we have dictionaries， which are the most complicated。Let's name the dictionary， my dictionary。

Dictionaries， you enclose with a set of curly braces， kind of like a set。

But each element is a key value pair。I will add a key of a with an associated value of one。

A key of B。Which has a value of 2， A key of C， which has a value of 3。

If you iterate over a dictionary， the dictionary is going to return all the keys， but not the values。

 We'll test that。For every key， in my iterable。Of my dictionary。Let's print each key。



![](img/6e8c40c8113edca802f95e776a7965eb_41.png)

This would give me the keys of A， B， and C， but none of the values，1，2 or 3。



![](img/6e8c40c8113edca802f95e776a7965eb_43.png)

If you need the values， we're going to follow this iterable of my dictionary。

 use the built in values method。This will return all the values of your dictionary， as an iterable。



![](img/6e8c40c8113edca802f95e776a7965eb_45.png)

But let's rename a key as value。

![](img/6e8c40c8113edca802f95e776a7965eb_47.png)

Because now we're working with the values。Then we're given all the values， one，2， and3。

If you need both the keys and the values， you're going to use the items method。

Will be given both a key and a value。 Make sure that the value in the key is separated with a comma。

Let's print each key， followed by the value。We get the key of a with its value of 1， B，2， C，3。

We can reformat the output， however we want。 Let's use enough string。I will add two placeholders。

 Let's print each key。Equals， then the value。A equals1， B equals 2， C equals 3。



![](img/6e8c40c8113edca802f95e776a7965eb_49.png)

Okay， everybody， so those are iterables， an object or a collection that can return its elements one at a time is considered an iterable。

 meaning that object or collection can be iterated over using a loop。



![](img/6e8c40c8113edca802f95e776a7965eb_51.png)

And well， everybody， those are iterables in Python。

