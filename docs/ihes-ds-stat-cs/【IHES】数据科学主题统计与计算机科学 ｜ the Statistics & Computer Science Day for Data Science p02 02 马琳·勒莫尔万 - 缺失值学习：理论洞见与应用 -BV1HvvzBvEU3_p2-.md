# 【IHES】数据科学主题统计与计算机科学 ｜ the Statistics & Computer Science Day for Data Science p02 02 马琳·勒莫尔万 - 缺失值学习：理论洞见与应用 -BV1HvvzBvEU3_p2-

![](img/2cad8d6e080e9d5d09fc0a9db6e1a0ad_0.png)

🎼Thank you。Yes yes， hi everyone， the good of my talk today is going to give you theoretical insight and practical guidelines if you have to handle missing values in a learning problem。

😊。

![](img/2cad8d6e080e9d5d09fc0a9db6e1a0ad_2.png)

Okay， so what motivates this work is typically this kind of data。

 it's a clinical database and here every black entry is a missing entry， there's no value in there。😊。

You see that for almost every clinical variable， we have at least missing one missing value and almost every patient has at least one missing value。

So if you suppose that here， someone asks you to train a prediction model let's say for a hemorrhagic shock。

 you have to do with missing values to do something with missing values first。

Because most models do not enroll missing values natively。

So the question we want to answer is what should you do？

So there has been quite a lot of literature on missing value since the 70s and actually it has been mainly focused on imputation and imprints。

😊，So imputation is the task of filling in the missing entries with likely values。😊。

And so if you look at the textbooks， you'll see that the classical method comprise expectation maximization。

 mice， which is multiple imputation by Che equation， matrix factorization as for rimodo systems。😊。

And also recently， you've had a lot of。Approaches based on GANS， VAE， graph neural networks。

 optimize transport， like everything is tried for imputation。

And the second task that's been studied a lot is inference。

 so trying to estimate means or varianceancies of some variables。Despite missing values in them。

So here in textbooks， you find mostly method based on likelihood based inference。

Multiple imputation and invest private weighting， something similar than what's used in causal inference if you know a bit about it。

So most of these methods rely on certain assumption on the missingness mechanisms。So actually。

How missing values arise is classified into three mechanisms。

And they have been introduced also in the 70s。To make inference or impetition valid。

So you have three of them， the first is Mcar missing completely at random。

So this is the strongest assumption。Basically in MCC， I may use that maybe。Okay。

In missing completely at from them the probability that a variable is missing。

 so here M2 would be a binary indicator indicating whether variable 2 is missing or not。

So the probability that the second variable is missing doesn't depend on it's a constant value。

 so basically it's going to be a coin flip， whether you're missing or not， so very simple。

Another assumption is called missing atron so it's not very well named because it's not missing atron here the probability of the second variable to be missing can depend on other variable but it just has to depend on variable which doesn't have missing values themselves okay。

So actually E care is included in Ma， MC care is stronger than Ma。

And everything that I showed to you just before require the more assumption basically。

 and it's why the more assumption has been introduced in the first place。And lastly。

 you have everything else which is gathered into the missing non a random mechanism。So here。

 typically。The second variable can be missing depending on its own value。

 So let's say if my variable takes high value， it iss going to be missing most probably。

 So this is a missing， not that from the mechanism。Okay。

So that is for the literature that's been going on for the last 50 years。

Now what I'm interested in is more the supervised learning with missing values。

 whether it is regressional classification， and in this area the works are much scarcer。嗯。

Here we want to consider。Inputs where which can have missing values so in the design matrix so typically here let's say you have a design matrix so it can have missing values in the second variable or in the first and the fourth etc anywhere。

So in your data， if you typically have 50 variables。

 you may have up to t2 to the power of 50 possible missing the mechanisms。Quite quickly， a very。

 very large amount of possible missing data patterns。So it poses statistical challenges。

