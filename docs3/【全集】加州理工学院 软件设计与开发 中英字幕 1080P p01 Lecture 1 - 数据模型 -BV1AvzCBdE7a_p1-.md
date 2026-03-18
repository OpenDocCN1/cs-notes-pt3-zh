# 【全集】加州理工学院 软件设计与开发 中英字幕 1080P p01 Lecture 1 - 数据模型 -BV1AvzCBdE7a_p1-

The next thing I want to talk about then is actual data modeling。

 so I have another presentation that I encoded into some ugly slides。

To talk more about the data modeling concepts， so in the last slide deck we mentioned that essentially any computer application that we're going to create is a combination of two things it's data models。



![](img/276efe21a56ade8666071927d04d30f9_1.png)

![](img/276efe21a56ade8666071927d04d30f9_2.png)

And it is an algorithm that then processes on top of those map models， so we have input。

 we have beginning things， we have some desired result。

 and then we create a sequence that gets us from beginning to the end。

 but the sequence relies on those data models we defined。😡，是。

And again we'll talk more about that in this section。

 so a quick overview for this is what is data modeling types of data modeling we'll talk about quantitative data versus qualitative data。



![](img/276efe21a56ade8666071927d04d30f9_4.png)

![](img/276efe21a56ade8666071927d04d30f9_5.png)

We'll talk about computers and data modeling because we can model data， right？😡。



![](img/276efe21a56ade8666071927d04d30f9_7.png)

Outside of computers data modeling was a thing like with recipes with cooking you don't need a computer for that it's just a way of formalizing a set of instructions and passing it and a way of implementing those instructions right so using particular data types we're going call that are data types and cooking or things like how to measure ingredients how to measure time and how to measure heat so whenever I say a data type think of it as a way of measuring something it's a unit a set of values and they're well definedfin。

😡。

![](img/276efe21a56ade8666071927d04d30f9_9.png)

![](img/276efe21a56ade8666071927d04d30f9_10.png)

![](img/276efe21a56ade8666071927d04d30f9_11.png)

Okay， so。

![](img/276efe21a56ade8666071927d04d30f9_13.png)

And one it is data modeling， data modeling is the scientific approach to express a given problem domain in terms of quantitative values。



![](img/276efe21a56ade8666071927d04d30f9_15.png)

And again， all that states there， it's a really fancy way of stating that。



![](img/276efe21a56ade8666071927d04d30f9_17.png)

Going back to our continued example of cooking that we have a way of measuring our ingredients。

 a way of defining the measure of our time， our way of de measuring our heat in physics， right？



![](img/276efe21a56ade8666071927d04d30f9_19.png)

There's lots of like being able to do movement we can do by measuring velocity， right？

So anything that we need to be able to build an application around。

 we have to be able to construct a data model and those data models will be when we start actually learning some Java code。

 be represented as a data type。😡，We can define it as the development of a model usually mathematical of a real world problem scenario or environment。

 this model is used to provide insights into the solution of the given problem。

 it isn't enough just to know the mathematical details of a particular modeling technique can be set up and solved。

 it is equally important to be familiar with the limitations the assumptions and specific applicability of the model。



![](img/276efe21a56ade8666071927d04d30f9_21.png)

![](img/276efe21a56ade8666071927d04d30f9_22.png)

And so the correct use of modeling techniques usually results in solutions that are timely， accurate。

 flexible， economical， reliable， easy to understand and easy to use。



![](img/276efe21a56ade8666071927d04d30f9_24.png)

Excellent， so does everyone understand what the slide is communicate， Is there anything that。



![](img/276efe21a56ade8666071927d04d30f9_26.png)

That seems。And I will provide these slides to you as well。

 and I'll also provide this recording to you as well so you will have a chance to look back at August。

😡，Probably sometime after this lecture， I'll do that。



![](img/276efe21a56ade8666071927d04d30f9_28.png)

