# 【苏黎世联邦理工学院】信息检索-｜-Information-Retrieval-｜-Eth-Zurich-2025-p22-P22_9._评估_(1_2)--BV1ndsBzdEss_p22-

Welcome back。 This is now part number 9 on evaluation。 So now we take a step back。😊。

From what we've been doing， we saw the Boolean retrieval rights。

 where we have documents that are sets of world， and we want to locate a subset of the documents without any ordering or scoring。

 right， just either a document is in the results or not。We saw that we can represent vectors。

 documents as vectors of Booles。 if we see them as sets of words。

 We saw that we can use a standardout inverted index。 That's all familiar to you now， right。

 the standardout inverted index in order to process these queries。

 we have seen that the left part of that index。 So the terms on the on the left。

 which is So the vocabularies， the set of terms and the dictionary would be the data structure for the terms。

 And that dictionary can be a hash table or B plus 3， for example。

 That's how you look up the terms efficiently。But we've seen more recently before the star break that we can also model the documents in such a way that we can rank the output and have the top 10 and paginnate the results and so on。

 and for that we need a way to scrub the documents and the way we do that is that instead of considering that documents are sets of wordss。

 we consider instead that there are bags of wordss and that instead of being vectors of bulloles。

 we have vectors of numbers， non-neative numbers， right。嗯。Once we have done that。

 we realize that the documents live as vectors in the first quadrants of the， of the vector space。

 very highly dimensional， right So could be half a million dimensions for a reasonable system。

So it's nice， right。 We've done all of that。 But now it needs to be evaluated。

 when you have built a system like that， you need to be able to say。

 is it a good system or is it a bad system， right， Does it actually produce results that make sense to the user。

 right Because it could be that it doesn't， right， we need to we need to test it， So in particular。

 we have so many things we can tweak in a system like that， Do you use top wordss or not。

 Do we excludeude numbers or not， Do we use champions list， right， if you use champions list。

 What is the length of this list， Opim， Do you use stemming， Do you use demotization。

 Remember in the post processing， Should you wait the query terms。

 What is the smart codes that you should use these six letters， how do you tune that optimal。😊。

Should you renorize。If you be normalize， do you use L1， Do you use L 2。

Which document weight should you use for the query weights， the document weights。

 So all of these are open questions。 And in order to make these decisions， you have to quantify。

 You have to quantify in order to have some objective ways to， to assess。



![](img/3b144c9578c6c09788c9ed6f06420e2d_1.png)

In fact， what we want to do with our system is to optimize relevance。

 We want to give the user relevant documents。 We have to give the user what they are looking for。



![](img/3b144c9578c6c09788c9ed6f06420e2d_3.png)

And so in order to be able to evaluate these systems that we are building。嗯。

We need to set up some evaluation methods。And so， I think thats。

These kind of things started to be addressed in a scalable way。 I would say in the 60s， right。

 That's so， that's also the， the time where the early information retrieval。

 the computerized information retrieval systems were invented。嗯。

And as part of building these systems， people also discussed how to evaluate them。

 And so they set up conferences that they traveled to and then discussed with each other。

 How do we construct these systems， evaluate these systems and so on。

And so what they came up with in these conferences and in all these meetings with all the information retrieval researchers is to create data sets。

 right， data sets that help us evaluate whether a system is good or not。

 And in order to build a data like this， it needs to be done with real people。

 you need to ask real people， typically domain experts。

 what they think about the relevance of documents， depending on information needs。

 And so what happens。😊，Is that they came up with a set of documents and set of information needs。

 And then they took combinations of them。 For example， they pick a document。

 They pick an information need， and they ask a domain expert。

 Do you think that this document is relevant or not， And maybe the domain expert said in that case。

 it's not relevant to the information need。 So that， that's a yes or no。

 or maybe in some other cases， they can say yes， that document is relevant to that information need。

So concretely， the one of the first data sets that they built by two days st out would be considered very small。

 of course， because now we， we are used to seeing many zeros in the， in the。

 in the numbers that we see， right， But for the time， it was actually already good。

 That's almost 1400 documents。😊，And 225 information needs。

 If you multiply for the catrogen product of that， that's already a lot of combinations， right。

