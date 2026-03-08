# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p13 P13 -BV1iwMpzfEDc_p13-

Good evening， welcome to the Pennultimate lecturecture of the season。Amazing how time flies。

 It's almost 2019。 and I just barely remember to write 18 on my checks。

I'm sure I'll mess up a little bit on that Of course most of you probably don't write checks anymore that's one of those things that's getting me more and more in common to actually have it What I have down here is the midterm stats that's the same thing I showed last week but a few people on Piazza asked and given back today a few people who missed there getting their exams back if you still want to get it back I'll be available between sessions。

So as you can see， a number of people did pretty well。 The meeting is 82。

 remember that's the midway point where equal number above and below you。

 So anybody in the 9s or 80s are doing fine，70s is no real problem，60s and below， there's an issue。

I see for the most part， the people who really got hammered。

 it was the case that first and follow got them。 Most people did pretty decent on first。

 but follow was one of those things that。That if you got， you got it and if you didn't。

 it was really， you were way off。So what I'll be doing next week is be doing a review session and I've got a practice exam coming。

 we already covered LL， but we haven't covered LALR and on the old exams and maybe on the upcoming exam。

 I oftentimes ask a question， here's a grammar， is it LL， is it LALR is it both is it neither？

As you probably guess， one thing is the case there that if something is LL。

 you can safely assume that it's also LLR。 turns out technically that's not quite so。

 but you need a really contrived example to set up just the wrong conditions to make it fail。

 So if you were somebody who had trouble with follow the grammars I'll give you， of course。

 to be really quite small， four or five lines， but that's something you might want to practice on if you decide。

 you know that that's a question you want to do。So let me， I've got some other hands for you。

 So let me go back to。The projection screen。

![](img/dc2da423b1158e19372fdef8ad080d2d_1.png)

ICom。唔屁。There we go。 So this is homework 5。 And let me。

Hand that out to you if you haven't already printed it。

 the reason I want to mention this is because it's due on Friday and normally thatd be oops that's not much time。

 but it turns out this is very much in keeping with what I'm talking about and if you read it carefully it's one of those situations that is not nearly as difficult as you may have felt it was。

So let me hand some of these out。So what this really develops is the fact that many cogenators have to worry about an issue that won't bother you。

 and that is namely they can't push operarans onto an operaran stack。

 rather the machines in question require that a register be used。

So if you're generating code and here's an example， let me slide this this guy up some。

Is that in very earliest days of compiling， people conjectured that， okay。

 how many registers do I need for a given statement or a given expression。And for binary operators。

 it's pretty clear you certainly need at least two。

And so the example up here is something like a plus B。Where you put one value in A， one value in B。

 I'm sorry A， you put in one register B in a second register。

 just call them one or two for convenience and then there's an operation that says do an add or subtract a multipier or divide based on what's in the registers so it's clear you need at least two because that's a binary operator but the question is do you need more than two so under the assumption to sufficed。

 they came up with little algorithm that's suggested there。

 namely I tell the node what register you're gonna to put your result into and call the node which may a tree or maybe a leaf and say please co-generate yourself and by the way leave it and register zero or register one。

And the question is， heres some expression starting from fairly simple。Two more complex。

And here's the example， I guess a minus b is doing in this case。

 and in this case you would load A into T0 and B into T1 and do a subtraction that had the effect of subtracting the value and register  one from zero and leaving it in zero。

 So here's a case where that scheme works fine。There's some more complex ones and the question is。

 does the scheme always work？Well，' that's part of the answer there。But there's part two。

 and it says， assume it doesn't hint。I don know why would he have a question two if question one had a particular answer。

 so in this particular case。It says， if you work on some of the more complex expressions up above。

 you may find out that two don't suffice， if that's true。

 then you'd like to know in advance how many registers will a particular tree need。

 as you might expect bigger trees may need more than fewer or maybe not。So in this particular case。

 I don't even want you to do a code generator。 All I want you to do is tell me how many registers this tree will need。

 The rules are you may not change the tree， nor may you change the operator。

 but you can evaluate in any order you want。 That means we normally do left to right。

 So in our code generator。If we were doing number B， where we did a minus B subtracted。

 C minus D subtracted， and then subtracted two subterms， we will do the left subre a minus B first。

By symmetry it looks like doing the right subt would be equally good or equally bad。

 but it's not always the case that the left and right subtrees are equal， so a。

 for example has a nontrivial expression on the left a trivial load on the right so the question then is simply come up with we code it as a little algorithm but all you really need is a formula that says you've got this tree here's how to figure out how many registereds it will need at a minimum。

 certainly if it's anything other than a leave it's going to need at least two。

 so that's kind of a sanity check because you can't assume and normally you don't assume that any of the leaves are the same。

It turns out if two or more leads are the same， then things get much harder because you may be able to set things up so you load somebody into a register and use it twice without overriding it。

 That makes the whole question more complex。 This was。

A simpler question that was asked and it's now known resulting in something I want to share with you。

 so in this case， I think just by playing around with various expressions you'll be able to answer number one。

 either it works or doesn't in those questions and if it is the case that two don't suffice then something like this。

Notice one thing that all。 It doesn't。Doesn't highlight here is that if you look at the second paragraph under question 2 says a recursive algorithm。

Now you've all worked on binary trees and binary trees are naturally prone to recursion。

 so if you're writing something that's not naturally recursive。

 you're probably making it more complex than you need to。

 so you intend to make it recursive and then you have to make decisions if one order is better than the other you take the better in terms of fewer registers and come up with a number。

Now， at least one person I was talking to yesterday， was coming up with fractional registers。

 And that's one of， no， that's initially bad。 I mean， remember that situation there that。

Mathematics and physics are full of impossible things。 There are， there are imaginary numbers。

 I hate to tell you one day when I came home from school。

 My father asked me what I was doing and studying imaginary numbers。

 And he must have had a bad day at work， boy， did he bounce up。 What do he blah bh。

 b las teaching you， you don't want real numbers。 I said， well， we， they taught us too。

 what this imaginary numbers stuff。There's also sort of things like if you're in physics。

 There's an effect called tunneling， which seems absolutely impossible。

 You have what amounts to a voltage wall and you don't have enough voltage to go over the wall。

 So you can't go over what you do。 You tunnel through， which seems totally impossible you。

Get from point A to point B without ever being able to get to the intermediate point。

 But it's one of the cool things about quantum physics。 But， I'll tell you right now。

 the solution I'm expecting does not use fractions。 Maybe it works out。 I mean。

 there's oftentimes alternative solutions。😊，I think there's something like over 100 different proofs of the Pythagorean theorem。

So I， situation there。 And I'm sure you don't all know 100， but probably at least at one time。

 you learned at least one。So anyway， that's why I want to talk in this。

 I think you shouldn't have too much trouble doing this。

 And I just want to remind you not to forget about it。But I also have two more handouts。

 and these will be valuable of the cogen series。 I did one， and I handed out。