So what do people do with that， well what they usually do is to first filling in the missing values with something and then proceed with the normal way of learning the model okay。

So you impute your data and then for example， you do your regression。

So here the question I want to ask and answer。Or the following first。

 we will see whether we have theoretical foundations for this widespread practice of first imputing and then doing your regression。

 do we have theoretical grounding for doing that？Second。

 we will wonder whether we need to impute well to predict well or not in practice。

 this is really an important question and the answer is not that clear and obvious。And finally。

 if we have time， we'll look at some real。Databases， clinical databases。

 and see how different approaches compare in them。But so let's start with the theoretical results。

Okay。So here I'm going to talk about impused then regress procedures just to formalize things a little bit。

I will talk about functions of the form G of phi。So here your're file。

Your phi is just going to be a function that impes the data so for example。

 for the first variable which is missing， it's going to compute a function of the up value so here a function of x2 and the3 so it's a conditional imputation on the up variable。

And on with my imputation function， I compose a prediction function G。

 which is just a normal function applied to the imputed data。And so we ask three questions first。

 if you consider the function of this form， can they be biased optimal。

 meaning can they reach the best possible performances on the data set with missing value， yes or no？

How should we choose the imputation function？To have something that's potentially based optimal。

And what happens if the data is missing， not that random。

 so you remember almost everything that exists for inference or impetition works and the missing at random a。

In a prediction setting， what happens if the data is not missing at Honda？

So we answer to these questions。So just a few assumptions or maybe notations to answer to these。

So here we are going to suppose that the response y is a function of the complete data plus some noise。

 so just very light assumption。And we focus on the following optimization problem。

 we want to minimize the squared loss。On the incomplete data because it's what is available。

 so here the F function that we want to optimize， we will consider it an impent regress procedure at G of5。

And the definition of a bias predictor is just a minimizer of this risk。

And we know that a minimizer of this squared loss is written as the expectation of why given the observed data。

And the missingness indicator。It's just a vector of size t。

 the number of variables with0 and ones indicating whether your variables is observed or missing in a sample。

So this is the expression of the biggest predictor。

And so the bias rate is going to be the risk of the bias predictor。

 it's the lowest achievable risk on the problem。😊，And the function is bias optimal if it achieves the bias rate。

So let's go back to the question。Can impute and regress procedures be by submalous or no？

So actually we showed that yes， they can， and in fact it's much stronger than that。

 in fact they almost always are。So let me give you the QM and we'll explain it afterwards。

So if you consider that G5hi star is a minimizer of the risk on your imputed data。

Then assume that your imputation is infinite， so it's not a strong assumption。

And that your response Y is generated as F star of per some noise。

Then for all missing data mechanisms and all imputation functions。

Then your G5 star of Phi is going to be based subma。So in other words。

 for almost all imputation function。A universal consistent algorithm that is trained on imputed data is going to be base consistent。

So it's an asymptotic result which tells you that。呃。Whatever the imputation function that you choose。

 if you have enough data， then you're going to reach the best possible performance。

 it's an asympttic results。But the fact that you can choose any possible imputation function means that you can choose something very cheap and very simple。

 such as the mean imputation。And for a supervised learning setting， it's going to be okay。

And the second important point is for all me mechanism。

 so it means including missing not at random settings。

So what this says is that for supervised learning settings。

The classification into MGma and missing that random them is not that important。Here。

 missing another that random。It's not a problem for it。Learning the best possible predictor。

So I'm now going to give you a bit an idea of why this CRem is true， just a sketch of the proof。

Because it gives nice insights into the problem。So here on the left， you have some。

Data and complete data。And on the right， you have an imputed version of this data。

And you see that after imputation， so he would choose just。An imputition of our choice。

And you see that after impetition， the data points each fold on a manifold depending on which original missing data pattern there was at the beginning。

The brown red and purplebble curves， they each correspond to an initial missing data pattern with two missing values。

