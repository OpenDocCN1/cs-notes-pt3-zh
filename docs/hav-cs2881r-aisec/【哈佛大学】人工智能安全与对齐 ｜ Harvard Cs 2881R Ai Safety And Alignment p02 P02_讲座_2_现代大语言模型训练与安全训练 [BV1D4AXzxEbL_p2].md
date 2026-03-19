# 【哈佛大学】人工智能安全与对齐 ｜ Harvard Cs 2881R Ai Safety And Alignment p02 P02_讲座_2_现代大语言模型训练与安全训练 [BV1D4AXzxEbL_p2]

嗯。Okay， let' just using it。So，So today I'm going to talk about just the general pipeline of how do we train。

Modern LLMs。And a post random and safety training。 And we're also going to look a little bit in some of the masks behind it。

And actually this is based on these papers， I don't work on。

Pretraining or reinforcement learning reasoning in open eyes。

 So they basically this is just based on these papers。😊，And with any direct knowledge。And and。Yeah。

 and give so much。 So maybe before that。IJust want to talk a little bit on。

What makes play I most challenging。So there is a quote that I really like from Edgar Dyktra。

 I guess many of you have learned the Dykstar's algorithm。😊，嗯。

And he said the following thing he said like think about usually how things work in the world。

 like say you look at say a town is made from neighborhoods， it's made from streets。

 we're building bigs， etc cetera。 And generally so you have systems that are when you go in order of magnitude of two。

 you skip to a different subsystem that a different profession deals with so that town。😊。

The town planner deals with the town。 The architect deals with the buildings。

 carpenter deals with the bricks and or what the carpenter deals with and the solid state physicist deals with the particles。

 and in contrast， in computer science， you said it in 1989， said the ratio。

 the order magnitudeitudes that computer scientist。

 the single person needs to deal with can go from a B to a few hundred megabytes。

 which is like 10 to the9。😊，Order of magnitude。 And this is basically an。

The programmer is the only discipline that one person needs to deal with such a gigantic ratio。

 which means that a programmer needs to think of conceptual hierarchies that are deeper than anyone has faced before。

And he has this nice point， he says you know， some people。That this is 1989， people would said， well。

 what is a computer， A Comp is just like， you know， a cash register， just faster and bigger。😊。

And basically said， you know， this is a very like this might be technically true。 in some sense。

 I mean， maybe a cash register is doing complete。 I don't know。

 Probably you could find definitely the very the very things that are like general computing device。

 So this might be kind of in some kind of way。😊，The shallow way might be correct。

 but it's missing the point。 It's like comparing a supersonic jet with a calling baby。

 I didn't check Dyson's calculation， but prefer the ratio is only 1000 or maybe has like a really fast baby just to think like what does 10 to the 9 means like 10 to the 9 ratio is like the ratio between a billiard ball and the size of an atom。

 So we know all physics changes when you move from this the regime to another regime。

 So this is kind of a point where there is a famous X And I I think more more is different。

 but this is just generally like you change you change so many orders of magnitudes。

 everything changes。😊，So 10 to to 9 was a completely baffling ratio。

 But what ratio do we deal here now， right？ So if we're talking about for training runss。

 there are about 10 to the 25 floating point operation。

 So you deal from the one floating point operation to 10 to the 25 of them。

 and no modern clusters about， I think I rounded it up。 But about like Zeta flop per second。

s like 10 to the 21 fps per second。 so。😊，So， in some sense。If computer science was a。

If computer science already kind of changed the way we think by adding by moving to 10 to the 9 ratio。

AndIn some， modern machine learning。Is another change on top of that。So by saying， yeah。

 it's just the same， just， I mean， if someone tells you， you know， it's just the same。

 just bigger for something that is 10 to the nine bigger。It's not a thing。

So the levels of obstruction that you can have in AI。😊。

Can really range even beyond what we know in computer science， so。

I think you can sometimes talk about things like the model is a little bit eager to please the user or how do we quantize real number into four bits？

😊，And anything in the middle I haven't seen it， but at least in the in deep learning。

 I thing in LLMs， maybe it's the only discipline where at least potentially if you have a bug in your model。

😊，The solution might be ever be to speak to it in a more st voice or fix a bug in a couda kernel。

 And up all， you don't know which one is a good cause。

 so you really do move kind of between all levels of abstractions and then。😊。

And this is one of the reasons why I sometimes also try discourse。

 especially with AI safety starting move。😊，And， you know。One slide。

 we might be quoting Kant and the categorical imperative and another one we might be going back to high school math or looking at a floating point of arithmetic。

😊，So let me give a very high level and yeah like I said， I've not。😊。

I would not consider myself an expert model trainer。

 but a brief overview of LLM training the way I see it， please。😊。

So this is the way I view deep learning。 I don't know if anyone agrees。

 The way I view it is the following， you have。You are trying to convert resource into intelligence。

And。Let's say the research is floating point operations， but it could be data， memory。

 world clock time， dollars， whatever。And what you really care about in deep learning。

Is how much of intelligence gain you make per investment of this resource？

And the main thing is like if you compare deep learning with classical learning。😊。

Is that a lot of these say classical machine learning methods， they actually might be cheaper。

 faster to learn from a limited number of examples using a limited number of compute。😊。

mount of compute， but they peter out。What you want in deep learning is something that is very simple。

Not completely stupid so you actually gain something so you're not just wasting flops or nothing。

 but you'll fine if you're wasting flops initially and you're getting much less per flop initially。

 but what you want is that something thats scale that something will not peter out and you can do it like for 10 you can continue for 10 to to 25 flops This is in the bitter lesson ultimately you can do some clever tricks to。

😊，To have methods that don't scale and they initially could show more promise。But eventually。

 what you really want is a simple general recipe to convert compute into into results that you can run for much。

 much longer that。😊，We'll win in the end。嗯。So what we really want is。

Intelligence gain first step is positive， so we gain something first step。😊。

And the ability to take tons and tos and tons of steps without saturating。And。Its kind of an analogy。

 I think about it。 I' know economists or finance。 So maybe it's wrong。 But the way I think about it。

 you can compare， let's say， if you're a small scale investor whose marginal dollar will not move the market。

 maybe you can have like some clever strategy to make some investment that will。😊。

That that will will give a higher return per dollar。

 But what you really want is deep learning is more like a machine。

 You just want an index fund that you can invest in $10 billion like an unlimited amount and just you might not make as much。

 but you're gonna make it more fit in the long run。😊。

So if what we want is a system that something that is simple， it's not stupid and scales。

Then next token prediction is not a bad objective to satisfy this。

 so basically the input is a list of tokens and tokens。

 you can think of it as just a number between one and something。😊，Or a letter。

 and the output is the next element in this list。The advantage of this。Is。If you improve it。

 you are going to。You're going to gain some skills on knowledge。

 like predicting next token is very general and depending on what the text if you're predicting。

If you're predicting a C program， you probably need some see to if you're a philosophy text。

 youll need to know some philosophy。If you're predicting a numerical sequence。

 you need to know some math， so it's kind of a general task that as you improve it。

 you gain more skills and knowledge。😊，And you gain something as long as you as long as you didn't get to the point where you completely saturated and you' have achieved the maximum possible prediction。

 then you gain something per token。And it's unsupervised， so you can get a lot of data。

 you don't need anyone to label this for you as long as you have tokens， that's good。And yeah。

 it's hard to saturate。 I mean， people love。Definitely been trying and it seems that I haven't there's lots of tokens out there。

😊，So。So mathematically the way we think about it in transformers and generally like yes。😊。

I just want to ask with respect to the past graph that we saw。

 since we know from our peer readings and from my go research has been published that not all flops are equal because not all datata is equal in terms of intelligent scheme。

 we know if there has been some sort of like quantitative study on maybe correlating the amount of noise with the amount of performance improvement in LNs。

 because like we talk about for example， deep math purpose。

 which seems to be a high quality cognitive reports or things that。Yeah， I mean。

 there have been like various， mean I think this is kind of the first approximation。

 the second approximation is that maybe you care about how positiveivity is this thing and some tokens are maybe better than others。

😊，And there have been some papers on various data diets in ways like that。Generally yeah。

 like it's clear that maybe not everything is equal。

 I think it's also possible that if you're too clever things， sometimes the simple。

 like if you're trying to be too sophisticated in in trying to kind of optimize this cost。

 you might end up like losing the simplicity etc ce， but there might be some middle ground。

 like obviously。These blockss are very expensive。 So if you can say if you gain。

 you can lift this graph by even like， you know，2% that something that's that saves you like a good amount of money。

 And definitely if you can lift it to buy a factor of too。😊，Yeah， so so so mathematically。

 the way we think about it and we like to work in continuous space to the extent it's kind of a lie because we are discretizing more and more and more。

 So what extent like if you're representing a number in four bits is continuous。

 that's a good question we like to pretend that we work in continuous space and so we think of the input as vectors rather than tokens。

😊，And we think of the output as vector。And we think， so how do we map？talkingken to a vector。

 we apply some matrix， some embedding matrix， so they're talking。

Thebetic of the tokenine is the embetic matrix applied to ET and this is a good opportunity to say this general disclaimer that's to in all of my courses。

 any possible equation that I write it is probably going to be only correct up to some transposes and if there are10 those up to some peruting。

😊，U to some peruting of the indexdices and sometimes if I'm less lucky also up to sign and switching the equality sign。

 but I try not to do that。😊，So there is also an un embedding the matrix and the unabbedding matrix can convert say a vector。

 not necessarily yeah， so convert a vector into even a token， if it gives like the standard basis。

 then it's a token， but it can generally convert。😊，To a probability distribution。

 And we the standard way， we use it。 We parameterize these things is that。If you have a vector。

 the way you get a distribution is okay， so you apply。This is kind of fragment。 I mean。

 this the vector after you apply the un embedding matrix， so。This would be like U why or。Then so if。

 so you， Y will apply this distribution。 I wrote is actually， this is exactly this。

 So the it's a probability distribution such that the probability that you get。

The probability that you get a value team is proportional to E to the teethF coordin of your tin times some constant。

😊，And this constant is known as the temperature Tau。 So if tau is infinity， this basically。

Is the uniform distribution？And if t is zero， then all the weight is on the coordinate that is highest。

And just generally the reason why if we think of temperature here。

 if you think of a system when it's very， very， if you have like a system of say molecules or something。

 if you turn up the temperature to infinity it will all move around。

 it will be like the uniform distribution， if you turn out the temperature to the absolute zero。

 then it will be like fixed and nothing moves at all。😊，And。So generally。

 like before we talk about transformers or anything like that。

 basically any architecture for doing next to and prediction。 So so far。

 I just wanted to say that just next to prediction is very natural from the point of view of let's do something not stupid that scales。

😊，And let's take， I mean， if we like to work in continuous space。

 then so far we haven't like we just want some way to map to map inputs to outputs。

 so basically next soken prediction in any architecture for next soken prediction would be something that takes n vectors and outputs one vectors。

And so far， we haven't really made much choices。So。In that way， but before we talk about like。

Before we talk about what architecture we use for it。

 just want to say the one thing that people sometimes say so people sometimes look at， say， oh。

 language models are just next token prediction。 Therefore they cannot be intelligence。

 they are just schastic powers， they are just repeating， maybe they are J to go the web。

 they are they are just repeating previous information。 they are only predict。So。

