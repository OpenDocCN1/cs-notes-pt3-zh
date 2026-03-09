# 特伦托大学【中英⚡学习编程：基础知识｜Learn to Program： The Fundamentals】 p33 P33 01_循环遍历索引 -BV1kQ11B5EWa_p33-

![](img/cb17adcb4d26ea65543b9ecadd9087e0_0.png)

In previous lectures， we used four loops to pass over the characters of strings and the items and lists。

In this lecture， we are going to use for loops to pass over the indices of strings and lists。

 and this will allow us to solve problems that we can't currently solve using forlips。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_2.png)

The first problem let will tackle is to count the number of neighboring pairs of characters that are the same within a string。

So here's an example string。And in this string， there are three pairs of neighboring characters that are the same。

 The C's， the F's and the G's。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_4.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_5.png)

In order to solve this problem， we need to compare neighboring pairs of characters。

 so the string at index 0 needs to be compared with the string at index 1。

The string at index 1 must be compared with the string at index 2。And so on。

 until we reach the second last character， the string at index negative 2。

And we compare it with the last character of the string， the string and index negative  one。

Generally speaking， we can describe this as comparing the string at index I with the string at index I plus1。

We'll use the range function to generate these numbers。

Zero1 up to and including negative 2 the I values in our comparison。As a reminder。

 range has three parameters， one required and two optional。

 The required parameter is the value at which you want to stop the sequence。And optionally。

 we can also provide the start and the step。 In this case， the start we want is 0。

 which is the default。And the step is one， which is also the default。

 so we only need to use the stock。And we want to stop at the length of the string，-1。 In other words。

 we want to go up to and including length of the string-2 or the second last character of the string。

And we indicate you this using length of strength -1 up to， but not including that value。

And then the values of the indices are printed。Now that we've written this for loop。

 we're going to use that same header in our function to count the repeated pairs of characters in the string。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_7.png)

The function that we're writing is count adjacent repeats。 It has a single string parameter。

 and returns an int。And when we call the function passing the example string as an argument。

 the function should return three。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_9.png)

For this function， we need to keep track of how many repeated characters we've seen。

 so I'm going to use a variable named repeatats to do that。

 and repeats will have an initial value of0。We want to go over the characters of the string。

 pass over them， and we need to use their indices this time。We wrote this for loop header already。

 we're starting at index0 and going up to the second last character of the string。

In the body of the for loop， we want to compare the character at position S at index I with the one that comes after it to see whether they are equal。

 so we can use the equality operator for this comparing S at index I with S at index I plus 1。

When they are equal， we found one of these adjacent repeats so that repeats variable should be increased by  one。

At the end of the loop， after it has exited， we can return the value that repeats refers to。Finally。

 let's just run this function call to ensure that it's working as expected。To do that。

 I need to execute or run the module。And now we can call the function。And it returns three。

 as expected。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_11.png)

So to summarize， it's because of the fact that we want to compare an element of the list with another element in the list that we are using the indices。

 It's not enough to know what the value of the item is。

 We need to know where the item is in the list in order to determine which other element to compare it with。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_13.png)

To gain a better understanding of what's happening when this code executes。

 we'll trace it using the Python visualualizer。The first time I hip forward。

 the function definition is evaluated and we' taken to line 19。

 where I've put a call to the function using a slightly smaller example。When the function is called。

The parameter S refers to the string ACCFF， H， which we passed as an argument to the function。

After line 11 has executed， repeat refers to the value 0。On line 13 is the first line of the forlo。

I will get the initial value of 0。I initially refers to zero。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_15.png)

And if condition is first checked。 So S I S at 0 is a is compared with S I plus 1， S at 1。

 which is C。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_17.png)

These characters are not equal， so the body of the for loopop is not executed。

We move on and increment I， so I gets the next value that range generates， which is one。Now。

I refers to one。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_19.png)

And S at1 is compared with Set 2， because the characters here are equal。

 the body of of if is executed， and repeats will be increased by one。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_21.png)

Repeatets now， but first to the value 1。And I gets the next value that range generates， which is 2。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_23.png)

The string at index 2 is compared with the string at index 3， and they are not equal。

 so the body of the F is not executed。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_25.png)

We advance to the for loop header again， and I will be the next value that range generates。

 I refers to 3。 The string at index 3 is compared with the string at index 4。

 Those two characters are equal。 So the body of the if is executed this time。

 Reats is increased by one。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_27.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_28.png)