And so for every combination， there is a relevance judgment。 Yes or no。

 the document is relevant to the information need， right， So that's how you build the data set。

 and the early data sets。We built on on specific specific topics。

 I think that one of the topics that was popular as as a research was sorry aereroautics。

 I think if I correctly remember And that that was focused on。

 So the first one was called of that size was called cranfield。 The cranfield data。

 then there is another one called the track data set。

 I think also associated with a conference and people would regularly meet in order to update that。

 Now you see that's already more。 now you have almost 2 million documents， right。

 So that's lot more than the cranfield and 450 information needs right。

 So you can see the challenge of actually building these data， because there is no AI。

 There's no artificial intelligence at that type。 So it has to be done by people that that can tell you。

😊，So this is why we need to ask these people， these domain experts that will be able to tell you if it's relevant or not。



![](img/3b144c9578c6c09788c9ed6f06420e2d_5.png)

But I need to reopen a parentheesis and say something that I've already said。

 but it really needs to be very clear that the difference between an information need and a query。

 which is not the same thing。E T H Zuric。Would be a query。

 That's why you type in the text box when you go to to a search engine or to an information retrie system。

But the information need that is behind that is what's happening in the brain of the person with typing this query。

So somebody who type E T H Zurich might be Alice， who searching for a higher education institution for her daughter。

 So maybe a bit early， but she's typing E T H Zurich in order to， to。

 to find a higher education institution。Or maybe somebody else typed E T H Zuric， but actually。

 it's both with searching for Ethereum cryptocurrency in Zuric Conas， right。

 So they would obviously also type E T H Zuric。 to find that。

 Or maybe it's gals We searching for the extended trading hours， E T H or insurance stocks， Zuric。

Right， so you see here that it's not an exact match。 We have the information need。

 and we have the query。So this is why the， the idea that a system。Is mathematically correct。

 might be obvious， right， If you just implement correctly the scalar product or implement correctly the Boolean queries。

 then you could argue it's 100% correct。 Yes， but then you're missing this。

 you're missing the information need。 It might be 100% correct。

 doing the right things with the query But you ask to ask yourself does itself the need what people are actually looking for in the。

 in this in this。In this context。 So that was an example I've already given to you on。

 on the other way around， you have a specific information need， And there might be multiple ways of。

 of searching for documents。 in that case， with a Buyan query language， right。Of course。

 not that we are in 2025。 I'm pretty sure many of you would just directly copy paste whats in the yellow bubble to chat GT and let it do it things。

 right， But this shows the， the， the， the evolution of things， how the systems。

Keep back getting better and better and better。 And how the queries evolve。

 So it's called the prompt， right， But if you think of it， a prompt is also a query。

 prompt is just a fancy name for a query that you put in in inside an LLM， right。Okay， but still。

 you see the evolution that in the a couple of decades ago。

 we were still using the Boolean languages in the lawyer offices and so on。

 And now we have the luxury of already with Google。 we were based on phrases， phrase search。



![](img/3b144c9578c6c09788c9ed6f06420e2d_7.png)

And now with prompts， alright。But we need to evaluate that。 So now I'm closing the parenthees。

 And now I'm， I'm going to give go very quick about that because that you already know。

 I've already shown it to you。 who remembers precision and record。



![](img/3b144c9578c6c09788c9ed6f06420e2d_9.png)

Okay。So， very quickly。The idea is that when you have a system and you type a query。

 the results that it returns may or may not be relevant to the information need that you have for the query。

 for sure， mathematically， they are relevant， but for the need for the information need you have in your brain。

 they might be not relevant。And so the precision was the first metric that I gave you back then。

 which is just a division。 It's a ratio of the number of relevant returned results divided by all of the all of the returned results。

 right， So you， you make a division of green divided by green， light green plus dark red， right。😊。

What is the precision here。50%， right？ Okay， good。 So this is true positives divided by little。

 Indeed，50%。 What's the precision here。 We've done it already， right。😊，Hundred of cents。 You agree。

 And here。0， you agree。 Okay， very good。 And now how much。80%， right。Okay，8 divided by 10。 Very good。

So you know how to compute the precision。Now， there are also documents that are not resolved。At all。

 they are not even in the results。 And some of these documents might still have been relevant for you。

 You wish they had been returned， right， And so these are the blue ones。

 And then you have the yellow ones that are not returned， and they are also not relevant。

 So we are basically very happy with the green zone， light light green zone and the yellow zone。

 And we are less happy about the blue zone and the and the and the red zone， right。😊。