Okay， so what are the different types of models so our data models can be broadly classified into two categories based on the type and nature of the decision making problem under consideration so you have what are called deterministic models and you have proable probabilistic models when I've been talking about the recipe for cooking a cake。

 we've been talking about deterministic models， these are models that when I say deterministic it's something that has no inherent randomness。

 no inherent chance no inherent change to it right it's well defined and it's going to be the same every time what's an example when I say probabilistic model which another term for probabilistic is stochastic so stochastic is another common word that you might encounter if you ever see it in the world of computer science is just ascribing that it is a model that has an inherent randomness to it or it is not deterministic。



![](img/276efe21a56ade8666071927d04d30f9_30.png)

![](img/276efe21a56ade8666071927d04d30f9_31.png)

![](img/276efe21a56ade8666071927d04d30f9_32.png)

![](img/276efe21a56ade8666071927d04d30f9_33.png)

So can anyone think of what a probabilistic model might be or like an action an event。

 exactly a card game or like rolling in a die， I can't。

 if I wanted to like formally define rolling a die。

 I have to use a probabilistic model for that right to if it's to represent the actual act of rolling a die。

 I couldn't just implement that as yeah， roll the whatever the average would normally be like the number three。

😡。

![](img/276efe21a56ade8666071927d04d30f9_35.png)

Like that wouldn't be a die roll right that because I could get different values from that and it's going to be different every time I roll it so that is an example of when we try to model something that is based off of probability and then I have to consider that when I define my model so keep that in mind as you start creating your models that you then build your algorithms on top of there are some models that are。

😡。

![](img/276efe21a56ade8666071927d04d30f9_37.png)

![](img/276efe21a56ade8666071927d04d30f9_38.png)

![](img/276efe21a56ade8666071927d04d30f9_39.png)

By definition， have randomness in that。So again， we'll get more into this when we start talking about developing our algorithms。



![](img/276efe21a56ade8666071927d04d30f9_41.png)

That's an important distinction so again determinants models assume that all the relevant input data values are known with certainty and that is that they assume that all the information needed for modeling the problem is available with fixed and known values so in our recipe everything's known everything's fixed and it's the same every time。



![](img/276efe21a56ade8666071927d04d30f9_43.png)

![](img/276efe21a56ade8666071927d04d30f9_44.png)

![](img/276efe21a56ade8666071927d04d30f9_45.png)

In a probaistic model， which can also be called a stochsastic model。

 we assume that some input data values are not known with certainty。

 that is they assume that these values of some important variables will not be known before decisions are made and so it's therefore important to incorporate this kind of ignorance into our model。



![](img/276efe21a56ade8666071927d04d30f9_47.png)

![](img/276efe21a56ade8666071927d04d30f9_48.png)

![](img/276efe21a56ade8666071927d04d30f9_49.png)

So probabilistic model techniques provide a structured approach for developers to incorporate uncertainty into their models and to evaluate criteria under alternate expectations regarding this uncertainty。

 they do so by using probabilities or random or unknown values。



![](img/276efe21a56ade8666071927d04d30f9_51.png)

And so we will see how to do that later on when we start building out some real software。

 let's talk about the difference between quantitative versus qualitative data because this is an important distinction as well that unfortunately the textbook just doesn't go into it and it assumes you already know this stuff。



![](img/276efe21a56ade8666071927d04d30f9_53.png)

嗯。So any modeling process starts with data right and so like raw material for a factory。

 the data is then manipulated or processed into information that's valuable to the people who's used in your application。

 so the processing and manipulating the raw data into meaningful information is at the heart of data modeling that's what we're trying to do when we build out our applications。



![](img/276efe21a56ade8666071927d04d30f9_55.png)

![](img/276efe21a56ade8666071927d04d30f9_56.png)

![](img/276efe21a56ade8666071927d04d30f9_57.png)

So in dealing with a problem， developers may have to consider both qualitative and quantitative factors。

 so the quantitative data are measures of values or accounts that are expressed as numbers。So again。

 we were quantifying。

![](img/276efe21a56ade8666071927d04d30f9_59.png)

Our ingredients， we were quantifying heat， we were quantifying time whenever we build out a recipe。😡。



![](img/276efe21a56ade8666071927d04d30f9_61.png)

So for our qualitative data， those are measures of types and may be represented by name a symbol or number of codes。

 so like for instance， the qualitative data could be things like labels like names。嗯。For instance。