And each surface， blue， green orange to correspond each to a missing data pattern with ordinary one missing value？

So the first thing in the proof is to show that indeed after imputation。

All data point with a missing data page M or mapped to a certain manifold。

 after they mentioned the number of observed values。

So this is the first point to see what the data looks like after imputation。Then the second point。

 which was maybe the most difficult is to show that。Once you have imputed your data。Actually。

The original missing data pattern of your data is encoded into the manifold if I check the image on the right。

I can almost say if I pick a point what was his initial missing data pattern？

So actually we showed this with the term transndaity UM， it's a old UM from differential topology。

The notion of strong vity is just a notion that describe how manifold intersect。

And the fact that two manifold are transversed is broadly meaning that it's a contrary of being duju。

 okay？So what this theorem says is actually for almost all imputation function to resulting in manifold or not going be they're going to be transverse。

And that means that their intersection is going to have a dimension that's always less that the dimension of the two manyfold that intersect。

And because of that for almost old points。We are going to be able to say what was the original missing data pattern of the point？

And once we've done that， it's easy。Once we done that。

 we can build a function that is just going to take the optimal value on the imputed space for each missing data pattern。

Okay。So this is the idea of the theorem。So now what does it mean if we recap we have some data。

 suppose that we do mean imputation on the data， what we know is that if we want to do inference on this data that it's not okay because the distribution is distorted but for supervis zoning。

Objectives。It's okay because given enough data we are going to be able to obtain the Bay optimalmal predictor。

So one could say， okay， so now that we have this white bother we are going to use only miniput here and do not think further。

But the thing is a theoretical result is aytootic， meaning if you have a finite amount of samples。

 then what happens？呃。Can a good impetition still provide an easier learning problem？

If you have a good impetition compared to the mean， that's a question that remains。

So actually we don't have theoretical results for this part。

 and I don't think there are theoretical results in the literature。

So we started with an empirical study to try to answer this question。

And this is the second part that I want to present。

So the question is here should we impute well to predict well and honestly when we started the project。

 we didn't have the answer， it's not obvious by the yes or no it's the case。

So it's still an ongoing work。So people have already thought about this question。

 so there are a few works in the literature that try to benchmark imputition plus prediction procedures and see what happens。

The thing is what I found when I was reviewing this literature is that in many works we have a serious limitation that I think hinders the conclusion。

 so I just listed a few。So for example， your works where the imputation is performed separately on the train and test set。

So that means， for example， if you take the example of normalizing your data。

 it would mean learning the mean and standard deviation on the train set。

Standardizing your trans and then learning the mean and sigma in your test set and standardizing there。

 So it's not something that's。Good。Then you had something with no hyperparmeter optimization。

 neither for the imputition nor for the prediction models， so if you don't do this maybe。Yeah。

 your prediction model is not at its best capacity。

You have works where the hypoothermeters are optimized on the complete data。Once for all。

 and then when people train models on the incomplete data， they keep these hyperparameters。

 but the thing is that you should retrain your hyperparameters for each imputed dataset set。

So it's not okay， we had a work where missing values were introduced in a single variable chosen at random。

So this is a service problem because if you choose it at random。

Maybe this variable is not so predictive of the outcome， so in that case。You get imputed。

The way you want it， we have no impact on the prediction quality。

 or maybe I don't know this variable is correlated with no other in the data set so you can't impute it。

And so depending on which  volumeible you choose for。Imutation。

 then you can have very different conclusions。Okay。

 and so words which only use a linear model for prediction， but we think that。

The way prediction imputation impact prediction。Can depend on your subsequent model that you use。

and then the number of data sets that are used are not always a lot， so for example。

 four data sets is maybe not enough to draw general conclusions。

And so maybe of this limitation have've actually been， I think。

 driven by the fact that this kind of experiments require a lot of。Have CPU time。

 and so for some time it's easier to just do the kind of。Choices to reduce the computational time。

