# 【苏黎世联邦理工学院】信息检索-｜-Information-Retrieval-｜-Eth-Zurich-2025-p28-P28_11._语言模型_(1_3)--BV1ndsBzdEss_p28-

So now we are going to move on to another part。 That's actually the last one。

 After all this we are done。 So I'm going to start today。 and then I finish next week。

It's called language models。So now it's a few years ago， when you say language model。

 it wasn't a buzzword。 So， you know， just a section like any other。 And now， of course。

 when you say language model， everybody thinks of LLMs and chat GT and you know。

 all of these models that are very popular today。 So I will contrast it， I will。

 I will explain also the differences。 So why， why， what is the difference between a large language model and a language model in the classical sense。

It's very important to know， you know， this is kind of the history， right。

 So before the large language models， how did the language models appear。

 So I'm going to give you all that was done around these language models。

In such a way that then for those of you who are interested。

 you can go to the LLM courses and then learn the the larger language models with the history in mind of what has been done before。

And again， with the idea that a large language model， if you think of it， is just a search engine。

 It's just a better search engine that actually can understand the semantics of the language via the embedding in the。

 in the vector space。嗯。All right， so。I'm going to start right away with a cool toy。

That you might know from。Theoretical computer science， Who has ever seen this thing。

It see a lot of nodding。 So， yes， you've seen these things。嗯。

So it's known as a finite state automaton。And it's used in the context of languages。

 which shouldn't be surprising because we are talking about language models， right？嗯。😊。

But with language here， we don't mean just English or German or human spoken language。

 We just mean language in the theoretical computer science meaning， right。

 So in the language in the computer science meaning is just a set of strings。Right， so the string。

 the set the set of world string has something that's called the monoed structure。

 monowe just means that you can concatetnate two strings。

 You have the empty string when you concatetnate it。 it doesn't change anything。

 So that's called and it' associative。 and that's called the monoweed structure。

 And so when you have defined this， the set of world strings。

 Then you can define a subset of the of the set of world string。

 and such a subset is called a language。And when you have a language。

The first thing you want to do as an interesting problem in computer science is you want to identify the strings that belong to that language or not。

 So if I give you a string， you want a way to tell me， yes that string is in the language or no。

 that string is not in the language。It has direct applications because， in fact。

 when you write a Python program or you have an X M L file or Json file and you try to pass it in a editor。

 you're doing exactly that。 right， The computer is looking at your text file， which is a string。

 And it's trying to tell you， yes or no， is it accepted or not， right， Does it pass。

 Does it not pass。 If it doesn't pass， You go， you're going to get some errors， If it passes。

 Then you get the syntax highlighting。 Sudden， everything is enhanced with colorss and so on。嗯。

And so these automats， you might remember， they are here to recognize the strings that belong to certain languages。

 some languages， not all of them， but there are certain languages that can be recognized with that kind of things。

嗯。Which， if I'm correct， is called a regular language。 That was so long ago for me。

 So the way it works is that we have these nodes that are connecting in this way with the edges and the edges have labels that are called transitions。

 And what you have on the labels， these are the letters of your language。 A B， in that case。

 So this is your alphabet。 And then a word is just a sequence， a finite sequence of such letters。😊。

And so the interpretation of that graph is that whenever you have an edge going from one node to another node and with a specific label。

 it's a transition from a state to another state， depending on the letter that you see。 for example。

 if you look at the transition table on the right。 If you are in state number one and you see an a or you consume an A。

 then you go to state number 5 and that you see with your row that goes from one to5 labeled with a And B would lead you to state 2。

 which you see with the edge from one to2 with B， Alright， I it all good， you've seen that， right。

 So this is just to refresh a little bit。😊，And so the way it works is that you just have your string that you want to test and you just put yourself at the start。

 it's like a video game and you start right here。 and then you。

 you consume one by one the letters and you follow the transition table to go where it tellss you to go B A A A A。

 And now I have this little rectangle in here。 It's just where I accept right if I end up in here。

 then it means that I'm going to accept the word as part of the language。

 which is what's happening right here。 In fact， it's going to accept it with any number of further letters a。

Okay。😊，You know， regular expressions， right。Who would be， what。

 what would be the regular expressions or the language that this accepts。Yes。😊，B A， A， A star， Yes。

 or B， A A plus， which is equivalent， right， So B A A， A star， absolutely。