In cooking you might have labeling like fruits or vegetables like when you make a meal you might have labels where it has to have a protein。

 a vegetable， a fruit and a starch right so those aren't quantify things those are qualified things so does everyone kind of see the difference between so when I give a label to something like for instance if I wanted to start quantifying this class if I want to start data modeling this classroom every person here can be a composition of different data models I might be able to ascribe the age which is a number thats that's a quantity right so that's a quantitative data for each person because it's represented as a number so you would have one age you would have one age you would have one age so everyone has an age so that is one way that I can define each person this's wrong Another way I could use would be the qualitative data which would be your name。

😡，That's not something I can necessarily ascribe a number to。

 but it's a set of meaningful labels or values， so you have a name， you have a name。

 you have a name and each person has a name and it's wrong and then maybe I can go ahead and also identify each person as their major well is there major a quantitative or qualitative form of data。

😡，It's qualitative right because it's a label and not a number okay。

 is your GPA a quantitative or qualitative form of data right exactly？😡，嗯。

So you could see and there are some times where you can take qualitative data and map it to become quantitative data because let me ask you this。

 your grade that you get in this class， is it a quantitative data or is it a qualitative data？😡。



![](img/276efe21a56ade8666071927d04d30f9_63.png)

Its quantitative and qualitative， it can be represented numerically or as a label from a to F right or maybe with the absence of E in there。

😡。

![](img/276efe21a56ade8666071927d04d30f9_65.png)

Right so you can have a translation between qualitative and quantitative and quantitative back to qualitative。

😡。

![](img/276efe21a56ade8666071927d04d30f9_67.png)

嗯你三。That's right any label that is not a number is qualitative and if we can describe a number to it。

 it's quantitative because we can define a quantity to it and you could do a mapping you can define a mapping to translate qualitative data into quantitative data or quantitative data into qualitative data but then you're transforming it right because the a isn't a number but it can represent something that's numerically relevant such as the value 90 or higher a B isn't a number but it can have the representation of a number between 80 to 89 so it's an abstraction it's the ambiguity that we sometimes like to have。



![](img/276efe21a56ade8666071927d04d30f9_69.png)

![](img/276efe21a56ade8666071927d04d30f9_70.png)

![](img/276efe21a56ade8666071927d04d30f9_71.png)

Because abstractions are powerful concepts and then numbers are super precise。😡。



![](img/276efe21a56ade8666071927d04d30f9_73.png)

And sometimes it's meaningful for us to represent the same thing in the form of both qualitative and quantitative。

 but I definitely want to hearken， I want everyone to understand that those are the two kinds of properties that we can start defining things。

 seeing the world in using the lens to start mapping things into formal languages。😡。



![](img/276efe21a56ade8666071927d04d30f9_75.png)

![](img/276efe21a56ade8666071927d04d30f9_76.png)

![](img/276efe21a56ade8666071927d04d30f9_77.png)

Okay， let's talk about using computers in data modeling because so far what I've talked about right now could be done on with pen and paper could be done in our minds right。

 it could be done smoking， it could be done written written down on paper。

 but it doesn't necessarily need a computer but what we learn to learn how to do is use computers right these tools。

😡。

![](img/276efe21a56ade8666071927d04d30f9_79.png)

![](img/276efe21a56ade8666071927d04d30f9_80.png)

![](img/276efe21a56ade8666071927d04d30f9_81.png)

To be able to implement our formal models， our mathematical models and our algorithms so that we can execute them。

😡。

![](img/276efe21a56ade8666071927d04d30f9_83.png)

Autoomatically and not by hand。😡。

![](img/276efe21a56ade8666071927d04d30f9_85.png)

Okay， and so the steps involved in data modeling can be very verbose and so this is the kind of。



![](img/276efe21a56ade8666071927d04d30f9_87.png)

Illustration here on the side of what this would actually look at so there you can think of this as having three distinct steps。

 so regardless of the size， regardless of the complexity of the model at hand， the problem at hand。

 your data modeling process involves a formulation of the the data model。

 the solution that you need to result in and then an interpretation of it。

So the figure provides a schematic over these steps along with the components or parts of each step。

 we discussed each of these steps in the following sections。

