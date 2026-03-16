# 【全集 附课件】加州大学戴维斯分校 操作系统与系统编程 中英字幕 1080P p28 Lecture 28 - 代码构建脚本 -BV1jXr5BBEKa_p28-

![](img/8038d42c0442aa53f884ced67aae4b8c_0.png)

Okay， so let's start with an example。Let's imagine that I'm working on a project that has multiple files。

I have a main file。That essentially is kind of a front end program that expects the user to give me a number via the command line arguments。



![](img/8038d42c0442aa53f884ced67aae4b8c_2.png)

And essentially， I received that number and then we call a factorial on that number。



![](img/8038d42c0442aa53f884ced67aae4b8c_4.png)

And the factorial function is defined in another file。



![](img/8038d42c0442aa53f884ced67aae4b8c_6.png)

Which means that I need a header to declare the prototype， which I can then include in my main。



![](img/8038d42c0442aa53f884ced67aae4b8c_8.png)

And the body of the function is defined in its own kind of module， in fact do C。

And then just for fun， I have a readme Magdown file。

Which I could potentially want to transform in HTML。So that's my project。

We're not trying to do anything smart here， but that's going to be a good project to start thinking about how to write a good Mac file for this project。

嗯。So actually， before we get into the Mac files， let's imagine I don't have a Mac file。

If I want to compile this project， one option I have is to just do the compilation manually。In C。

 for every C file， you have to first compile it into an object file that is if you have。

A project that has multiple C files。

![](img/8038d42c0442aa53f884ced67aae4b8c_10.png)

So you have those this intermediate step， and then you can link all of the C files into a single executable。



![](img/8038d42c0442aa53f884ced67aae4b8c_12.png)

That you can then use。And if say I want to compile my markdown file into an HTML， I could use。

 say a tool like Pan Dooc， and then I could look at it with Firefox。

Now the thing is if I do that manually， it can cause some issues because what if the next time I continue changing my C files？



![](img/8038d42c0442aa53f884ced67aae4b8c_14.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_15.png)

If I， for example， like change factag。c， then I would need to recompile factag。

0 and redo the linking into my executable。

![](img/8038d42c0442aa53f884ced67aae4b8c_17.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_18.png)

If I change main dot C， then I would need to redo that step and the linking step。If fact。

 H changes these， because it's included by both fact。c and fact。 and main。tc。

 I would need to be doing all of those steps again。



![](img/8038d42c0442aa53f884ced67aae4b8c_20.png)

If I want to change the compilation options， then I need to remove everything and just retype all of the comments from scratch。



![](img/8038d42c0442aa53f884ced67aae4b8c_22.png)

In essence， I hope you're getting what I'm trying to say here。

If you do things manually on the long run， you're going to be spending a lot of time probably making mistakes。

 not a good solution。So instead of doing things manually， why don't we automate them？

And that's what make is about for building projects， it's a building tool。



![](img/8038d42c0442aa53f884ced67aae4b8c_24.png)

嗯。

![](img/8038d42c0442aa53f884ced67aae4b8c_26.png)

So a Mac file typically it's just a file that contains the building recipe or recipes of your project。



![](img/8038d42c0442aa53f884ced67aae4b8c_28.png)

So in your project you would have a magFide， usually the name is kind of important it starts with a capital M and then just says magFide。

When you type make。It will try to locate if there is a Mac file with that name in the current directory and just run it。

You could also specify which file specifically you want to run with make with the flag dash F。

 but in that case here， those two command would be exactly equivalent。Quickly before we up no。呃，O。

So now if we open a Mac file， we're going to see a bunch of recipes。



![](img/8038d42c0442aa53f884ced67aae4b8c_30.png)

Or rules。The rules have three components。A rule starts with a target。

 that's what this rule is trying to build。

![](img/8038d42c0442aa53f884ced67aae4b8c_32.png)

In order to build this target， it might need some prerequisites， like files that are needed。



![](img/8038d42c0442aa53f884ced67aae4b8c_34.png)

