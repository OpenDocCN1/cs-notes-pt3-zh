# 约翰霍普金斯大学《入侵检测｜Intrusion Detection》中英字幕 - P39：7_ROC分析概述.zh_en - GPT中英字幕课程资源 - BV1sGu1z5E2J

![](img/411a7a9aa436fa71c353bc2257ec52ee_0.png)

So this module is all about receiver operator curves or rock curves and rock analysis。

 The whole idea behind rock analysis is to try to put a quantitative measure on the performance of classifiers of the idea of the heart of an ideas tool classifying events between normal and intrusive events。

 so we're going to cover many different elements of rock analysis during this module leading up to your ability to be able to actually perform some rock analysis on sampled data。



![](img/411a7a9aa436fa71c353bc2257ec52ee_2.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_3.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_4.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_5.png)

So first of all what is rock analysis or what is a receiver operating characteristic it's a technique for visualizing organizing and selecting classifiers basically it's the idea of taking the results of what a classifier does and putting them in a way that you can compare and an apples to apples kind of way different kinds of classifiers different kinds of classifiers that are configured differently and essentially everything you want to do in order to select a classifier based on its character It's often it was created and used in signal theory designed to evaluate signals to noise ratio or detection algorithms within signal processing this is going to be really important because as we've applied this to intrusion detection data。

 there are some significant differences in differentiating signal from noise in sort of the signal theory versus trying to distinguish attacks from normal behavior。



![](img/411a7a9aa436fa71c353bc2257ec52ee_7.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_8.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_9.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_10.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_11.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_12.png)

In in the IS world， it was first adapted to IDS by Lincoln laboratories in 1998。

 This was based on a DARPA program that was attempting to try to compare different types of intrusion detection algorithms。

 so Lincoln laboratories designed a way to measure based on a series of test data。

 what kind of performance。 Each one of these different types of IDS classifiers would have。

 Now there were a number of tremendous problems in doing this kind of classification and will definitely be talking about those。

 but this is the data that you'll also be using within your own labs and evaluations。



![](img/411a7a9aa436fa71c353bc2257ec52ee_14.png)

So before we can really get into talking about rock。

 we really have to start talking about classifiers and the whole idea of we've talked a little bit before about the classifier being the heart of an IDS。

 but remember that a classifier is really just a partitioning algorithm to essentially partition and input data sets into two or more different areas for our purposes we tend to think of it as P and N P being the the attack signal in our case and n being normal behavior in sort of what we go here so for the IDS the way that we consider IDS P is the positive identification of an incident N is the identification of normal behavior by the classifier so the classifier takes the input data partitions it into two sets P andN that we can count so we can count the number of items in P and the number of items in N so that and we can compare those with the ground truth so we can know whether when a class。



![](img/411a7a9aa436fa71c353bc2257ec52ee_16.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_17.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_18.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_19.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_20.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_21.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_22.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_23.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_24.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_25.png)

FDes something as P as in that data set in the set P。

 we know whether the classifier made a correct or an incorrect decision。So， the two。

Basically items that will come out of the classifier are two hypothesized classes for P&N。

 This isn't necessarily the true class。 so it's really important to realize that an intrusion detection system doesn't know the ground truth so doesn it can't tell whether or not the data was really an attack or not really an attack。

 so it always creates hypothesized classes。 and now how well the classifier maps that input data into two sets that are similar to the ground truth is the measure of its performance。

 so we're comparing not only the number of true positives that an IS actually found or even just the normal behavior that it found。

 so we're trying to compare the positive behavior with regard to the ground truth and the negative behavior with regard to the ground truth so that we can now show how well these methods operated。



![](img/411a7a9aa436fa71c353bc2257ec52ee_27.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_28.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_29.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_30.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_31.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_32.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_33.png)

Now， we've talked about the confusion matrix before in previous modules。

 but remember that the confusion matrix is basically mapping the true classes and the hypothesized classes。

 and from the paper that you are reading from Tom Faaucet， you could see that the true positives。

 the true negatives， the false positives and the false negatives。

 allow us to have rates that we can now calculate precision recall accuracy。

 all of these rates take away the idea of how much data you actually use to calculate these things and put them into numbers that if I had two different data set sizes。

 I could still have similar false positive or true positive rates， similar precisions and recalls。

 So in the data， I don't have to use the raw counts as you would in the confusion matrix。

 but I can use these to generate rates， which I can then use to compare different idss to each other。



![](img/411a7a9aa436fa71c353bc2257ec52ee_35.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_36.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_37.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_38.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_39.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_40.png)