So repeats now refers to the value2。And I advances to the next value， which is 4。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_30.png)

The stringent index 4 is not equal to the string at index 5， so the body of if won't be executed。

 and notice that this is the last pair of characters that we need to compare。

 So when the string at index negative2 or the second last character of the string is reached。

 that will be the last iteration of the for loop。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_32.png)

We reached the header one more time， and there are no more numbers generated by range。So after this。

 Python advances to line 17。The value to be returned is the value of repeats， which is2。

And that is returned and then printed on line 19。Now let's write another function that involves looping over indices。

This function is named Shi left。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_34.png)

It has a single list parameter and modifies that list， so the return type is none type。

 none is returned。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_36.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_37.png)

The modification to the list is that each element of the list or each item is shifted one position to the left。

And the first item is shifted or moved to the last position。

A precondition to this function is that the length of the list is at least one。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_39.png)

Here's an example list that has four strings， strings， A， B。C， and D。

The strings will be shifted to the left， moving B from index 1 to index 0， C from index 2 to index 1。

D from index 3 to index 2。And a from 0 to the last position where D originally was。Therefore。

 the resulting list is B。D and a。In the example， I showed moving B to the position that A was in and then C to the position that B was originally in。

One thing that I didn't explicitly show in the example is that when we move B into A's position。

 we need to keep track of a。 What value is at index 0 in order to later be able to move that value to the last position in the list。

The variable first item is what I'm going to use to keep track of this。

 so it gets the value at list index0。And we will then be able to take the value from index 0 and put it in the last position later on。

The task that we're doing is the shifting of items starting from one。 So I'm using range again。

 The first index that I will work with is index 1。And the stopping position is the length of the list。

The task is that we would like to take the list at position。I -1。And set it to the element。

 to its right。So in other words， if1 is the first value of I。

 we're going to take the list at position  zero and have it get the list at position1。

So once all of the elements have been shifted to the left。

 we then want to take the element that was originally in the first position and move it to the last。

The last element of the list can be indicated using negative 1。

And we will set that to our first item variable， which hung on to the original value at index0。

At this point， L L has been modified and the function can exit。Let's call the function。In the shell。

 I will create a list with the same example of values that we used。

We can call shift left passing L as the argument。And now， when we examine the contents of L。

 we see that the values have indeed been shifted to the left with the first item being moved to the last position。

We will once again use the Python visualizer to visualize the execution of this function call。

 This will help us gain a better understanding of the code。

 and it's something that you should be doing as youre writing your code。

The function is first defined。And on line 17， the letters variable refers to a four element list of strings containing the strings。

 A， B， C， and D。Now， the function shift left is called。The functions parameter。

 L refers to the list of strings that was passed as an argument to the function。On line 10。

 first item is a variable that gets the value of the listedit index0。First item refers to the string。

 a。The four loop begins on line 12， and the initial value of I is one。I refers to one。

 the first value generated by range。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_41.png)

In the body of the loop， the'll list at index 0， I minus-1。Gets the value of the list at index 1。

 So I list at 0 is currently a。 The list at one is B， and we're about to assign the list at 0。

 the value of list at  one。

![](img/cb17adcb4d26ea65543b9ecadd9087e0_43.png)

Now we can see that the list at 0 refers to B， and so does the list at index1。

That's why we use the first item variable to keep track of the value that was initially at listist and index 0。

 We're going to need that later when we move the first item to the last position。

Back to the loop on line 12， the value of I will be increased。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_45.png)

Ira now refers to two。And the list at index1 will get the value that is currently。At Felicit index 2。

List at 2 refers to C， and list at one is about to be assigned that memory address。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_47.png)

So now both list at one。And list at2， refer to the sea。I gets the next value， which is 3。

And the list at index。2 is about to be assigned the list at index 3。So we have a list with B， DD。

And it's time to replace the last D with the A。That's what happens on line 15。

 The list at the last position will be assigned the value that was originally at index0。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_49.png)

![](img/cb17adcb4d26ea65543b9ecadd9087e0_50.png)

This is the last line of our function call。So the function finishes executing and returns。

Then letters is printed。 So notice that what was printed when the function returned was the value none。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_52.png)

And now， letters with the values。With the strings， B， C， D， and A is displayed。



![](img/cb17adcb4d26ea65543b9ecadd9087e0_54.png)