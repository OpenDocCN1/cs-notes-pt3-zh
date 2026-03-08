# 悉尼大学【中英⚡计算模型｜COMP2022 Models of Computation】 p01 P1 Natural Deductive Logic： RULES #1 (R, &E, &I, MP, CP) -BV1vTe6zzENb_p1-

In this video， we're going to start rules of inferences and proofs in propositional logic。 So first。

 let me explain what a proof is， a proof of alpha from a set of ws， gamma。 So this is capital gamma。

 This just means a collection of one or more wellform formulas。

 It's a sequence of inferences or rules using the wofs from gamma and any extra hypotheses that result in alpha。

 and those extra hypotheses are also subject to rules and constraints。

 And we're going to talk about some of them today day。Now。

 if we have a proof a proof of alpha from gamma， we write gamma proves alpha。

 So the symbol you can think of it as the meaning proves。So what do I mean by this？

We can take English sentences in an argument form， and we can translate them to propositional logic。

 So we've done this at the very beginning of the series。 So if I am hungry， I get something to eat。

 I am hungry。 Therefore， I get something to eat。Now， we can represent this logically。 So one。

 if I'm hungry， I give something to eat。 So this is H Ar E。 I am hungry。 H。 Therefore。

 I get something to eat。 So therefore E。So what we do is we set up our hypotheses。

 and we use rules on certain lines， and we justify them to get to our conclusion。

 So this is a simple application of something called modispons MP P。

 so we can use that in order to get E。In this video， we're going to learn five rules。

 do a couple proofs of those。 And in each video， we will introduce new rules。

 and the Bruce will get more complicated。 We're not going to deal really with sentence translation。

 That's not what the point of these videos are。 The point is to have something already in translated form and to get from A to B。

 because that's the most difficult part。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_1.png)

So the first ruler're introducing is called reiteration。

And I should really explain how these proofs work first。 So whenever we start a proof。

 we have a line。And what we do is we put our hypotheses above that line。

 and all of our inferences occur after it。Now， you can add more hypotheses at any point。

As long as a rule is being used， and we'll talk about those rules by starting a new proof inside。

 So you can add in a new hypothesis that has to eventually conclude。So if you have。Let's say。

Some hypothesis A or some line earlier in the proof。 And you have a new subproof B。

 So you're introducing like an extra step at any point。

 what we can do is we can reintroduce something from outside the proof。 So let's say in line K later。

 we can take it from line I and we can reiterate it with R。Now， in some systems。

 you just assume that everything's already there。 But reiteration is a way of explicitly introducing it again。

 It's sort of like in our truth trees， when we had branching paths。

 and we introduced that variable in again， just to make it explicit。Okay。

 so we'll see reiteration in action a little bit later。 Basically。

 that means that if you have something earlier in the proof， you can just copy it again。

Conjuction introduction is nice。So if we have two lines， I N J， where you have。

 say A in line I and B in line J， then later， let's say in line K， we can introduce A and B。

 So what we do is we write which lines we get it from。 We got it from I N J。

 And this is what's called and introduction or conjunction introduction。

So basically this says if you have P and Q in proof， you can introduce P and Q。

So to show this more explicitly with this example， suppose we have two hypotheses that werere starting out line 1 and line 2。

 We have P。 we have Q。 Then in line 3， we can introduce P and Q。

 So this comes from line 1 line 2 and an introduction。So this makes sense from a truth table。

 P is Q P is true， Q is true， therefore P and Q is true。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_3.png)

The third rule we have is called conjunction elimination。So basically， if A and B is true。

 we know that both A is true and B is true。 So there's two different ways you can use the rule either I'll do this in yellow to make sure that we're seeing the rule in action。

 so either you can put a down。And you would justify this by saying， oh， line I。

 this was and elimination or conjunction elimination， or we could hike B。

 And this would also be from line I。 And this is conjunction elimination。So specifically。

 if you want to see the example with P and Q， let's assume that we have P and Q somewhere in our proof。

 let's just say it's the hypothesis， for instance， then right away in line 2 and in line 3。

 say we could put P in line 2 and we could put Q in line 3， and both of these would say， oh。

 it comes from one， it's and elimination。Again， the later we could put them back together if we want to。