So here the formulation can be broken down to defining the problem。

 developing the model and then acquiring your input data。

 your solution is then developing the solution， so the algorithm that processes your input into the output and then testing the solution to make sure that it's correct and then once you have the result you want to interpret it you want to translate your formal language result into you reparse that and translate that back out into what it is in the real world to see if it matches if what the data you put in and the result you get out actually is representative of the problem that you're trying to solve with your application regardless of whether it is whether it's a physics problem or an accounting problem whether it's a cooking problem。



![](img/276efe21a56ade8666071927d04d30f9_89.png)

![](img/276efe21a56ade8666071927d04d30f9_90.png)

![](img/276efe21a56ade8666071927d04d30f9_91.png)

![](img/276efe21a56ade8666071927d04d30f9_92.png)

Okay， so let's talk about formulation formulation is a process by which each aspect of a problem scenario is translated and expressed in terms of the mathematical model。

 This is perhaps the most important and challenging step in data modeling because the results of a poorly formulated problem will almost surely be incorrect and again this is what we're really going to stress training you on all throughout the semester this is the hardest part of codingve I've heard repeatedly I've taught this class for many years now and the number one thing I hear on a consistent basis is that I understand what the individual Java statement do when you show me how to print something I understand what's happening in that statement when I do selection statement so when I use like an F statement but I do a repetition statement so if I do like a while loop or like a for loop I understand what that's doing but I don't know how to piece those individual pieces together to build an application。



![](img/276efe21a56ade8666071927d04d30f9_94.png)

![](img/276efe21a56ade8666071927d04d30f9_95.png)

![](img/276efe21a56ade8666071927d04d30f9_96.png)

![](img/276efe21a56ade8666071927d04d30f9_97.png)

![](img/276efe21a56ade8666071927d04d30f9_98.png)

![](img/276efe21a56ade8666071927d04d30f9_99.png)

![](img/276efe21a56ade8666071927d04d30f9_100.png)

And that is the most challenging part and that's the part that's handw the right that's the part that a textbook can easily try to ignore and say here we're going to teach you Java and we're going to show you all these Java bits。

😡，But the magic isn't in learning the Java bit that's like trying to tell someone who wants to write a novel。

 I'm going to teach you all these words I wants to teach you all the words。

 those are the same words that are used in all these other novels so then you could just write a novel bit。

😡，不。😡，Writing novel is more than just combining words that you know together。

And it's the same thing with applications and it all starts from that basis so like with a novel you might start with designing like a plot like an outline right you might start with an outline and you keep building on top of that basic outline so for our algorithms for our applications our outline is going to be the models we select and the story will be the algorithm that we apply on top of that model。



![](img/276efe21a56ade8666071927d04d30f9_102.png)

![](img/276efe21a56ade8666071927d04d30f9_103.png)

ok。So inside of this inside of step one， we're going to define the problem。

 we're going to develop the model and we're going to inquire our input so defining the problem。

So the first part is to develop a clear concise statement of the problem。

 the statement gives direction and meaning to all the parts that follow parts that follow it in many cases defining the problem is perhaps the most important and the most difficult part it is essential to go beyond just the symptoms of the problem at hand and identify the true causes behind it。

 one problem may be related to other problems and solving a problem。



![](img/276efe21a56ade8666071927d04d30f9_105.png)

![](img/276efe21a56ade8666071927d04d30f9_106.png)

Without regard to the related problems may actually make the situation worse。

 i'll give you an example of that where you might have actually seen where the solution of one problem requires some other problem let's go back to a cocktail recipe。

 for instance。😡。

![](img/276efe21a56ade8666071927d04d30f9_108.png)

![](img/276efe21a56ade8666071927d04d30f9_109.png)

Let's say I'm making something like a old fashioned and so the ingredients might be bourbon right。

 and it might be some bitters， it might be a cherry。

 it might be an orange and it might be some simple syrup， right？