So once we have these rates， now we can actually do a receiver operator characteristic。

 We can create a twodimensional graph with the true positive rate on the y axis and the false positive rate on the X axis。

 This is now going to be a way for us to plot in a two-dimensal space。

 the characteristic of the classifier so that we can start to compare one classifier against another。

 Now， in the case of many classifiers that only have a single configuration In other words。

 they don't have a sliding threshold or a different type of configuration that we can change。

 Then running the data across that classifier will create a single point in either the rock space or a precision recall space as we have in there。

 So it don't always get a curve。 That's why we call it a receiver operator characteristic。

 the characteristic isn't always a curve。 it can just be a single point within the rock space。



![](img/411a7a9aa436fa71c353bc2257ec52ee_42.png)

When we have single points within the rock space， we can see that each point that we have within this rock space reflects a single classifier。

 single configuration， and a single way that the data set was run across the classifier。

 So since we're comparing rates。 Remember， we're comparing the true positive rate to the false positive rate sort of down here。

 what we're going to get for each run of the same data set。

 And that's very important that we're running the same data set will get different points within there。

 And then we can evaluate。

![](img/411a7a9aa436fa71c353bc2257ec52ee_44.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_45.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_46.png)

Based on where these points fall within the rock graph， what the different points actually mean。

 So we can do things like the point D。 So this point D that we have up here。

 which has a perfect true positive rate and a zero false positive rate。

 We can call that a perfect classifier， because every element that was found as a true positive by the Id S was indeed the ground truth showed it was a true positive。

 And it didn't find anything in the normal traffic and identify that as an event。

 So that's why we would call that a perfect classifier In this case， because for every event。

 We've done the appropriate calculation of both normal and attack。😊。



![](img/411a7a9aa436fa71c353bc2257ec52ee_48.png)

There are a couple of other elements on here that are always important to point out。

 if we look at point C， for example， or any point along this diagonal that we have here。

 all points on the diagonal represent a random classifier。 Now， what does that mean。

 that means that the true positive rate is equal to the false positive rate。 Now。

 if the true positive rate and the false positive rate are equal。

 that means the classifier for any given point in the data is just as likely to market as an incident as it is to market as normal。

 So really， if you just took a random swath across the data。

 all of your points would end up being along the diagonal of the true positive and the false positive rates。



![](img/411a7a9aa436fa71c353bc2257ec52ee_50.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_51.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_52.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_53.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_54.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_55.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_56.png)

So you can think of points D and points C as sort of two extremes along the different things that a classifier can do from a perfect classifier to a completely random classifier。

 But then you have other tradeoffs。 And that's what you get when you sort of compare points A and B here。

 So A and B are both better than point C， They have a better， true positive。

 false positive rate tradeoff。 But the A and the B's really emphasize different things within the classifier。

 Neither is perfect like D would be， But A is something that really minimizes the false positive rate。

 And B kind of maximizes the true positive rate。 So what do you want out of your detector。

 Would you want a low false positive rate and a high true positive rate or would you want something in the other way。

 Now， ideally， of course， we want point D。 But real classifiers often represent tradeoffs like we would say。



![](img/411a7a9aa436fa71c353bc2257ec52ee_58.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_59.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_60.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_61.png)

Within sort of these points， A and B。 And that tells us more than just how good the classifier is in a single number。

 It tells us a little bit about what the trade offs are between the identification of true positives and the mischaracterization of normal into a positive。

Finally， we have this odd point down here， point E。 So point E。

 because it falls to the lower side of the diagonal， is in some respects， worse than average。

 So how can a classifier be worse than average。E turns out to be a negative classifier by doing worse than random。

Essential， you are taking more normals and putting them into the category of positive and more positives and putting them in the category of normal。

 So if all you did was swap the labels on E， you would end up with a reflected point in rock space up here。

 where this new point would actually be a pretty good classifier in comparison to A And B。

 So points below the line usually mean that you have some kind of an error。

 either in your counting or in your code。 because you have a classifier that could potentially be better than random。

 But because you have reversed the labels in some respect。

 you got something that's sitting on the lower part of your diagonal。



![](img/411a7a9aa436fa71c353bc2257ec52ee_63.png)

![](img/411a7a9aa436fa71c353bc2257ec52ee_64.png)

So that's kind of a quick overview of what we would see with regard to classifiers within the receiver operator characteristic space。

 the subsequent videos are going to get into more detail on the specific aspects within rock analysis。



![](img/411a7a9aa436fa71c353bc2257ec52ee_66.png)