So that's conjunction， elimination and conjunction introduction。

 probably the most intuitive rules out of literally everything。Now。

 the one we saw on the very first slide was called Mouspons。

Some people call this conditional elimination， I like moduspons， it's just how I learned it。

 and we abbreviate that as MP。So basically， if we have a and we have a arrow B。

 we can just follow the arrow。 So La K， we can write down B。

So you can justify this by saying from line I and line J， we used mods opponents。So basically。

 we just follow。The arrow and get the consequent antecedent。 then consequent， we had the antecedent。

 Therefore， we get the consequent。So this looks just like it did on our first line。

 let's say we have P arrow Q。 Let's put that first。 Why not， And then we get P in our third line。

 we can get Q by saying from line 1 and line 2， we have modspons。

It doesn't matter the order of the ones and the twos。 As long as we see those two patterns。

 no matter what order they're in， we're good。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_5.png)

Okay， that's mor pollins。The last one we have is something a little bit more complicated。

 is like the reverse of modisspons。 Well not the reverse necessarily。

 But if you think of modiss opponentents as conditional elimination。

 you can think of this conditional proof as。Conditional introduction。So basically， at any point。

 we can start a new subproof。And if we add a new hypothesis P。And we end up with a consequent， you。

We， weve essentially said， okay， what if we have P。 Well， then we can get Q。

 So then in a later line in line K， you can write P arrow Q。

 And what you do for this one is you justify by saying from line I to line J。

We've proven P R O Q through conditional proof。 So this is a hypothetical。

 This is what gives you that conditional。So this all has to be kept within the subfruit， though。

 you cannot just take things from outs from in the main proof and put it in there。

 Like you have to do everything within the subruit and we'll see examples of that。

So we just did that example before， but let's say let's just make a new hypothetical example here on the right side。

And let's do it with reiteration too。Okay， so let's say in line1， I start with C。

This is my only assumption。So we'll call this the hypothesis。

 And what I want to do with this is I want to prove。That if we have A and B。Then we have to C。

 that's what I want to prove。So what I can do is I can a subproof。I can say， okay， well。

 hypothetically， hypothetically， what if we have A and B？And we can add this as a hypothesis。

 so what if we have that？Well， in line 3， what we can do is we can say， oh， well。

 we have C as a hypothesis already。 so we can copy that into our subgroup。 So from line 1。

 we use reiteration。 I can write it R， I can write it read it。Okay。Well， at this point。

 we don't actually need our line to be this long。 So let's just shorten that line a little bit to where it is。

 And what we've done now is we've proven that if we have A and B， then we get C。 So in line 4。

We can say， O， A And B is our antecedent。 And if we have that， we have C。 So from lines 2 to 3。

 we had a conditional proof。 So that would be the end of our proof。

 We've shown that if we have A And B， then we have C。

 And this just follows naturally because we already assume that C is true at the very beginning。

So actually。What we could do here just to really show you how powerful this pros。

 You can take it from the very beginning。 so you can consider the assumption from one from C as being a conditional proof。

 So in line 5， once we get rid of this little bar， we could say， O from C。We get。If A and B。

 then we get C， and this is just a large conditional proof。From one to four。

So this is essentially the same thing。 If we have C， then we have if A and B， them C。

So I like that example。Because it shows a conditional proof twice。 And actually。

 it shows you what you're really doing in all your proofs。 When you have hypotheses， Again。

 these are just like what ifs。So。Almost every proof you do， theorem or non theorem。 In a way。

 it's just sort of a conditional proof。I shouldn't say that for every case。

 taologies are not conditional proofs， but if you have any sort of assumption and any sort of conclusion。

 you have a conditional proof。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_7.png)

Okay。So let's do some examples， that's really the more important thing is just to show a bunch of examples。

So I want to show that A arrow B and B， arrow C gives us a arrow C。

So let's set up a couple rows here。So our assumptions 1 and2。

 Our assumption is that we have a arrow B。And our assumption is a  Ar O C。 So this is our hypotheses。

