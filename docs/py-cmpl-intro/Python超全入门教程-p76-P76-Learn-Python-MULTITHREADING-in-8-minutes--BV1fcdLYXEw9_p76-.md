# Python超全入门教程-p76-P76-Learn-Python-MULTITHREADING-in-8-minutes--BV1fcdLYXEw9_p76-

So yeah， I'm going to talk about multi threading and Python today。

 Multi threading is used to perform multiple tasks concurrently。 Think of it like we're multitasking。

 We're performing a few different actions at once。 For example。

 I could study and listen to music and eat something at the same time。

Multi threading is good for IO bound tasks， IO， meaning input output。

 such as reading files or fetching data from an API， things that may take some time to do。

 and we don't know when it's going to end exactly to multi threading will import the threading module。

Import threading。We access the threading module， then called the thread constructor and pass in a target function。

 What we'll do for this demonstration。 Let's say we have a bunch of chores to do。

 We have to walk the dog， get the mail and take out the trash。

 Let's define some functions to handle that。We have a function to walk the dog。

Then I will print the following message。You finish。Walking the dog。

Let's create a function to take out trash。Then， we will print。You take out the trash。

Then another function of get mail。As in get the mail from the mailbox。Then， I will print。

You get the mail。Just to simulate these functions taking an indeterminate amount of time。

 I'm going to import the time module to help us。Let's say walking the dog takes eight seconds。

I will access the time module。Call the sleep method and pass in eight for eight seconds。

When we call the walk dog function， we'll wait around for 8 seconds， then finish walking the dog。

 This chore will take quite a bit of time to complete。



![](img/df30b99d4a6a270538b1500402a6549f_1.png)

Taking out the trash， it's fairly quick。Taking out the trash will take two seconds。

Getting the meal will take four seconds。Let's call these functions and see what happens。

We will begin by walking the dog。I will call the walk dog function。

Followed by take out trash function。And the get mail function。



![](img/df30b99d4a6a270538b1500402a6549f_3.png)

Here's the result。We're going to wait around for 8 seconds until the walk dog function is complete。

Right about now。You finish walking the dog， you take out the trash。And you get the mail。



![](img/df30b99d4a6a270538b1500402a6549f_5.png)

These functions are running on the same thread， the main thread， our main Python program。

We have to complete these chores in order， one by one。Because they're all running on the same thread。

 Instead of walking the dog。 And then when we're done， taking out the trash。

 And then when that's done， we get the mail， We could accomplish all three tasks at the same time。



![](img/df30b99d4a6a270538b1500402a6549f_7.png)

Let's say we have a thread object。 We can say a thread1 or to be more descriptive。

 Let's say we have chore one。Let me zoom in a little bit。Chhoor 1 is going to contain a thread。

We will access the threading module。Call the constructor for a thread。

We have to pass in a keyword argument of Ta。 What is the first chore that we have to do。

 Let's walk the dog。To start this thread， we will take our thread object of chore 1。

And call the start method to start it。Okay， let's do this with chore 2。Access the threading module。

Called the thread constructor。Pass in a target。Than the name of a function。 Take out trash。

Core 2 dotstart。And then we have chore3。I'll just copy what we have because I'm feeling lazy。

Choore 3 will be get mail。

![](img/df30b99d4a6a270538b1500402a6549f_9.png)

Here's the result now。We finished taking up the trash first。Then we get the mail。

Then we finish walking the dog。So we're executing these functions concurrently， we're multitasking。

 we're taking out the trash and getting the mail and walking the dog all at the same time。



![](img/df30b99d4a6a270538b1500402a6549f_11.png)

![](img/df30b99d4a6a270538b1500402a6549f_12.png)

One thing that I did want to point out， notice how we finished taking out the trash first。

 followed by getting the mail， then walking the dog。

 These tasks finished in a different order compared to when we weren't multi threading。

 That's because taking out the trash finished first。It took two seconds。

 Getting the mail took four seconds and walking the dog took the longest。 It took 8 seconds。

Previously， we finished walking the dog first， then took out the trash， then got the mail。



![](img/df30b99d4a6a270538b1500402a6549f_14.png)

When all the chores are complete， I would like to print a message。I will print the following。

All chores。Are complete。

![](img/df30b99d4a6a270538b1500402a6549f_16.png)

Here's what happens currently。We get this message that all chores are complete。

 but we haven't finished any yet。We're still completing them。



![](img/df30b99d4a6a270538b1500402a6549f_18.png)

There may be at times you want your program to wait for all threads to finish。

Before we print to that confirmation message that all chores are complete。

We're going to use the join method。Take each thread。Use the join method。

We'll do this with Chore 2 and chore3 as well。With the join method。

 we will wait for these threads to finish before continuing with the rest of the program。

 Here's the result now。

![](img/df30b99d4a6a270538b1500402a6549f_20.png)

You take out the trash。You get the mail。And you finish walking the dog。All chores are complete。



![](img/df30b99d4a6a270538b1500402a6549f_22.png)

When constructing a threat object and we have a keyword argument of targetrg。



![](img/df30b99d4a6a270538b1500402a6549f_24.png)

If some of these functions take parameters， for example， with the function of walk dog。

 let's say we have a first name。I will convert this print statement to enough string。We will display。

First， for the first name。

![](img/df30b99d4a6a270538b1500402a6549f_26.png)

You finish walking whatever your dog's name is。So when we're creating a thread and the target is that function and that function accepts arguments。

 we need one more keyword argument。 And that is args。 We will send this function a tuple。

 We need a set of parentheses。

![](img/df30b99d4a6a270538b1500402a6549f_28.png)

Within this tuple， we will list our arguments。Let's say that our dog's first name is Scooby。Now。

 since this is a topple， if we only have one argument， we have to end that tuple with a comma。

To let Python know that this is a tuple。

![](img/df30b99d4a6a270538b1500402a6549f_30.png)

Here's the result。You take out the trash。You get the mail。You finish walking Scooby。

All chores are complete。

![](img/df30b99d4a6a270538b1500402a6549f_32.png)

If we were missing this comma。This is what would happen。



![](img/df30b99d4a6a270538b1500402a6549f_34.png)

We're no longer passing in a tuple。What if we have multiple parameters。

 We have first for first name and last for last name。You finish walking。First and last。

We have first name of Scooby， last name of do。You take out the trash。You get the mail。

You finish walking Scooby do。

![](img/df30b99d4a6a270538b1500402a6549f_36.png)

All chores are complete。Art everybody。 so that is multi threading。

 It's used to perform multiple tasks concurrently， as if we're multitasking。

Were executing multiple functions at the same time。 Multi threadreading is good for IO bound tasks。

 such as reading files or fetching data from APIs。 And well， everybody。

 that is an introduction to multi threading in Python。



![](img/df30b99d4a6a270538b1500402a6549f_38.png)