So this is also connected to regular expressions。Of course， there's many more languages。

 You also have more powerful ways like context free grammars that are even more powerful than that。

 and then gets even more and more complicated， complicated。 And， of course， the human languages。

 These are the toughest right to， to get。 This is where the LL Ms actually were super useful。😊。

This one gets rejected B A B A goes to the sink。 This is called the sink， right。

 it's just the trash can， whatever follows you， you're just there and that's over。Alright。😊。

So formally， you do that with a bunch of letters and the Dlta for the transition。

 It's a function and a big sigma for the alphabet F for the state of finite states and so， right。

 But I'm not going to annoy you。 There are sufficient notation elsewhere。

 So I'm gonna stick to the drawings for that。 Speaking of notations。

 That's actually the one we are going to use。So， again， a language is a set of strings。

 So I'm going to call my set of string deep in in curved in a curved letter。

 It's the it's a set of documents， right， a string I can call it a document， right。

 A document that I have on the Internet is technically a string， right， And I can ask myself。

 do I accept it or not。The letters here， B， A A and so on。 If I map it to information retrievalal。

 these are， in fact， the wordss。So the worlds that belong to documents。

Corresds in the regular language terminology to letters in strings。Right， so it requires a bit of a。

 of a jump， cognitive jump that you really need to consider the terms。

 the worlds as letters as in in， in terms of the， the regular language。

So I have documents that are sequences of wealths。And so what I'm going to have。

For my language model is a probability distribution。More precisely。

 my documents are random variables that shouldn't be new， right。

 We've been doing that for two weeks that we had random variables that are documents。And so。

 I associate every document。That can be a value of my random variable。To a number。

 And if I sum the probability over all documents， I get what。 And I prefer this notation。

 It's the same， right， You can use this， the one or the other notation。

 and I use that notation more for the probabilistic retrieval。All right。

 so if I sum over all documents smallly， then the probabilities sum up to one。So again。

 I have a language plus a probability distribution over that language。 Is that here for everybody。

Right。All right。And so， again， if it helps， whenever you see these formulas with the probabilities of documents and one thing of the little levelss。

 right， the elementary events， sepilions of them and every one of them is associated with the document。

 query or everything。We need。Now， the first cool thing that we can do with this is that we can。😊，呃。

Reurpose。This finite state automaton as a generator。 It's like gene AI， right with the with chat GT。

 Not only can you identify or understanding， you can also generate stuff。

 So I'm not going to call this GP T because it's no I like it。 But， in fact。

 we can use that in order to generate documents。 Imagine that A And B， which are later here。

 this would be wells like information， which we roll T and so。

 So how can we turn that into a generator when I can add some probabilities。😊。

For the state transition， if I add a probability， and then I just toss a coin every time I toss a coin。

 maybe B， maybe a with probability one half every time or I use a dice， if you prefer。 And then so。

 for example， here， I do a probability of one half， I get B with the probability of one half。

 I get a with the probability of one half， I get a。

 And then And so here the probability that I generate this number。

Ignoring whether I accept it or not is one over 64， right， So it's1 half for B，1 half for a。

1 half for a，1 half for a， and then one4， that's the probability of stopping every time， Right。

 So it， it's independent， right， So when you arrive there。You decide， do I stop， do I not stop。

 And if you don't stop， then you， you toss your coin for A or B， right， And then you check again。

 Do you stop， Do you not stop， then you tos the coin again， right。

 So here we get a probability of one over 64。 Then， of course。

 if you consider only the words you accept， you need to renormalize with the the probability of the。

 of the language the the entire language set。W with me。Right， it's quite simple。 Really。

 I just inverts this and I just use it to， to generate instead of consuming the other world。

 So now it's pretty cool， right， that we can start generating documents in this way。😊，Now。

 if I do a little bit of math。We are， in fact， in known territory。Because if you think of it。

 a string is a sequence of letters。 And since I said here。

 a string is a document and a letter is a word。A document is a sequence of wealths。