The files are prerequisites also is meant to keep track of the dependencies。

 so say like if one of the prerequisites is modified。

 then it means that the rules should be the rules should be run again。And then optionally。

 we have a comment。That will extend build the target。

 And that command has to be prefixed with an actual tab character， not spaces like a hot tab。Okay。

And if you want to comment your code or your like Mac file， you can do that with a pound sign。

So let's start。With very simple makephi here with some basic rules that would apply to our project here。



![](img/8038d42c0442aa53f884ced67aae4b8c_36.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_37.png)

And it could look like that。So we're trying to eventually build the executable my fact。

 my fact depends on having main dot0 and fact。0 and once we have them we can run this comment which will。



![](img/8038d42c0442aa53f884ced67aae4b8c_39.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_40.png)

Produce the target based on the two prerequisites。If we don't have them。

 then those are the rules to generate them。 So main dot O， for example。

 depends on main dot C and fact dot H。And that will be the command to run in order to generate main。

Same for5 dot O。And we also have a rule here in order to create readmi。html ourofrimi。md。

 that would be the command that needs to be read。If I put that in a Mac file， and I type make。



![](img/8038d42c0442aa53f884ced67aae4b8c_42.png)

It works pretty well。Oh， it seems like， well， I have those options here and they're not there。

 but that's just the typo。

![](img/8038d42c0442aa53f884ced67aae4b8c_44.png)

What matters is that now I can just type make and you see that it's going to run all of the comments that otherwise I will have to have typed manually。

 so it's pretty nice。

![](img/8038d42c0442aa53f884ced67aae4b8c_46.png)

However， as you can see。It's only creating the executable my fact， it's not creating the HTMLR here。

If I want to create the readmi thatt HTML， I need to actually。Specified。

 like make and make this specific file。The reason for that。

 let me clear the screen is that by default， when you type make， make will locate the first。Rule。

 and that will be the default rule。So here， if that's the default rule， then make。

 that's what it's going to do。

![](img/8038d42c0442aa53f884ced67aae4b8c_48.png)

And if you want to make another rule， then the default rule， you have to specify it explicitly。



![](img/8038d42c0442aa53f884ced67aae4b8c_50.png)

So how can we change this Mac file so that it does both。

 it does the my fact executable and also the Rmi do HTMLtml。

What I can do is have kind of a meta rule。

![](img/8038d42c0442aa53f884ced67aae4b8c_52.png)

That I would put right at the beginning。So this rule with this target。

 the target itself is actually kind of a fake target because it's not a file that I'm trying to build or anything。

But I'm using the same syntax so that in fact， now I can list multiple prerequisites to that target。

 and those are all of the things that I want to build。Now， the using the name all。

It could be anything else， it could be like any name you decide。

 but it's true that using all is kind of a convention that is used in many different Mac files。



![](img/8038d42c0442aa53f884ced67aae4b8c_54.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_55.png)

But so now it works。If I only type make。We're actually going to generate both the executable and also the HTML。

Okay。One thing that's missing in that Mac file is that I would also would like to be able to clean all of those generated files。

 so what I need is a clean rule。And same it's a meta rule in the sense that like it's not actually something that we're trying to build。



![](img/8038d42c0442aa53f884ced67aae4b8c_57.png)

But it's just going to be a rule that when I activate it specifically， it will run this line。

 meaning that it will delete the executable the HTML file and both object files that were created。So。

 let's see it in action now。If I typet make。It builds my entire project if I type make clean and you see here I have to specify it because it's not the first rule and it probably shouldn't be。

Then it's going to remove all of my files and I can go back to a clean directory with only my source code。

O。So。Altogether。That's what I can get at like first version。

Of a Mac file for that project that works pretty well。And that was good enough。

 it's probably close to what you wrote for project one。

 although project one could really be written in like four line stops。

 but at least like the same spirit of what was expected from you for project one。U。

Now for product two， we want to be a little bit more ambitious because we can improve this Mac file in many more ways。



![](img/8038d42c0442aa53f884ced67aae4b8c_59.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_60.png)

So。How can we do that？First of all， let's look at this Mac file and try to notice that lots of things are written multiple times。

