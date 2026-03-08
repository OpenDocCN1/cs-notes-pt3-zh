# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p07 P7 -BV1iwMpzfEDc_p7-

Okay， I see most of you found your way up here。I actually taught up here a few years ago。

 but this was supernova at that time and it didn't have this tremendous artwork here。

I don't know if you love that or hate it， but I imagine Judy paid more for decorating that one wall than we paid for decorating the entire compai building。

But I must say in campai， they give you more choices than you have here。

 whenever you have your building， your room painted， you can have light beige。

 medium beige or dark beige。And who could ask for more than that？So at any rate。

A few more people are in here first thing let me hand out。

 I have extras of the project three that I handed out last time。

 if you don't have that or you didn't get one don't you put your hand up because I'll be talking a little bit about some of what's on here。

好。I must say teaching on campus here is always more exciting than back on UW campus。

 I was coming in today and all of a sudden there was a guy behind me with a flasher on that said。

 oh my God Judy's hired her own traffic cops and given no epic charges is probably $100 for running stop sign。

But then fortunately I turned one way and he turned the other and I guess they spotted something really serious like somebody drinking a bottle of coke out in public。

 you know shamelessly or something。But seriously， what was this guy doing。

 was I doing something here， is he trying to signal the error？

Is that like a cab saying that he's looking for a fairer？I mean， you don't flag them down and say。

 take me to Camp Raall and pick me up after the game or something。Yeah。Okay。

 so it didn't have me do anything bad， I didn't think I had but。It gets a little spooky now。

 particularly it's getting a little darker and you can't really tell。So anyway。

 let me put this guy on， this is what we just handed around。

 and I wanted to make a couple of points and then we'll get into some other details。Oh。Yeah。

Not sure if this can be better focused or not。An。Is that readable or semi I readable？

I'm not sure if it's in focus or not， it could be my。 Oh that's not too bad。

 maybe I just take my glasses off。So any rate， one of the things I wouldn't mention。

Most of you last time is when I printed these out the optional semi second line。

 this guy right there didn't come out cleanly， that should have been a lambmbda I've since fixed a version that's online so if you reprint it or bring it up that'll be there what happened is。

I transferred a lot of information from PDF back to word。

 turns out the new Acrobat actually does it and does it pretty well。

 so if you have a document that you don't have the source for。

 you can kind of reverse engineer it but special symbols that sometimes messes up a bit and that's when we're dead。

The second thing I want to mention， I've gotten a couple of questions about this is these two productions here。

Look a little odd and the fact they are a little odd。

 but they are not incorrect what happens here is this thing is supposed to be generating zero more fields followed by zero more methods and it doesn't in odd way because in many cases we use lambda turns out in this circumstance because a design decision badly made when I guess when C was invented which was in the 1970s they made a bad decisions which made parsing a little harder than it had to be and you have to do a little engineering to get it to work but basically the way the thing works is I want to generate fields followed by methods unlike full Java I don't allow them to be intermixed I don't think it's all that much of a blessing and sometimes having fields segregated and then methods in their own areas it enhances readability So what happens is if I want to generate fields I look at production number two counting from the top and just apply this。

It is production as many times as I want fields， so if I want three fields。

 I do it three times if I don't want any fields at all or I'm sick of generating fields。

 I go down to method decals and method decals then generate zero or more methods so in that particular case you can generate what you want。

Again， it looks a little bit odd when you get around to actually building the AST。

 you'll find out you have to do a little more rewiring than you typically do。

The explanation for this， I can't give you the full explanation yet。Or I guess I could tell you。

 but then I'd have to kill you or something， but no it's the situation there or that。

If you try to generate a pser using the more obvious way。

 it runs into an error and choosing between these two productions。If you generate the way I did it。

 the difficulty is resolved using the kind of parser that Java cup generates。

 which is something called an LLR that has nothing to do with Los Angeles but it just has to do with a screwry abbreviation somebody decided so that's the explanation for that if you want to try to change it you can but if you find out the parser is complaining about these you'll understand why if you change these and the parser is not complaining that will usually say something like a shift reduce error which is it's a way of saying I can't figure out what to do so if you come up with that。

That's what I was trying to avoid doing this， and this does work and it does avoid the error。

There is one error that I warned you about that I'll talk about a bit more in just a moment or two。

 and that is the if then and if then else statements。

 these things have a true ambiguity and I'll show that to you。

 and there's a general rule that if a grammar is ambiguous。

 ambiguous means there's two or more different derivations， different pris trees for the same input。

We try to avoid that because ambiguity means that we can't be sure that what you and what the compiler writer are thinking are the same。

 so you might write down something thinking you're getting interpretation A and the parser and the compiler writer gives you interpretation B。

So we tried to avoid that。It's rather much you may have noticeds in programming languages and you may like it or not。

 is that have any of you ever read 1984？It still a few people are used to be mandatory way back when。

 and it's a story about a totalitarian state and somebody using kind of a precursor to modern computer technology。

 and one of the things the state had is something called newspeak。

 which was a modification of old English or our English。

To remove words that represented politically incorrect or politically unacceptable concepts。

So for example， you are only supposed to be loyal and love big brother who depending on your politics could been Adolph Hitler or Vdimir Lenin or Joseph Stalin or who know whoever it is that you politically hate。

And anybody else， your family， your friends， your pets， or anything like that。

The way you're not going to be able to express and not be able to have those bad thoughts is you couldn't express them。

Now what happens is in programming languages we try to make it impossible to write down things that aren't clearly and definitively stated and ambiguities are one of those things we'll see later there are other choices where sometimes what people like is not what's good for them and examples of that are if you use eclipse or Java there many。

 many times the thing complains that for example， this particular field or this particular variable may be uninitialized。

Sometimes it's right， many times it's right， sometimes it's wrong because that's a very complex determination。

 but what happens is what it's trying to do is say you cannot write down a program which may be undefined because given the fact it does undefined would lead to problems presently or in future。

So we'll get more into that， but I wanted to point these two things out and we'll refer to this from time to time。

 in fact， I'll be talking a little bit about how you approach the project and in a nutshell what your project really is is taking these。

Oh， roughly two pages worth of productions starting the middle of one and going to the top of page three and essentially put them into the Java cup format and in doing so。

 you'd also have to transfer from these productions into construction of an abstract syntax tree。

The abstractite syntax tree you build is essentially the same as what we gave you in Project one。

 except there we gave you the powerer working and it built an abstractite synintaxt tree and then you would walk it for project one。

 it was to get information on declarations and uses。For this project。

 what you'll do instead is simply do what's called。