And more of a few works draw insights into when and why imputation helps prediction or not。

 so we'll try to draw these k of insights。Okay， so ourll go here we'll be ready to compute basically correlations between imputation and prediction quality and see whether there's a correlation。

😊，And determining if and when imputation improves prediction。And as I say。

 we strive to set up experiments in order to gather useful insights so for that。

We want to have the impact of the downstream prediction model。

 so we use a number of different prediction models， not only linear models， for example。

We want to see the impact of the missingness indicator。In missing values。

It's a general practice to add the mask， to append the mask to your features。

 you have your D features， you concatenate your mask of sizesD and you learn on that。

 so widespread practice。So we also compare to this practice and without the mask。

Then we also wanted to see what was the impact of the outcome nonlinear already。

 you have a lot of works which concentrates on linear models。

 we wanted to see also what happens on nonlinear models。And finally。

 we'll use 20 data sets to try to have the most that we a during organization。

eneGeneizing conclusions。So I'll tell you what are the data sets we use。

 the prediction models we use， and then I'll show you the results。So for the datasets。

 which actually chose a benchmark suit that's been published with a recent paper that was comparing g neural networks and trees on Tular datasets。

So we chose this data。And what we like with this spin Smart food is that it's regression tasks with numerical features only。

And here we added m core missinginess， so it's a bit restrictive that actually the goal here is to set up a favorableable ground for imputation to impact prediction so that we will have a nopp bound of how much imputation can have prediction。

And for East dataset sets， we create a semi syntheticthetic version where we create an outcome that's a linear version of the real data X。

On top of the real outcomes why？Now for the prediction models， we chose three models。The first one。

 which is just as simple until the epiceptual on its baseline。

And then we shows one representative of a tabular model and the representative of a tree based model。

 so here you have sat， it's an architecture based on a column and a row attention。

And it's been shown in the paper that I was talking about to be the best tab learning representative。

And I boost， which is still according to this paper。

 was the best three based modules on the tabular data。Now for the imputation strategies。

 which shows four of them， the goal is not to choose the best possible imputation strategies based on a new method。

 the goal is to have a。A wide range of qualities so that we can compute correlations。So for that。

 we chose the mean imputition， which gives up normally the lowest impetition quality。

Then we have a classical method， it's mice， it's an iterative imputation where are you first filling your missing values with something。

 for example， the mean。😊，And then iterly， you take each variable and you predict the missing values based on all the other columns and you do this。

Colon after colon and you repeat until some kind of convergence。And then you have misforest。

 this one is one of the best performing methods currently， it's the same thing as the mice。

 but you use a forest instead of a rich model that we had in iter。And finally。

 we have something that we call cons is just a method where you compute a mean and the covarience matrix from your data empiricalically。

Then you suppose your data is Gaussian and you compute the conditional expectation of your data。

To inputute。So that's going to be our four impetition methods。😊，And in our experiments。

 already these cost， it took us the equivalent of one year on one CPU。It's not that huge。

 but it's still quite a lot。And the reason of that is that we have 26 impotent regressiongress models to test if we count't with and without the mask。

We have we do 50 trials of I parametermeter tuning for each model using atuna。

 so we draw randomly 58 I parameters。Turn the models 50 times。

 record the best on the validation set in one。We repeated each experiment 10 times。

 so we had 10 splits into trival test sets。And 10 times the generation of the missing data is like done。

It's a new missing values。And finally， we have 20 data sets。

 but each data set is duplicated because we also simulate the y with linear a。So what does it give？

So here this is just a first figure， it's not all the result at all to show you a bit what the data looks like。

So here we have just have the results for the MLP with that we use up the mask as input on real data。

 so no DNA outcome， each panel is one dataset set。X axis is the impetition quality and Y axis is regression quality measured as or to score。

And each color is an imputition given by the legend。So here you see that for this model。

 in this case， you have some data sets where you have a lot of。