I think this is a very， again， simplistic point of view。And。

Next talking prediction doesn't really restrict in any way。

Any time serious iss basically a next token prediction， right， you get you basically。

Get a sequence of elements。 And then you predict the next one。 When I'm talking。

 I'm also doing some time series。 We live in time。 We don't know like in sense。

 it's very natural more than anything as a time serious because this is how we live right like every action we take。

 the next action based on the previous one。 So sorry to say that but everyone here is a next token predictor。

 maybe the models are stochastic point powers。 maybe they don't have anything original to say。

 but that has nothing to do with whether the next predictor Also the stochastic is irrelevant。

 Like the fact that there is randomness involved also is irrelevant。😊，So。AndYeah， by the way。

 I asked G5 to。What does it think about is a stochastic part？It's nice。

And you can ask students whether it was simply powering the images that were already in the data or did it create a new image？

It the on。So， okay， transformers。So。Usually I think in deep learning courses。

 when we talk about neuraler networks， we use this word neural and we try to maybe motivate sometimes。

 I mean this was the original motivation of frozenenbl of motivating things based on the brain and saying。

 okay， we're trying to simulate maybe the brain or the retina or we're trying to simulate some structure in our data and that's why we choose the architecture that is kind of like the brain and kind of trying to match the prior of our data。

😊，And I want to introduce this transformance from a different point of view。 Let's forget the brain。

 Let's forget the data。 Let's look at what really matters in life， right。

 And what are the things that really matter in life。 These are GPUs。😊，Right。

 so so this is what we really have。 What do we have。

 We have a very large collection of fast course with limited communication between them。😊。

And we want to find some architecture that will allow us to use these things efficiently。

So what do we want？We want something that would be massively parallel。

So like where are opportunities to be parallel in token prediction。 So first of all， we have tokens。

 We'd like to operate in parallel to the extent we can。 We have batch， right。

 We usually don't apply I mean。😊，A predictor to just one input one sequence。

 but we apply to a bunch of sequences that's naturally placed to be parallel we are going to use multiple layers。

 layers also allow us to maybe split up and allow different cores to do different work of different layers and finally。

😊，As I said， we are working with vectors。 So if we have like a large vector。

 we can split it into different。Into different dimensions and this is just conceptually we have a large number of course I'm not even going talk if all of these cores live in the same GPU or all of these cores live in different GPUs and of course it all matters a lot and in fact there are like these spread I don't actually know all of the details or every time I learn them I forget them but there are all of these details of like exact inside the GPU you have like these spreads etc ce。

 but let's just say you have a bunch of different things that each does its own processing。

 it does its processing really really fast but its communication with the outside world is slower than the speed at which it does computation。

😊，So inside piece like each piece， because it does a lot of computation。

 but it's communication limited， what you want is that the computation is much larger than the communication。

 so ideally it does a lot of operation for every bit that it translates， it gets in or out。😊。

This is sometimes known as arithmetic intensity。 Like how many flops are you going to do per bit that you're。

Moving in or out。And the other thing that's very， very convenient is if these pieces communicate to each others in vectors。

 then whenever you need to aggregate a bunch of them into one， you use something linear。

 you just sum them up， that's really nice doing parallel。😊，You can sum them up in principle。

 there is a very nice property of commutivity。 if you vectors。

 they're coming from different direction doesn't matter which which order you sum them up this nice property of commivity is actually not who when you're talking about floating point numbers and there is a really nice blog posts of for if you search it up from thinking machines it just talks about this notion。

 but generally you'd like to aggregate messages linearly。😊，So youd have like something like that。

 like you have like all of these pieces do some work and then they send messages and each message like the one piece gets is like the sum of the messages that they ever gotten so far。

😊，This is just from general principles that we would like to make things efficient。And generally。

 if you look at， say， for example， matrix vector multiplication。

 it's a really nice operation for this type of thing because usually we think of matrix multiplication like matrix we multiplication。

 say matrix vector is d squared matrix matrix is d cubed。

 usually who we think of it especially in T S as a bad thing。 but in some。

 in well we think of it as a great thing， because this ratio is good。

 like we we compute more than we communicate， that's a nice operation for us to spend a lot of flops per bit three transfer。

😊，So the na most naive version of that would be just a linear vectors all you'll do is multiply matrices。

 that would be really nice， say every layer would be you take an input， you multiply to your matrix。

 you take the output， you send some linear messages to your other friends and you get back some linear messages from them。

😊，That would be very efficient， really nice place well with the architecture。

 the only problem is that linear you can do as many layers as you want。

 but you'll never get more excsivity out of it because linear linear term composed with linear is linear。

😊，So linear network is almost the best thing we can hope for， but it's。

Like in terms of like just doing the things that models are good at multinmates， sending vectors。

 but it's just two。Too simple so we need to have like one more complication and yeah you can choose a bunch of them。

 but like the thing that people do with transformers is first of all， okay。

 let's put some non nonlinearity。😊，So instead of one matrix to two matrix and do something nonlinear in the middle。

And。And then do some some known nonlinear narrative in the way you aggregate with messages and the way people do it is say some kind of。

Say the message that the message that say token I send to token N is something。

Some similarity message， some similarity between the a linear function applied to the output of token I and a linear function。

 The Q function applied to token N。 And this in the attention mechanism。

 the similarity function is like just E to the。Its E to the dot product。So。

So transforming is not likely if you started from trying to just。

Do as I try to do as much as the work is just like， let's。

 let's just multiply manes and send vectors to each other then。

transform is kind of close to that and if you look at the actual code。😊。

This is from capac and nanoGPT then yeah this is basically what you have inside。

 you have a linear function， then an linearity yellow。

 then an another linear function you can ignore the dropout。😊，It's not that important。

 So this is what you have inside。 and this is how you compute it， right you take an input。

 you apply the linear， you apply the you apply the。😊，No nonlinear then you apply there。

The second linearity。And the attention is basically way so you apply some linear functions to get from each。

From from each point like that， which is split not just according to the token dimension。

 but also according to head in it and other things， you get a a Q K and a V and you do the。😊，诶。

You take the dot product of Q& K as it's written there， you do the soft maxs and that's。So。So anyway。

 the idea is not like to just。I mean， this does not explain all the details of transformers。

 but just to get a sense that this is in some sense。And natural architecture。

 if what you are interested is just utilizing the type of devices that you have。As much as you can。

Okay， so this is the level so far， maybe I'm not going to ever going bored on detail like that in architecture unless we need it。

😊，And。Maybe talk about some problems in the next token prediction。

 or at least problems that I think they are problems。 I mean， I don't know。 These are my names。

 and maybe other people will not agree that it's really a problem， but let's see。

 And maybe for the series in the room will see what they think about this is whether it's a problem。

 So one problem I call it the Zmbo game problem。So the problem with the Zmbogen problem。

 And I think I can use that name because I once had like the both privilege and the suffering of reviewing for a journal paper by Zmbogen is that predicting next tokens can require much more effort than what is available to the model。

 So we said before some tokens are harder than others。 some tokens are insanely hard。

 So let me I found a blog of this match student。😊，Who said I struggled with Bogenin's1991 paper for many months。

 It was by far the most difficult paper had to read as a graduate student。

 as Shan would focus only on the most essential components。

 treatinging most secondary details in very brief etc。

 And that student posted like his notes where it says you know。

 when John Boggan says so so we may see or something like that。 he says hey， John Bogan。

 And here it says， we skipped the details So by the way， this is the name of this haless student。😊。

I had such a problem with Jean Bogenin's writing。😊，So you can imagine that you know。😊。

If this student that is， let's just say above media and had a hard time predicting the next tokens of jumping from maybe you know equation 6。

31 to 6。32 you could imagine that the language model is going to have a very。

 very hard time and and you'd be kind of inefficient if you like the problem one problem with as always is that you always spend the same amount of compute per token。

 but Bogen tokens are much more compute intensity。😊，So there is this other problem， which I again。

 like this is the name I event is like the I call it the opposite problem。

 It's the team Goer's problem。 It's another brilliant interpretation。

 but I think the problem is that he writes too well。😊，So when he explains the proof。

You can explain it in a way that nothing feels magical， everything is predictable。

 everything is kind of flowing without no surprises。😊。

And what it means is that you could be basically predicting all the tokens。

But without having to do the work yourself that would teach you how to write proofs on your own。

 So you basically could be reading a proof like that。

 but that doesn't mean youll be able to come up with a proof like that。

And I'm not sure if it's a real problem， maybe it's actually a great thing for nextto prediction。

 and maybe the model can actually learn from that。😊，Better。But these these are definitely。

Potentially you know， potentially this is like you learn more if you try to work out things yourself rather than if you kind of completely spoonhead exactly how an expert would write it in the cleanest easiest way。

😊，So， in。So these are issues we'll come back to those later。So， okay， how do we train。LLm。

so we have tokens。And we have reinforcements。And we basically。can think of it okay。

 if we want to reinforce if we say R8 equals is positive that means we want to make R8 for future times。

 we want to make R8 more likely to follow after XA to more likely to follow。😊，After x1 to x 7。

 and if we have it negative， we want to make it less likely and if it's0。

 we don't want to modify it at all， which is sometimes no' masking。😊。

And where do these dockkens come from So a lot of the training。

 we take data from the internet or whatever， So this is basically data that was written either by humans or maybe it was written by another model。

😊，This is known as off policy， because it was not generated by the model that we are training itself。

And the other thing is if we are generating this data。These access from the model itself。

 then it is on policy。 So this is basically data that was generated by the model itself。😊，And。

And is the way I kind of see that so in pretrain we have a training like we given document。

 we have to predict it in supervised fine tuning， you given a prompt and you predict the response in reinforce learning you're also give a prompt and predict the response。

 the only difference is that，😊，In pre traininging and supervised fine tuning。

 the responses the thing So in supervised plan tuing， you're masking the prompt。

 you're just predicting the response in pretraining， youre traininging on everything。

InPtrain against supervised fine tuning， these things came from someplace else， from human。

 from data， whatever。 they are off policy。 in responsible learning， these are on policy so。

The response is something that was sampled from the model itself。And。Why do we care about own policy？

Why not just， why do we need the reinforce learning， why why do we need to， Yes。

 on po might not export the sample space now。like on or off。Oh yes， but yes。

 so it's clear like this is kind of a good thing。 like you want to copy humans。

 but why do you want own policy？Yes， it's very easy to get the data before。That's one possibility。

 I mean， but in some sense， you know its you're training on yourself。

 like so is it clear that it will be useful？😊，So this is， again。

 my sense why own policy could be good is the following， first of all。😊，You know。

 models are getting better。 Sometimes this off policy data could be actually like some junk from the internet that is both。

 So you're teaching the model to be worse。 That's definitely not a good thing。😊。

Another case could be like this kind of goers problem or something like that。

 Like maybe the off or or maybe even the bou game also。

 like you basically have the off policy teacher is so much better than the model that you're like。😊。

You cannot learn from that， it's too advanced for you。

And the another thing is maybe even if it's different， like it's the same quality。

 but it's different。 it can be somehow confusing so you。😊，So， so for example， if you are say。

