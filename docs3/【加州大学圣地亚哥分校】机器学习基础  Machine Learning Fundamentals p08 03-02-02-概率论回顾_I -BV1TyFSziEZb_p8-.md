# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p08 03-02-02-概率论回顾_I -BV1TyFSziEZb_p8-

![](img/6a1c74cc8a50909c358924a06558bc31_0.png)

In order to progress with machine learning， there are three types of math that you need to get pretty comfortable with。

Probability， linear algebra and optimization。Of these three。

 I'm guessing that probability is the one that most of you are probably the most familiar with。

But just to be sure， what I'd like to do is a little bit of a review broken down into three parts。

And by the time we're done with this， we'll be ready to delve much more deeply into generative modeling for classification。

So what we'll do today is to define the notion of the probability space for an experiment。



![](img/6a1c74cc8a50909c358924a06558bc31_2.png)

We'll see how to formulate an event that interests us。

And we'll see how one event influences the probability of another event。

All of this will lead ultimately to Bays rule， which is the central formula for probabilistic reasoning in machine learning and statistics。



![](img/6a1c74cc8a50909c358924a06558bc31_4.png)

So let's start with probability spaces。A probability space for a random experiment is a summary of all the information we need in order to answer questions about the experiment。

😊。

![](img/6a1c74cc8a50909c358924a06558bc31_6.png)

Let's see a concrete example Okay， so suppose we roll two dice and we wonder what is the probability that they're going to add up to10？



![](img/6a1c74cc8a50909c358924a06558bc31_8.png)

So it's a random experiment。And the probability space for this experiment has two components to it。

The set of all possible outcomes， which is called a sample space and the probabilities of each of these outcomes。

So what are the outcomes for this experiment， Well， we rolled two dis。

 so maybe the first one is a four。

![](img/6a1c74cc8a50909c358924a06558bc31_10.png)

And the second one is a two。We'll write it like that， or maybe the first one。

Is a one and the second eye turns out to be a six。The sample space is the set of all possible outcomes。

 so it's the set of all possible pairs like this。So the sample space consists of 1，1，1，2。

 all the way to 16。

![](img/6a1c74cc8a50909c358924a06558bc31_12.png)

Thenhan 2，1， and so on and so forth， all the way to two6es。These are all the possible outcomes。

 the set of all possible outcomes。We could also write this a little more consistent a little bit more concisely as all possible outcomes for the first day set product。

😊，With all possible outcomes for the second day。And in fact， an even more concise way of writing it。

Is just as one，2，3，4，5，6。

![](img/6a1c74cc8a50909c358924a06558bc31_14.png)

Squared。Okay， so that's the sample phase。 What are the probabilities of these various outcomes。

 So the number of outcomes， the number of possible outcomes is 6 times6 to 36。

 and they'll all equally likely， and so each outcome has probability 1 over 36。

And that is the sample space for this experiment。

![](img/6a1c74cc8a50909c358924a06558bc31_16.png)

Okay， so now that we have our probability space。Let's formulate the event of interest。

 and so the event we care about is when the two dies add up to 10 and were wondering what is the probability of this event？

So let's call the event A。An event is just a subset of the possible outcomes。

So it's a subset of the possible outcomes。And in particular， the event consists of all pairs。Z1， Z2。

 let's say that add up to 10。

![](img/6a1c74cc8a50909c358924a06558bc31_18.png)

Okay， so which pairs are these well？If the first die is a1。

 then the second one has to be a9 so that doesn't work。

 so the first die actually has to be at least a four Okay so if the first one is a four。

 then the second one has to be a6。

![](img/6a1c74cc8a50909c358924a06558bc31_20.png)

If the first one is a five， then the second one has to be a five。

 and if the first one is a6 then the second one has to be a four and that's it。

So this is the event that interests us， it consists of three possible outcomes out of the 36。Okay。

 so if we were to draw a Venn diagram for this。We have。The set of all 36 outcomes。

And the event that interests us。

![](img/6a1c74cc8a50909c358924a06558bc31_22.png)

Which consists of just three out of these events， and what is the probability of it？Well。

 the three outcomes， and each of them has probability 1 over 36。

And so the probability of a is just 112。So that's how we define an event and compute its probability。

Now， when we are using probabilities in statistics and machine learning。

 we are typically dealing not just with one event， but with multiple events。😊，For instance。

 we measure a patient's temperature and blood pressure and wonder whether the patient has a particular disease。

 So that's a coming together of three events。 There's the event。



![](img/6a1c74cc8a50909c358924a06558bc31_24.png)

