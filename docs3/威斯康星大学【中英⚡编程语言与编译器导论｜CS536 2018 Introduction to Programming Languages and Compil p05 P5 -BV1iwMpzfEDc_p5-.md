# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p05 P5 -BV1iwMpzfEDc_p5-

![](img/26cf8b261d3dd95f933468908db64430_0.png)

![](img/26cf8b261d3dd95f933468908db64430_1.png)

Thatt fact。Now， that's boy is that working？Is that a little bit。 Yeah， that's， well， maybe not。Okay。

 well， that looks better。See do we turn on the little light here？Yeah， I think that's readable。Go。

 okay， good afternoon。We're within a week of having Project2 do。

 So people are actually starting to worry about it now。

 And I thought I'd make a couple of points that will help you in， in doing the project。

Firstst of all， I mentioned this last time， but it's turned up a couple of times since last lecture。

 So I'll repeat it。Now， this has to do with you if you're running your eclipse on a Windows box。

And it's a fairly minor thing， but being minor， it can still be frustrating when you trip across it。

It turns out the file system format for ordinary text files under DoOS。

 which is what Windows is inherited from， is different than what is on Macs and Uniix systems。

 A Mac really has a Uni system underneath and really it's a very fancy goUI on top whereas DoOSOS and now Windows are quite a separate product。

 which is probably why it took so long to get DoOS and Windows up to the level of reliability that Unix has had UniX goes all the way back to the 1970s。

And in some ways， I say， oh my God， that's pretty ancient。 And it is。

 But it's also a long time to be using a software product。 And the longer you use it。

 the more faith that you have in it， that all the major bugs and most of the minor bugs have been recognized and fixed because only know if something gone wrong。

 why is it taken 40 plus years for it to turn up， maybe because you're extremely bad luck or something。

 But usually most of the stuff are there。So from our point of view。

 what happens is way back in the beginning， it turns out that for Uni systems。The end of line。

Marker is new line。 The actual character that backslash new line represents in those systems。

 They have a combinations of backslash new line and backslash carriage return。

 which is a backslash R。The only problem， and both of these are are reasonable alternatives。 I。

 As I said last time， it's more like， do you prefer having ketchup on your fries or vinegar。

In the United States， ketchup， I think is more popular in Britain， fishish and chips。 for example。

 they always use vinegar。So what happens is if you happen to be on a Windows system and you use one of the Windows editors。

 it'll assume you probably want to have the standard Daw slash Windows file convention。

 which includes this carriage return。There's nothing wrong with that except when you feed it into the scanner we're generating。

 I don't say anything at all about carriage return because I'm in in the Mac OS slash UniX environment where carriage returns are not routinely used。

Say， oh my gosh， you know why no， I don't give us equal treatment。

 But all you really have to do is when you're scanning， be aware that you may see a carriage return。

 And I think probably the best thing you can do is match it and ignore it rather much like white space because I believe what you should do is double check and make sure that you're getting your line numbers correct because what would happen is when you see a new line。

 you should increment the go to column 0 of the next line or column 1， I guess of the next line。

When you see a backslash N in the， N， and R combination。You want to do one， but not two increments。

 So I think just ignoring our will be okay。Now， what happens if you don't ignore R in this case。

 Well， what'll happen is you'll probably get this carriage return character floating through。

 None of your patterns will match it。 And it turns out J Le has a rule that a generated scanner that is Y Y Lex。

 If it doesn't match a character at all。 What it should do is essentially terminate scanning。

 So it's a runtime error。Now， that's kind of arbitrary。 But as I'll show you momentarily。

 there's such an easy work around that if you don't want that。

 and that if you don't want to terminate without some of meaningful error message。

 there's a pretty easy way of doing it。 And let me show you that。 Some of you already are doing it。

 but let me go to others just too。Catch you up。Yeah。

 so what this is actually something drawn from not Project2， but Project1 and that seems kind of odd。

 but remember everything I gave you in Project1 is open source。 that is you're allowed to use it。

 and one of the things in there was essentially a JL specification for that version of CSX light that we were using to test Project1。

And， and therefore， anything in there is a fair game for you to examine and draw from。

And if you go to the very bottom。What happens is I have a little couple of lines that essentially protect me from illegal characters。

 So remember， the rules are that you use the rule you apply the patterns from top to bottom。

And the first pattern that matches the character gets it。Therefore， if you get to the bottom。

 nobody but nobody else wanted it， and that might have included， for example。

 your carju and your backslash R。So remember， Dot is a matcher that says。

 I'll match any single character except back such new line。So it's almost like any care。

 but it's any care that stops at the end of the line。 And it does that because if you。

 if you wanted to do， you can also matches anything by saying dot or backslash n。

 And now you've got something that matches one character。 That's not too bad。

 But if you put a plusr star on it。 it's like the monsters dev in Cleveland。

 It eats anything and everything to the end of your program because anything and everything looks good to it and the rules keep matching。

 matching， matching until you can't and you can't when you hit the end of the file。

So that's kind of a all dangerous。 But what I have here is sort of like a little bit of protection。

 And you're welcome to copy this verbatim or paraphrase it。

 But essentially I say there's a lexical error。 I。e。

 some character I couldn't match and I give the line number and column number because I've got it。

 I print out the YY text。 Remember if it's unprintable。 that won't help you a lot。

 but it could be some other thing it is printable and you simply missed it somehow。

 and mentions that it's ignored。 And then it。Goes ahead and in increments the column by one because there was a character there and it's ignoring it。

 But it wants to go on。So those couple of lines， a four lines， I guess it is there。

 is a really easy way for you to protect yourself from characters that either are totally illegal。

 You might throw some of those at you just to see what happens or you're at the point where you mean to actually start matching that。

 but you haven't gotten to it yet。So， and it turns out if you look at this， too。 also。

 there's some things like some reserve words and so on。 Actually， I gave you more in the。

The definition for Project1， the JX definition， then I did。