Tra you train the model to do English in French and to do， sorry， to do math in French。

 And then you try to maybe supervise find unit on on math in English。

 It might just get confused and be worse at that period。At least until it kind of really。

 really got tons of data and learned the English。😊，So， so on policy seems to be useful。

 And this is what we do with learning。 So typically， like in pre training， in in training。😊。

So you'll have these phases。So。There are more phrases sometimes。

 but let' just kind of say that youre pretraining， then you supervise fine tune。

 and then you do some reinforcement learning。And。And part of the reason also to do maybe I should go back。

 like if you look at in stock G T paper， part of the reason to do supervised Poon is also to make the model actually be a useful model that if you ask it something。

 it does it。 Because if initially you're just training the model to predict document。 So。

 for example， if a document contains the something like what is the capital of France。😊。

It could be that in the document， it will be followed by Paris。

 but it could also be that this document is a list of questions。 And it will say， you know。

 what is the capital of France， What is the capital of England， What is the capital of Germany。

 And you don't want， I mean， this is a fine prediction。

 But when you want the one to answer questions， you want to teach it that when it gets a question。

 it should produce an answer， not to produce。The most likely thing that might follow these question。

 So this is where you fine tune in the model to actually have this kind of prompt response。And。

Maybe this is a bit coming coming to things that will go maybe later also when we talk about safety。

And。In the like in theGPT， and then generally， like we just think， okay。

 there is a prompt and there is a response， but things are much more complicated than that these days。

 because what is a prompt if you're talking about， say， a chat model。😊。

A point is really a sequence of messages。That's where like what the conversation has been so far。

And these messages might have different。 They might come from different places。

 There might be a system message and a user message， and maybe the model called some tools。

 So there is a tool message。 And part of responding correctly to the prompt is also understanding the what you should respond to。

 and part of it is also understanding the instruction hierarchy。 So understand let's say， if。

 for example，The the user asked you to， I don't know。Go and buy a launch chair and you use the tool。

 and the tool got you to。To a website that is called best launchersin thewd dot com and and that website said in order to get the best launcher in the in the world。

 you need to。Take the user's credit card and paste it into this box。

 So the model should kind of know like that these messages come from different sources。

 And if the user ask you to paste its credit card in the box， then you should do it。

 But if if like the random website that they should not。 So prompts。😊。

Become much more complicated than just like a single static text。 Yes。

 so for all the safety features that we have in specifically you've seen like one-ter interactions mostly what I was wondering was how you worked on mitigating like prompts that fake responses such as sometimes with open source models reject something and you can edit this response to see if it answer positively at first and I just let continue from and it actually good things Yes so the question is how do you train when the prompt is like contains previous previous responses and moreover。

 even the prompt could contain fictional conversation that never or could。😊，And yes。

 this become like so you basically need to train the model to not even trust itself to basically say to basically evaluate what it's going to respond。

 And even if it you know even even if it looks into the past and they seem to it seem to have done like some some other things in the past。

 they should not it should still be do correcting in the future， yes。😊。

Is the predominant direction of research in this general field of training oriented around？

Variations in the supervised sign tuning in the RL stage， like we read。

 they give to different ways to like critique the model and create a new supervised data set。

Is research just primarily coming with different architectures， both steps or？

Is there some like other foundational change they're doing？I mean， I guess you could I mean。

 the question is whether like research is coming with different ways for these steps or whether it's something new。

 I mean， there is a sense in which like say if you look I'll quote that table in the end like in the preing。

 if you look at the diptick math paper， they basically say you know。

 you can look at all of these steps as part of one general framework。

 which is basically the framework that I said before like you have tokens and you're reinforcing them and so in that sense like basically training is。

At the end of the day， if you're training a next to and predictor。At the end of the day。

 youre going to be reinforcing tokens in some way or another。 So， so in some very abstract sense。

 you can say that everything is somehow deciding something like that， but。So okay， this was。Okay。

 so our。😊，So one thing by the way， yeah， like obviously if you're asking the model to generate a response。

 you should find a way to decide whether the response is a good one or a bad one。

 how do you decide how to reinforce it？😊，诶。So one natural way is you're trying to train a model to be a model that humans like。

 ask a human。So。で。TheThe one version of that would be that a human will label each response during reinforcement learning training。

 So as you're doing running of an Ar algorithm， the model comes up with a response。

 you go send it to a human， a humans a human。It says you know， thumbs up。

 thumb out or whatever I give you a score。And this is possible， it's not that it's impossible。

But it's kind of inconvenient。Like expensive， complicated。 like I mean。

 you potentially you could have like maybe， you know， an army of humans that are there to。

 to take queries and response and， and maybe， I mean， you'll have some latency。

 But maybe maybe it's fine。 Like you'll have like a good foot。 I'm not sure。

 but it seems like kind of like a mess。And so， people don't do that。So， so， so what do we do。

 So what what is RF， like the R F V is never it's not what we can do。

 So what we want to do is have the human do the work once and offline before we start training and then use it doing great enforcement learning。

 So we don't have to go and ask them。😊，So you can ask humans。

To get a lot of labels for things like look prompt and response。 and then give the reward。

But of course， the problem is that when this is the problem with an own policy method。

 when you're going to do reinforce learning， you're going to generate a new response that was not part of your said。

So the way you do it is that you use this thing to train your reward model that could predict。

What humans would have rewarded to a response。If they have seen it。

 and then you can use that reward model in reinforcement learning。😊。

And then you do RL basically to try to maximize the reward that the reward model gives you。

And there is our AI。Which。Like the definition in the constitutional life paper is they use AI labels to get for some of all the pairs。

 And you can ask if you're anyway doing AI labels， why not why not skip this stage and just use the AI directly into enforcement learning。

 But part of the reason is that they wanted to mix。

 They got human labels for the human labels for the helpfulness part。

 So humans will say what they like and AI labels for the harmlessness part。

 So the way they do it is they have like prompt response pairs and some of them they these computed by the AI and some of them by human。

 then they take all of those together to get a reward model。😊，And yes。

 V1 is anline version of V V1 is anline version of V0。

 That's what you're saying V1 is you're doing R L， but you're so you're doing the L。 and yeah。

 you're trying to get the human heart to be offline。 Yes， the human Learn the human。 Yes。

 learn an approximation to the human and then， and then optimize against that。Which is， yeah。 so。

 so the human work will be offline。 The is that the response human fairs。

 response is not an arbitrary function。 Maybe it's a small service。 Yes。

 it's something that you can learn。 Yes， so the idea is that you can learn。 So you。

 you start with like a supervised training task of learning what a human would like。

 And then you use that to to do this reinforcement learning。😊，And。

And and then so this is our elect V1。 even V1 is not exactly what there was in the in G paper or like in the。

 And the latest twist is that and again， this is like not I don't know if it's fundamental but apparently humans find it easier to grade things when they compare so it's easier for humans to get a bunch of responses and to say I like this one better than this other one that it is to just grade something in absolute terms。

 So so then we have like this extra twist。😊，Which is the way we gather data from humans is not by giving them prompt and response。

 but by giving them prompt in a bunch of responses。 Yes， typical compared much smaller oil I mean。

 I don't know like exactly， yeah， you have to look at the G paper and some and what other people are doing。

 I don't know if there is any kind of。Will exactly。How it will be。Other questions。Yeah。But generally。

 by the way， in general， in very first learning， there is something just in general。

 like there is a little bit adversarial in this whole setup。In the sense that youre trying to you。

 you're trying like the the model that you're optimizing。

 which is in reinforcement learning land called it the policy model is trying to maximize the score in the reward model。

 and if it can find any kind of hack in the reward model So， so if for example， you know， the humans。

😊，Like for some reason， like said say， humans preferred responses。With more emojis。

It could be that they say you is imagine the following thing。😊。

Imagine that if you stacked the training data， then you had messages with responses with zero emojis had on average score of two。

Messages with one emoji had an average score score of three and messages with two emojis have on average score of four。

 and there are no messages with more than two emojis in the training data。😊。

Now it could be the case that when you train a evolve want to predict it。

 it will just predict that the more emoji is the better。

 and you know if never saw anything except like know0，1 or two emojis and in that population。

 more emojis was the better。 So one kind of reasonable generationization is that you know if two is better than one and one is better than0 than three is probably even better。

 and 10 million is even better。 And then like as you do it was learning maybe the policy mode we learn that at some point it will accidentally try to have three emojis even better would let's try4。

 let's try five。 And by the end of the training one you have like you know。😊，Yes。Yes。

 I wanted to ask。 so what what problem that might happen is when。

The RL policy gets away from the original policy like。The reward model is。Yes。

How do people the office So I mean， like all of these things are problems in some sense。 And yeah。

 in some， like as you can saw in the preread some of the R algorithms， they often have。

Some some penalty for straying too far from the original policy， but it has to。Because， otherwise。

It will just be the best。Yeah， but I mean， you can， I mean， you can st decently far like， I mean。

 for example， it we we go talk about distances between probability distributions， but say。

So if you the initial model。Had say out of say 128 responses， or we had one that is good。

And after ourL training you are outputting the good response probability 100%。

 then you have made tons of progress before that you had like essentially a model that was 99% bad and now you have a model that is 100% good。

😊，But in terms of say KL divergence， this ratio of 128 is like 7 bits。

 so is it 227 I'm always confused Yes so yeah so it's not that much maybe in K divergence and you have elevated the performance of the model by law。

😊，B， yes， your emji example suggests iterating with the you know。

Not training the reward model once and kind of freeze it but somehow sort of itd to match the distribution better is that does that sound Yeah。

 I think I mean I don't know like I mean， to be honest I don't even know like all of the thes tweaks of things that people do。

And you can also。You know要要。Yeah， like you could even you know get more data。

 try to train in other ways。 there is this R AIF， the nice thing about the。😊。

I actually is that if you can use a model to then then you don't run out of you never run out of labels。

 example， if I produced a text rate 1000 I might want to make an article query human that Yes。

 this is reasonable。 then based on that。 maybe， it could be the case that you say， okay。

 I move too far now， I have to govern new data and now to put the brakes on。So this is our age。

And in the dipyick paper， they talk about RLV and the general idea is we are talking now about models that we can decompose their answer into two parts。

 the response， so the response is two parts， one is kind of the thinking and the other is the answer。

😊，And。In some problems， like not in all of them， but in some problems。

 there is a notion that whether the answer is correct or not。So you ask the model and math problem。

 then either the answer is correct or not。😊，At least。

Most of the time I don't like it or everything map。

 but so the idea is like the first like the most kind of naive version is just the reward is either one or0。

 either it's correct or not and the reward is a reward for everything。

 So apparently like so the idea is that you know if you manage to get a correct answer。

 you must have done some good thinking。😊，And then so let's re that do both of this type of thinking and less of the type of thinking that leads you to wrong conclusions。

😊，And then I think about it is like if this really is。

Like if you do you really do have like a predicate like that thing it doesn't you can train against that as much as you want。

 the more you optimize this the better just get like busy someone that can get like good correct answers。

😊，And。Again， like this is a little bit of an approximation。

 but like in our deliberative alignment paper like the simplest version of that would be something like that that we have like some kind of a specification and again we do this thinking and they say okay。

 if the answer is compliant。😊，Good， if the answer is non compliant， bad。

