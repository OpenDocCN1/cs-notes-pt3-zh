# 特伦托大学【中英⚡学习编程：基础知识｜Learn to Program： The Fundamentals】 p36 P36 03_嵌套循环 -BV1kQ11B5EWa_p36-

![](img/2dc490641e16553d7f515e2be3a0098a_0.png)

The bodies of loops can contain any statement， including other loops。

 We'll explore that in the lecture。

![](img/2dc490641e16553d7f515e2be3a0098a_2.png)

Here we have a loop inside another loop， the outer loop。Has I range over the values 1011 and 12。

 And for each of those iterations， J is going to range through 1，2，3 and 4。When I visualize this。

 I starts off referring to the value of 10。Ja doesn't exist yet because we have just reached the foreloop for the first time。

 this inner forloop。Jay is going to take on the value 1 in the first iteration。I still refers to 10。

And we're about to print I J， so we should see 10 and 1 appear。

Notice that as soon as we printed 10 and 1， we went back to line 2， not to line 1。

 And the reason for that is we are going to completely execute this inner for loop until Jay has gone through the numbers 1。

2，3， and 4。So that means that J will take on the value， too， next。

Then we're going to print tend into2。Now J is going to take on the value3。Jane now refers to 3。

 and will print 103。And4。Now， we are done with this inner fore loop。

 And so we're going to jump back out to line 1 because we have completed execution of the body of the outer fore loop。

Now， I is going to take on the value 11。Ja is going to take on the values 1，2，3， and 4 again。

And now we're done with this inner loop。 So we'll go back out to the outer one。

Now we will do the last iteration of the outer loop。My starts office 12。

And Jay is going to go through the numbers 1，2，3， and 4 again， and I will not change again。Now。

 we are done with this inner loop。We go back and check the outer loop once more。

And we are done with the program。Here is another example。

 We will keep track of a list of lists of numbers。These are going to represent grades。

 So perhaps a student will have received a 70， a 75 and an 80 in one class。

 And in another class that they're taking， maybe they have a 70 and 80， a 90 and 100。

And in the third class， they have an 80 and a 100 and。

They want to know what the average is for each of these list of grades。

We're going to write a function to calculate this list of averages。But before we do that。

 we're going to start with a simpler problem。 Just find the average of a list of numbers， so。

Let's say that in one class， maybe be English。

![](img/2dc490641e16553d7f515e2be3a0098a_4.png)

你啊。List of grades that we're going to calculate the average of is 70，75 and 80。



![](img/2dc490641e16553d7f515e2be3a0098a_6.png)

In order to calculate the average of this， we need to go and add up all the assignment marks。

 and then divide by。How long that list is。There's our accumulator。And then for each mark in English。

What we're going to do is we're going to add the mark to the。你。The total is 225。

 We need to divide that。By the length of。都还系。Now that we know how to calculate the average of a list of numbers。

 we would like to do this for each of the lists in our grades list。

 and we would like to assemble the result into a list of these averages。

As we're developing this function， we need examples。

The first example we're going to do is this list of grades that we have started with over on the left。

The average of 70，75 and 80 is 75。 The average of 7080，90 and 100 is 85。

 The average of 80 and 100 is 90。 All of these are flux。

Let's make this window just a little bit wider。The type contract is next。

 What we have is a list of list of numbers now。These are all integers。

 but we can certainly imagine giving floating point results for scores on a piece of work。

The type contract is going to be a list of list of number。And that is the the type of the parameter。

 And we are going to return a list。A lot。Were fine with averages is the name， so。

Believe it as that such。And we're going to take in， Levy。Graade says the name of the parentm。

In our description， this is going to return a new list。In which each item is the average。Of。

The grades。indy。Inner list at the corresponding。Position。That's great。Well。

 we know we're building a new list， and we're going to be doing this nested list by nested list。

 So we're going to be accumulating this result。 So we'll have。

Maybe averages as the name of our variable， which is going to be the list of averages at the end。

And when we're done。We know we want to return averages。Well。



![](img/2dc490641e16553d7f515e2be3a0098a_8.png)

We want to put into averages the average of each of the lists inside our grades list。



![](img/2dc490641e16553d7f515e2be3a0098a_10.png)

So。For each of the sublists in the grades list。What we want to do is。

Calculate the average of grades list， and append it。2 averages。



![](img/2dc490641e16553d7f515e2be3a0098a_12.png)

Well， we have code that does that over on the left。



![](img/2dc490641e16553d7f515e2be3a0098a_14.png)