You never know how big these proofs are going to be so just give yourself as much space as possible。

 Now， we need to prove a arrow C。So what we should do is we know we're going to need some sort of conditional proof。

 because we have to assume a and we have to eventually get to C。 That's how we get it。

 That's how we get the arrow in our final result。So in line three， I'm going to set that up。

I'm going to start a sub proof。 I don't know how long it's going to be。 I'll just say it starts here。

 If I need a longer line， I'll make the line longer， and I'll assume a as a hypothesis。Okay。

In line 4。What can we do， Well， I see that We have。Well。

 I should go back and fix my mistake here because we have actually that this is B arrowrow C。

 not a arrow C。So I see in line one that we have Aarrow B。

 So I want to bring this back into the proof because I can do something with it。

 So this comes from one， and this is a reiteration。Now， in line 5。

 because I have A and I have A R O B， I have B。 This is just an application of mods poins。

From 3 and 4 or conditional elimination， because I have a and I have Aarrow O B。 Therefore， I have B。

And now I have a bee here。Okay， well， in line 6， I can reiterate Barrow O C because I can do something with that then。

 So from 2， I'm reiterating it。 And then in line 7， I can take B。 I can take Barrow O C。

 and I can apply modda's opponents once again to get C out。 So this is from 5 and 6。

 And this is modda'sons。So at this point。I've started with A， and I've proven C within that subproof。

Therefore， in line 8， what I can do is I can introduce a arrow C using the conditional proof rule。

From lines 3 to lines 7。So I said， well， what if I have a。

 And I've shown that with the assumptions I have， I can get C。 therefore， from 3 to 7， If I have a。

 then I get C that gives us a arrow C。So that was the proof of example one。If A then B， if B then C。

 therefore， we have if A， then C。Let's do another example。This one's a little bit more。

 So if we have A then we have not B and not C， if we have D， then we have E and F。Therefore。

If we have A and not D， we should get n B and E。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_9.png)

I'm going to turn on the lines for this one because I have a feeling。At this one。

Might be a little bit long。So I have two assumptions here。I'll turn the lines off at the end。

 so that way we can see it in all of its beautiful glory。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_11.png)

So we， if we have a， then we have not B and not C， as our first assumption。

Our second assumption is that if we have not D， then we have E and F。

And we want to show that if we have A and not D， we get Barrow or not B and E。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_13.png)

So because I see an arrow here， I'm probably going to have to assume that we just have A and not D and then see what happens。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_15.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_16.png)

So let's set that up。I don't know how long it's going to have to be。

 but we can put some lines in here。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_18.png)

So for my assumption， I'm going to say， okay， what happens if I have a and not D。

 So this is another hypothesis。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_20.png)

Okay， well here we can use conjunction elimination。So， four and5。We're going to get A。

 We're going to get not D， and this is just conjunction elimination。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_22.png)

On three。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_24.png)

ok。Well， at this point， I have A， I have not D。 and in one and 2， I see some modisponent's potential。

 So in 6 and 7， I'm going to reiterate these rules so that way we can use them in the sub proof。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_26.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_27.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_28.png)

So if we have A， then we have not B and C， this comes from one， it's reiteration。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_30.png)

And then we're going to have not D arrow E and F。So this comes from line two。

 and this is reiteration。Okay， at this point， we can use mods componentss。So in lines 8。

 we have a from line 4， we have a and line 6， we have a arrow， not B and not C。

 so we can use modda's poins to get ourselves not B and not C。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_32.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_33.png)

So justification46mp。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_35.png)

In line 9， we can do modepons again with not D and not D arrow E and F。 that gives us E and F。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_37.png)

So this comes from line5 and line7 as modponents。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_39.png)

So these two lines right here。We get E and F。Now we have to remind ourselves。

 what do we want to prove？

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_41.png)

If we have A And D， we're trying to get that we have not B and E。 That is our goal。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_43.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_44.png)

So I'm going to use conjunction elimination on8。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_46.png)

To get not B。 So that's 8。 And that's conjunction elimination On line 9。

 I'm going to use conjunction elimination to get E。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_48.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_49.png)