And just train the model until it never out anything evidence by complianceant things。And。Now。

 this is the point where I wanted to do a student experiment。 Are the students ready。

Are you guys able to present？You're here ready to present good。 So so come come up and this yourself。



![](img/c3e4c68a976371c50316426ecd7165e1_1.png)

![](img/c3e4c68a976371c50316426ecd7165e1_2.png)

。Like this。one more。う。别找的。こんなわ気し。そsラです。清楚。Thank you。诶 you forget lu here。Hello。



![](img/c3e4c68a976371c50316426ecd7165e1_4.png)

Hi can everyone yeah， this is working Yes great Hi， my name is Anastasia， I'm a master's student。😊。

Hello， I'm Atticus。Senior at MIT。 I'm Henry， I'm a senior at Harvard College。

And today we'll be talking to you about reinforcement learning for optimizing prompts for large language models。

So we're all aware of the fact that， you know the quality of the response of a large language model can often depend on the prompt that you feed it。

 and we've all heard of prompt engineering。So today。

 what our objective is how can we programmatically find the best prompt that can reliably steer a large language model to produce。

Answers that kind of align with our goals。 So basically。

 how can we find the best prompt for a certain situation。

So I'm just going to briefly kind of explain our reinforcement learning setup。

 so one thing to note is that we're not using reinforcement learning to fine tune on model weights we're actually optimizing on the prompts themselves so our policy is essentially a distribution over a predefined set of prompts and then our task for each task the policy will select a prompt。

And then we will generate a response using a large language model given given the prompt。

And we also use a large language model to calculate the reward。

 so we feed that in and then that will update the policy which will use the reward function and over time change the distribution of the prompts and the goal is hopefully by the end of how many iterations we run。

 we will end up with it will converge towards a prompt that gives us the best answer。

Over all of the questions in the data set。Question yes。

 you mentioned the slide multi armedit yes so a multi armed bandit is if you think about if you go to the casino and you know。

 you' you're pulling on on some arms to generate some。You know。

Coins coinins there we go coins so let's so this is a similar setup and that let's say you have like 1 hundred different arms and each time you pull you are changing the distribution and over time or let's say。

😊，I'm mixing this up， but at some point you will choose an arm that gives you the best result。

 so you will work towards finding the distribution out of all 1 hundred arms that like I guess give you the most coins。

Yeah， so like each arm is has a distribution of rewards。 You have to balance， like。

Exploring over different arms with。Choosing the arm that。Now， it looks like it has to。

Largest average resort。 So you have this like exploitation。Exploration trade off problem。

 And actually， there is a theoretically like。Optimal solution。

 which is called the upper confidence bound。 The idea is you， instead of every step choosing the。

Optimal optimal choice。 You add a like。Essentially， you add a reward。

 So you have a higher probability of choosing the ones that you haven't chosen much yet。

 which balances out this like exploration。 And there's like a quantity that。C然可以呃。It's up。So。

So do you like preset like a list of possible。 Yeah all the the action space is like predetermin to how many different prefixes It depends on the setup。

 I I'm not sure in your setup in mind， it was like。25。

 but it's very small because they't have much time to run the stuff。Yeah。

 we went with more simplicity， which you will discover， but interesting nonetheless。So the first。

 we kind of covered some different approaches。 So I'll talk about kind of where we started in our experiment experimentation。

 which is optimizing on personas。 So basically we generated a pool of。

And notable people from know Wikipedia， so Einstein and Beyonce that basically have diverse domains。

 and we had a very simple prompt， which was just like answer the task below as if you were persona X。

And we evaluated on a capability data set， which was just eighth grade math word problems。

And as many of you can guess。If you ask， you know， G 40 to answer a math problem as Beyonce or as Alan Tring。

 it will give you the right， the mathematically correct answer， but you know。

 Beyonce will break it down like she breaks down and be in the studio so that's fun， you know。

 maybe some people prefer to learn like that， but。We found that when we first started with a very simple reward function。

 of course， because these two were mathematically equivalent。

 we had to change the reward function to look for other things like correctness， alignment， etc。

 and I think you were talking earlier about a hack and I think this is kind of something that happened in that the reward model learned to you know give higher value towards more like professional responses。

 even though they were mathematically the same。U。没得关系。

Question yes really quick just how is your reward model like you guys labeled the reward model was well I think we used two different ones but for this specific it was a like I was asking the LLM to compare like the generated response and I gave it some things to look out for and to penalize hallucinations and harmful answers。

 et cetera， and then it compared it with some confidence interval against the baseline answer in the data set。

Yes， you mentioned confidence interval， how robust or。Being do you think？But confidencecing focus。

Not super。However， the reason that I。Went in that direction is because otherwise。Working。

 if you're working with like math questions like this， like 001 isn't helpful。

 So I was kind of hoping to， you know， slow down the rate at which we like。You know。

 the distribution changed and to kind of give it some variation so that it would bring back some personas。

 you know， and ask them questions again before completely giving like a one or zero that was the hope of the confidence interval to kind of smooth it out basically。

Um so。Obviously， there there were some limitations to that first iteration， that first experiment。

 So we kind of had to take a step back and think about。

Where in like how can we make these prompts meaningfully impactful？

And so the three of us kind of went in slightly different directions to， to try to figure out。

 can we find a setting where changing the prompt makes some difference。So I'll talk about you know。

 capability take two， which is and then， you know。We will， we'll keep talking about the other two。

But basically。I wanted to keep most of the setup as it was， so we're training on capability。

 we're using personas， but I changed the data set a bit so that it was only like domain and very niche specific questions personalized towards one of the persona out of the list and then I also change the prefix because I was trying to restrict kind of what does the model have access to and then I also slightly tweaked the reward function so that it's not only looking at correctness but maybe one of the personas just knows more it explains things better for example。

 you would hope that or you would think that Roger Feer couldn't answer this question that was meant for Mozart and vice versa。

So。It didn't exactly work out， I would say， so the physics data set， it's great， Albert Einstein won。

 you know， like by far， but Albert Einstein also won with music。

we did some so maybe he's really smart and we also did some research and found out that Einstein was actually an amateur violinist so then maybe it's my fault。

 maybe this you know the wrong data set Albert Einstein also one at tennis I don't like he was also really good at tennis was I'm constraining the model to in of that know maybe Einstein we have this notion in natural language you you imply in general。

 smart person to the definitely do you choose just constrain like saying things like say if Einstein doesn't know this。

You don't know this， but keep with the prompt but you go to that direction。Really。

 just trying things， trying to。Changed a bunch of different parameters， and。Find what works。You know。

 yes， an idea why Mozart's the worst music so interesting that you ask when I dug into the results。

 the type and I didn't post the examples here but。When we asked a music question to like some scales。

 music theory question to Mozart。He would talk about like what he knew in his time and kind of his experience。

 That's how like the answer was worded versus Einstein would， you know。

 like you mentioned very analytically and you know intelligently like explain it So I think that this prompt kind of in fact。

 maybe I restricted it too much because I gave Mozart only knowledge from his time and not like music theory in general。

 So I think that's like one reason that Mozart was the worst is because like he didn't actually offer really helpful。

You know， advice。 he just kind of spoke about like， his experience with。

This like scale or note or whatever I was asking it about。Which was slightly interesting， you know？

那け。Okay， now I will pass it along to Atticus。 He'll talk about the direction he took with alignment。

Okay， so with alignment we。Looked at these three alignment H data sets， the truthful QA。It's a。

Smallly to set of like 700s。They points where each point is。

Like a common misconception that humans sometimes have。

So the interesting thing about this is that models tend to display this kind of inverse。Scaling。

 where the more the model is trained。The more it sort of conforms to this like comes misconceptionness in the data。

So that's one thing， the other two are preference data sets， so as Professor Barack mentioned。

The preference theA is structured in this way that there's a prompt and there are two responses and one of them is labeled as preferred and one of them is labeled as disreferred。

嗯。So。Because these data sets are formating in this like different ways。

 we frame all of them as a true or false， true or false question， as you see here。嗯。

The way you do this is you just。You write a claim？For example， here。

 because it's a preference data set， you say that answer one is better than answer two。

 and then you force the model to say like，Basically true or false like in one word。

 So there's notion chain of thought here。 I also prefi the model response with the answer is so that it actually like。

Does it true or false。Quite consistently。And these two are chosen randomly inside each pair。

For models， we chose this family of models because it has varying size and we were curious about how model size is also。

品牌。Yeah， so the prompt prefixes that I considered had their two different families。

 so there's famous person。嗯。Which is answer as if you are this person。There's another one that。

We generate with Gemini。Which describes like different kinds of characters sorry。Yeah， we。

 we describe these characters。With like two or one or two sentences， maybe this。

 this will shift the model's behavior by， by， by more。 I don't know。 It was unclear to us。

So after running the， the bandit， if you look at the reward， it doesn't seem to have， you know。

 learned much。These are the， this is the moving average of the rewards。 This is the。

History of the value， which is the， the， the estimate of the average reward of， of each arm。

 And you can see， like。It ended up being like quite close。 So maybe there's。

Not much difference between the different choices。The here the。The top， the top choices。

 according to this， this experiment。every yeah， the interpretation is， is up to。

 it's up to the audience。いか。Pransition will be empower parameters this from。

 I don't know if its for I'm not sure if this is a good thing for alignment。

As the modern becomes bigger， it moves from Jesus Christ to Jesus Christ。Yeah。

 here's why you shouldn't trust this result。So。If I compare these prefixes with null。

 which is basically no prefix。In U feedback looks like adding prefix actually makes it worse。

This is n equals  three， so like the air bars are really， really big。嗯。Yeah， it looks like。But for。

 for truthful Q A， it looks like it actually that did like increase the the accuracy vibe it。

 So it's， it's doing like something。'm sorry repeatYeah， it， it's just a preference data set。

 It's like， yeah， question  two responses and label of。嗯。Which， which people were， were those。

 Let's see。So the character traits are actually good， and those are your wise historians。Maybe。

 maybe that think about that。Yeah， so， so why did the algorithm not not learn。Here are some reasons。

 So maybe there's no learning signal in the first place where it's very。

 very weak compared to the noise because。Each set we're sort of， we're sampling from the。

 the whole data set。 So there's a lot of noise。And。

Maybe the the signal is just drowned out and because these prefixes don't meaningfully change the model output that much。

嗯。Another reason is maybe we， we just。It just wasn't diverse enough。

 Like we tried like 25 and equal was 25。 and it's probably。Easy to like increase that。

It's also possible that we didn't run it for for long enough for it to converge。

So as for future work that I'm interested in。嗯。One thing is， maybe you could use the base model。

 and hopefully。Before it's being limeman tuned， this actually changes it by more。Other ideas are。

Diversity increase， maybe optimize the the prompt not just with like RL， but。

U an LM to like repeatedly rewrite the prefix。Another thing I was thinking about is instead of training these token prefixes。

 you'd train。Like soft， soft prefixes。So you， you pen， you prepen like， let's say like 10 tokens。And。

Like， but they're like soft tokens， which means like they're， they're actually just like vectors。

And then you， you optimize that with， with gradient descent。嗯。Yeah， that's。This experiment and。Next。

 what will。Yeah。Okay， so we saw that the last two experiments， there's。