Of correlation between impetation quality and。And regression quality。

 So super condu herem and isolate， a lot of corion。And others such as this one， California。

 where there's absolutely no correlation？So this is just for the MLLP now let me show you the figure which gathers all the results。

😊，嗯。So here， each box plot actually comes from。One figure that I showed before。 so typically here。

For the MLP here， the MLP with the dog gray is the MLP without the mask on real data。

 so on the left it's real data， do color without the mask， and this is the MLP。

And here each bound corresponds to one that I set so you see that the pink points at the top that correspond to super condu your isolate。

 these were the three。With a lot of correlations here。Okay。

And then you have California here with that correlation。

That ends up here at the very bottom in a kind of a。Brown green color。 Okay。

 so each box plug is this 20 pluss。So we have a lot of things to see here。

And the first thing that strikes me。Is that actually the good imputation matters less when the response is nonlinear so if you look at the correlation on the left this on the right。

 you see that on the right the correlations are higher， meaning that when your outcome is linear。

Apparently， the impetition quality is going to be more important。

So that makes a bit of sense because actually the base predictor in the linear case can be written as the best possible imputition。

And a linear model on the best possible imputation is basically going to be beta transpose the best possible imputation。

So。We could have thought that actually for a linear model， impetition is going to matter。

 and that's a bit what we found。😊，And also found that when your outcome is real outcome， normally。

 no nonlinear。The imputation quality matters less。That's the first insight。

Then what we see that the good imputation match or less for more expressive models。So actually。

 we thought that the MLP would be the less expressive model followed by sa and followed by exbu which is a tree model。

 which is very well adapted to tabular data。And if you look， for example， at the real outcome。

 you see that the correlations for the MLP are more around 0。6， then it's more around 0。

5 percent and more around the 0。3 for exist。So depending on the model that you had after your imputation。

 the imputation quality is going to match less。And actually。

The more you have a flexible model behind， then the less imputation apparently matters。

 and this is actually in aligned with author results。😊。

Because what we saw in the theory is that you can have a very simple imputation as long as。

The model behind is universal consistent， so as long as it's very flexible to cope with the fact that you didn't impute so well。

So we will recover that kind of results in this experimental setting。

And also I didn't insist on that， but you see that I'm talking about averages。

 but you have data sets where really there's absolutely no correlation， the correlation is at zero。

And the is towards the control， it's very highly correlated。

So these quantities were correlations so when we look at correlation it doesn't tell us what is the effect size of imputation quality on prediction quality just talks about correlation so in correlation there's an notion of significance so how much noise there is in in the relationship。

So then we look at the effects of imputation quality and prediction quality。 So that's basically。

You learn the coefficient， if you request。Prediction on imputition quality in a linear model you get a coefficient slope and this is the effect that we give here。

So here what you see is actually that the good imputation matter less when you use the mask。

 it' is very clear when you compare a dark gray box plot and light gray ones。

The size of the effect clearly decreases。So this is a very quite clear finding here。

So when you use the mask， you should care less of about impetition apparently。So as a conclusion。😔。

The better amutation are not always worth it， this is basically what we say here。😊。

The more expressive models you have。The more nonlinear outcomes you have and if you use the mask。

 then your imputation is probably going to be not that important on average。Okay。

So now I'm going just to show you the like the kind of a normal plot of performance just to see what works best if we look at this。

Work as a benchmark。😊，So here the white axis is the prediction performance given as the R2 on the test set。

And each color corresponds to the animputation and you have on the left to MLP。On the right。

 exusan in the middle saint。So we look at if we do a sivity test。You see that's the best method。

 there are three of them which are。Like altogether the best method。

It includes all of them include exbu。And so two of them use a mask with an imputation and one of them is the purple one non pre ex boost。

 this corresponds to ex boost with the native and aling of missing values so with ex boost you have an option to learn directly with missing values it doesn't exist for many models but for trees it does。