Do you remember the recall， The recall is the number of returned relevant resultsrizzles divided by everything that would have been relevant to you。

 Basically， it's among everything you wish you would see。 How much of that did the system give you。

 That is the recall。Alright， what is the record right here， It is。50% exactly Very good。

 What is the recall here。Hundred percent， which is the recall here，0%， obviously， and here。2000。

 right，67%。 Okay， very good。But that we've seen， I've already explained to you in the Fox weeks。

 And as the， as a reminder， the type 1 errors and the type 2 errors are basically the documents that we don't like to see。

 So the relevant documents that are not returned and the。

Non relevant documents that are returned to you。 So false positives and false negatives。

And then you have the true positives and the true negatives of you see。

 So these are the documents that are correctly returned or non returned， not returned。Now。

 you might have systems that have a very high precision。 like this system， for example， is very good。

At not giving you irrelevant results。But the price to pay is that it might not give you all the re event results。

 right， So this has very good precision， but the recallco， so， so， right。

This system has very high recall。It's giving to you almost everything you need。

 except that what it gives you is dilu into a C of useless stuff， right， So you see high recall。

 but the precision is not so great， right， So it's a compromise between the two because， in fact。

 getting high precision and high recall is varied of right So typically。

 you have to move a slider here between high precision or high recall and find the compromise that might depend on the use case。

 I mean， there's no absolute truth about that。 It depends。

On whether you fear the true positives or the true negatives more。 And that depends on the use case。

Okay， so it's a compromise。But there is more， because I only talk to you about precision and recall。

 And it turns out that there are others。 There's also the specificity who has ever heard of this one。

Specific C T。 So the specific C T is when you look， it's like the recall。

 except that instead of looking at the relevant， you look at the non relevance。So， the recall is。

How good is the system。At Toing。As many relevant results as possible to you。Specificity is。

 How good is the system at not bothering you with useless stuff。Right， so。

 in a way it's the opposite of the recall， Right， So the specificity is basically how many。

Relevant non relevant results are not returned divided by the total not relevant results， right。

 So what is the specificity here。50%。Right， here。Hundreds。Here。0。Here。60 or 40。60， right？

 It's the yellow ones that that we want so60， right， okay。Very good。So， precision。Recoll。Specific。

We also have accuracy。 We already heard of accuracy。

Who has already heard that iss a very bad idea to use the cur seed machine learning。Yeah， so let me。

 let me show you what it is。 And then you know why you have to be very careful with the accuracy。

So the accuracy is basically everything you've done right， divided by everything。

 So what you've done right is the true positives and the true negatives。

 So everything that's relevant and that you return and everything that's non relevant and that you don't return。

 So that's everything where you are successful， right。😊，So that's the accuracy。

 So the accuracy here would be how much。66，67， exactly 2 cells。 That's exactly。 it's absolutely。

20 of accuracy。 You see， it's only base now on the diagonal， right， I want as many。

 as many as possible on the on the on the diagonal。What's the accuracy here。100%， right。

 I've done everything right here。 There are no no true， no false negatives and no false positives。

 And what's the accuracy here。0， right。No。Imagine。That somebody builds that a system that has zero accuracy。

Do you think。That this is valuable or not。It's actually the perfect way。Exactly， you can invest it。

 So if somebody manages to mess it up in such a way that they bring the accuracy to 0。

 they're a billionaire。😊，Because as you said， you invert it and you have a system with。

 you just need to invert what you return and what you don't return， right。Alright， very good。

But the problem with accuracy accuracy。Is that。You can hack it， for example。You can hack a system。

Very quickly， I can build you a system that has an accuracy that is very close to one with just a few dollars。

I just return nothing。I can just set up a website。 You type your query and read the results as empty。

 I can claim higher accuracy， right， I I， I was very good at not giving you non relevant results。😊。

So， this can be act。very high accuracy。😊，嗯。Recoll can also kind of be hacked。

 even though that's that might be a bit multi demanding， but you just return on everything。



![](img/3b144c9578c6c09788c9ed6f06420e2d_11.png)

If I give you everything， then I can claim I give you all the relevant results。 right。

 So you always have to ask yourself， like， how are the metrics relevant。

 Can they be hacked in a way Can I cheat on these metrics and so on。😊。

So here I would have a recall of 100% if I read on absolutely everything， right。



![](img/3b144c9578c6c09788c9ed6f06420e2d_13.png)