We've already seen documents as sequences of wealths。 That is the list of wealth model， right？

 We can have sets of wes， bags of wes， list of wes。

 So when we are looking at as documents in this way as sequences of wealth。

 we are looking at the list of wealths model。Right。嗯。Alright， and in this semester。

 we've emphasized more sets of world for Boolean retrieval， bags of worlds for vector space model。

 sets of worlds for probabilities。 But now we are going to go into the list of worlds model。

 which is pretty cool。 We've already also seen the list of world for phrase search， right。

 when you have the the by world in this season。 So on phrase search。

 that's also a list of worlds model。😊，But anyway， I have a documents。

 So the appcaseD is a random variable that takes its values into this set of documents。

 which again is a monoo8 T star。 And then I can have another random variable that is its length。

 right？ It's just a function of the document。 If I have a document。 I can take its length。

 And you probably agree that that gives me a random variable， which is the length of the documents。

 which also has a probability distribution over all the length。 So I'm going to call it LD， right。

 the the， the， the。😊，The document length， I could have just called it L， right， It would have matter。

 but I just put it LD for making clear that it's the length of some documents。And so， now。

What we are going to do is that。We take documents。 We take one document。

 and we can use that document in order to generate other documents。 And now we， again。

 it's not something like GPT， right。And the way we do that， if you think of that， how can we get。

 a generator like this， So this finite say totalmaton。



![](img/1b0ef725221d98a1fab6eb5751f0d171_1.png)

If you come back to here， what we need is the weights。 we need to， to have some structure。

 and we need to know the weights every time the weights that I'm going to to be associating to the letters。

Now， how can we get these weights。 So you probably start having the intuitions by looking at the documents。

 right， if， if there are wells that appear a lot in the documents。

 then there will be a high probability。 that will have a high probability of being generated。

 And if you have wells that are a bit rarer in in the document that you're looking at。

 the probability that they get generated is lower， right？ That makes sense， right。

We're going to have a high probability of generating the f generating the frequent wells。

And so that's exactly what we are going to be doing。 We take a document。

 We analyze it statistically and build out of that document， some generator of wealths。

And so the generator of words， what you have to imagine is that。

It always comes down to a probability distribution of other documents。

 Once you have a generator of documents that gives you the probability distribution is the probability that this specific generator will generate that specific documents。

So now， if we take a list of world model。And we use， don， don't be scared。 I'll explain。 And in fact。

 you will see it's pretty easy。 I'm going to use the chain rule。

Remember that the chain rule gives me the probability of some。Conjunction of events， ABCD and so on。

 So the probability of ABCD is the probability of A times the probability of B knowing A times the probability of C knowing A And B times the probability of D knowing A。

 B and C， right， That is my chain rule。Everybody with me？Right， so that's the chain world。

 So now I'm doing exactly this。 I'm going to look at the probability of generating documents。

 D 1 D2 D3。D1， D2 D3 can be anything， right， These are just lower case。

 So these are mathematical variables。

![](img/1b0ef725221d98a1fab6eb5751f0d171_3.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_4.png)

So here I could put information retrieval system， right， So D1 is information。 D2 is retrieval。

 D3 is system。

![](img/1b0ef725221d98a1fab6eb5751f0d171_6.png)

Word of warninging， the subscript here， that's not the same as in the previous week。

 The subscript here is just a position， position 1 position 2 position 3 in my list of wells。

 That's not like in the probabilitybabil seek information retrieval where we had a vector。

 So just just re， remember that。 Not the same notation。



![](img/1b0ef725221d98a1fab6eb5751f0d171_8.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_9.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_10.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_11.png)

So。The first world， the second world and the third world。 And now I'm asking the question。

 what is the probability that this generator that I built is going to generate exactly that document。

 The probability that I'm generating。 So D is equal to exactly that specifically， and it stops here。



![](img/1b0ef725221d98a1fab6eb5751f0d171_13.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_14.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_15.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_16.png)

So when I look at that document， I'm just going to decompose it into multiple things。

 How do I obtain that documents。

![](img/1b0ef725221d98a1fab6eb5751f0d171_18.png)

First， do you agree that the first thing that should happen to generate that document。

 it has a length of  three。Is that I have to generate at least one world， right。

 Because if I don't generate anything， I'm not getting that document。 So my first event that。

 and I will have a conjunction of them。Is that the length of the document。

 this random variable must be at least one。But that's not enough， right， because although way。

 I would generate any document that has a length of at least one。

 So the second thing that I must have。Is that my first word。MB D1 information， for example。