That the patient has that particular blood pressure。

There's the event that the patient has a particular temperature。

 and there's the event that the patient has the disease。So we get to observe two of these events。

 the temperature and the blood pressure， and we wonder what they tell us probabilistically about the third event。

 the one we don't get to observe the one we care about the disease。Okay。

 so let's see a concrete example of this type。

![](img/6a1c74cc8a50909c358924a06558bc31_26.png)

So here's a situation， a toy situation， so you have 10 coins in front of you。😊。

And they all look the same， but theyre not the same。 N of them are regular fair coins。

 coins that come up heads half the time and tails half the time。

 But the 10th coin is a bad coin that always comes up Tas。

 So you close your eyes and you pick a coin at random。And then you toss the coin four times。



![](img/6a1c74cc8a50909c358924a06558bc31_28.png)

And you find that it comes up tails every single time。

What is the probability that you picked the bad coin？Okay。So this is。

 this is something that's not obvious。 And we're going to have to work this out。 Okay， so first off。

 what is the sample space for this random experiment？ So what's going on。

 We first pick a coin at random and then we toss it four times。 Okay。

 so the way I'm going to write down an outcome is first， I'll say which coin we picked。

Just the coin number， coin number one to 10， let's say 10 is the bad coin。

And then what happened on the first do？

![](img/6a1c74cc8a50909c358924a06558bc31_30.png)

Heads or tails and the second tos。The third to。And the fourth does。

That's how we'll describe a particular outcome， and so the set of all possible outcomes。😊。

If the set of all choices for the coin， there are 10 possible choices。



![](img/6a1c74cc8a50909c358924a06558bc31_32.png)

Product with the set of all possibilities for DoOS1。



![](img/6a1c74cc8a50909c358924a06558bc31_34.png)

And to2。And three and four。But。そ。This is the sample space of possible outcomes。 In fact。

 we can write this a little bit more concisely， so we can also write it as one。All coin choices。

Times H T to the fourth。Okay，So how many possible outcomes are there well there's 10 times 2 times 2 times 2 times 2。

So 160 possible outcomes。Okay， so that's a sample space。



![](img/6a1c74cc8a50909c358924a06558bc31_36.png)

So now， the event we care about。Is。Whether or not we got the bad coins。 So let's call that A。

So is the event that we picked the badco？And formally， what the event is。



![](img/6a1c74cc8a50909c358924a06558bc31_38.png)

Is the set of all outcomes in which the coin we picked was the bad one， coin number 10。

 and then it doesn't matter what happens afterwards。



![](img/6a1c74cc8a50909c358924a06558bc31_40.png)

So this is the event we care about， but it's not what we get to observe。

 we get to observe a different event which is related， and that's that all the coins come up tails。



![](img/6a1c74cc8a50909c358924a06558bc31_42.png)

![](img/6a1c74cc8a50909c358924a06558bc31_43.png)

Okay。

![](img/6a1c74cc8a50909c358924a06558bc31_45.png)

And so here we don't know what the coin number is， but all the outcomes are tailed。

So these are the two events that we're dealing with。What is the probability that both of them occur。

 Okay， so what is the probability？A and B。And the way we usually write this， in fact。

 is A intersection B。

![](img/6a1c74cc8a50909c358924a06558bc31_47.png)

What is the probability that both of these things happen？Well。

 it's the probability that we pick the bad coin。

![](img/6a1c74cc8a50909c358924a06558bc31_49.png)

Times the probability that we get all tails。Given the badco。Given that the coin is bad。Okay。

 so the probability picking the bad is 110。Since there's one bad coin and nine good coins。

And once we pick the bad coin， the probability that all four tossses are going to come up tails that is wanna。

Okay。So the probability that both A and B happen is1/ tenth0th。Okay。

 so this has all been fairly intuitive， but we are using some general rules about conditioning over here。

 and so let's be a little bit more explicit about that。



![](img/6a1c74cc8a50909c358924a06558bc31_51.png)

So when we have two events A and B， we can talk about the conditional probability of B given A。



![](img/6a1c74cc8a50909c358924a06558bc31_53.png)

The probability that B occurs， given that we know A occurs。 Okay。

 and the notation for that involves this bar over here。 This bar means given。



![](img/6a1c74cc8a50909c358924a06558bc31_55.png)

![](img/6a1c74cc8a50909c358924a06558bc31_56.png)

Now the most basic formula for conditional probability is this one shown over here。

 it says that the probability that A and B both occur is the probability that A occurs times the probability that B occurs given that A has occurred。



