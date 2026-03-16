# 【全集】MIT麻省理工 黑客工具 中英字幕 1080P Hacker Tools p12 Lecture 12 - 包与依赖管理 -BV1jcPTz6EE2_p12-

So moving on to the next topic。Which is package management。

 this is going to be a little bit more high level than profilers。P followersers and debugers。

 which is already pretty high level because it's really language specific。

 but a lot of the ideas behind package management are common across languages and tools。

 so we'll talk more about the ideas here。So softwareft usually builds on other software right like any program we write is using language libraries and probably a bunch of other packages。

And so that means you need to manage these dependencies somehow。

So a couple of things that are involved， package repositories。

 when people write programs or when people write libraries。

They need to put them somewhere in order to make it so that other people can access them。

And so different languages and different build tools。

 you'll use different websites for this sort of thing。For example。For Python packages。

 the place where most people put them is in the Python package index。I don't word。For rust crates。

They go on createates DoIO。And so on so it's all very language specific。

 but in general the communities usually。Agreed on some place to put。

All the libraries that are written for a certain language as they can be found in a single place。嗯。

And so what these。What these websites do is they store basically source code and then often precompiled binaries。

For a bunch of different platforms。Every version of a package。

So I' to write some software and for every version of that software。

 this will host to the source code along with some binaries。Now， software evolves over time。

 mean some much of refers to different pieces of software。So like how can we do that。

 well maybe we can just give a sequential number to each piece of software like as the program evolves。

Okay， thiss version one root to twoer to two version4 and so on。But。That's kind of clunky。

 and we can do a lot better than that in terms of communicating meaningful information。

Maybe one thing we could do is。Refer to different versions of a library by like their Gi commitment。

We had the version control lecture last time right so every time someone needs a change and version control commits it it'll be associated with some commit hash。

 but that's also not a very informative thing like all I'll tell you is。

Exactly which code it corresponds to， but it's not really interpretable to a human。

So people come with better ways of reading software， and there are a couple of different approaches。

 but I think what most people are standardizing on these days is something called semantic versioning。

变真的吗。And so sesymmetricmantic versioning is something that is like you might see version numbers。2。

And then the wayre supposed to interpret version numbers like this。This is a major version。

This is a minor version。And this is a patch version。

And then the way this is supposed to be interpreted is that， okay， at the right of software。

 when you actually change these version numbers。If you fix the bug。

 and it doesn't really change the behavior of anything else。

Then you implementcrement this thing so it go into one point。

It does all the same functionality as your earlier version。

that works with this version of the library should also work with this version of the library because all you've done is fixed about it。

嗯。When you in the minor version， well you're supposed to do that whenever you introduce a new feature in a way that background is compatible so that you add a new function to the library without affecting any of the other functions in the library。

 well then you might release。Thank。And when you increment a major version。

 you only do that when you introduce backwards incompatible changes。

 so like any software that originally worked with this won't work。中パ。

Or is not guaranteed to work with the the version？And so。

And these version numbers are actually super useful right。

 like if I write a program and I want to specify which version of the library。It will work with it。

被快て。Smantic version number。That should work with anything that has the same major conversion number。

At least the specified minor version number。And then any patch version number。Does that make sense？

And you can see how this is more useful than just having sequential version numbers or something like that。

嗯。So you can see， for example。Let's just make sure we understand what exactly this means。

If I say that a software package depends on at least version 1。2 of some software。Well。

 that means that。I can。Run this on top of anything where this is exactly。The version I'm looking for。

And this can be anything equal to this or greater。The minor version numbers only increased。

When new functionality is added。doesn't affect backwards compatibility。

 can't break any software that real on anything。In the older version of software。Also。

I can rely on any patch for you because that's only the inement when bugs are fixed and so it shouldn't matter。

Bgs are fixed， my library that builds on top of this should still behave insane。

So that's version numbers。And then one thing you can do in addition to specifying version numbers。

And I might have some， but I might be writing some software that has a couple dependencies say。

Depending on package。Version 1。2 or greater。Let me use this notation to study， okay。

I'm depending on package A and I need at least version 1。