Conditions。On the length of at least one， because that's the chain rule， right。

 probability of A B is the probability of A times the probability of B knowing A。

 So these first two here， probability of L D greater than one times the probability of。



![](img/1b0ef725221d98a1fab6eb5751f0d171_20.png)

D ones equals D ones information。 If you multiply these two。

 this gives you the probability of the conjunction。 This is the probability of this and this。



![](img/1b0ef725221d98a1fab6eb5751f0d171_22.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_23.png)

Weho agrees with that。It's the channel， right。 So at that point， when I'm here。

 I have the probability of having a document of length at least one and of having information。

 D1 as my first world。 But that's not enough right， because right now， I'm， I'm only are only here。

 What should happen next to get this document here。 What should happen next is that。



![](img/1b0ef725221d98a1fab6eb5751f0d171_25.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_26.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_27.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_28.png)

There's one more wealth。

![](img/1b0ef725221d98a1fab6eb5751f0d171_30.png)

So now I'm going to throw in one more condition if that the length be at must be at least two。



![](img/1b0ef725221d98a1fab6eb5751f0d171_32.png)

Conditioned on the fact that it was already at least one。 and the first world was D web。 That's。

 again， my Che rule。

![](img/1b0ef725221d98a1fab6eb5751f0d171_34.png)

So now if I take the conjunction of all of that， it's this and this and this， right。

 So it's the probability that the length is at least one and the first one is the1。

 and it's at least2。 And not then， of course， I can， if， if you realize that this implies that。

 then you can drop that。 So at that point， when I'm done with the first three factors up to here。

 I have the probability， that the length is at least2。 and the first world is the1。😊。



![](img/1b0ef725221d98a1fab6eb5751f0d171_36.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_37.png)

What happens next。

![](img/1b0ef725221d98a1fab6eb5751f0d171_39.png)

The next world is D2。So now I multiply with the probability that the next world is D2 conditioned on what came previously condition on the fact that the length with at least2 and the1 is the1。

 That's again， the chain rule。 At that point， I have a length of at least2 and D 1 D2。



![](img/1b0ef725221d98a1fab6eb5751f0d171_41.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_42.png)

And then I continue。 The next thing that must happen is that the length is at this three condition of everything that came before。



![](img/1b0ef725221d98a1fab6eb5751f0d171_44.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_45.png)

Then knowing it last3。The third world must be D3。

![](img/1b0ef725221d98a1fab6eb5751f0d171_47.png)

Conditions on all of that。And it must stop。

![](img/1b0ef725221d98a1fab6eb5751f0d171_49.png)

Now， my stopping condition is that the probability is equal to three conditions on previous because of the chain rule。



![](img/1b0ef725221d98a1fab6eb5751f0d171_51.png)

Who gets that formula。

![](img/1b0ef725221d98a1fab6eb5751f0d171_53.png)

Right， so in other world。If I look at the probability of obtaining exactly that document as the conjunction of length at least one first document is d well length。

 at least2 second world， sorry in no document， second world is D to length at least3。

 third world is D3， length exactly3， the conjunction of all of that， that is equivalent to that。

 and I'm right writing it as the chain。

![](img/1b0ef725221d98a1fab6eb5751f0d171_55.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_56.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_57.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_58.png)

That's what I'm doing here。Just a chamber。

![](img/1b0ef725221d98a1fab6eb5751f0d171_60.png)

No。If I look closer， there are similarities in there。

 Look at all these probabilities when I have the probability。That the length is at least n plus one。

 given that it was N， right， I'm adding one world。And look at the probability of the length being exactly N。

 knowing that it was at least n。 If you think of it。

 that's the probability of stopping versus the probability of continuing。Right。

 and so here we can give them some constants and we can decide that these are constants。

 So I have P stop。 P stop is the probability of stopping。 It's just a number，1 half1 f， whatever。

 And we just say， okay， that last probability here is P stop。 And the other one is one minus P stop。

 It's just the probability of stopping or continuing， right。😊，Generally， that must not be。

 It doesn't need to be a consent rate that could depend or it could vary and so。

 But we are just in our model for the purpose of our model。

 We are going to assume that there is a P stop such that this is P stop and one minus P stop， okay。

