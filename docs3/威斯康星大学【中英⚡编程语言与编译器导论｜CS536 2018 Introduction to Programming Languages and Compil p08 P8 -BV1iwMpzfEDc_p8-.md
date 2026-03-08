# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p08 P8 -BV1iwMpzfEDc_p8-

Okay， good afternoon。Pretty close to good evening， I guess so。

First thing I want to do is show you something that is in the build do XML that would be handy for this project and for the remaining projects and that has to do with previously the build do XML had a particular file name wired in a test file so it' would say run assignment1 or assignment2 on this particular file we also have that in assignment3 but as you're learning probably the best way to test your parser is to have a variety of fairly small programs that try this feature and that in the other so if there's a problem you can hone in on it quite rapidly well we actually have something to that effect and I'm going to show you how to use it so essentially now and this is included in the startup。

Into something that's Args processorcessor do Java。And in that， very near the top。

Just what is about line 27？There's a couple of goois that are available。

 one of them is a simple GuoI that rather than getting the file name from the buildoutt XML itself。

 pops up a little a GuoI window with essentially a line where you can enter the name of the file。

There's also more involved one that I think is actually more useful that essentially allows you to look around and move across directories or files。

 find the one you want to then click on it。So what happens is the simple one will simply bring up a window that has a line that says here's the name of the file I want。

 I'll type it that save you the bother of having to go in build that XML and edit out the file you don't want and edit in the file you do want let me show you the other one。

 which is more useful， I think。And again， what we have here is we go to build that X，M L。And。Run ads。

Number two。And among the various targets you have notice there's one that I already have clicked is not test。

 but test1 test is the one that takes the file let's wired it into build do XML that was there mostly when you're starting。

 let's get anything to run and modify it a bit， but in this one if you do test one。

 let's hope it works。It'll do any recomps and all that stuff it needs。And。It will then build。

 bring up what you just saw， which is essentially is one of these little windows you see in Guis that allow you to go around and find various。

Fileles you want， so if you had a top level file you do that。

 but notice there's something it's called test files。So as usual， if I click on that。

 here's a whole heck of file number of files I've already created for you。 And， of course。

 you might create your own。 So the usual sort of thing is， let's try number one。And open。

 which in this case means process。And beinggo， what happens is it took this one and in this particular one。

 the build was successful and it ran。It， it ran the piser， and it looks like everything pared。

 and then I unpared to something that looks reasonable。 So in this thing。

 as you're doing more and more tests， you can put the tests anywhere you want and simply go ahead。

 run test1 and then just navigate around to the particular file you want。

 So that's already there and you simply have to go ahead and use it if you'd like。

So let's go on to I've been getting a number of project project questions yesterday。

 and I'm assuming I'll get more this week。 and certainly next week。

 the project being due a week from today will get a lot more business。 So let me just。Switch over to。

My notes and。These notes， by the way， are actually available to you。 If you go to the actual tab。

 that has lectures， there's an entry for supplemental information。 And that's this。

 So the first guy you can ignore。 This was something last time I taught we had a different set of homework。

 So we can just ignore that for the time being。And one of the questions that's come up at least three or four times yesterday several more times on Piazza and you may be thinking about it or if not。

 you will soon， is there's a problematic production。

 when it comes to actually building the associated AST and it's production number two which is difficult because I have member decals。

 and if you look at the construct for member decals， it has two subries。

 one of which is field decals with an S， and the other is method decals with an S。

But if you look at the right hand side here。It doesn't have those guys at all。 It has a field decal。

 just one and。It has member decals， but we already have member decals。

 So the intent here is essentially to take members and add fields to them one by one。

Turns out it's a little bit odd， but by certainly not unreasonable that it actually build these from right to left。

 that is each time it finds a field decal， it appends it to the head of the list representing field decals in member decals and。

Basically， what happens is there's a third production which says member decals goes to just method decals。

 So what it really does is it finds all the methods first and puts them in methyl decals with no fields。

 and then it adds fields to the members one by one right to left。And say。

 why in a world is he doing this to me and the reason is if I do it in the obvious way and that would have been having field decals。

 filebte method decals， and in fact I actually tried that way back when I created this。

 it doesn' imps and it doesnt for the reason that either members or methods can go to Lambda。

I haven't developed a shit I will today， but parsing lambmbda is really kind of difficult。

The reason is most things the way you parse it is you find a match， so if for example。

 I'm looking at some tokens and I see an if， I say， ay， this is either an if then or an if then else。

But lambmbda is empty， It's invisible， so you can see it anywhere and everywhere。

 it's kind of like seeing a ghost。 you know， if you're into seeing ghosts there everywhere。

 So in this particular case， how do you know you've seen one when you can't see it？

And we'll develop how to do it it's sort of an indirect way。

 but in terms lambda is so handy that we don't want to give it up。

 some very early grammars didn't use lambmbda at all。

 and that turned out to be difficult because there are places where you want to have an option。

 you want to say I may have this or I may not and the obvious way to do it is say if I have it here it is and if I don't it goes to Lambda。

So driving is fine by reversing it， you have to say kind of， well， he didn't take this choice。

 so he must have gone lambmbda and taken that choice， so it's sort of indirect。

But but by finding lack of evidence。 and we'll develop that a little later today。

 So I didn't do it to be mean。 I did it because if I did it this way， it was persable。

So what's going to happen to you is remember the parser works。

 so you don't have to worry about telling the ps or how to par， it knows that。

 but you do have to tell us how to build the AST because that's your choice or my choice and our joint choice perhaps。

So what happens is。When I see this production， I go ahead and say well I can't just call a constructor like I usually do and most of the productions is pretty easy。

 you say okay I see an if so there's a constructor for the if node and I fill in the parameters and the same thing for a while。

 the same thing for a binary app and name nodes and lots of other things。

 but in this thing you got to create a member decals and the constructor for it is give me some fields and give me some methods and those together are called the members。

 fields come first， methods come last and altogether together they're the members of a method body。

So or a class body， I should say， so in this particular case。

 we have to do some indirect construction， so unlike many of the others where it was really very simple。

 call the constructor set result equal to the result and you're good to go so what we're going to do is。

Do a little editing。 And again， you did editing when you took C S 3，67 or C S 300。

 where you had a list， for example， or a tree and you'd wire things in or out。

 So there'd be something， if I have a binary search tree， for example。

 how do I add a node that usually pretty easy， How do I remove a node。

If you had the pleasure of remembering red black trees。

 those are even more interesting because there' are all these sort of rules about I have to have something that has these patterns so you've done tougher things in this particular case here's my suggested approach and I know a couple of people have already done it because they were in yesterday and we talked about it during office hours。

So what's going to happen is。Going back here temporarily， what you have are two little subries。

 One is for a single field decal， probably a variable， maybe a constant， maybe an array。

And you have a tree of member decs， which contains all the methods and maybe some other fields。

 which appeared further to the right。So we know that because here's a field decal and member decals are the place where I put other fields and other methods。

 So I've got to go ahead and produce a member decals out of this。

So what we're going to do is we're going to say。Well I already have a member decals。

 all I have to do really is edit that to include the single new field and the single new field has to be found at the extreme left of the set of field decals that I happen to have so if I think of the field decals as a tree really representing a list it's at the beginning of list the fire left。

So here's what I suggest doing， and let's see if we have， oh Ja last night。