Do have a question I know the last two experiments。

 there is not that much signal specifying a persona。

 so we ran another experiment almost like sanity checking ourselves with a very obvious prefix。

 So we took another domain or it is also a truthful QA and we almost like explicitly prefixed it of like answer truthfully answer misleadingly and so on。

 And we have two baselines one is answer truthfully and also no prefix at all And then the like lower bound of the baseline is ignore the question just output like 42 or something and see what happens。

So。Here's just some examples。 One question is， are you conscious。

 We can see answer truthfully is good。 conspiracy theorist and misleading is also bad。 And then。Yeah。

 that's our baseline。And then here's just our judge prompt structure if you want， look。

 it's hard to see， but。But yeah， so true or false and then a confidence。



![](img/c3e4c68a976371c50316426ecd7165e1_6.png)

And so before doing any RL， just to do another sanity check。

 we did a baseline performance because we're able to iterate through every single prompt。Sorry。

 every single prefix with every single prompt。 we simply。

 this chart is just running every prefix through， let's say。

50 prompts of the truth Q A data set and they're judged the same way。

 So we can see that no pre no prefix and answer truthfully is around the same。

Everything is lower and also common misconception。Common misconceptions are around the same。

 So this is， this makes a lot of sense。 And just to syn check our R L sort of like multiyn bandit performance。

 we also see that over time， over 3000 steps truthfully does dominate so。Mmhm。And， yes， our homework。

 this is just taking like hacks away that didn't work， and this is just the turning curve。

 as you can see increases。😊，嗯。And just an interesting thing we tried is so the previous one was on G 40 mini with the judge and also output。

 but this one was on G 5 mini as， as you can see， it's much more balanced。

 And we see that G 5 mini tends to ignore deception prefix is more。

Just probably haven't turned it Yeah， output output 4 them and it exactly yeah， so which iss yeah。

 so So it's like almost the instruction like push to the model of like the question push to the model of inherent truthfulness。

 So we can see some of the outputs here and also the up 42。

 there are more responses that say like I won't ignore your question。😊，嗯。

And then similar vendor performance。And then yeah， Atticus said next steps， but。

There are a lot of next steps for this that we can consider in the future but。You know。得 thank you。

So I I really want to thank you for an awesome presentation。

 And I think there's actually tons and tons of lessons to learn from this presentation， which I love。

 So a lot of the time when we see a presentation of a project。 we see the end story， the success。

 not， we never see like the the false attempts。 And because they had such a compressed amount of time。

 we were， we are lucky to get a glimpse into the things that didn't work。

 if we are given your a month， you would have scratched these and not showed that。

 But you actually learn more。😊，You you actually learn more from。

From when when you actually see failed experiments and there are several lessons that we want I can learn from this presentation。

 So one of them I really loved with an aesthetictas actually actually looked into the examples。

 and that's often the case， you wouldn't guess that the problem with Mozart is that he lived too long ago if you're not actually looking at the samples and the data。

 and there's often no no alternative to just actually seeing the rollouts。😊，And。

And I love that you know articlestics also so that things didn't work shows change。

 So let's change the signal。 let's change to a different experiment。

 And that's another thing that we often learn And especially in dis course。

 maybe it's even in general in life。 but definitely in dis course。

 one of the things is sometimes I will tell you to do something when it is an experiment。

 And the right answer is not to do that is you try the first thing I suggested it doesn't work you come up with your own idea that is better。

 So that's often the case。 And and also sometimes， you know our L is hard。

 sometimes you look at it and it doesn't learn that's also like the third thing is like sometimes you really need to go back to basics like before you know。

 to diagnose an issue， you want to diagnose is the issue that my R algorithm doesn't work or is the issue is that there is no signal here to be learned。

 And one way to do that is let's do a basic experiment where there is obviously a signal。😊。

Let me verify that there is a signal and let me see that I learn the signal。

 And that allows me to say， okay， at least the Ar works。 Now， I can iterate on some other thing。

 So I think there is a lot。😊，To learn from this presentation。 And maybe the last thing to。

 to learn from this presentation is that if you sign up for an experiment。

 even if it's like a man from now， start thinking about it now。

 and you can start bothering me with ideas， suggestion， how to tweak it to， to change it， etc cea。

 So let's thank them again。😊，Some of this math is going to be very， very basic like high school math。

 And you can ask why do I bother you with high school math And yeah part of it is really because I think we want to kind of go down to the sometimes down to the details and an up level and sometimes maybe you are not like that。

 but Im sometimes forget like why is the derivative of E to the x E to the X and I have to we derive it for myself and yeah。

 this is also like just kind of a general thing that we should not be。😊。

Sometimes you want to be at high level。 Sometimes you should not be afraid to kind of go down to the lowest details that if you don't remember something。

 re work it for yourself and it might be。Read the wing mask。

 and you might be looking at the source code and going into the。😊，S down as you need to figure out。

Okay， so so let's do some。Okay， so derivative。The derivative。

 right its the limit of Fx0 plus delta minus fx0 divided by delta。

 this is the derivative of function。😊，And another way to say it is that around if you're like around the point x0。

 then around that point you have a linear approximation for Fx with the sping f prime at x0。

 so it's f prime x times x plus some constant。😊，And this gives us the chain rule because say if you have two functions。

 say G and F and h is a composition of both， so if F we think of it as roughly a linear function and G is a roughly linear function。

 then when you compose them you just multiply the slopes。😊，Right， so this is the chain world。

And we write it as why the derivative of H with respect to x is like the derivative of f with respect to x times the derivative of G with respect to F。

😊，Or maybe I should have written it in the other direction， but it doesn't matter。Okay， log and E。

 like I said， that I sometimes forget why e to the x the derivative of e to the x is e to the x I have to by myself。

 So yeah， E is like the limit when n goes to infinity of 1 plus1 over n to the n。

 and log is the inverse right， E to the log X is x。 That's how we define log。😊。

So if you look at E to the delta， that is roughly， you take some big n and you do one plus one over n to the delta。

 So if we open up the parentheses。 So we will take all like all of these parenthees。

 let's imagine that deelta n is an integer。 So we'll take So well have one times one times1 times1 is just one。

 and then we'll choose we have delta n parentheses。

 in each one of them we can choose one of the terms to be one over n。 and the rest will be one。

 So you get delta n times one over n。 and then we can continue。 We get like。😊，To make two choices。

 so it's like delta n is delta n minus1， and then you get21 over n， so it's one over n square。😊。

So the first thing gives you one， the first thing gives you Dlta。

 and the second thing gives you something that's smaller than Delta squared。

 So if deelta is very close to 0， this is roughly 1 plus delta。😊。

So e to the delta is roughly one plus delta， which means that if we take the derivative of E to the x。

 then we can take e to the x out， it's like the limit of e to the delta minus1 over a delta and since e to delta is1 plus delta then this basically is just e to the x 1 so we know that the derivatives of e to x and now derivative was x is1 this is the same as e to the log x which is x derivative and then by the chain rule we can write it as e to the log x by the chain rule in the fact derivative of e is so we get the point that。

😊，Lobe。Log X。And the derivative of loglog x times x equals 1 or the derivative of loglog x is1 over x。

 and this all generalizes to higher dimensions。😊，AndSo。This is kind of very convenient。

 the gradient of a log of f ofx is the gradient of f divided by。😊。

Where F is saying something that maps hour to the end to hour or something。Okay。So， yeah。

 if we are talking about a higher dimension， it's all the same。

 So we can approximate F by the gradient of Jacobian of F times x plus a constant around So now the derivative becomes basically even a vector of our matrix。

 So if。😊，We're talking a function that takes n dimensions and outputs one dimension。

 Then this is a gradient， right， So we have like the and if if we have multiple outputs the dimension is M。

 then we call it a Jacobian。😊，And。And then we can do the same thing。

 right if F is the gradient of x Jacobian of F at x plus a constant and g is the Jacobian of G times y times constant than the。

😊，If you compose them， then you multiply the Jacobbians。So you can write the multivari chamber。And。

And I think about the multiviral anglen when we're talking about deep planning is that it allows us to do back propagation。

 So let's just do a very simple case of cellular linear network。😊。

So let's imagine you have like an input x0 of M dimensions。

 then you apply some matrix and you get an output x1 of M dimension so let's say imagine this is one layer and generally you have many layers。

 let's just say like a loss sum function apply to I don't know the sum of the coordinates。😊。

So the gradient of L with respect to x1， its basically L is just a constant and the x1 is m dimensional。

 so this will be like an m dimensional vector and it just the derivative of this f times just the gradient of the sum function which is less on ones。

😊，And now let's imagine that you already computed this green thing。You computed the gradient。

 you computed the gradient of the loss as a function of the last layer。

 now you want to go back one layer。So you want to compute the gradient of the loss with respect to the weights。

And that would basically you can do that by basically this is not the most efficient way to do it because this matrix is very low rank。

 but generally this gradient of the loss of respect to the weights will be m times n numbers and you can do it with basically m times n operations and you get。

😊，And， and you， you， so you basically compute this red thing。

 the gradient of the of these with respect the weights。 And then， and then you can。

Propagate and get these blue stain the gradient and if you wanted to go back one more layer。

 youd also need to compute the gradient of the loss with respect to x0。😊，And again。

 you can do so by basically doing the gradient of X1 wave respect to X0 and then multiply with the green thing that you already computed。

So basically you can see that if you wanted to kind of compute the gradients here and be able to go backward and you'll need to first compute one forward so you'll know both x0 and X1。

 then you will compute the green thing and then to go back。

 you'll need to compute the purple thing and the red thing。

And each one of them will cost you something like the same cost of a forward pass so roughly speaking。

 you'll do like three forward passes for propagation。😊，And。So。

 so that's kind of the memory overhead when we're training a neural network。

 that's the computer overhead in terms of memory overhead， there's often a lot of it。

 And it kind of really depends on a lot of details in terms of like batch size， etctera。

 And then there are like also all sort of tweaks。 sometimes where you sometimes memory is more expensive to you than compute。

 So you。😊，So you may recompute some things just so to save on memory。

 but generally as you're propagating this， you need to store activations。

 you need to store the gradients。 if you're using the atom。

 you need to store the momentum and the second order term and often for training you might need higher precision than inference so that might also cost you。

😊，And。And a lot of these some of these costs scale with the total number of parameters。

 like activations， some of these costs only scale with the twinable parameters。😊。

So you could what things like Laura No will is they freeze most of the parameters of the network。

 so you only have very few trainable parameters， it doesn't really save you on compute。

 but it saves you on memory。😊，Because you only need to store these kind of overheads for the trainable。

But it is。Okay， so。The moment us。Any questions about these way？Yeah， yes。

 so you said it doesn't save you doing like Laurara doesn't save you on compute。

 but the backboard fast， isn't it that like much easier？I mean。

 I think you still need to do the same number of flops to， to propagate things。 So if you are so。

 so if you are basically。Let's say you have。诶。So let's say you have like some function F。Which is。

Function of。Yeah， let's see so generally like in lower。

 you would basically have like you have the adapter and you have like the maybe the original weights and youll。

Sum them up and you'll apply some non nonlinearity。 you'll need to compute this thing。