2 because maybe I'm using some new feature that was in 1。2 that was not in 1。1。

 but also I don't want version 2。0 because that could be backwards and compatible。ま一際に。De C。

 you have some other version number。And here， maybe I might even specify a patch version like， okay。

 I want 3。5。4 because some critical bug was fixed here and I don't want to be running on some older version。

 but I also I，So that requirement and so on， I might have some requirements in terms of different dependencies and what versions I want。

So as we talked about， version numbers are super nice。

 but maybe something I can do in addition is specify exactly which software I want to be running。

 and this is nice for making the whole process really reproducible。More reliable。

So if I released say my software called X and I relies on these versions of A andP。

 if I just gave somebody my。and told them like these are my requirements and then they went to ahead and install things that kind of satisfy these conditions they gave。

 but were a little bit different than what I did like say I installed，嗯。はて。Say I like version 1。

3 of this and version 3。4 of this。TodayI was running my software and he installed what version I put four of this。

Version3。Version 3。5。最 ofです。In theory， if everybody does semantic versioning correctly then follows the whole increment patch version when you fix bugs。

 an increment minor version number， when you add new features。

Increment major version number every time you introduce any backwards and compatible change。

 well then everything should work out， but sometimes people make mistakes and like accidentally introduce new bugs。

Laterter versions of software， things like that。So maybe in addition to specifying just my constraints。

specify exactly which versions of dependencies I want to install like maybe I might specify my constraints。

 but I would also say make sure you install exactly version 1。

3 of A and make sure you install exactly version 3。6 of B。

 so went have a situation where like say I install some software and it works。

Jose goes and installs the same thing and he has different behavior。And then in addition to this。

 you can do one other thing。You can actually give。A cryptographic hash of the contents of the dependency。

 so this is kind of like the give commit hash it's kind of equivalent to that in addition to all of this and that gives you an additional。

That you don't need to trust the package repository anymore， like your tool will check， okay。

 like E has commit hash。Something and A has commit cash， something。

And when you go and actually fetch the dependencies from online from IP or wherever else。

 and you actually check that the contents match what you're expecting。

You can be really sure that nothing was tampered with right。

 otherwise say a malicious package repository could be like。

 okay I go and install my packages and everything works fine。

 but then when Jose goes and installs my software， it gives them different version of these dependencies that actually have some kind of malware or something in it so by giving cryptographic hashes you enforce that G installs your software along with dependencies gets exactly what you installed as well。

So that's a concept usually called lock bottom。Ldown dependency。Also outside of log piles。

 like you may see that when you're done only like some Linux I like E like。

And the scheme is they brought you like an MD5。It mean like if you get the thing。

 you can run the high。I'd say the like that works out。

And as long as no one is kind of tampering with the main repository。

 then you can get it from anywhere and just check what the has is。

Any questions about cryptographic hashes or have you guys heard that before should we do it？

SoRaise your hand in your house。So any questions about block files？Yeah， can you explain。So again。

 this is all very language and tool specific。嗯。But basically a lot of language tools will just do this by default so you don't need to worry about it。

 and I think all the ones that support this will do it by default and the ones that don't support it well they don't support。

呃。Yeah， so yeah， it's a language specific。But usually it'll be in the form of like you have one file which will describe these kinds of constraints。

 and then you'll end up in another file， maybe called like something。

 block and it'll have the actual hass or specific version numbers or things like that。

And they'll keep both of these， but the high level descriptions of dependencies and the lock file contents under version control for your own。

かしら。This all seem a little bit abstract， but again。It's all very language specific。

 so if you understand the concepts of then you can apply obtain any particular language tool。

So the next thing I want to talk about is how you specify version numbers through your software X might depend on a couple of different packages。

 how should you specify which version of the package you need？

You can imagine you a couple different things。Maybe you could give constraints like I take here。

 like okay， I need at least 1。2 because I'm relying on a feature that was in the 0。

20 release of major version one and I also， of course I don't want to go to the next major version number because。

be breaking backward compatibility and like similar thing with this one。

 except the additional thing that I'm specifying the patch version is like。

 oh it's some really important buglist space and my software doesn't work with older version list。

how messsses it up。Both of these are given in terms of constraints， you could imagine。

Here it's like I'm specifying minor version。And I'm specifying you。没有。Cha on President committee。

Maybe you can also imagine giving。Constraints in terms of like， I want exactly version 1。4。

3 of this offer。And there's different trade offs in terms of specifying these constraints in different ways。