In practice， we want both a good mix of precision and re。

So we need a metric that combines them that combines precision and recall。

 The naive choice would be the arithmetic mean， right。

 You just take a precision plus record over2 and that's it， right。There's a problem with that。

Is that。If one of them is good and the other is really bad， like。

 let's say the precision is close to 0 or the record is close to 0， but the other is close to 1。

You already have one half。So it looks like it's not such a bad number。

 even though if one of the two is bad。 So that's the problem with the arithmetic mean that it's not very useful to actually express much。

But you know that there are other kinds of means。 What other kinds of means do you know。

At least two others， yes。The harmonic mean， which is the one that we are going to use。

 Do you know another one。The geometric min， the square root of the， of the product， right。

 So there are others。 So the harmonic min looks like this。 The one that you mentioned。

 it's actually very popular in electronic for parallel resistors who has ever seen that。

If you put with cell， you don't do any electronics。Okay。

 maybe so it's something that that well probably need at they， they， they cover this。

 So when you connect resistors in in serial， you basically。嗯。I think， why。

 I don't have a very good recollection at them。 And then when you。

 when you do it in in in parallelhalel， then they combine in a harmonic fashion。Okay， but anyway。

 you can write this formula in multiple ways。 So this is just a rewrite of the formula。

And now this is actually a better measure for combining precision and requor to use harm the harmonic mean。

Allright。😊，Now， I put a little bit 0。5 in here because， in fact。

 it's a particular case because you can also use weights。 You know。

 you can compute weighted averages， right， For example， on your transcript of record that it T8。

 you can compute the， the average weighted by the credit points。Right， which is typically done。

 It's the same here。 We can actually also add weights to the precision and to the recall。

 So there's just two of them。 So it's alpha and1 minus alpha。 So I can have weights。

 And so the generalization of this is， is alpha and1 minus alpha。😊，And that is called the F measure。

 And Al Al is1 half gives you the special case of the harmonic mean between the the precision and the recall。

 okay。And so you would adjust the weight， depending on whether you care more about precision or whether you care more about about equal。

 But basically， the idea of the harmonic means is that if any of the two is bad。

 that is going to drag down the overall metric， which is the intended， the intention of the。

Of this combination。Okay， but now。I'm going to， because that might seem easy。

I'm going to now go to ranked retrieval。 How do we make precision and recall make sense in ranked retrieval。

So that's how it works。If I have a ranked retrieval system。So imagine I type a query。

But let's say I'm not directly displaying the top 10。 Instead， I'm displaying them  one by one。

 The first results。 then I click， I see the second results。

And I keep clicking to display the next results， right。So I'm going to set up a graph like this。

Precision and recall。 And I'm going to start plotting stuff on this based on the on the system。

 So now I imagine that I type a query and I look at the first result。 So just the top one。

This is Alice。 She types her query。 and it turns out that this first result is actually relevant。😊。

What precision do we have and what recall do we have so far。

Where would I put a point in that in that quadrant here。So let's start with the precision。

 What precision do I have so far。Have I ever written something non relevant yet。No， right。

 so I have a precision of。Hundred%， right， I'm perfect， right。

 Everything I've returned is relevant so far。 So my precision is going to be somewhere here。

 What about the recall， Imagine that I have thousands of relevant document in the collection。

 Where is my recall right now。😊，Do you agree， it's close to 0。

Because I've just written one that's not so much compared to everything there is。 So do you agree。

 I would be here。

![](img/3b144c9578c6c09788c9ed6f06420e2d_15.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_16.png)

Right， I see a lot of nodding。 So great。 So indeed， this is where we are。😊。



![](img/3b144c9578c6c09788c9ed6f06420e2d_18.png)

And now， I continue。Just as an alternative， imagine that instead of being relevant。

 it would have been non relevant。 if you think for a few seconds。

 do you agree that if it had been non relevant， I would have been here 0，0。



![](img/3b144c9578c6c09788c9ed6f06420e2d_20.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_21.png)

I have a precision of 0 and a recall of 0， right， Okay， but let's come back to the。

 to the case where it was relevant。 Now I have a second result。 I click next。

 and my second result is also。😊。

![](img/3b144c9578c6c09788c9ed6f06420e2d_23.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_24.png)

Relevance。Do you agree that my precision remains at 100 do。But my recall has increased。