So for example， right here。I define the two targets that I'm trying to build and then it's repeated here and there。

 and it's also repeated here and there。Then the executable my fact depends on the two object files。

 which are also repeated here and there。If you look at those two。Rules here。

They're almost the same rules。Apart from the fact that this one builds main dot O out of main dot C。

 and this one builds5 do O。Based on fact that C。 But other than that， they are the same lines。

You can also notice that the commands。They have all of that part totally in common and yet I'm duplicating all of that information。

And so on。So。Here we're trying to be good programmers and good programmers are lazy programmers。

 You don't want to type something more than once if it's not necessary。



![](img/8038d42c0442aa53f884ced67aae4b8c_62.png)

So let's try to see how we could simplify that Mac file and try to make it more generic。



![](img/8038d42c0442aa53f884ced67aae4b8c_64.png)

The first thing that we could try is to remove the fact that。

Here when we say we're trying to build main。0 from main。c。

We have the same information repeated over here and over there。



![](img/8038d42c0442aa53f884ced67aae4b8c_66.png)

For that， we can use some specific variables that are called automatic variables。



![](img/8038d42c0442aa53f884ced67aae4b8c_68.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_69.png)

And namely， it's a dollar at sign， dollar inferior and dollar carrot。

Dollar ads will be automatically replaced by whatever the target of the rule is。

Dollar carrot will be。Automatically replaced by the entire list of dependencies。So here。

 well it's going to be replaced by dasho， my fact， and that's going to be replaced by main do0 and fact。

0， which is exactly what we were doing before， except that now it takes four characters instead of like having to retype the whole thing。

And so here for this one。The Do art will be replaced by main。

 and the Do inferior will be replaced by only the first。



![](img/8038d42c0442aa53f884ced67aae4b8c_71.png)

A member of the list of prerequisite， so main dotsy because that's the only thing we should not。



![](img/8038d42c0442aa53f884ced67aae4b8c_73.png)

Have fact dot H be part of the GCC line。So that's first kind of optimization or simplification。

Let's simplify some more。What about here。As I was saying before。

 we have two rules here that are almost the same。Except that one is for main do O and the other one is for fact。



![](img/8038d42c0442aa53f884ced67aae4b8c_75.png)

How can we compact them Well we can use something called pattern rules。

Patn rules is when we use the percentage sign。To essentially match any pattern。



![](img/8038d42c0442aa53f884ced67aae4b8c_77.png)

And so here now we only have one rule instead of two that says that pretty much like whatever name dot o depends on whatever name the same dot C will merge this rule。

 So now when we need main dot O and fact dot O， they will both be identified。



![](img/8038d42c0442aa53f884ced67aae4b8c_79.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_80.png)

By this rule， and we will run this rule for both of them instead of having like two different rules。



![](img/8038d42c0442aa53f884ced67aae4b8c_82.png)

And we could also do the same for the matching the HTML to the MD file so that like when we。



![](img/8038d42c0442aa53f884ced67aae4b8c_84.png)

Try to generate this HTML， this rule is going to match no matter what， even if we change the name。



![](img/8038d42c0442aa53f884ced67aae4b8c_86.png)

Okay。What's next？Let's simplify that next， see， we have we have this Gcc and this set of options twice。

W whichch means that if I want to change， if I want to stop using Dw extra， for example。

 I would need to remove it twice， which is a pain。So let's try to combine that into a variable。

And make it more generic。So here's what we could do， we could declare that Gcc。

Will now be associated to a viable C。And we're going to have another variable C flags that will have all of the flags as before。

 and we can even like expandend C flag to， for example， like compare with the dashD option。

So now that I do that， I can quickly say like comment this line with。A pound sign。

And make the does G option disappear temporarily or remove the pound sign。

 not make it into a command， and then it's back again just like a few character strokes。

And so now in my rules， in my commands， I would use those variables so in Mac 5s the variables are defined like this。

And they're used with a dollar sign and then the name of the viable within parentheses。

 that's how it's expended。