Giving these constraints in terms of kind of like I want at least this version number is good in terms of letting the developer of these libraries fix bugs and then those kind of will automatically be used by anybody who installs my software later。

 right？So。I released my package exit uses version 1。

2 of Library A and then someone discovers a bug in version 1。2 and that's fixed in version 1。2。1。

 well 1。2。1 still satisfies this constraint。Whatever tool I'm using to install dependencies should hopefully install the latest version of the software that satisfies the constraint and select like updates。

Bug fix should profitate automatically if I do this out of thing。

But there are also benefits to specifying exact version numbers because maybe my software relies on specific quirks。

 maybe it relies on a specific bug that was in an earlier version of a library or maybe I just don't trust the developer to follow a semantic version like maybe I'm just think oh。

 they might mess up and break my software accidentally and so for that reason it might be good to specify exact version numbers and so there's just some tradeoffs there and you need to think when you're releasing a library or releasing some software which is right for you I think there's no single right answer。

But this is some new。People try really hard to follow semantic versioning。

It doesn't work out in slight corner cases。s something you need to be aware of。

So any questions about how you specify version numbers？

these general ideas will be present in most tools you use where you can specify things like what minimum version number you want or whether you're want an exact version of something or things like that。

 the syntax will be different for different languages。But the ideas won't be same。嗯。

So the next thing I want to talk about is how you actually go from things like these constraints to I say okay。

 I want to install software X， it has these dependencies。

 go fresh these dependencies like how is that actually done Well。

 so package managers use different dependency resolution algorithms to look at these requirements and then figure out how to satisfy them。

It can actually get really complicated and I think for a certain class。

 like if you allow pretty sophisticated ways of specifying dependencies。

 you can actually make this problem computationally hard。hi is kind of mut。

But this is again just something to be aware of because you can enter really complicated situations right。

 like I can have packet A and A and C， but suppose like，If I look at the dependencies for package B。

 B might actually depend on C， so here's like dependencies for X。

And here are the dependencies for being。And say B depends on packet C。

 and it has this constraint that this needs to get least version 1。5 and less than two。

Now I have a problem right if I want to install x， x needs specific versions of A and B and that needs this exact version of C。

Possible allowed versions。B needs， obviously， is not compatible with this， right。

 so things can get pretty complicated。And especiallyspecly if you're doing things like installing software system wide。

 which you might do if you have programs that use dynamically loaded libraries。

 you can end up in situations where you want different programs that want incompatible versions of libraries and it can get really complicated。

And so。Again， here's a kind of situation where there isn't really a。

Solution to it in all cases is more of a， this is something you need to be aware of that this kind of issue can exist。

Here's another reason to be kind of careful in specifying your own dependencies so you don't end up in situations where you get stuck like you want to be as expressive。

Clleeer as possible when saying like， okay， this is。The true requirements。

 I don't want to say something more strict than I need to。It might cause problems somewhere。

Trying to figure out how to satisfy my。And if you're curious you can even look at the source code for have some of these tools handled a dependency resolution。

 some tools take really simple approach like Loco， you want to install X to look at the requirementscurre one at a time and for each one I'll just install the latest version of the software that satisfies the constraints and then when I try to recursively satisfy dependencies I'll just install the latest version and so on。

 and if there are ever any incompatibilities well I'll just ignore and pretend it works。I like works。

Other tools might design find more sophisticated， like it'll look at all the dependencies and try to find the versions that satisfy all the different constraints and thenll report back to things don't work out。

Again， all very tool and programming language specific。Pip， the Python package manager， for example。

 does not do anything particularly sophisticated here while appT。

 which is one package manager for Linux like installing system wide programs。

Does not be much more sophisticated here and we'll report errors to you and even give you kind of interactive prompt to say like。

 oh， here's the incompatibility， here's the choices you can make to try to resolve it。自个。

So any questions about the idea of dependency resolution？In these tools。OK那。

So the next thing I want to talk about is something called virtual environments。

So say you're developing multiple different software projects like I'm writing software Project X。

 but I'm also working on some project Y that might have some different and maybe overlapping set of dependencies。

And。Maybe the penencies the versions aren't exactly the same， like Sam developing software Y。

We use the same format used over there， so here's dependencies for。And say this depends on library A。