![](img/3b144c9578c6c09788c9ed6f06420e2d_26.png)

At that， right， just slightly higher， same precision， slightly higher in record。 right。

 So I'm moving slightly to the right。 if instead it had been。



![](img/3b144c9578c6c09788c9ed6f06420e2d_28.png)

Non relevant。 I would have lost precision because here I would have had a precision of one half。

 So I would have fallen down here， and my recall would remain the same。



![](img/3b144c9578c6c09788c9ed6f06420e2d_30.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_31.png)

Right， so you see， whenever I add。APo， true positive。 I'm going to the right。

Whenever I add a negative1， I go down。

![](img/3b144c9578c6c09788c9ed6f06420e2d_33.png)

Right， do you agree with that general principle。So let's continue。 So imagine my third results。

Is non relevant。 I go down by one third， right， Now。

 my precision goes down to two third and my record doesn't make any progress。 Now。

 another non relevant result， I go further down。 Now， my precision is at one half。Now。

 now I have a positive results， so my precision increases and so does my recall。😊，Then。Non relevance。

 relevance， relevance， relevance。Pre events and so on。Who sees the logic？

 I just keep updating the precision and the record。

 and I just go all the way down the list of results。 and I plot this curve like here。And。

 and I see how it looks like， right， So that is how I do it for a ranked retrieval system。 Now。

 you can actually adapt it a little bit with some math to avoid the up and down and up and down。

 And you just take， you know， the， the lines on here。 And you get a plot like this。

 That is a precision versus re。😊。

![](img/3b144c9578c6c09788c9ed6f06420e2d_35.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_36.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_37.png)

K。Typically， people will not do it for every single result。They will only do it for the first。

 So at the very beginning。 And then after 10%， after 20% and every 10%。 So they will have 11 points。

Right， they will have 11 points in here。 That is called the 11 point interpod average precision。

 right，11 points， because if you have110th every time， there's 11 points， right，0，0，1。

02 all the way to 1。 That is called the 11 point interpod average。



![](img/3b144c9578c6c09788c9ed6f06420e2d_39.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_40.png)

Precision。No。Where is my awesome search engine。Do you agree that this is an awesome search engine。

Keeps returning relevant results， high precision all the way and by recall just increases。

This here is an awful search engine。And because it's a rent retrieval。

 it would be tough to turn it into a useful engine because it's tough to reverse， you know。

 what is not returned， Right， So this is not very useful。



![](img/3b144c9578c6c09788c9ed6f06420e2d_42.png)

Yeah， so this is just to give you， to give you an impression。

 I think I will stop here to not run into the danger of， of too quickly adding new knowledge。

 But I think that this now makes sense to you。 right this idea of with the rank re just go down the results and you see how as you increase the recall by returning more results。

 the precision goes down。 And the goal is to keep it as high as possible rather than going down here。

 right， So this is good。 this is bad。

![](img/3b144c9578c6c09788c9ed6f06420e2d_44.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_45.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_46.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_47.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_48.png)

Right。

![](img/3b144c9578c6c09788c9ed6f06420e2d_50.png)

So thank you very much， everybody， for attending this lecture。 Thank you， George。

 for moderating everything。😊。

![](img/3b144c9578c6c09788c9ed6f06420e2d_52.png)

And do I see， I think I might still have time to check。The slowdown accelerate thing。Before you go。

 if the link。Yeah， it worked。

![](img/3b144c9578c6c09788c9ed6f06420e2d_54.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_55.png)

So you know that if you have any questions you can write a email， you can write on the forum。

 you should read the book， by the way， this is a must。

 you should read the book and all the relevant chapters。Ask us questions， we are here。

 solve the exercises， solve the program programming exercises。That was when。

 that one was a bit tougher today。All right， very good to know。啊。我 v。Okay。😊。

So what we'll do is next week we'll take it slowly。

 if you have any questions come with the questions to next week。

 then we will slowly finish the evaluation lecture and then we'll move on to probably seek information retrieval all right so it was a good thing that I ask because that gives me the thermometer of my speed。

😊，Alright， so thank you very much。 have a nice weekend ahead， and I'll see you next week at at 10 AM。

 as always。 Bye bye。 thank you very much。😊。

![](img/3b144c9578c6c09788c9ed6f06420e2d_57.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_58.png)

![](img/3b144c9578c6c09788c9ed6f06420e2d_59.png)