We know that we want to start total off at0。 and then。For each mark in。This particular subgrade list。

We would like to add it to total。And then once we are done with that。

sumumming up the values in the grades list， we would like to append to averages。The average。

And we're done。We will now call this in the visualizer and watch it execute。



![](img/2dc490641e16553d7f515e2be3a0098a_16.png)

We have added two statements at the bottom of this file。The first one creates the the nested list。

 and the second one calls the average as function passing in that list。



![](img/2dc490641e16553d7f515e2be3a0098a_18.png)

Let's visualize this。We first define our function。Next。

 we are going to create about 10 or so objects。

![](img/2dc490641e16553d7f515e2be3a0098a_20.png)

Gras refers to a list with three items in it。The first one is a list with three items in it，70。

75 and 80。The second one。ItRes to a list that has 7080，90 and 100 in it。

 And the third item at index 2 in this outer list refers to a list with two items in it，80 and 100。



![](img/2dc490641e16553d7f515e2be3a0098a_22.png)

![](img/2dc490641e16553d7f515e2be3a0098a_23.png)

![](img/2dc490641e16553d7f515e2be3a0098a_24.png)

This first， nested list。Contains。70。75。indy。The second nestedless。Contains 70，80。Then where is it。

90 and 100。This third， nestedless。Contains8。And 100。So， indeed。

 the list structure that is built in computer memory。



![](img/2dc490641e16553d7f515e2be3a0098a_26.png)

Is a representation of what we have done on this line。Now， we're going to pass that list。



![](img/2dc490641e16553d7f515e2be3a0098a_28.png)

Into the averages。Look'll at a stack frame for function averages containing parameter grades。

 referring to that same list。We will start。Here's a fun one。

 We will start a new variable averages that is in empty less。

Notice we also have a function averages outside。 there are obviously two very different things。Next。

We're going to go through the lists inside this outer list， so。

Gras list is initially going to refer to the list at index at memory address I D 3。

Then we're going to go through 70，75 and 80， add them up and divide by the length of that list。

We'll start total off。At 0。Thenhan for every mark in the grades list。 Well。

 Mark is going to start off at 70 and then 75， and then 80 each iteration here， we're going to。

Take that 70 here on line 17。 and we're going to add it to the total which is 0。 So we'll get 70。

 of course，70 plus 0 is 0。We will assign that to total。On this next iteration。

 we're going to have Mark B， the 75。

![](img/2dc490641e16553d7f515e2be3a0098a_30.png)

Now， we're going to take 75。And add it to 70，70 plus 75 is a hundred and45。

 and we will assign 1 and 45 to total。

![](img/2dc490641e16553d7f515e2be3a0098a_32.png)

![](img/2dc490641e16553d7f515e2be3a0098a_33.png)

On the next iteration， we're going to assign the 80 to mark。 That's what this for loop does。

 grabs the last item in the list。

![](img/2dc490641e16553d7f515e2be3a0098a_35.png)

Mark now refers to 80。On line 17， we have an assignment statement。

 The right hand side evaluates to 1 hundred45 plus 80 or 225 will assign 225 to total。

We have now gone through all the items in that first vested list。 We've done the 70 to 75 in the 80。

 And so this for loop will now terminate。We will calculate 225 divided by the length of grades list。

 which is 3， and we will append the result to the averages list。

Now averages refers to a list containing 75225 divided by 3 is 75。

We have completed execution of the first iteration of the outer for。We will now。

 on this next iteration， get the second list with four items in it。

Gra's list now refers to that second list with。70，80，90 and 100 in it。We will initialize total to 0。

Reset it。 and then we're going to go through the four numbers。2。3。4。And we're done。

 And now total is 340， the sum of 70 plus 80 plus 90 plus 100。We will append 340， divided by4。

To our average is list。And that happens to be 85。And now， for the third nest， at least。

Graade's list refers to the list with two items in it。 That's 80 and 100。Will， reset total to 0。

There is the 80 that we're dealing with。Mark is now 80。Well add 80 to 0， giving us 80。 Of course。

 We will then get the 100。And we'll add the two together。And then。

We will append 180 divided by the length of that nested list or two。

 So hundred80 divided by  two is 90。We've now gone through all three of our nested lists。

 So this outer loop will terminate。And we're done。 We will now return。This average is list， which。

 as a reminder， now contains 75，85。And tonight。About to return that value。

We don't do anything with it in the main program。 So when I click forward， the program will just end。



![](img/2dc490641e16553d7f515e2be3a0098a_37.png)