And so well now I have another problem， S syrup in itself has a recipe right I might not just have simple syrup。

 so then I have to go look up the solution for that problem before I could solve this problem of building an old fashion so then I see oh a simple syrup might be two parts of water one part sugar and you boil that and you dissolve the sugar into the water and now I have a simple syrup so then I have to do that before I could make my old fashion so just like and so we'll see things like that in a more generalized approach where we'll have these smaller problems that we solve that feed into the larger problem that we're trying to solve and we identify that during a formulation phase where we're defining all the different parts of the problem and what problems rely on other problems or like what models rely on another。



![](img/276efe21a56ade8666071927d04d30f9_111.png)

![](img/276efe21a56ade8666071927d04d30f9_112.png)

![](img/276efe21a56ade8666071927d04d30f9_113.png)

![](img/276efe21a56ade8666071927d04d30f9_114.png)

![](img/276efe21a56ade8666071927d04d30f9_115.png)

![](img/276efe21a56ade8666071927d04d30f9_116.png)

Or other smaller models， does that kind of makes sense？



![](img/276efe21a56ade8666071927d04d30f9_118.png)

学级。嗯。Then we'll have then once we've defined the problems that once we define what it is we're trying to do。

 then we start developing the models around them so again the first thing we wanted to do when we' were making a cake was say hey we want to make a cake。

😡。

![](img/276efe21a56ade8666071927d04d30f9_120.png)

And then we're like okay the next thing we need to do before we make a cake is then make sure we understand the models by which we're going to follow the recipe so making the cake requires us to understand what a cup is right if you don't have a cup measuring told in the recipe that says use a cup isn't going to work out so well like if you use a pan glass as your cup that's going to be wrong right so here we start developing the models now in cooking we already have those models developed but when you're writing software you get to design the models。

😡。

![](img/276efe21a56ade8666071927d04d30f9_122.png)

![](img/276efe21a56ade8666071927d04d30f9_123.png)

You get to ascribe the systems of meaning or you get to decide which ones to use。



![](img/276efe21a56ade8666071927d04d30f9_125.png)

Right like so whoever decides to do the cooking recipe decide to use cups。

 but they could have used pints right， they could have used pints of flour。😡。

There's no reason why they couldn't。It's another measure for it。

 but what they couldn't have used is degrees of flour or seconds of flour because those measures don't quite make any sense。

😡，Okay， so once we select the problem to be analyzed， the next part is to develop a data model。

 even though you might not be aware of it， you have been using models most of your life， for example。

 cooking recipes or models plus algorithms for making food。



![](img/276efe21a56ade8666071927d04d30f9_127.png)

What sets data modeling apart from other modeling techniques is that the models we develop here are mathematical。

 a mathematical model is a set of mathematical relationships in most parts the relationships are expressed as equations and inequalities where they may be processed to compute。

 for example， things like sums or averages or standard deviations。😡。



![](img/276efe21a56ade8666071927d04d30f9_129.png)

Most models contain one or more variables and parameters。

 a variable as the name implies is a measurable quantity that may vary or that is subject to change。

 variables can be controllable or uncontrollable a controllable variable is also called a well a variable a problem parameter is some measurable quantity that is inherent to the problem in most cases variables are unknown or changing values where parameter or input data are given values into the model。



![](img/276efe21a56ade8666071927d04d30f9_131.png)

![](img/276efe21a56ade8666071927d04d30f9_132.png)

Okay so let me kind of express that out there's this concept with our model that we'll call parameters the parameters are the things we feed into it so those aren't known to the model itself until you execute that model so an example of a parameter for our cake would be inputting all the different flour or the size of the cake maybe like so for instance。

 for a cocktail。

![](img/276efe21a56ade8666071927d04d30f9_134.png)

![](img/276efe21a56ade8666071927d04d30f9_135.png)

Recipe we might express all of the units and partss and then you can change the quantity that you're inputting into the cocktail recipe so you can make a picture or you can make a single glass and you can follow the same recipe so the input into that algorithm into our model could be represented as a set of parameters so the initial inputted data and then the values that are actually defined inside of our model so when we start creating our recipe if we have a starting point and ending point right where where the ingredients come in all the way into where the ingredients are composite together and produce the final product then those are going to be our variables within the model that can mutate and change state over time and the things that don't change state over time are constants those concepts kind of make sense so three things to think of when we're talking about models parameters in variables inherent within the model parameters come from the outside look get inserted into our model and constants are。