And there is a second。 So the first assumption， P stop 1 minus P stop。

And I'm going to make a second assumption。Which cheese。

Can be argued is a limitation of these older languages。

We are going to assume that we don't have unlimited memory because I wrote that chain rule with just three documents。

 right D1 D2 d3， but it can go on and on and on and on and on with millions of letters right you can have huge documents and so if you write that chain rule you're going to have the probability of generating the millions words。

 given each one of the 999999 other world， that is a huge list that is a lot of memory that you need to build the system like that。

And that was a few decades ago， right， we didn't have so much computing power and so on。

So we introduce the simplifying assumptions， which is called the the Macov fool。We assume that。

 in fact， we only remember the a window of wealth。The last， what did I call it， The last n Wells。

 we remember。 So it means that the probability of the next world being the what it is。

 depending on everything is the same as the its probability， knowing only the previous n wells。

Right so we have a memory， a limited memory。 We only look at the previous n wes。

 and that is some parameter of the system。 and we look at the special case of not having any memory at all we see it's called the Uniigram model which behaves a bit differently from the ones that do have a memory where you have one。

2，3 or more wes before。 right So look at that formula The only thing it's setting us is we forget everything that's too long ago in the past。

 right The probability detail of the next one only depends on the previous n termss。😊。

That is a big difference with the large language models like charge GPT。

 because in large language models， you have a much better reach when you look at a world。

 it reaches much farther in terms of connections to the other world。

 It even goes to the future in charge GPT when that's the attention mechanism here。

 we only go to the past。 We link a world to whatway before。 but in LLMs， you go both sides。

 you have this attention mechanism that connects the world in its context to everything that's happening around。

So now it looks a bit primitive， right compared to LL Ms。 But this is historically the， the。

 the first way that we that we， that we analyzed and and generated some language。

 So we look at the previous n terms。And so now if I do that， let me have a window。

 a memory of two worlds。 I only remember the previous two worlds。

 If I want the probability of generating exactly document D1， D，2， D3， D4。😊。

Poordiban is unexpectedly working。 for example， four well。 Then you get that it's my chain rule。

 exactly the chain rule。 But now I put this1 minus piece up。 So probability of D 1， D2，3，3。

 D4 is the probability I don't stop times the probability of getting D1。Times the probability。

 I still don't stop。 Time the probability of getting the2， given that I had the1。

Times I still don't stop。 Time the probability。 I get D3 condition on D1 and D2。Times。

 I still don't stop。 And now the probability I get D 4 based on D 2 and D 3， not D1， limited memory。

 I only have the memory of the previous two world， and then P stop。 Who agrees with that formula。

Right， it's just a chain rule using the assumptions。 Ptop and 1 minus P stop are constants。

 And we only have a memory of two in that case。 It's a parameter。No。Just looking at my watch。

 if I have to let you go。No， I'm gonna let you go。 Forget that I showed that because I。

 that's going to start the whole you thing。 And then in five minutes， I'm just going to lose you。

 So we stop about this one， The chain rule with the Markov rule with the memory of two。😊。

And P stop1 minus P stop。

![](img/1b0ef725221d98a1fab6eb5751f0d171_62.png)

So thank you everybody for attending this， this lecture。 Enjoy the exercise session。

 The mystery game。 Do we have a winner already。😊，Okay， so the results are going to be checked。

 so I hope you enjoy all of this。😊。

![](img/1b0ef725221d98a1fab6eb5751f0d171_64.png)

So enjoy the exercise season。 I'll see you next week at at 10 AM， as always。

 for the continuation of this In the last week of the semester， we are just going to enjoy。

 have a quiz with everybody and a wrap up of the semester。 So the material should stop next week。

 Thank you very much。 goodbyee。 See you next week。😊。



![](img/1b0ef725221d98a1fab6eb5751f0d171_66.png)

And thank you， Joshsh from Mog。A good note。 Actually， the mystery game will be released later today。

 Oh， it's not sure。 Yeah， we haven't released it yet。 Okay， so it will be released today。 Okay， yeah。

 that's great。

![](img/1b0ef725221d98a1fab6eb5751f0d171_68.png)

![](img/1b0ef725221d98a1fab6eb5751f0d171_69.png)