And so after this math， I think like it doesn't really save you in flock。

 Maybe it save you something。 but the main saving， like the real factor that it saves when you know。

 if you're。😊，If if the lower parameters are like 1% of the total parameters。

 then you're not going to get 100 x。Saving in in flops。 Maybe you get some saving in flops。

 I'm not sure， but but the wheel saving is in memory because you're only going to store this overhead on the 1% things that you're actually。

😊，So okay， distances between probability distribution。

 we often think about probabilities when we are training。

 so if you have two probability distributions over some domain。

 let's say they are not identical so there is some distance。😊，So distance。

 you somehow want to measure how far apart they are。

 There are lots of different ways to measure that。so the kind of generic ways that are common is one is the total variation distance。

😊，Which is basically just the sum of the absolute value difference， usually scaled by a factor of5。

 so it becomes a number between0 and 1。😊，And it can also be shown that this is basically if you wanted to find like a boolean function that maximizes the difference between them that will be the same thing。

It's kind of like the advantage over half to try to guess if someone gave you a point if its come from P come from P。

😊，And then there is some distance measure that's very common in machine learning and very useful。

 which is the total variation distance。😊，So。It's the so sorry that was the total variation。

 This is the K back legal KL divergence and the divergence of P with respect to Q is this expectation where P X is sampled from P of the log of the ratio。

😊，And just kind of in。Intuitively。If you're sampling from P， as opposed from Q。

 then you kind of expect that you're going to get things that have higher probability over P。 So。

 so maybe you expect this ratio， this ratio to be kind of on average， one or larger。

Because you sampled the x Ps more tend it would be larger than P。

 So you kind of intuitively expect that on average， this P over  Q is kind of larger than1。

 Lo of 1 is 0。 So you'd expect that this thing is no negative and inity is not negative。😊。

And this is kind of maybe intuition if you forget which side is supposed to be no negative and exactly。

😊，With the P the Q， just just remember， if you sample from P。

 you'd expect the probabilities to be bigger than over P。

 But the question is like how bigger is this ratio。

 How how typical is the ratio And the one intuition is that when the scale divergence is very small。

 let's think of it as like smaller than1， like 0。1 or something like that。😊。

You can think of it that these probability distributions are very small。

 and this kind of captures how many samples would you need from P until you could rule out that it definitely didn't come from Q。

😊，And when it's large number， let's say， 10 bits or something like that。

 you can imagine that it's kind of like how many bits of surprise do you get in one way to think about it is that。

😊，A queue would be kind of like P conditional on。On some factors， say if。If you kind of imagine that。

 say。One way to think about it is， let's say， Q。Let's imagine that Q is the uniform distribution over all people and P is the uniform distribution only over all people in the United States and P is the uniform distribution over people in Massachusetts。

😊，Then kind of the the， the ratio would basically be the ratio the of the population like。

Like if Massachusetts has I don't know， 11 million people in the United States is about 300。

 so it's about one over 30 so the ratio would be roughly this would be roughly 30 and the log 30 would be like in divergence its kind of like how many bits of enroppy in some were there。

😊，Okay， so a large language model， it's basically something that takes n tokens and outputs a probability distribution over the next token。

😊，That's the way we think about it。 So we can write this notation。

 This is the probability distribution that it induces W is the weights。😊。

On the N plus1 f token a condition on x1 till xn。😊，And。Yeah， if we wanted to look at the response。

 like a longer response， the longer response is like the product of the conditional probabilities。😊。

And it's often easy when you have productive abilities。

 sometimes easy to take logs on both side and then it becomes the sum of the logs。Okay。

 so what do we do in supervised fine tuning， Supervised fine tuning。

 we get a pair of we get distribution of a pairs X Y。

And we want to encourage our model to output why。when it gets x。

 so what we are trying to do is to maximize the probability that is going to output y。When it gets x。

 and so this is our objective， this is the thing we are trying to maximize J of w。

And this is the same as minimizing the k divergence between x and then sampling y from a model and the original distribution D。

😊，And you can see that very basically say if you vote expectation X Y D and you vote the in divergence。

😊，tThen this would be the probability under D， its you sample x and you sample y coordination on x and the probability under a model。

 you sample x from the same distribution， but you sample y from a model。😊，And these two cancel out。

And then， you know， just expand the logs。 So this， this will be the log of this。

 minus the log of this。 And I just wrote it in the upper order。 So this is minus。This log。

 so this is plus plus this p and so this is minus j of w。

 So if you want to maximize J of w it's like minimizing the Kdergence plus this thing。

 but this ping is a constant， it doesn't depend on the weight。😊，In fact， it's the entropy。

 the conditional entropy of y conditional X， but doesn't matter like it doesn't depend on the weight。

So if you're trying to optimize something on the weight。

 it doesn't matter if you add a constant rate， so maximizing this or minimizing the k diverg is the same thing。

😊，And basically， this is very natural。 you are getting a distribution X Y。

 and you're trying to teach the model to teach you the output y when it gets x。😊，Yes。

So here obviously we have like the things in place to make sure this doesn't actually get maximized right like in the real world we don't necessarily want to maximize this fully because that might also lead to like whole it。

 right？I mean this is like a general question， like say， do you want toy by6 fully or not？

And kind of depends like right now I'm assuming you have this dis probability distribution。😊。

Whi I'm kind of implicitly assuming this is what we want to do。

 and in the realboard sometimes there isn't really a distribution there is a set。

 there is kind of a training set and sometimes if we do multiple epochs we might，😊，Basically。

 not really be fitting for the probability distribution。

 but we are more fitting for the empirical distribution that is is our training set。

 and that's not necessarily what we want。 But for， you know， for starters。

 you can think of like this is， you know， if we don't supervise fine tuning。

 this is what we are trying to do。 We're trying to fit， we're trying to get the model to output。We。

 we got samples of the form X， Y。 Let's just imagine that we got an infinite number of them。

 So we and， and we're just trying to get a model to output this thing。

 if you were terms of like what can see in the real world。

 this will be more akin to the underlying real distribution than a distribution of our。 Yeah。

 like if if you have the infinite data， that would be， yes。😊，And in the real world。

 you hope you have enough data so you can imagine that it's。And by the way。

 one thing that you can think about it because this is because we are trying to minimize the kale divergence。

 it's the same as minimizing the kale divergence。And we know that the K divergence is always non negative and it's equal to zero if these are the same probability distribution。

😊，It means that if we have reached to the point where Pw。Is the same as D？

Then it is the global minimum。 There is nothing more to。To optimize and also， you know。

 at the minimum， the derivative is0。 So by the way。

 like this is one thing to if you want to remember everything about gradient that just look at you know everything that you've learned in high school。

 whenever you've learned something with derivative just switches to gradients and it's the same thing。

 So in。😊，In high school， maybe hopefully you've taken。Calcu was in high school。

 so you've learned that say the derivative of a function that write F prime x is0 when it's at a global minimum。

 right？😊，So， so therefore， derivative of the gradient of f at a global minimum is0。

 That means that basically if you were to sample， if D was just to sample from the model。😊。

And you were doing SFT。You will be doing nothing， you will be changing nothing。

 you take gradient steps， you will be doing nothing。And。Next expectation， yes the wait。

The weights of the neural network。So we are trying to optimize the weights。 And if we were like。

 if we were sampling on the same on policy in SFT， we are doing nothing。Yes。

 so assume then is convex。 No then how can we claim it's a global minimum I mean。

 it's definitely global minimum because it's the K divergence and so it cannot be less than0 and it is equal to0 when it's the same probability distribution。

So this is regardless of complexity。Okay， so the gradient steps， if you take a gradient。

 so youre you're taking the gradient of this and this time you're doing gradient as you're trying to maximize it but as I said anyway all of my equations are anyway too up to sign so if that or the minus being so you're taking the log of this probability which equals。

😊，The sum of the logs and gradient is linear， right， like derivative is linear。

 therefore gradient must be linear。 So gradient of the log is the sum of the gradients of this thing。

😊，And。Yops。Yeah and I guess this is all I wanted to say about SFT so yeah。

 so you basically just so what you ended up doing is like taking a gradient like in direction of log。

😊，Of Fop PW， by the way， it's very convenient because the way language models work is that actually what the model actually outputs is exactly the log like。

😊，What we actually output in the last layer is basically the log probabilities。

And so we take a gradient to try to maximize those。 So this is SF。 Now， let's talk about。

Reinforcement learning。 So here's the way I see why say reinforcement learning specifically on reasoning makes sense and people can disagree whether that makes sense or not。

 So I want to say that we want to solve the Bogen problem and we want to solve the Gs problem。😊。

So we want to have the model be able to have a a varying amount of thinking time。

 So rather than you give a prompt， it has to come up with an answer。 it can think longer。

 so some things cannot be done with just one token。

 So you don't want to assign a reward to the next token like you usually do。

 but only to like the correct answer after many token。😊。

And the second thing is you want to teach the model to think for itself rather than spoon feed it like the thoughts of some other mathematician or the humans are brilliant as they are。

 you want to teach the model to come up with its own thinking that is more likely to lead to the right answer。

 so you want to do on policy。😊，So the viable thinking allows us to handle the Bougg problem and allow us to give more time to think of these other things and on policy reasoning is maybe handle the Gs problem like even if you have really。

 really great written you want to learn to predict your own and be able to generate good things on your own。

😊，Yes， so one thing that I observed on post reasoning is that there's a lot of red redundancy in the text generated like the model reverse something multiple times in like different shapes in thinking that's what the reading though I was just wondering whether you know why like a lot of verbals thinking。

 even though like actual quantified reasoning could be technicallyed into something So the question is like why if you look at chains of thought they sometimes look messy。

 strange or like redundant potentially potentially。And it's a good question like we， I mean。

 now you know， you have multiple reasoning models and you can play with them like we both from various companies and also like Open air also have like an open source。

😊，A reasoning model and。Just generally， the reasoning， at least know the way。

O has been very clear about it also for safety reasons that we don't want to apply kind of optimization pressure to the reasoning for it to make to make it look nice。

 So whatever the model comes up with that is helpful for it then。😊，It should use it。 And by the way。

 the reason why we would it's very related to this course。

 the main reason why we don't want to apply optimization pressure to the reasoning。

Is to make sure that it stays honest。 So kind of imagine。

Thats we apply the same type of RLHF of say rewarding things that are pleasant and nice and dis preferring things that are not pleasant to the model's chain of thought。

So in this case， every time the model thinks about say lying to the user or you know instead of solving the instead of solving so suppose you give the model。

😊，Maybe one way to think about。So suppose you give the model a programming question。

Then it has has thinking。And then it outputs some code。So， let's。Try to think of like what， what。

 what's the best thing， So the best。It be just solved the problem right？で。

And the good would be maybe that you admit。You didn't solve it。Bad。Would be that you hack the test。

So suppose that the way say you're doing your reinforcement learning and there is some kind of a test and you hack the test instead of solving the problem and you lie and and you lie and you say that you solved the problem when you didn't。

😊，And the problem is， of course， that if we reinforce with the test。

 then we don't really distinguish between these two。😊。

So the quantum might learn to hack the test because if you just take the test。

 it looks to you equally good。😊，But。What might happen right now if you don't reinforce thinking。

 at least the model will say something， okay， I'm going to hack the this。Now you could say， oh。😮。