![](img/276efe21a56ade8666071927d04d30f9_137.png)

![](img/276efe21a56ade8666071927d04d30f9_138.png)

![](img/276efe21a56ade8666071927d04d30f9_139.png)

![](img/276efe21a56ade8666071927d04d30f9_140.png)

![](img/276efe21a56ade8666071927d04d30f9_141.png)

![](img/276efe21a56ade8666071927d04d30f9_142.png)

![](img/276efe21a56ade8666071927d04d30f9_143.png)

![](img/276efe21a56ade8666071927d04d30f9_144.png)

Things that are quantified， they or qualified， but they never change over time。

Most models contain one or more y， so all models should be developed very carefully。

 they should be solvable and realistic and easy to understand and modify and the required input data should be obtainable。



![](img/276efe21a56ade8666071927d04d30f9_146.png)

Okay， so for acquiring input data， once we've developed a model。

 we have to get the input data into the model， so usually almost every kind of model we have。

 we have to tell it what the starting state is。

![](img/276efe21a56ade8666071927d04d30f9_148.png)

And then so step two is where we try to process a solution。

 so the solution step is when the mathematical expressions resulting from the formulation process are actually solved to identify the optimal solution。

 it's broken into two parts developing a solution。

![](img/276efe21a56ade8666071927d04d30f9_150.png)

Where we we figure out how to use our model and manipulate our model so that we can evolve our initial state。

 our starting set of ingredients into the final processed。😡。



![](img/276efe21a56ade8666071927d04d30f9_152.png)

Output that we want so again， the entire point of developing the solution that's going to be our algorithm that's going to be our step by step instructions that say how do we move from a set of ingredients to a final cake。

😡。

![](img/276efe21a56ade8666071927d04d30f9_154.png)

And then we test that。After we're done we might take a bite of the cake right like when you're cooking you're constantly testing when you're serving it like is it lumpy。

 let me taste this the batter to see if it's sweet enough if it needs salt。

 if it needs sugar and then if you're happy with it you move to the next step right？😡。



![](img/276efe21a56ade8666071927d04d30f9_156.png)

If you're cutting， you might go ahead and spread it out and make sure that everything's diced appropriately and you might miss a piece or maybe there's a piece that looks kind of rotted or whatnot and you throw that part off。



![](img/276efe21a56ade8666071927d04d30f9_158.png)

So each part through the process of cooking， even in between stages you might test before moving to the next step and that's important that's an important part of the process。

😡，And then when the cage's finally made， you eat a part of it and say like， yeah。

 that's a wellade cake。And then finally you have the interpretation。

 which is assuming the formulation is correct and is successfully implement itself。

 how does the user use the results with recipes this doesn't make so much sense。

 but sometimes for other things that are more abstract in general there's an interpretability there like how do you translate what your output is back into the thing it's supposed to represent。

 so when I was first talking about natural languages and how you're parsing my words back into concepts that's the interpretability step。



![](img/276efe21a56ade8666071927d04d30f9_160.png)

![](img/276efe21a56ade8666071927d04d30f9_161.png)

![](img/276efe21a56ade8666071927d04d30f9_162.png)

And then again， you can have like the concept of ambiguity there so you can ascertain how much ambiguity is。

 which is what your sensitivity analysis is， but now I'm not so worried about that。



![](img/276efe21a56ade8666071927d04d30f9_164.png)

So it's also important that your model is readable。

 we strongly recommend that you get in the habit of using descriptive titles。

 labels and comments in any data model you create so this means while we're authoring our code or if you're building a recipe you just don't use like random variables like accent and Y be very descriptive as to the labels or things that each things supposed to represent so when you go back to read your algorithms or your models in the future。

 you understand what you intended。😡。

![](img/276efe21a56ade8666071927d04d30f9_166.png)

![](img/276efe21a56ade8666071927d04d30f9_167.png)

![](img/276efe21a56ade8666071927d04d30f9_168.png)