And basically what it does is that when you do a split based on the variable。

 if it has missing values in there， it's going to optimize to put the sample with the missing value on the left or on the right of your split to optimize the criterion。

And so this is one of the bad method and actually as it's very easy。

 it should maybe be the advocated method。😊，So maybe ex without imputation is a good default。

But which would be careful because here you see that there is a lot of variance in the results。

 so it means that there's no one side fits whole champion。Exhibuusist with native handling。

 for example， perform worse on four dataset sets。The worst one on four dataset。

And it's the best one only in a query of data sets。So it's。

 I think it's still a good idea to test a few。Of your method， among the best ones。

And also we see again here that adding the mass as input is always beneficial。

If you compare each possible module and without the mask， if you compare the two。

 the mask always significantly improve your results。

And this is true even with MC data because here we have MC data。

So actually this finding has not been reported before。

 what's been reported before is that when you are in a missing not at front setting。

 the mask is useful and it makes sense because in missing not at Fdom in the missing indicator you have information。

 the fact that the variable is missing means something， for example， your variable how do I value。

But in MCAR， it's not the case。And it can be very surprising at first sight because。

In the missinginess indicator， there is absolutely no information about the outcome。

 the fact of being missing is just a run coin flip。😊，So it has absolutely no information。

 so why does it help with predictions？So way we hypothesize is related to the theoreticalical work that I talked about。

😊，What we are both those is that in fact。😊，Your best possible predictor on the imputed data here is going to be discontinuous from a manifold to another。

诶。Unless you。Optimal prediction function。On the complete data is linear unless in this case。

 you will have discontinu conities in your best possible function on the imputed data。

And we expect that that using the mask is going to help you build the function that is going to jump a bit when it goes from one manifold to another。

Because you have this。These binary indicators that allow you， for example。

 to change the bias of your model。But we didn't show it very properly。All right。And yes。

 I forgot to mention that currently in the literature in MCC setting。

 it was just shown that adding the mask does not degrade performances as some particularly ill linear models。

O。So that's all for this benchmark part。I don't know how much time may have left five minutes。

So I will talk very quickly about the last part。😊，The last part is about a benchmark on a BL health database。

In the previous work， the missingness was M Car because we wanted to draw insights。

Now this work is on real data， so it's four clinical databases。And for each of them。

 you have a task which is predicting。嗯。The presence of emmerlanoma。

 death or emeragic shock and so on， so you have a number of tasks for each database。

And in each database， you have a lot of missing values which were not created ability here by design。

And here you see the proportion of missing values， so the x axis is just ordered variables from the one with the most missing values to the least。

So you have missing values with almost only missing values and variables， for example。

 with very few missing values， but it's just to say that it's not only two or three missing values around in the deficit。

And so in this match， we used great and boost state regression trees at a prediction market only。

And we tested four ways of imputing the missing data， the mean or median。We also use mice。

 which is the same thing as before， iterative imputation with a linear model and the key snakeboard approach。

And finally， we have MIA， which is just the native handling of missing values that was talking about before。

So here are the results， you have four de sizes here。

 so each time we only give the results for the databases which were restricted to this size。

 the size and so on。And on the left， all the possible impetition methods。

And the X axis gives you the the performance score and predict the performance score in classificational regression。

So here the first thing that you can see is that the mask improve the prediction again。

 so you have to compare the light color with a dog collar each time it's the same imputation with and without the mask and youll see that the do color always improves significantly the prediction。

Here it's maybe because there is information in the missingness indicator or maybe because just as we saw。

 even in MAR， adding M improves prediction。You see that the conditional imputation is on par with a very simple method。

 which is the constant imputation。 So the。Red is on par with the blue and green。

So spending time on better conditional imputition here did not improve the results compared to using just the mean imputation。