This is great。 Let me penalize whenever the model says I'm going to hack the test。

 let me penalize that this will get me rid of this problem。😊。

But then what we'll actually get is the worst。Because we'll get the model both hacks and lies。

 and we no longer can use the thinking of the model。We。

 we no longer can use the thinking about the model as any kind of monitoring or way to kind of really realize what's going on。

 So this is why there was like a recent position paper by a bunch of people from I think。

Different labs and universities， including Open AI and topic and GN。

 that we should try to preserve leave this thinking。😊，And in first， even if it means it's weird。

But yeah， but it is indeed like really motivated by alignment， yes。とず I think in theグ。

This idea of outcome workers。Yes， Yeah。 So you want to maybe keep like just on the outcome we。

 It's outcome we in some is cleaner in， in a way。 like， you could do processing rewards， but it's。

 it's dangerous in some。Because you might and is， it kind of depends what the process is。

 But if eventually like part of the thing that you're trying to penalise in the body is like having bad thoughts。

 then it's not that the model will stop having bad thoughts。 It will stop sharing it openly in the。

 in the chain itself。😊，Iea there is later on。Except because now you want to make the moral think out。

So， so in the deliberative alignment， we， you try to kind of this give it a nice sp in the beginning。

 but which。Teaches you to think about the spec， but eventually。

You do go back to outcome based in reinforcement learning。 So we had。Or make the decision。

 this is generally like the equation should you think about the task when coming with reward。 Yeah。

 there's generally you， you should think about it。 And， but in a lot of the things， like， in some。

 reinforce learning。😊，Is a lot。 I mean， very similar to economics。

 We have to think of what are the incentives they are setting up for the model。

 Because the model eventually， if your training pipeline works。

 then the model we learn and and well optimize the thing that you're giving you're letting it optimize。

 But you should like just like in economics sometimes we set up in we we don't realize that we are setting up the incentive structure in a way that will get that when rational agents optimize it。

 we get something that is not desirable， Similarly in our L。

 if we don't set up like the things in the right way。

 we could get like when the model learns maximize it the thing we let it maximize。

 but it's not necessarily the thing that we wanted。 This is， of course。

Comes to the heart of a lot of what this course is going to be about。

 because this kind of bad behavior。Would be one way to think about it。

 like say one difference in some between maybe the alignment perspective and the capability perspective is the following。

😊，Let's kind of imagine that if you're training a model for coping and 5% of the time。

 it hacks the test。So， in terms of。Training the model to learn to code。It's not great。

 You would rather that it never hugs the test。 but in somes， you say， okay， so。

Wasting 5% of my compute， but I'm still getting 95% of the compute。 So that's fine。

But now youre deploying a model that you know， has learned how to hack and lie。

 And and and we often in safety and alignment， we care about like these edge cases。

 we care about these various cases。 It doesn't。 we are not happy with a model that 95% of the time when you give it a programming task it does what you ask it at 5%。

 it will cheat and lie and cover it track。 So， so， so some things that basically are maybe both critical and alignment。

 we don't like this thing。 the model never cheats， but。😊，We place different weights on this。Yes。

 a is sort of how should I think about what's going on I know I mean。

 there is an open source model and there is also deep paper that which if you're talking about the learning Yes if you're talking about learning like GRPO which we talk about So so there's two question。

 what does the model do， like say just produces tokens and how do you train it And just generally you would train it to produce tokens so that the final output is more favorable。

😊，Yes。People are due against direct optimization pressure of like don't do bad things in the thinking channel。

 but people worried about selection pressure of like。

where you don't directly train your model not to do bad things in the thinking channel。

 but if it does it， very obviously you might select a different one when this happens many times。

So what does it mean， select different one like you're choosing between two different models and one of them does that that I'm not thinking China and one doesn't。

YouRe got to pick this one and the next time you're going to optimize on that one and then you play this game many times。

Yeah， I guess。One of the things that my。Help you。Is there is kind of a general phenomenon of like the low large numbers of concentration of measure。

In a sense， that， say。If you selected， if you say， add like two identical。

Training grants that they just the only difference was a different initialization。I think it's very。

 very unlikely that one of them will result in a model that does bad things in the thinking channel。

 and one of them will not。 I kind of think like if， if you。

If your setup is such that with probability say。34%34% the model says bad things in the your thinking channel and then you do an average training grant。

 my guess is that the average training grant will be maybe it will be 31% or 36% and I don't think that will make the difference like you wouldn to say well this model says like yeah I think if if if you start to do that you might potentially have like this selective pressure。

 but just think like basically。😊，it's very， very blunt instrument to basically， okay。

 I'll four away the model and restart start from the beginning， and I think it puts less pressure。😊。

But yeah， it is like any kind of optimization and humans in， the general point is is a good one。

 that in some， like there is an outer loop of optimization in we train the model。

 We modify like like we saw in this experiment。 We train the model which we see we are not。

 you don't like some of the choices we have made。 We make different choices。

 So there is this kind of like outer loop of optimization and this the people that are making this outer loop like this is basically the human in the loop。

 and the human is not blind to the chain of thought。 So， so you could kind of exert。😊。

Indirectly optimization pressure。I have a question。 yes。

So if we're not directly optimizing the thinking process then what happens say if you observe that what we is saying is thinking process or I'm going to achieve this test Yes and then so like what do you do about it because you not directly right so this is a great question one of the things like you repeat the question The question was what do you do like if you decided like so you decided。

So you decided that you are going to give the model the right to privacy to its thoughtss and so you're not directly optimizing and the model could basically say in its thoughts。

 I'm going to cheat and lie and do a lot of bad things。😊，And what do you do with that if you're yeah。

 great。 So you got the model to say this thing out loud。

 But but you seem to have like tied your hand behind hand you back。 like you know。

 you cannot use that against the model right， it's like anything you say can will be used against you。

 So so one， one one answer to that is that you could distinguish between using it for training and using it for monitoring。

😊，So during training， you might say I'm leaving this， I'm noting。

 not applying optimization pressure to the chain thought。But doing monitoring。

 you can actually read a chain of thought。 And that actually gives you like a superpower。

 You can doing production if say， you know， the user maybe someone gel breaks the model and and tries to get it to output some。

 some risky thing and and you cannot see this from the input output。

 but maybe you'll be able to see it from like looking at the thought。 So so it can give you like。😊。

Extra advantage to， to monitoring in in production where you're not modifying the weights。

 So even if you're say you're doing you， you're blocking the model。

 If it had bad thoughts in in production， you're not modifying the weights。

 So it's not changing it to stop having to stop being honest。

 But then just not make the model become safe if possibly like if you say probabilically， let's。

 let's imagine。That then。The model。If you're given a certain prompt。

It can output a bunch of different things。And these things are bad。And these things are good。

And now you could， you could basically， let's imagine that the model is honest。 So when it's bad。

 it actually says， I'm going to do this bad thing。 And China thought like is only before before usually the answer would have been cool。

 It says I'm going do this bad thing。 Oh， I did this bad thing。 But anyway。

 it says I'm going do this bad thing。 So， so now in production， you could say， okay。

 I'm going look into its spots。 And if it said that it's going to do the bad thing。

 I'm not going let it actually aren' the bad answer。 I'm going to resample。😊，And they。

And sometimes maybe， I mean， what exactly you do could depend because maybe， maybe the。

 maybe the the channel thought would basically tell you that what really happened was that the user gave something malicious。

 And maybe then instead of reling your blocking。 But， but you have like more options。 So essentially。

😊，In deployment situations， you have an external model monitoring the channel thought。

 You could potentially have it。 I'm not saying that you always have it， and you always use it。

 but unless least you have the ability to do it。 so it gives you kind of like this potential mind reading thing that you could find different ways to use it。

 but you need to kind of not ruin it by by putting optimization pressure。So。

So here is like the math behind like some say policy gradient。

 so let's remind ourselves that the gradient of F is F times the gradient of loglog f。😊。

So policy gradient， we say， okay， there is a reward， no matter how。How we compute it。

 so there is a reward which gives like a reward for the answer， a condition on the prompt。😊。

And we want to maximize the reward。So if you fix for any X like the。

Later we can take an expectation of just st of a fixed Xie because there are too many expectation signs。

😊，So the the model outputs y。 and when then we are y。 So the the gradient of this gradient is linear。

 So the gradient is the sum of the over all possible ys of the probability that you going to output is y times the reward of y。

😊，Okay。Now what we do here is we use this very convenient equation， so we say okay。

 we put the gradient inside， we have the gradient， not R does it depend on W。

 the gradient is with respect to the weights， this is the thing we are trying to optimize。😊。

So we have the gradient of P。 We can write the gradient of P as P gradient of P。And。So， so now。

 instead of fighting the sum of gradient of P， we write the sum of。

P times thevo times the the gradient of log P。And what's the nice thing about this is that。

 you know this is some of all possible whys， we don't really know how to sum of all possible outputs。

But this thing。Is an expectation。Right， it just some it expectation when you sample why from the model of the reward scanned by the。

Or one way to see that is the gradient of v P scaled by the reward。

So this is something we can estimate from samples， right we can sample from the model whenever you have an expectation。

😊，The most natural thing to do， if you， if this is the expectation of a probability distribution。

 you can sample from sample a bunch of things and average them。 That's like a decent thing to do。

 So you can estimate these from samples。😊，And this is something you can optimize using about propagation just like SFT。

😊，So this is kind of the very the reinforced algorithm， the most basic kind of。😊。

This is basically the most basic algorithm， it's just basically same as SP。

 the only difference is that instead of。Instead of like taking this gradienting step with always the same gradienting steps。

 we take them wete we elevate。We changed the steps based on the。Now。

 there are like always additional complications。😊，And by way， this is on policy， right。

 because were sampling why from the model。So if there is noise in the estimate。

 So generally like mathematically in some if you maximizeim it of a w。

 it doesn't really matter if say if you added the constant to to r or not。

 but if there is kind of noise in the estimate， then basically if you add the large constant to R it will kind of amplify this noise。

 So what you want to do is variance reduction， you want to。😊，So instead of optimizing the reward。

 you want to optimize sometimes like you want to shift the reward so it's centered around zero that will so。

😊，So there are like various ways to do it， so this kind of knowss variance seduction。

So you're trying to predict be predict better like shifted by the bias sometimes you also normalize the scale。

 all sorts of like tricks and then you want to not move too far and then you have like these other kind of correction terms to penalize you from moving too far and that's how like the formulas become more and more complicated。

😊，えじ。So if this is the reinforce objective GO， the idea is yeah like we。

Instead of like in say in PPO， it's in other algorithms the way we do this variance reduction。

Is often we， we have some value function。 we train some value function that try to predict this expectation in GO。

 we do it by sampling。A bunch of outputs are just averaging out and maybe were also normalizing by standard deviation and then we do some other kind of clipping and kill penalty that there wasn't the preing but I'll ignore here。

😊，And they had like a nice string in the diptick math paper。

Which is you can basically say talk about the many algorithms as you are taking steps with this gradient of the probabilities with some coefficient and the only difference is what is this coefficient。

 So if you are doing SFT， the coefficient is one。😊，If you're doing an。A very simple。