Don't care about that so I just want to finish off this slide so so'm not I don't really care about problems with modeling because we'll encounter that over the semester。

 but I will share these slides that you can go ahead and see them in the future so I just want to finish off by giving an example for developing models and so here computer applications are composed of two things right systems of models usually more than one like in our recipe we use three different models right so those could be quantitative or qualitative and it's definition for an object or behavior on our application it's also algorithms to process information results from the models so that's our order set of instructions so for instance with our cake if we wanted to make a cake we have to define how do we measure our ingredients。



![](img/276efe21a56ade8666071927d04d30f9_170.png)

![](img/276efe21a56ade8666071927d04d30f9_171.png)

![](img/276efe21a56ade8666071927d04d30f9_172.png)

![](img/276efe21a56ade8666071927d04d30f9_173.png)

![](img/276efe21a56ade8666071927d04d30f9_174.png)

How do we measure our heat and how do we measure our time and so those are three different models so if we were to express a cake as。



![](img/276efe21a56ade8666071927d04d30f9_176.png)

A composition of what it is in a software application， well that would be a quantity model。

 plus a temperature model， plus a time model， plus the algorithm， the sequence of steps。😡。

So if I wanted to do this to say make a video game I might have to ask myself well how does my character exist I might give it labels like a name and so I would have a list of names。

 how does my character walk around I might use a coordinate system like a grid where I have an X and Y coordinate so I'm quantifying the idea creating measures of my idea of how I can movem I'm qualifying an idea of existence and finally my character might have to survive if I have to be alive。

 I have to define mortality so I have to quantify I might give hit points then if I'm at zero hit points I'm dead if I'm at positive hit points I'm alive and I can take damage to the form of hit points without to subtraction operation so I process the character's mortality by reducing the hit points when it gets damaged or adding hit points when it heals back up and again what we're doing is we're taking a phenomena and observation a concept and we're mapping a model on top of it and then our game within defining an algorithm on top。

😡。

![](img/276efe21a56ade8666071927d04d30f9_178.png)

![](img/276efe21a56ade8666071927d04d30f9_179.png)

![](img/276efe21a56ade8666071927d04d30f9_180.png)

![](img/276efe21a56ade8666071927d04d30f9_181.png)

models that we can then use to make our character move around when the user wants it to move around to engage in combat and potentially die or get experience points when they kill monsters and that's going to be the underlyinglin basis of how we're going to start building out our applications okay so I'm out of time is there any questions but that's also the last slide for this presentation so i'm perfectly where I want to be here is there any questions up to this point who we're at？

😡。

![](img/276efe21a56ade8666071927d04d30f9_183.png)

![](img/276efe21a56ade8666071927d04d30f9_184.png)

![](img/276efe21a56ade8666071927d04d30f9_185.png)

![](img/276efe21a56ade8666071927d04d30f9_186.png)

Everyone feels good about these concepts okay so next lecture next week we will start with talking about the basics of algorithms。

 especially as it relates to computer algorithms and what are our requirements on that so I can't wait to see you all next week next Tuesday I guess。

Yes， but it's the same thing you did in lab。But what's that well okay i'll do this i'll go ahead and i'll extend I won't change the due date but I won't apply a late penalty for it so i'll give you until the end of day of next Tuesday so we have at least one more lecture day so that we can actually see me execute Java code so if you can't get it turned in by Friday don't stress。

😡。

![](img/276efe21a56ade8666071927d04d30f9_188.png)

![](img/276efe21a56ade8666071927d04d30f9_189.png)

if we didn't lab we're done yeah， but yes， if you didn't but make sure you turn it in on Moodle so I have a Moodle submission because that lets me know again I use Moodle to be able to track the progress of each and every one of my students so I know whether you're caught up with all the like course content or not so please submit any like homeworks that you've completed so I know that you're caught up with where we're at。

😡。

![](img/276efe21a56ade8666071927d04d30f9_191.png)

![](img/276efe21a56ade8666071927d04d30f9_192.png)

Excellent， any other questions？Have a great day， have a great weekend。

probably I think I don't remember that I think it's like 316 or 317 or something like that。

 but it's on this side its like almost directly on top of us it's right next to the like the main office。

Okay so if we have questions with the lab， sometimes， can we ask you those？



![](img/276efe21a56ade8666071927d04d30f9_194.png)