But here I need something that's like version 1。3。This is kind of fine if I'm working on both X and Y at the same time。

 even if I install all these libraries kind of system Y， because I could install version 1。

3 or later of A and that's still compatible with the set of dependencies for X。

It's looking at really crazy really quickly， right。

 like now suppose I want to use library B in product Y as well。I need some older version of B。

 so maybe I need version 2。0 of B。Right。This is a problem， there's no set of versions of like A， B。

 and C that I can install to work on both projects X and Y。For A， it works out， but for library B。

 I need some version 2。X。For Project Y， and I need some version of 3。 x per week。right？

So like maybe I install this version when I want to work on Y and I go and install different version whenever I want to work on X and keep switching versions that can get really annoying and so there's a better solution for that。

And one solution is something called virtual environments。

And the idea is that instead of installing these libraries kind of system wide。

 you install libraries in a way that are specific to each particular project。

And I can give a quick demonstration of that in the context of virtual。

 which is a tool for doing this for Python。We do a lot of Python demonstrations that I think。

ICon here use a lot。It's pretty useful。So。I went to a very complicated demonstration。

 but I'll show you a simple thing。嗯。So there's this library called NPy。

 and I've installed it system wide on my machine， so if I just open up Python。

And look at what version of numpI I'm using， version 1。15。4。嗯。Well。

 one thing I can do is create a virtual environment and what this does is okay。

 I say I have a folder and I can give it any name I want。And I'm going to install dependencies。For。

Whatever program I'm working on in this folder end。

 and so it's going to be separate from my system wide dependencies。

And don't worry about the specific commands I'm using for Pyth under， you can look them up later。

 there's a link in our nodes for this section。But I can go ahead and do like fitness onumpy inside this virtual environment。

嗯。And I can even install a newer version。Inside this virtual environment， like inside here。

 I'm running version 1。16。0 of NmI， whereas for my system wide install of NPI， I'm running version 1。

15。4。And so this just shows how you can easily have different sets of dependencies for different projects。

I can have a system wireless itself and I have as many virtual environments as I want to just activate one or the other to kind of swap in a whole different set of dependencies that will be loaded whenever I。

And so they're like this is the virtual end a particular software that's used for Python programs。

 there's even other alternatives to virtual and for Python and then for different languages like say for Ruby。

 there's a tool called Bler and so on， so you'll need to look up for whichever language you're using with the particular tool。

 but this is the general idea that you maintain separate sets of dependencies per project。

Some other languages don't really have this problem， like say Ru for example。

 what it'll do by default is compile a static binary。

 so when you're building a program it' will pull a all of dependencies and just make one fat binary that contains kind of like in line or like stuck into the binary。

All all the code from the dependencies， and since if you're working on two different projects。

 well there's no kind of like system wide install or shared libraries or shared anything between the programs。

 so you don't really need to worry about this issue。

 so it's not an issue in the context of a certain language。

Any questions about this idea of Bridgeburn？Okay， and then the last thing we're going to talk about is something called vendoring。

 so this is a very different approach to dependency management。

 but one thing you can do rather than bothering with all this complicated stuff is if you're working on a software project and you need to use another library。

 just take all the source code for that library and copy and paste it into your project is you have one gigantic tree containing all of your code and all the other people's code and just kind of build everything at once and don't really worry about the dependencies in the traditional that。

嗯。And so there are some advantages to doing this， like you're not depending on package repositories anymore。

 you're not relying on dependency resolution anymore。

 if you compile your code as like always the same code every time。And so you know。

 like exactly what you're building against。And certain people do this， like for example。

 Google I think maintain one gigantic repository and it has all their code and they've also vendored all the code that they're using from other people because they don't want to be relying on package repositories。

 they don't want to be worrying about like oh， author advisor A accidentally broke something。

 an patch version and now they have to deal with it and so Vening is a pretty good approach in some ways and so it might be something you want to think about if you're working on a software request。

There's a very different approach of dependence against。Yeah， and so that is all we have for。

Package management， all the high level ideas we think you need to know。And then of course。

 to actually make use of any of the stuff， you need to look at the documentation for the particular tool you're using for the particular language。

 but that should be easy once you understand stuff。So any questions。Okay。

 so let's take a 10 minute break and then after that we will talk about OS customization followed by remote machines covering topics like SSH and SSHFS and so on。