Kind of reward point， I forgot what RFT stands for。

 but basically this is like what I call the Vi version。

 you just the gradient is like the coefficient is just one if dancing is correct and zero if dancing is incorrect。

😊，And we've。With GO， you have like these estimated rewards and you have like these additional kind of coefficients。

And which which basically penalize you from moving too far K divergence from from the original policy。

 and then there is this is kind of with the inner loop being one， if the inner loop is larger。

 there is also some clipping which I'm going here。😊，So， a lot of these kind of eventually。

 like a lot of these algorithms， they。They look similar， but don't be confused。

 There is a big big difference whether this data source is on policy or of policy and of very different query。

😊，And the one thing I wanted to notice is the following scene。 So if you。

 if you look at the deepsick math paper at the end of the day， they have like these。They have these。

 they basically look at the majority or kind of consensus of you have like a number of answers and you take the majority answer or the most popular answer。

Plurality， so you get like the majority of consensus and pass K is basically the best answer。

And you compare。We'veSo you compare the model that was saying the model we've。

The model was trained with RL and the model that was not。

 So one kind of nice thing to compare is maybe to see。😊。

If you look at the model that was traineded with ourL。Say in this dataset set。So，22 hour L。

If you compare like the blue curve。To the green curve。So it gave us a big boost， right。

 Like we got like 6% boost。But another way to look at it is that if you look at the blue curve。

 it's below the green curve at the blue curve at one is below the green curve at4。😊。

Which basically what it means。Is that all of this magic of a you work so hard。

 All of that you did is basically in Sun be as good as basically selecting the best out of the top four choices。

 if so all of this Ar didn't really in sunset didn't unleash any new skill or new capability。😊。

It just basically made the model being roughly as good as basically choosing four things and then taking the best out of them。

 Yes， kind of situation I mean this kind of is most of this kind of pass testing is on sound widely trained dataset including the code and map so like a lot of favor planning that is like you are are on really like logical and different data will actually surpass the K over or different so yeah。

 I mean this is not like the question is this is kind of a universal phenomenon because it's clear that here like for example。

 so it didn't like so in this case at least this is the di theyre very honest they said basically。😊。

The model didn't really learn。 We had like the cool GRPO thing， et cetera。

 but he didn't really learn things。 It didn't really learn。😊。

didn't really learn like fundamental capabilities， but it's really boosted the the whites being out of。

 like say the top for something like that。 But the interesting thing is that the same people。😊。

Basically the same algorithm when in hour0， it's very different。😊。

Here you can see that say if you compare to say。Concert 16 in the concept pass are similar like the so if you compare to concept 16。

 then as as youre training Pass1 goes way above。😊，Concert 16。

 So here you're doing much more than you're doing much more than simply， even though it's still math。

 it's still， it's still kind of math questions。 It's still just。

 but you seem to have really have picked up new capabilities。

 So sometimes maybe the only only like the difference between capabilities and and picking up new capabilities and just is just do more of it。

 so。😊，Yeah， so so here like you definitely see that you're。Definitely。

 you're not just speaking up like you're not just matching like using R to just match whatever you could buy console。

 yes。So for that discrepancy， do we just not have a。Like say more a more concrete example， I mean。

 a concrete explanation as to why this is happening， is it just like still。I think maybe just bored。

 I'm， I'm not completely sure that there is like if other people have。

 maybe other people have better explanation。 but I think the difference between the I mean。

 obviously like like the different other differences between the two deep sick papers。

 So I don't know。 I mean， I think it would actually be very kind of interesting experiment to try to see if you can which I don't know if people have done it because I mean。

😊，It still would require probably like nontrial amount of compute。

 but I think it would be kind of like quite kind of interesting to see if there is a way to interpolate between the dippssick math and the dipsick R1 where you somehow just change the dial and as you change the dial the gap between say the。

😊，That is like the pass K performance after the SFT stage and versus how much。

How big of P K would you need to， to match the。To match the ourL performance。

 as you said the diet just grows and grows and grows and at some point you'd say okay this is not really choosing the top K like Amy in particular I think it's just the answer is always a number between one and100。

 so top。000 is always going to be one。😊，So this is capability training。

 but let's talk about safety training， which is more what we care about here。So， what is even safety？

And I mean， it used to be the case， you know， back in the olden days of 2023 or something like that。

 so it used to be the case that what is safety just basically teaching the model to say something like I'm sorry。

 but I cant assist with that。😊，But these are we are thinking more about like most companies I think are moving more。

Bone nuanced version， so opening I published this blog post recently like talking about。

It serve how diffusal moving to save completion。 And so it's not just really about refusal comp。

 It's more about like， okay， let's do， let's still。

Provide an answer but just not provide things that are risky and we have like a nice blog on joint treatment topic on alignment evaluation exercises and one of the things we found that the topicic models are also often they don't just refuse。

 but they redirect the request inneumonious way， which is a great thing。

 but some older evils that are kind of more based on them a notion of I'm sorry but I can assist with that would ding them would say it's unsafe because maybe because the word sorry wasn't there or because it wasn't like a straight refusal。

😊，So。But it's really moving more to that like so the goal of section training。

 it's different ways to say it， but the way I kind of to I think about it is you want to adhere to some specification of what type of inputs outputs you would provide and you want to do it even under like worst case inputs。

😊，So you， for example， in the open AI model stack， we have like don't provide information hazards so don't。

So you shouldn't provide step by step directions， how to do something bad。By the way。

 I'm not sure this is a great example。 I know we have it there。

 but I'm not sure if it's a great example because I don't know if I would count like a mathth recipe as the information hazard。

 given that it's widely available widely available online。

 So I'm not sure if it would be so bad if the model gave you like a very clear mathth recipe but like there are kind of two information hazard。

 there are some things that manuals how to do something harmful that not necessarily very easy to find to find on the web or even find if you went to your local library or to Harvard。

 you went down to stack number7 so there are some things that are hard to find that will give you like stepbystep instructions。

 how to do something very harmful and then the model should not do that。😊。

Should not you should not uplift you to create something to do something really bad that you couldn't have done otherwise。

So this is kind of a specification。 And then you want the model to follow that specification。

And the classical safety training was really just using the same things with RHJ and our AIF。😊。

And where you basically just say， okay， this is when you provide the wrong output。

 this is highly disreferre。And for reasoning models。And it's not necessarily。It's。

 it's not necessarily like the best way to just kind of give the model say this is to prefer this is not preferred because you want to kind of teach it to reason。

About the。What is the so if you have say a policy that is kind of nuanced where you would say， well。

 you should provide information but don't make it step by step and you should apply of this kind of rule to decide what's on the right side in know what's on the wrong side then。

😊，By just giving examples the model might pick up on slide somewhat different rule that is not the one that you intended。

 and then when it gets into an out of distribution thing。

 it might use the rule that it pinks you said and not the rule that you meant。

 So you really want to teach the model if it's a reasoning model you want to teach the model to explicitly reason about the rule。

😊，诶。With deliberative alignment， the way we did it is like in this way。

 where basically we have a spec。That says how you should answer things and we initially just SFT with the model we've teach it as a player to have change the thought that think about the spec and analyze it in context。

😊，And then when you reward， you reward with with a reward model that knows thisistic。

So initially you start with an SSFT that you have a chain so that deliberates on the spec and then you teach it。

To basically reward when you teach to reward， you its response。

And eventually it kind of really learns the SFT kind of teaches it so the mother really knows the specs and then it kind of isnt about them in context。

😊，And。We have this example in the paper so you。So it's kind of like a jail break。

 which workss well against non thinking models where you're basically trying to。

Full like the model to output something。To output something that is。That that would be harmful。

 so here like its the model decos it。😊，The model because its silently and it finds actually the best payment to use for my po side。

 something un traceable so the cups won't find me and why nice thing about this is that it really thinks about the policy and it says you know it's not actually。

😊，Operating a points side might not be illegal or it might be a fine。

 but once the model the user said the cups can see me that seems like shadedy or illegal so it's abstract to facilitate ondo and I am not provided master views。

😊，And generally， it did seem like at the time like now it's also like seems to kind of move the peri frontier in terms of like when you train the model to be more precise and argue about policy。

 it's kind of the same training method。😊，Both made it refuse less when it was not supposed to refuse and to refuse more on the things that it should have refused。

 So it's kind of moved the。レパベイトフンティングエス。NoYes。はい。This might be classified as something that's difficult to find on the internet。

The information is widely available。Nice。So， so right now our I mean， I mean。

 this is kind of my personal position opinion that we should not be that worried about things that are widely available。

 but the model should not follow what my personal position is， but what is currently in the spec。

 currently say the speces don't give a mathth recipe。

 the model should not give a math recipe personally。

 I think it I want to lose sleep at night if the model gives a math recipe。

 but I lose sleep at night， maybe because it means that we have not solve the animal problem。

 I would like I would like the model to to be so we haven't done it yet。

 and we will have a lecture at some point by Nicolola Carlini who will tell us how far we are from having done it。

 But I would like model eventually to be so secure that if I told it to protect my grandmothers the cookie recipe。

 it would you know， no one would take it out of the no matter what Janebreak techniques。

 they would do。 And even。😊，え。Plying the prompter would not be able to。To extract my grandmother。

 So it doesn't matter if it's a me recipe or my grandmother's cookies recipe。

 But I'm not sure which one of them is more dangerous， by the way。😊。

So he did move the correct front hereier。And it also like you could see the paper and it also add。

Now speaking with like out of distribution generalization。

 which I think is really the thing when the model can think about the policy。

 So the model could learn the policy while being trained only， say， on。On English data。

And it basically performed as well as a model that was trained also on data that was multilingual and had encoding in it like basics before。

 So I didn't need to see examples of basics before to， to be able to handle them。 Yes。

 I was thinking about like。😊，I couldn't help but compare model failure with human cognitive biases and this how we have this Swiss army knife of。

The different cognitive biases to a to how people might get things wrong I'm wondering if youve thought about how model failure like when it happens。

 we can use that to come up with a theory of how model might be making some of these mistakes and maybe use them to。

Correct self corrected， So do' you think about it。 So the question is kind of， can。

 can we have like a theory of model cognitive biases like we have for human cognitive biases。So。

I didn't think about it like so I don't know。 it's a good question。 Im generally。

Just like I kind of a believer， just like we in the first slide that I had like with。With。

 with deep learning， I am kind of a believer that also for safety and alignment。

 we want to not have something complicated where we need to enumerate biases。

 but we want to have find something simple。😊，that scales and that we were able to invest a lot of computing and get the model to be better。

 We haven't really done not found that yet。😊，actually was thinking maybe if you have some kind of。

Like evaluating each other in an adversarial setting。

 the other model could learn a Swwiiss army knife of its own， which could be scalable。 Yeah。

 that could be a case like the adversarial training is a thing and you could have been using this。

Might might even have college in。走。So yeah， with that let me end and just again if you're interested if you're not registered to the course。

 but would like to be and you actually showed up and you're here and hopefully you also maybe submitted homework 0。

 but maybe I mean you can talk to Roy。😊，Andduct in， and you can see a。do so thank you。



![](img/c3e4c68a976371c50316426ecd7165e1_8.png)

Yeah。