![](img/8038d42c0442aa53f884ced67aae4b8c_88.png)

嗯。So starting to look pretty good here and as you can see when I run it。

I still have exactly the same like the same comments are being run。

As like when I was doing it manually， so I have not changed at all the behavior of what the magfi really does do。

 but I was able to like really compact it a lot。So there's still some redundancy here。For example。

 there I have the list of my kind of high level targets。And I have it here as well。

 and here I have a list of my object files which is reproduced over there in the clean room。

And as you know， redundancy not great because if you change one location。

 you have to update all of the other locations， so it's better to just have like things declared once。

So let's use more variables。

![](img/8038d42c0442aa53f884ced67aae4b8c_90.png)

Let's have a viable targets that will list the high level targets that I'm trying to generate and the viable objects。

 which will have the list of objects。 And so now I can use。



![](img/8038d42c0442aa53f884ced67aae4b8c_92.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_93.png)

My target here and also in my clean row and I can use my objects here。



![](img/8038d42c0442aa53f884ced67aae4b8c_95.png)

And clean them in the clean rod as well。Now it's starting to look really good。

And what's nice is that typically in that Mac file， if my project ever changes。

 if I start adding more Si files to my project or if I want to， I don't know。

 I have like new high level targets that I would like to generate。Usually。

I would need to only modify those two lines because the rest。It's completely generic。

 I usually have no reason to like directly modify that。

Everything that I would ever want to modify is towards the top of my Mac file。

 which is a lot more convenient because if I have something to change very quickly。

 I can edit my Mac file and I know that everything I should edit is towards the top。

 so that's convenient。

![](img/8038d42c0442aa53f884ced67aae4b8c_97.png)

P。So。Next step here， I don't know if you'all like me， but I like shiny things。

 I like when things look good and typically。When I type make。And I see all of those lines。

 I feel like it doesn't look that great。

![](img/8038d42c0442aa53f884ced67aae4b8c_99.png)

What about if it looks something like that like you type make and then it actually kind of hides what it's doing behind the scene and it just says likecc main orcc fact。

0 and so on and it looks like super clean in the terminal and you feel like you're a great hacker。



![](img/8038d42c0442aa53f884ced67aae4b8c_101.png)

Well， it's not that complicated to do that， let me show you how。



![](img/8038d42c0442aa53f884ced67aae4b8c_103.png)

Essentially。You want to hide the way to hide that the Mac file is running a command is to prefix it with the a sign。

 The a sign here will make the command be run， but not printed by the Mac file when it does run。

And so here now I can use Eco and use CC and say what target I'm trying to build and I can do the same here and the same there and the same in the clean role。

And that's what will make that output appear。

![](img/8038d42c0442aa53f884ced67aae4b8c_105.png)

There is one issue with that technique。Is that sometimes if my compilation goes wrong and I can't see exactly what set of options were used。

 then it's a pain because I would need to go to the Mac file and look at the C flags and try to remember like。

 oh， what exactly what were the flags that I was using again so。



![](img/8038d42c0442aa53f884ced67aae4b8c_107.png)

It's kind of a bannermer。It would be better from a high level perspective to have access to be able to print the commands that are actually run by the MacF。



![](img/8038d42c0442aa53f884ced67aae4b8c_109.png)

So let's tweak it a little bit。And use something called conditional variables。Here。

 let me actually show you from the example first and then we'll go to the code。

 So the idea is that if I type make。

![](img/8038d42c0442aa53f884ced67aae4b8c_111.png)

I get the nice output that hides a lot of information。

 but kind of just shows me like what is being compiled the at which time and so on and it doesn't。



![](img/8038d42c0442aa53f884ced67aae4b8c_113.png)

Take a lot of space in the terminal and it looks nice。Now， the idea is that。If I type make and I say。

 hey actually like can you be verbose， can you like tell me what what's going on and which command are you running exactly。

 you would， for example， say v equals one。And now the Mac file would actually show you the exact lines of compilation that it's using so that you can really like check out which flags are being used exactly and what's happening。

😊。

![](img/8038d42c0442aa53f884ced67aae4b8c_115.png)