![](img/6a1c74cc8a50909c358924a06558bc31_58.png)

Okay。

![](img/6a1c74cc8a50909c358924a06558bc31_60.png)

So returning to our example， there are two events that we're dealing with。

 A and B A is that the bad coin is chosen， B is that we have all tails。

 and we are interested in the probability of A given B。



![](img/6a1c74cc8a50909c358924a06558bc31_62.png)

We've seen the B is true and we're wondering what is the probability of A given this information？

Well， we can compute it directly from this formula。So if we rearrange terms。

 we see that the probability of a。

![](img/6a1c74cc8a50909c358924a06558bc31_64.png)

Given B is the probability of A and B。Divided by the probability of B。



![](img/6a1c74cc8a50909c358924a06558bc31_66.png)

你 too。So what is the probability of A and B， we've computed that， that's110。



![](img/6a1c74cc8a50909c358924a06558bc31_68.png)

![](img/6a1c74cc8a50909c358924a06558bc31_69.png)

What is the probability of B， what is the probability that all four tosses come up tails？



![](img/6a1c74cc8a50909c358924a06558bc31_71.png)

Well， that's something we have to figure around。Okay， so let's go ahead and do that Okay。

 so the probability。

![](img/6a1c74cc8a50909c358924a06558bc31_73.png)

That all four tosses are tails。Let's figure that out。 Well。

 it kind of depends on whether or not we chose the bad coin。

 So let's break it up into those two cases。So it's the probability。Though we got the bad coin。And。

We get all tails。Plus， the probability that we did not get the bad coin。



![](img/6a1c74cc8a50909c358924a06558bc31_75.png)

And yet， we still get old tales。So now let's compute these。

 the probability that we get the bad coin is 110。If we get the bad coin。

 the probability of all tails is one because the bad coin always comes up tails。

The probability that we don't get the bad coin is nine tenths because there are nine good coins。

And if we don't get the bad coin， if we have a fair coin。

 the probability of getting all tails of getting four tails in a row is a half times a half times a half times a half。

 so it's 1，16th。

![](img/6a1c74cc8a50909c358924a06558bc31_77.png)

![](img/6a1c74cc8a50909c358924a06558bc31_78.png)

Okay， so let's work this out1/10 plus9 over。1，60 is。25 over 160。Which is5 over 32。

So this is the probability of B， the probability of all tails。

 And now let's go back to what we actually wanted， the probability of A given B。



![](img/6a1c74cc8a50909c358924a06558bc31_80.png)

![](img/6a1c74cc8a50909c358924a06558bc31_81.png)

And as we saw。It's the probability of A And B。Over the probability of B。The probability of A and B。

 we figured out that was1/10th。

![](img/6a1c74cc8a50909c358924a06558bc31_83.png)

The probability of B we've just figured out is5 over 32。Okay， and so this works out to 32 over 50。

 which is 64 over 100 or 0。64。So there is exactly a 64% probability that we have the badco。



![](img/6a1c74cc8a50909c358924a06558bc31_85.png)

Pretty impressive，huh。So when we were doing those calculations， we were implicitly using Bayes rule。

 which is the central formula for probabilistic reasoning in statistics and machine learning。

 so let's spell out this formula a little bit more precisely now we have two events A and B。

 and the event we are interested in is event A， but we don't get to observe it directly。

 we get to observe some other event B， and what we are interested in is given that B happened。

 what does it tell us about the probability of A happen。



![](img/6a1c74cc8a50909c358924a06558bc31_87.png)

So here is Bay's rule。If we don't observe anything about B。

 the probability that a happens is just probability of a。



![](img/6a1c74cc8a50909c358924a06558bc31_89.png)

But now that we know that B happened。That changes the probability of a by how much by a multiplicative correction factor。

 And this is the correction factor。Okay。Now， this formula is just two applications of the general rule for conditioning Okay。

 so let's see how we get it。The probability of a given B。Is， as we know。

 just the probability of A and B。Over the probability of B。And now let's just work on the numerator。

 the probability of A and B is just the probability of A。Times the probability of B given A。



![](img/6a1c74cc8a50909c358924a06558bc31_91.png)

We keep the denominator the same。

![](img/6a1c74cc8a50909c358924a06558bc31_93.png)

And sure enough， we have Bs rule。🤧So。The various calculations we've done today might seem very simple but they're actually very powerful。

 Be's rule tells us how we can reason under uncertainty and it's no surprise therefore。

 that it's one of the fundamental formulas for inference in machine learning。😊。



![](img/6a1c74cc8a50909c358924a06558bc31_95.png)