And finally， the native ending of missing values。TheThe black hair gives， again， the best results。

 So we have。Like concordant clues with the previous work here on these three items。Okay。And just to。

If you look at the importance of every feature， it's not only the features with a lot of with no missing data are important because you could say the imputation doesn't matter so much because in fact the predictive variables do not have missing values。

But what we show here is not the case， the importance is not a function of the missingness proportion。

So， even。Varis with love missing values can be important。So if I break up everything。

 the tick mes would be that。We have a theoretical foundation for imp and regress procedures。

 so we said that they are based opt amount for almost single data mechanisms and almost all imputation function。

 even very cheap ones， which is nice。嗯m。About how well you should impute to predict well。

 I think the decocom message here is beware of diminishing returns。

 it may not be worth spending a lot of efforts， CPU effort and time into better imputition because it may not improve your prediction in the end。

And finally， appending the mask as inputs is useful even if you're in MC car seat and that's citing an important message also。

And if you want to use a default for tabular data。Tree basedase model was native even that still there next。

So thanks for your attention。A there any。Any questionss。还有美个生。男生。So。First。

 I wonder if my interpretation is adding Damascus is correctly。

Are you allowing essential for each missing pattern to build its own prediction model what it means more or less that's more or less No is just if you add in a way youre saying for each missing pattern。

 I have a prediction function。 Yes， I'm going to adapt slightly my prediction function to missing data pattern。

 That's to your correct。And then the case when its worse。嗯。Okay， that it seems the all the sort。

 But because in general， you can have like two to the D。ま。

Which essentially could be that you dot have too many models。Yeah so that's a good question。

 I think maybe with the mask you can adapt to group of missing data pageants， you know， I don't know。

 like not having the best possible function for each missingness pattern。

But having a better impetition function for different groups。

But it's not clear actually the exact way of this。😔，嗯有。So you mentioned that for three based models。

 there is a method to if I correctly ignore the missing values when you split。

So that you can like deal with it it seems like a very intuitive way to do it Do you think we can we could adapt such a method to other models like Canon or doing that。

Honestly I'm not sure everything I can say is that in the Tala deep networks endeavors， for example。

 sat， you have a way to natively deal with missing values， that's why you had a purple plot for sa。

And in there you did just a lady em bidding for the fact that you have a nun。

And the same way they learn an embedding for each numerical feature。

 each numerical feature is mapped to the dimensional embedding and then because of that。Every entry。

 including the missing one， have an a bedding。 and you continue with that。 because it's another way。

Different。Buttter。Yeah。Can I if you。I don't know if you looked at this。

 but when you're adding the mask。So you mentioned two masks are really closed and they can some him in distance。

Would it be true that the correspondent models are also kind of given very similar predictions in some sense。

 like as just functions， let's say a fixed too much of the same size and they just differ in two positions？

And then it's just a function from R to the side of the mask to R。

is functions like function be veryI mean， the learn function on the missing indicator。I don't know。

I guess you can。If if we want， we can build function which are far away that on average or they far not。

 I don't know honestly。嗯 sure。AndFor this condition for all。

For almost all imputation mechanisms for almost all parties it means that。

There exists imputation function for which it's not true。And typically。

 it's going to be the imputation function， which。Map。

2 missing data patterns to exactly the same manifold or two manifold， which。Have a intersection。

Of the size of the intersected manifold。 So if you intersect， for example。

If you the manifold is 1 D and when you impute for two different missing data patterns。

 the imputation end up to be the same line。Your the initial missing that a pattern of your points cannot be identified youre completely confounded。

And if you have that， it's absolutely impossible to have a base optimal prediction because for one point in the space。

 the optimal prediction are going to be different。Yeah like kind of productivity。That's a point。本上。

I can continue any questions after that。Thank you。

![](img/2cad8d6e080e9d5d09fc0a9db6e1a0ad_4.png)

![](img/2cad8d6e080e9d5d09fc0a9db6e1a0ad_5.png)