The way that you can do that is by in the code of the Mac file。Is like。

Check the value of a potential variable V。 And so you say if V is not equal to one。

Then we declare this other variable Q。To be equal to at。

And then you use this variable Q to prefix all of the comments and so what's going to happen is that。

If you just type make。Then v is not equal to one。Q is equal to at。

 and so you're going to have a at in front of your command and it's going to be hidden and it's not going to be printed。

Now， if v equals one。Then Q will be an empty variable， so it's just going to be replaced by nothing。

And you'll have the command， and in that case， MakeV will actually print it on the screen and you'll be able to see what it's doing。

O。What's next？There is one last issue with this Mac file。And it's in that rule。

So far we've been really trying to make rules be generic。

And that rule here is not generic because we're hot coding。The fact that。

Every generation of an object file coming from a C file depends on this5 dot H header。

In our case for that project， it is true， but say the project gets bigger and I get more c files and some of the c files they don't include fact。

 H。That rule here。Would not be generic。If I make fact that H B a hot codeed dependencies to all of my C files。

 I need to find a better way。The problem is that。

![](img/8038d42c0442aa53f884ced67aae4b8c_117.png)

If I remove it。And I make it into a generic rule。Then the Mac file is actually not going to do its job properly。

 Let me show you an example。

![](img/8038d42c0442aa53f884ced67aae4b8c_119.png)

If we do a generic rule。IfWhen I make my project for the first time， it compiles everything。

If I try to make it again。Make will actually detect。 Well， nothing has moved。

 So there's no reason for me to redo anything。 That's that's one of the goals of make is to only recompile what is necessary to recompile。

 If nothing has changed， then the executable is still proper。 So there's no reason to regenerate it。



![](img/8038d42c0442aa53f884ced67aae4b8c_121.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_122.png)

Now the thing is。If I cannot fake the fact that fact that H would be modified。

Which is very important because fact dot H is included by two of my c files。

 So if fact dot H changes。

![](img/8038d42c0442aa53f884ced67aae4b8c_124.png)

Then those two c files should be recompiled as well as the executable， and that's what was happening。



![](img/8038d42c0442aa53f884ced67aae4b8c_126.png)

When I had my rule with the hard codeed dependency。Now， if I remove that dependency。

And I modify this terrifiedified and I make again， Meg tells me like there's nothing to do。



![](img/8038d42c0442aa53f884ced67aae4b8c_128.png)

Which is incorrect that actually it might be dangerous because if fact that age actually was changed。



![](img/8038d42c0442aa53f884ced67aae4b8c_130.png)

I need to recompine my project， that's the whole point of it。So the question is。How can I be generic。

To make sure that like I can have my product grow。And not have like anything occurreded in it。😮。

And at the same time， do proper dependencies of headophiles。So before I give you the answer。

 let me show you something。

![](img/8038d42c0442aa53f884ced67aae4b8c_132.png)

MacFile allows you to do something called rule composition。

It means that you can have multiple rules for the same target。So for example。

 when we're trying to build main。0。

![](img/8038d42c0442aa53f884ced67aae4b8c_134.png)

Main dot o。Can possibly match this rule， which is the rule that actually builds main dot0 out of main dot C。



![](img/8038d42c0442aa53f884ced67aae4b8c_136.png)

But we can also have another extra rule that says， a， you know what。

 main dot o depends on main dot C and also fact dot H。😮，When Mefile。We'll try to build main。0。

It will。Kind of look at all of the rules that match main dot O。



![](img/8038d42c0442aa53f884ced67aae4b8c_138.png)

And compose them， like it will look at all of them and consider all of them。Now。

 if I have this rule or those two rules。That specifically say main do0 depends on fact dot H and fact。

0 depends on fact dot H。I am properly tracking the dependencies。And I can allow myself to have only。

One generic rule to actually build。The object files。

So now when I make my project for the first time it builds everything， if I try to remake。

 Macg tells me nothing has changed。If I touch or modify fog dot H and I retype make now make will redo everything that。