Comes from 9。 That's another conjunction elimination。 So now I have not B， and I have E on their own。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_51.png)

So I need to make this line a little bit longer， so I need one more line here。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_53.png)

So in line 12。We're going to take not B。 I'm going to take E。

 and I'm going to join them together because we know those are both true individually。

 So they'll be true together。 So from line 10 and line 11， that is and introduction。

 So now I have not B and E。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_55.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_56.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_57.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_58.png)

So this concludes our conditional proof now， because we're saying if we have A and not D。

 then we're going to get not B and E。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_60.png)

So for our final line in 13， we can say， okay， if we have A and not D。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_62.png)

Then， we're going to get。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_64.png)

Not B And E。 And what does this come from， Well， from line 3 all the way up to line 12。

 that was a conditional proof。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_66.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_67.png)

And there we're done。We have shown that A arrow， not B， and not C and not D， arrow。

 E And F proves that if we have A and not D， then we get not B and E。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_69.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_70.png)

So if we take out of the lines， this is what our final proof looks like。W should get rid of。

These colorful lines again， that way we can see what it looks like。Okay。

 so that was example number two， a little bit more complicated than example number one。

 but another good illustration of the conditional truth， reiteration， moduspons。

Conjuction elimination and conjunction introduction， like everything we introduced。

 was used in this proof。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_72.png)

Now one more example。Show that A arrow B and C gives us if we have A and B， then we have C。Okay。

 here's an interesting one。It's interesting because you might think to approach it a little bit differently than how you should。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_74.png)

So let's just set this up。Our only assumption we're given is that if we have A， then we have B and C。

So that's our hypothesis。Okay。Well， we need to show that if we have A And B， then we have C。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_76.png)

So what we have to do in the subproof。Is we have to make an assumption。That we have A And B。 Now。

 you might be thinking， hold on， we just have a here。 Why don't we just use a as an assumption。

 But nope， you have to take everything on the antecedent as an assumption。 Otherwise。

 the C P proof will not give us if A And B， then C。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_78.png)

So。That's a new hypothesis。In 3 and 4， what we're going to do is we're going to use conjunction elimination。

 Now， do we have to actually。Get B。We don't need B。

 So let's just use conjunction elimination to get A。 So 2， conjunction elimination。

 Why bother writing down B if we don't need to use B for Mos opponents or anything。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_80.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_81.png)

So we have a。4， we're going to reiterate our hypothesis。 If we have A， then we have B and C。

So that's the reiteration from one。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_83.png)

And line 5， we're going to use moduss poins on A arrow B And C to give us B And C。 So from 3 and 4。

 we did mods opponents。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_85.png)

Now， at this point， what do we need， We need C， That's what we need。 Well， C is in line 5。

So we can use conjunction elimination。On line five to get a C。At this point。

 we can exit our sub proof。 So in line 7， we can say， okay， if we have A And B。

 then we're going to have C。 So this comes from lines 2 to 6。 And this was a conditional proof。

 And therefore， yes， our proof is complete。 We have shown that if we have A and B。

 then we have C based on the fact that if we have A， we have B and C。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_87.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_88.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_89.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_90.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_91.png)

So you don't have to write out everything。 If you're doing conjunction elimination。

 you only have to do it on what you need。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_93.png)

In every other example， I did everything because we needed everything。 Why not？ But in this case。

 there was no point in writing B again。 same here。 Like， we didn't need the be here。

 We didn't need the be here。 So why bother writing it out。😔。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_95.png)

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_96.png)

Just write out what you need。Now， what do you need， that takes practice， that takes experience。

 the more examples you do， the more practice you get。

 you'll get a little bit more comfortable with it。

![](img/95c0aea16fe811d96ff0b6e188c6c7b9_98.png)

So what I want you to try on your own are two more proofs there' will be a solution video in 24 hours if you can do these in the comments fantasticastic。

 if not， that's all right too， try them on your own and we'll go over the solutions in the next video as always if you have any questions。

 post them in the comments below and I will answer you one again。



![](img/95c0aea16fe811d96ff0b6e188c6c7b9_100.png)