![](img/8038d42c0442aa53f884ced67aae4b8c_140.png)

Depending on the fact that fact that H was modified， which is exactly what I wanted。 So okay， great。

One problem though I'm lazy， I don't want to type that， that's too much work。

I don't want to have to like type myself。All of the internal dependencies of my C files and my hair files。

I want to find someone else who can do that automatically for me。Who can do that for me。Well。GCC。

Can do that for me。So。Let's take an example here。If you remember， that's the content of。Fact thatt C。

And fact that C includes。5 dot H。Now， it turns out that when I run Gcc in order to create fact dot O out of fact dot C。

If I add this option， dash MMD。GCC will actually create a file， an extra file。Called fact that D。

And this file。Will have this content be automatically generated by GCC itself。Now， look at the file。

 What does it contain。It contains exactly the rule。That I'm too lazy to write。

GCC generated that rule by itself。All I need to do is include the results。

 like include that file with that rule inside of my make file。And they'll do the trick。So。

 let's continue。So we're getting there。 So now it means that as part of my sea flags。

I'm using this new option， dash MMd， which will create a dot D file that contains the rule to be included in the MEg file。

And the way that I will include it is via those two lines。So， first of all。

I will derive the name of the。Dot D files out of my list of objects because。😮。

Every time that GCC compiles an object， it will compile a D file。



![](img/8038d42c0442aa53f884ced67aae4b8c_142.png)

All of those dependency files， the names can be derived from the list of object files。



![](img/8038d42c0442aa53f884ced67aae4b8c_144.png)

And then I can include all of them as part of the MacF itself。And that will have， as an effect。

 let me go back a couple slides。Essentially， that will do that。The include。

 except that I'm not typing that myself。

![](img/8038d42c0442aa53f884ced67aae4b8c_146.png)

And it works so at the very beginning when my project is has not not been built。



![](img/8038d42c0442aa53f884ced67aae4b8c_148.png)

There are no dependency files in my project。The first time that we build the project。

 that's when make well like run all of the different commands and so on and build everything。

And every time that it will build those object files。

 it will also create the dependency files so after building the project for the first time now we have those dependency files being created automatically maint D and fact D。

And if we open them。We see that they contain exactly the rules that we were too lazy to write。



![](img/8038d42c0442aa53f884ced67aae4b8c_150.png)

But those rules will be included in the mag file next time we type make。



![](img/8038d42c0442aa53f884ced67aae4b8c_152.png)

So next time we type make。Actually， nothing has changed， make Fwall tell us no。

 that's fine nothing to be done。

![](img/8038d42c0442aa53f884ced67aae4b8c_154.png)

If we now modify fact。 H and we retype make。

![](img/8038d42c0442aa53f884ced67aae4b8c_156.png)

Make， which includes。Those two files that were auto generated and which contain the fact that fact dot H is a dependency to main dot O and a dependency to fact dot O。

MF will be smart enough to recompile both of them and then the executable。



![](img/8038d42c0442aa53f884ced67aae4b8c_158.png)

Cooray， everything works and we are doing like a minimum of job。And so overall。



![](img/8038d42c0442aa53f884ced67aae4b8c_160.png)

The Mac files can look like that， it's pretty advanced。It uses variables。

 it has conditional variables to be able to have like different behavior。

It has automatic dependency tracking， uses patent rules， and so on。So the idea is that。

For project two， you need to write the mag file that it is a Lib U thread。

So the Libview thread Me file。Sorry for the writing style， oops。

That you need to write has to kind of look like something like that。

 so it actually will probably be simpler because you don't need to do the pen Dooc thing at all like that's just need to like focus on creating the static library but you should use pattern rules you should use the dependency tracking you should use variables and so on so it's really just a question of adapting thisM file to your needs。



![](img/8038d42c0442aa53f884ced67aae4b8c_162.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_163.png)

![](img/8038d42c0442aa53f884ced67aae4b8c_164.png)

Okay， that's the end of this discussion and good luck writing a advanced magF。



![](img/8038d42c0442aa53f884ced67aae4b8c_166.png)