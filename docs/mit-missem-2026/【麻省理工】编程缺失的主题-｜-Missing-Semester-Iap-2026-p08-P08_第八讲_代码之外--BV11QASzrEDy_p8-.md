# 【麻省理工】编程缺失的主题-｜-Missing-Semester-Iap-2026-p08-P08_第八讲_代码之外--BV11QASzrEDy_p8-

All right it's fivepa I guess let's get started so in this lecture we're going talk about something that doesn't really feel like it has anything to do with code like it doesn't have anything to do with engineering it doesn't have anything to do with you know the technical aspects of your computer it's more about the soft skills that sit around being an engineer and this is actually one of the things that most engineers that I know struggle the most with they tend to be very good technically but where they struggle is in collaborating with others well knowing how to interact with online ecosystems knowing how to interact with large code bases knowing how to collaborate in large code bases。

 knowing how to learn knowing how to interact with people who are their seniors or their juniors and how to effectively work in either an open source context or in a team context at a company or university or anything like it。

This lecture is therefore also I'm not going to show you any code I'm not going to really write it on the whiteboard。

 I'm just going to talk to you about what it is like to be an engineer and how you should think about interacting with other engineers in that work。

😡，The reality is that being a good software engineer is actually like I'd say about 50% about writing good code and writing good systems and the other 50% is about communicating with others It's about telling them like how your system works or bringing them up to speed but it's also learning from them what they need from your system。

 it's engaging with other engineers that work on systems that yours have to interact with。

 it's interacting with open source systems， libraries that you need to make use of or that in turn make use of you。

 and it's also maintaining the software that you build over time。

 whether it's in the open open source projects or proprietary code bases inside of a company I'd say that the ways that you communicate as an engineer tend to sort of fit into roughly two categories so there's one way communication and two way communication one way communication is when you are writing something for other engineers to consume It's not really a dialogue。

 it's not like you phone them。On a video call or anything。

 it is just you usually write something down and then they are going to process it at some point in the future。

 potentially far removed from you。And actually the primary vehicle that we have for this is in code comments。

 so when you write comments and code， this is one of your primary ways to engage with future engineers that look at that same code and that could also be you in six months from now or a year from now when you don't remember all the stuff that you had in your head when you originally wrote that code code comments I find tend to be underutilized or maybe not underutilized。

 but they tend to be used ineffectively people will generally know that writing code is writing comments is something we supposed to do but they don't really know what to put in those comments so by far the most comments I see are things that explain what the code does these are also the most useless comments because the code is right there and you can just read the code to understand what it does the more important things that you want to capture comments or the things that are not trivial to parse out from the code and when used that way comments can be extremely valuable。

😊，For in a number of different ways， one of the obvious ways to use comments is to point out things that need to be done tod right so you will write a comment in your thing that is slash s to do colon and then you write a description of something that needs to change in the codeb near the location where you put the comment you can use issue trackers and stuff for this。

 but sometimes it's useful just have it written out there right in the code where someone can easily find it later such as through like GP like the first shell lecture introduce you to。

😊，The other of references so it'll be you know in some codebs is more common than others。

 but you will implement algorithms that come from other places。

 this could be it's been implemented in a different programming language and you port it it to yours it could be an algorithm from a paper an algorithm for a blog post maybe it's a data structure that like in a class or a textbook somewhere and you want to put a reference in there this is super useful to people who come to that code after you because now rather than just seeing some weird sequence of code that does something that ultimately let's say sorts an array then great that they know that the function is supposed to sort an array and they can see the code and they see what it does but usually there's a better reference for why that algorithm works that way and why you chose it and that can be useful to actually put in code Commons there are a bunch of others some of them are listed in the lecture notes for today's lecture as well but one of the ones that I particularly find or useful to include are。

😊，What I'd call why nots， so these are things where you put a comment in the code to explain why you didn't do it the obvious way。

So you'll have written some code and for whatever reason。

 maybe you ended up spending like two hours debugging something because you did it the straightforward way and it turns out it doesn't work。

And this can be it's hard to give good examples of this。

 but it could be things like the obvious thing would be to use let's say the standard library from your programming language use the built-in dictionary orh type hashmap type and for whatever reason that is a bad idea for this particular piece of code and so you have some other data search and said that is actually a map but and you're using it like a map but you're not using the standard library map。

 why not well you need to explain in the comments why you have made a different choice than the default one because otherwise some clever engineer is going to come later on read that code to go this is just a map。

 let's just switch it to be the standard library map and then have to go through the same pain you went through to discover why that doesn't work in the first place。

😊，Because your insight at the time when you made that choice is otherwise going to be lost of time。

TheThe next mechanism we use for communicating with other people down the line about our software are readmes so most projects you'll find whether sort of proprietary or open source tend to have a readme file usually in markdown syntax readme files are they've ended become in the sort of grab bag for anything about a project and you will find that as you browse the internet you find some readmes are significantly more useful than others some are extremely long and mostly useless and some are very short but that's all you needed to know writing readmes is sort of a threestep process maybe before where you first should explain what does this thing do like you should not assume that someone came to your repository and already know what this project is so the first step is what does this thing the second thing is why should I care so for example it could be that people are just looking around for an interesting projects to contribute to they see a description of what this is and they go I don't care？

😊，Need this thing， I'm just looking for something that's like fun to work on。

 so why should I care what does this thing do and why is it interesting？😡。

Or why is it nontrivial the third is how do I use it right so let's say I've decided that based on the first two this was useful to me and I understand what it does and now I want to use it。

 how do I get started and the obvious next question is how do I install it if I now know how to use it and I've decided I want to use it how do I get it on my computer and it's kind of important that they happen in this sequence so very often you'll see projects have readmes that give you the install instructions first and you go well but I haven't decided if I want to use it yet so why should I give the install instructions and then they have a bunch of other things in the readme there are mostly useless that I'm not even going to go through because there's no point having them there in general you want to keep the readme fairly concise so that people can actually use it as a useful skimable reference。

😊，And then there are other files you'll often find in projects that explain other aspects of the project。

 so for example some projects will have a contributing dom which has instructions on if you want to contribute to this project。

 here's how that works well here's our process for filing bug reports submitting pull requests like changes to the project here's how you're supposed to test it。

 here's conventions we use in the code you might not be used to and so on those things don't need to go in the readme they can go in a separate file because the readme is intended for users of the thing and contributing is intended for collaborators on the thing。

😊，The third kind of one way writing that we do is commit messages so we already talked about in the version control lecture we talked a lot about Git but one of the things we didn't really talk about is sort of Git hygiene like how are you supposed to use Git not on the command line sense but in the collaborating with others sense so one of the key things that Git commits give you is the ability to not just say here's a bunch of changes store them for me but also to give additional description of what those changes are and here too you can easily fall into the trap of just writing in the commit message the what of the change but the what of the change is usually obvious from the contents of the change if someone runs Gittiff and they see this was changed with this well they know what the changes what they want to know is why did you make this change and why did you make it in this particular way。

So they act as a sort of historical record of why the codebase evolved in the way that it did rather than in some other way。

 and there's this tool called GitBme， GitBme is a tool that you can point it to a file in a Git repository and for every line in the file it tells you the last commit that modified that line and you can go in and look at it。

 look at the commit message and see why that line was changed and what it was before。

 and you can keep going this back all the way through history。

 but this tool and other tools like it are only useful if the commit message actually explained why things changed。

In general， the commit messages you write should answer what problem forced this change。

 like why was this change necessary？The second is what alternatives did you consider Like why did you not change it in some other way Some of these sections are you can leave them out if it's obvious why you had to do it this way。

 like if you're fixing a bug what alternatives did you consider might not be relevant because it was just an off by one bug and you had to fix the off by one bug there's no real alternative to it what are the tradeoffs or implications of the change that you made so sometimes you'll make a change and that change hopefully makes things better but you might also make some things worse so for example this happens a lot with optimizations where you benchmark your program you find that it is faster in the common case when you make this change but there'll be some cases that are now slower because it's usually rare that you get optimizations that are truly for free and so you want to explain why you made that tradeoff Why do you think that the upsides of this were worth the downsides。

And similarly you want to point out non-obvious implications of the change， so for example。

 in if you write code where there's sort of a separation between the build part of the process and the runtime part of the process this is not the case in Python but in compiled languages like CE or Ru it is so if you make a change that makes the runtime of your program faster but it makes the build time of your project slower。

 then that is a worthwhile implication to note in the commit message because it's a tradeoff that you chose to make and it's not obvious to someone just looking at the di that this is the case。

 and so when someone is reviewing your change， that additional context is very。

 very useful because they might disagree with that particular choice of trade offs or implications。😊。

Now obviously you should scale the detail here with the complexity the bigger the more complex the change。

 the more context you should give and if you have something that it's a trivial change you can give much less context even so you usually don't want to give like you they fixed fo kind of commit message with no additional detail that tends to not be super useful even if you're working out a project just by yourself you can easily fall into this trap here where all your commit message or just like blah they don't contain any contents and so this means that when you later on try to figure out why did I leave this line in here why did I choose this algorithm over here。

 all of those things are just lost to time they might be obvious to you write now when you're writing the code。

 but later on in a year or two it will not be Now LLMs can actually be really helpful here and writing good commit messages the problem is that if you tell an LLM write a commit message for you it will spit out a long commit message with all sorts of details about the what of the change。

Because ultimately， if you point it at the diff that you have and say write me a commit message。

 the only context it has is the di， it's what changed， it does not know why。

 it does not know the tradeoffs or the implications。

And so if you want to use an LLM for writing commit messages， you tend to take one of two approaches。

 the first of them is to ask it to write the commit message in the same session where you had it make the change。

 if you were using an LLM to make that change。And the reason for this is the conversation you had with it in prompting it to make the changes to your code is giving it context。

 that conversation is the context， and so then if you ask it to write a commit message。

 it has much more information about the what and the why and the implications than it did if you just pointed at the di。

So in an existing session， it can already be useful to tell it to commit。The second way。

 if you don't have change that was made in anL session or that's gone away。

 then what you want to do is point it at the di， also point it at instructions kind of like the ones I've given here。

 like you could even point it at the lecture notes for this lecture and say would I would like to write a good commit message if you find that you are missing context if you find that something is not obvious if you find that you don't understand why this change was made。

 ask me。😊，And so you make it into an interactive session where the LLM essentially gets to use you as the oracle。

 use you as sort of like a tool， an agent tool that it can query for additional information to make a better commit message。

 but it will not do these things by default， you really need to make sure that it understands both what you want to go in the commit message and to make sure that it gathers that information over time。

 otherwise it will just produce a a commit message that looks very impressive but is' not actually useful。

As your changes get more complex you'll also want to break your Git commits into smaller chunks。

 so imagine you've been working on your project for a while。

 been working on them for like a week and you haven't really committed it which I would not recommend but let's say you have right and then you decide I should probably commit something and push it because my collaborators need help with this or whatever it might be。

So you do a， you know， get to add dot， you add all the things， you get commit。

 you write a commit message and you push it off This is not going to be super useful to other people for historical reasons or for review because it means that there's one giant change that probably contains lots of other unrelated changes。

The most obvious example here is when you also ran a format around the code and so now you have a diff that is huge but most of it is just formatting changes and only some of them are semantic changes。

 so in general you will want to separate out into different commits the logically or semantically independent parts of your change。

You can do this in using Git add P， it allows you to add in patched form so it basically takes all of your all your diff and for every sort of white space separated or like for every change that has a nonchange between it and the next change for each chunk of changes it will prompt you do you want to add this to the upcoming Git commit and then you can answer yes or no。

 and so you can use GitA dashP to selectively add things from your current diff into the commit to your staging into your the environment you're about to commit from。

And then you do a Gi commit of that and then you do GitP again to add other changes and you keep progressing through this LLMs can help with this as well you can even tell them things like I have a bunch of diffs in this figure out what the semantically related ones are and try to write commits for it and then you might have to do some cleanup after you would need to make sure it gets the context but it is a useful tool for finding logically separate ways to split giant diff into commits the other thing that's valuable here when you have multiple commits you can also open multiple pull requests for review that are separate from each other so this is is particularly useful and open source projects where if you bring them a giant diff that has multiple unrelated changes in it。

 they will tell you to go away and come back with a better structured pull request they will not review things that have lots of unrelated changes in them and part of the reason for this is they might want to accept some of the changes and reject others。

They might not want your formatting change， but they might really want your feature edition。😡。

And so if you split these into multiple poll requests。

 then what can happen is they can review all of them and they can review them in chunks as they have time to review them and they can also merge the ones that are uncontroversial early and then the ones that require more debate。

 they can leave open， so that way you get your changes into the project faster and you get to reduce over time how much stuff still is remaining to be reviewed。

😊，嗯。😊，There's one piece of caution I'll give you here though。

 which is as you start doing more of this like let me try to actually do good technical writing。

 be it in comments or in git commitms or in readmes or anywhere else。

 there's a danger of letting the pendulum swing too far and starting to write too much。

It is very important when you write any of these things， any kind of communication really。

 that you try to respect the time of the reader， the reader will eventually see that there's too much text and they will read none of it。

😡，RightLike the way this scales is that they will if there's no text there。

 well they won't read it obviously， if there's very little text there they'll read it and then there's sort of a tipping point somewhere where they just go I'm not even going to be bothered or they read the first paragraph and then they stop and so when you write things that are intended for other engineers to write。

 think about if you were the engineer reading it， would you bother reading it and this is particularly relevant when you use LLMs to write things because LLMs are really good at generating lots of text as you usually need to be very specific with them to say make sure you've produced a concise summary。

 not a long you know prose that is going to go in there somewhere。😊。

Another aside here on why good commit messages are really useful is there's a tool called Git biect。

😊，So what Git by sec will do is imagine that you find some bug in some open source piece of software and you know that that bug didn't used to be there。

 like you updated the software and now it has a bug。

Git by sect allows you to basically say here's the version where the software worked correctly。

 here's the version where the software does not work correctly。

 find me the commit where the problem was introduced。The way it does this is it does a bisection。

 so it does a binary search by saying， okay， let me first check the commit in the middle between those now tell me whether the bug is there。

😊，And then if you tell it， oh the bug was not there。

 well that means that the bug must be in this range of commits so it finds the middle commit there。

 and then it's as is the bug here， if you say yes the bug is here where it goes okay must be between these and then it bisects and it keep bisecting until it finds the commit then introduce the bug。

😊，But if that commit is useless， like it had a commit message that like it doesn't explain at all why this change from A to B。

 or if it's a diff that just changes lots of unrelated things。

 the bisection hasn't really helped you all that much in figuring out what introduced this bug and so you have to do a lot more debugging。

There are ways to automate Git by Sect as well， so if you can reproduce the bug with a test。

 you can run git byect and pass it as script that has to exit with successor failure depending on whether the bug is there and then you can just run Git by S script and it will just run and eventually tell you the commit is here so you don't necessarily need to do it manually it's a very cool tool。

😊，嗯。So let's move on now to twoway communication or also known as collaboration there are a lot of different ways in which you will collaborate with other engineers up through your career perhaps the most common way of collaborating is contributions so this is stuff where you are making some change or submitting a bug report or something to someone else and they are the authority on the project and in the case of bug reports that might be they are the maintainer of the project in the case of a pull request this might be know you're submitting to someone in a senior engineer is going to review or change to tell you what you need to change before we get it into the codebase。

No matter what it is that you are trying to submit to someone who's in that position of reviewing or being a maintainer。

 keep in mind that there's sort of a there's an order of magnitude or more difference in the number of users versus the number of maintainers and this tends to be a real problem for open source projects in particular where there will be maybe even millions of users and they'll be like two maintainers or one maintainer this means that their time is very oversubscribed and so as a result you really want to spend the extra effort to make sure that whatever you submit to them is already in a place where it's an effective use of their time to look at it part of the reason for this is just to respect their time but the other part is sort of self-interested they will ignore your issue or pull request if it is not wellformed if they de that this is not a worthwhile use of their time they might simply close the issue or ignore it for your pull request they might。

Never review it or leave it off for a year before this start coming back to it， you know。

 until they have more time， which we all know you never get more time。

As a result there are a couple of sort of or there are a couple of tricks you can use here to try to make your contributions be more worthwhile not just see more worthwhile but also be more worthwhile the first of these is around bug reports Finally good bug reports is a skill that you will get better at over time but you will only get better if you try if you really practice there are some cornerstones of good bug reports that I think you should all know about the first is to make sure that you bring along enough context for someone else to reproduce the problem this usually includes things like the environment you're operating in like what operating system。

 what version number of the software the configuration files you have that sort of stuff The second is what you expected to see versus what actually happened right so a good bug report obviously need to say what went wrong but it should also say what you expected to happen because sometimes the thing that you observe is actually the intended behavior and maybe that intended。

behavior does not match what you expected， but that's not necessarily a bug in the software。

 it might mean that there's actually a bug in the documentation。

 it should have better explained to you that this is how the software works not that way。😊。

And that delta is useful to the maintainer looking at your bug report。You also want to give。

 and this is maybe the most important part of a bug report， the steps to reproduce the bun。

So this is usually like an ordered numbered list where you say open the program， do the thing。

 click this， type this into here， press enter and now the thing that I expected to happen did not happen instead did this happened so' a sequence of steps to reproduce the bug you should also include what you've already tried what things have you tried to work around the bug or maybe you've looked at the code and try to figure out what went wrong。

 tried to show them that you have also expended some effort in figuring this bug out。😊。

It's still useful to file a bug report， even if you don't have the time to dig into the code yourself。

 but if you can， it can be hugely useful。One of the best things you can do when filing bugg reports though is to make sure you could introduce a reproducible example。

 so sometimes that's just the steps to reproduce， sometimes if you have a dependency on some code project like as a code library。

 the reproducing example is often going to be code that you give them you say if I use this code with your library。

 it does not work correctly。😊，And if you just give a link to your giant project and say when I compile this。

 it doesn't work correctly， it will be completely useless to the maintainer right if you have like 100。

000 line codebase and you happen to use their project and you go my thing doesn't work。

 they're going to ignore you。😊，Instead your job is to produce a minimal reproducing example。

 so the way you do this is you start with whatever software you have and you try to cut away as many things from it as possible。

 such that only the things that trigger the bug with that particular software are included this can be a lot of work but it is effectively the work the maintainer will have to do anyway in order to fix your bug they will only be able to fix your bug if they can reproduce it themselves and so either you take the time to produce that reproduction or they have to find the time to produce that reproduction。

And given there are more users than there are maintainers。

 it is usually better for that to be you if you can。

Another common failure mode for filing bug reports to open source repositories in particular is that people don't search for whether there's already a bug report on the same thing。

 it is extremely common to see lots of bug reports that are all duplicates of each other。

This tends to correlate sort of inversely with how technical the users are。

 so the less technical the users are， the more of them file duplicate reports and also the more of them file comments that are just like me to or plus one。

 these things are just noise and the noise serves as sort of double negative here。

 the noise both makes it harder for other people to find whether there's an issue that is akin to their own because they're now way more issues to search through but it's also for the maintainer much more pain because they need to sort through all this noise to find the actual signal。

There's a third downside， which is imagine that there's a bug in some open source software that you make use of。

 and you go， I really want to know when this bug is fixed。😊，So you go and subscribe to that issue。

 so whether that's Gitthub notifications or you get emails or whatever it might be。

 you want to hear when this bug file gets fixed。And now you get hundreds of people filing comments on that bug report saying I also have this problem why hasn't this problem been fixed This bug has been open for two years now those comments are now going to email out to everyone who cares about that bug and just be noise there is no value in it the maintainers already know it's a problem because there's a bug report there the closest you can do here to be helpful is usually on at least on Gitthub issues there's a little like thumbs up emoji you can put on the topmost post and you can maintainers can rank issues by that that is the only thing that's useful in the context of plus ones。

If， on the other hand you provide something like I actually managed to create a minimal reproducible example for this bug or here's another way to reproduce it if I follow these exact steps I get the bug every time。

 those comments hugely useful and end up being much increasing the likelihood that the bug will actually be fixed。

And also keep in mind that because maintainers are volunteers at least much of the time。

 they don't have time when you have time， in fact， they probably have very little time at all and you really want to keep that in mind when you go。

 oh， why hasn't this bug been fixed yet？In general。

 try to give quite a lot of grace to especially open source maintainers because of how overloaded they are。

 it is usually not worthwhile to poke them the next day for hey。

 can you review this if you have a pull request to them？Instead。

 the sort of the etiquette here is more along the lines of， you know。

 it's fine to send a polite follow up like maybe a few weeks later。

 but there have been pull requests that I know have been made to my repositories that I have not had the time to look at for six months。

And that that sucks， I wish I have the time but I simply do not right and this could be because this is a project I worked on ages ago and I sort of cycle through when I use which project and there have been more important bugs in other open source repositories I maintain that I've had to deal with in the limited time I have for open source these days so it's not against that particular contributor but it's just that in the open source ecosystem we're relying on people's volunteer time and you want to keep that in mind when you interact with them yep。

What's a pull request again a pull request is when you submit a change to a repository to a code repository so someone else has a repository and you bring a Git diff to them。

 a Git commit or a set of Gi commits and you say can you please incorporate this into your project Is there online place that list a good example of a web report？

So we can like model ours after this is what perfect it like this so the question is。

 is there a good example of good bug reports， good pull requests that the yeah these are good the answer is that no there's not really a here's the one to go look at that said some of the exercises for today's lecture are find some and the reason why we've phrased it that way it speaks very often you can tell quite quickly whether a bug report whether a poll request is actually useful you can tell just by the way the maintainers respond to them as well and one of the best ways to get better at these is not to say here's a template that works but rather to see the interaction and then sort of absorb biosmosis like just learn from seeing the interactions and where there's friction and weather isn't。

😊，一。Some private boy。Yeah， so the observation here is that there are some projects that have their own templates you're supposed to follow。

 if you go to GitHub， for example， for many projects if you open a pull request or an issue。

 they will have a template that sort of auto fills for you and then they expect you to fill in certain fields。

Those templates are useful syntactically for making sure you follow the format they want for these。

 but they don't fix。诶。They don't fix the absence of understanding of what a good bug report is right they just give you the format and they fill in the blanks and you can fill in the blanks poorly or well and whether you fill them in poorly or well is going to depend on whether you understand what the purpose of a good bug report is and hopefully you have've conveyed some of that here that the purpose of a good bug report is to save the maintainer time in fixing it for you。

嗯。Now if you decide to open a pull request send in a change to a project。

 there are a couple of things that you should keep in mind so this is going beyond just filing an issue but actually contributing your own changes to the project the first as I mentioned is to read contributing Md which usually ask additional instructions here you'll also usually want to look at the license of the project the reason for this is because when you submit changes to a project。

 your change will tends to be sort of absorbed into the license of the project so if the project is licensed as GPL for example。

 you make a contribution to it when it's eventually merge that code is no longer yours。

 you don't have copyright over it， it now belongs to or is published under the same GPL license of the project was the same is the case for most other licenses you'll encounter in the wild and usually this doesn't matter to you but if you are an employee at a company for example it might because companies tend to care about things like if you like。

On company time， the company gets to decide whether to give away copyright of that code。

And so if you work in a commercial setting， make sure you do some checking here on what is the policy for contributing to projects。

 depending on the license they have。嗯。😊，When it comes to actually filing poll requests。

 the first thing to do is obviously the hygiene around Git commits and trying to make sure you split them as well and make sure that you file pull requests where each poll request is independently reviewable and useful in isolation。

😊，But the other thing that you can do is sometimes you have a sequence of changes where it's kind of like the project should either take all of them or none of them。

 so for example， this can come up if you had to change some deeper parts of the project in order to enable you to implement a feature。

 but if they don't want the feature， they also shouldn't take these lower level changes to the library。

And so in this case you will often open one pull request that says here's the feature and then you will have two commits in the pull request that are separate。

 and you say this pull request contains two commits。

 one that changes this stuff and one that builts on top of it。

 and you can even tell the reviewers know give reviewer instructions and say。

 prefer to review this commit by commit， rather than trying to look at the overall diF as one。😊。

And maintainers tend to appreciate this kind of review guidance because you as the author of the poll request。

 have a better sense of how it should be reviewed。And just like for commit messages。

 when you file pull request， you usually give a description of the pull request。

 you can almost think of it as like an email with an attachment that's a Git commitit right and you need to put in the email why you want or in the pull request on GitHub。

 why you want this change to go in， so this is not just why was the change made in this way。

 but why do you think the project should have this feature or bug change or documentation change？

Like why should they entertain bringing this di in？

One of the reasons why this is important is because maintainers accepting a pull request。

 accepting a diF and merging it into their project means that they are adopting responsibility for it。

 so if I'm the maintainer of a project and I take your diff that adds a thousand lines of code to my project。

 those thousand lines， I now need to maintain imperpetuity whereas you as the contributor do not you as a contributor are free to just walk away after you make the contribution and you got your feature and you're happy but as the maintainer I need to think about not just is this a feature I would like to have。

 but it's also this the way that I want that feature be implemented。

 such that I feel like I can hold the responsibility of maintaining it over time so that when I add other features down the line。

 they won't think conflict with this change。And so I need to think about all of those things in addition to just your change in isolation。

 and this is why it's so important to articulate why is this change worthwhile。

 especially if it increases the complexity of the project you're contributing to。

There is also another option here so if if you contribute to a project you find that the maintainer goes I don't want this change。

 they just say this is out of scope， this is too much。

 there's a feature I don't want whatever it might be。

 then you do have the option of forking forking is to take an existing project and making a copy of it usually under a slightly different name and then you now just start publishing this and maintaining that while they maintain the pre-existing project separately。

😊，Forking is a pretty expensive process it's expensive in the sense that you now have two projects each with one maintainer。

 but they have a lot of overlap and functionality and code and so you're now splitting that maintainer time between sort of two copies of the same code base。

 it also means that if one gets a pull request that makes an improvement。

 the other does not get improved。So in general， forking is sort of seen as。

Not as a no no but a sort of a measure of last resort。

 there should be a very very good reason why you say this needs to be a fork。

 the original project is like the scope is different from what I'm aiming for this will be a materially different project where this feature is important if it's just like I didn't get my feature in that's usually not a great reason to fork and also you will end up being unhappy about the outcome because if that's the only reason then you will now be the sole maintainer of this piece of software or this copy of this piece of software and you will have to maintain it for all perpetuity for yourself if you are the user of it。

Are you going to regularly check the original project and figure out what changes happen to it and make sure they can be merged into your project。

 regularly tested， regularly sort of do reviews of it， you're going accept contributions。

 you're going to debug bug reports that come in and fix them。

 are you willing to take on that responsibility？Yes。 anything ever say。

 if you accept my full request， I will maintain this part of the code and collaborate。 Like。

 I can't take on the whole project， but Im really just collaborate with whoever's making it。 I that。

So so the question is does anyone ever offer to become a maintainer of this part of the project that they contribute to and the answer is sort of split。

 it depends on the size of the project so if you look at the Linux kernel for example。

 the Linux kernel has lots of subsystems and the different subsystems have different maintainers partially for this reason so the maintainer of this subsystem is the one who cared really deeply about the subsystem either because they used it they wrote a lot of it or whatever it might be and so if someone brings in a completely new subsystem they will sort of there's almost an expectation that at the very least you should be willing to maintain it over time for smaller projects is tend to be less common and one of the reasons is。

It doesn't really work if you have a 2000 line project if someone says。

 well I'll be the maintainer for these 50 lines right that doesn't really make sense because usually as you change your codebase over time。

 those changes tend to diffuse across the codebase。

 it's not as though a feature is just like a contiguous block of lines that will never change again。

 and so maintainers of just one part tend to then miss the whole。

 it also like having multiple maintainers comes with a lot of coordination overhead that usually projects don't want unless that coordination overhead buys them a lot such as a full new maintainer。

😡，That said， making contributions to open source projects is often the best way to start to sort of step into becoming a maintainer for yourself。

 usually the people who become maintainers of open source projects are the people who have contributed the most。

And eventually， you might even get to the point where the maintainer of the project says。You know。

 I don't have time for this anymore， but you've made really good contributions。

 are you willing to step up to be the maintainer and I will step back？But again。

 you only get that offer if you have proven yourself to be a trustworthy and good contributor over time。

 a reliable contributor over time。Now， AI obviously enters into this as well， because you will see。

 especially when you do the exercise here， that as you explore open source projects in these days。

 there is a huge amount of pull requests that are generated by LLMs。😊，Some of these are useful。

 most of them are not， but that is because people tend to。

 if they make LMS's file pull request for them， they tend to not really act as a filter on those pull requests。

 they just say， I want this feature implement it， make a Gi commitit and make a pull request。

And what you end up with are usually pull requests that are not particularly well structured。

 they're not minimal so they tend to be， you know they tend a bunch of other things that are unrelated to the change。

 the description of the why is not particularly good。

 and also when the maintainer asks why did you change this， why did this have to change。

 why didn't you change this， then the human who has to respond to the comments。

 the author of the pull request？Often doesn't have the answers because they didn't make the change。

 they don't actually know why it chose to do A over B because they just automated the production of the change。

So very often you'll see that open source maintainers are pretty skeptical of AI written pull requests。

 that doesn't mean that you can't use LLMs to help you make the change quite to the contrary。

 they can be very useful for that， they can be useful for writing good Gi commits。

 they can be useful for writing good pull request descriptions。

 they can be even useful to address comments from review， but you have to be part of the process。

 you have to make sure that you understand both why the change is needed。

 why it had to happen this way， because otherwise what are you contributing to this process。

 that the maintainer couldn't do themselves。If all you did was describe the bug and say fix it and press enter。

 and then it vomit it out a bunch of things and then you paste it in a pull request。

 the maintainer could just as easily have done that themselves。

And chances are they didn't for a reason。It is true though。

 that there are a decent number of open source maintainers who don't really use LLMs very much and as a result。

 maybe they hadn't thought to do it themselves， but it's unclear that you giving them a sort of quick and dirty pull request so you haven't even looked at yourself or you haven't thought through the changes that that will give them a favorable view of starting to do that themselves to speed up fixing bugg reports over time。

Now the next step here in collaboration is reviewing reviewing code is something that we tend to think of as like juniors submit Pol request and then seniors review this review them and then tell them all the things that were wrong until the poll request becomes good。

 but that's not really what reviews are intended for， nor is it how they usually tend to work。

 reviews are just an asynchronous way for us to talk about code。

 they are a way for someone to propose to change and someone else to think about that change and then talk through almost like if you were in a brainstorming session。

 what is good， what is bad about that review。And and。Unfortunately。

 I think partially because of this mental model of there's like someone senior to you who's telling you what's wrong with with the code you wrote。

 because of that mentality， reviews have gotten this kind of weird language almost that's used that feels。

我。Derogatory is too strong right， but it feels judgmental。

 reviews can often feel like oh they're telling me everything I did wrong。

 and it's very important that to remember the code reviews aren't about the person writing the code。

 they are about the code itself， they are about whether that code makes sense in this project for that purpose at this time。

And so when you have to do review and you will find that reviews are something you will be asked to do much sooner than you might think。

 even if it is just a group project in your， you will be reviewing each other's code or at least you should and part of this is because it's a great way to learn reviewing others people's code lets you both identify mistakes that you then hopefully don't make yourself but also see really good code patterns so you can learn from and it lets you read more code so that you now know about more concepts。

 it is a great way to expand a lot of your abilities as an engineer。

 it will serve you very well for a long period of time。But when you review。

 there are a couple of things that I would recommend apart from just remembering that you're reviewing the code not the person one of them is to prefer actionable comments。

 so when you write a review for someone you can imagine that on a like let's say in Python or in JavaScript you can have variables at the top of the file that are global they're known to be they're known to the entire program they're accessible everywhere in the program these are usually in anti-pattern you don't usually want to use these because they make testing harder for example you can't run two tests in parallel because they're going use the same global and get confused because they' both write to it and both read from it so imagine that someone used a global in a pull requests that you're reviewing。

You could review that and say， you know， put a comment on that line and say， don't use Gos。

But that's not actionable， that doesn't tell the person who wrote the code what to do instead。

It also doesn't even tell them what they did wrong if they don't know about this particular advice around globals。

 and so a better review comment here would be， can you please replace these globals with a config data class because that way we can run test in parallel？

This is not that much longer to type， but it is hugely more helpful for the person contributing the code。

It also means that they can respond in a more useful way if there was a really good reason why they were using globals here。

 maybe they're an extremely experienced developer who looked at your code like actually this needs to be a global and arguably they should have left a comment for that because it was like the why not kind of comment but they didn't。

 but that lets you start a conversation， if your conversation starts don't use globals。

 it is not a particularly positive place or constructive place to start the conversation。

And a related thing is that you generally want to ask questions rather than make demands。

 so rather than say， you know， handle the null case。

 you could say what happens if null is passed here？They mean the same thing。

 but one is a much much more collaborative tone than the other one judges the person like why didn't you think about the fact that there could be a null here。

 the other is while reading their code I was like oh wait what happens if there's a null here and then you can leave it to the other person to realize。

 oh right that's wrong， thank you for reminding me。

And that makes a huge difference to the experience of the person making the contribution。

 and especially in open source projects， it also increases the chance that they might come back right。

 whether that is they actually address your review comments or whether they submit more changes in the future。

 maybe if they decide to eventually become a maintainer。

 if they leave with sort of sour feeling after every review， they're not going to come back。😊，U。

And then the other thing that you perhaps obviously want to do is you want to explain the why you want to explain why you think something is a great in the review。

 so the example here again of the global explain why you don't want to use globals。

 why for this project have you made this decision because they might not have that context。😡。

The other thing that people tend to make the mistake of when doing reviews is that they leave far too many comments。

If you leave too many comments， the person will not get to all of them。

They will just get tired and walk away if it's their job， then obviously they will。

 but they will still put it off not to mention if you have lots of comments。

 they don't know which are the most important and sometimes changing one thing is going to make some of the other comments just。

Invalid now because that code also had to change and so it tends to be that if you leave 100 comments。

 then only 50 of them are useful to address because the other 50 are going to be relevant by the time those first 50 have been addressed same thing with if you spot a pattern that is like repeated of like I don't know。

😊，The way you want certain variables to be named， if you leave a comment on every single variable。

 you want to be named differently。That's not， that's just noise， it's not signal。

 it's usually enough to leave one comment on the first one saying this is the kind of variable naming scheme that we use in this repository。

 please make sure you use it across the code base。That is a much more actionable comment。

 and it's also much more useful than pointing out every single place where they made a mistake because again。

 it feels like you're just sort of hammering them while they're down。You also want to。

 if you leave a bunch of comments distinguish the ones that are blocking from the ones that are not。

 so usually when I do a review there'll be some changes where if this change isn't made。

 I will not accept your change and there'll be somewhere I would prefer to do it this way but if you prefer this way that's fine。

And it's useful to distinguish between the two because that way they can do triage。

 they can basically prioritize which things they address first。

 it also means that they can do the blocking ones and then we can do another iteration of the review where maybe some of those nis have gone away。

😊，The way this tends to be done in reviews is that if you have something that is not blocking in the comment。

 you write ni Col and then you write your comment。So it's specifically something that's left up to the reader。

嗯。😊，The other thing that I really want， sorry， yes， go ahead。The needss go on。

ASo if if you have a comment that is not a blocking comment so something where take it or leave it。

 it's fine if you don't change this， you can write knitt colon to indicate and so a knit in English is like a thing that's not very important it's something small。

 something tiny insignificant and so it's a knit not it's not blocking it's not a large comment。嗯。

And then the last bit is and this I think is forgotten a lot is that code review viewers tend to focus on the things that have to change。

 they tend to focus on you didn't do this right or this part of the code needs to change or use a different data searcher here。

 they tend to forget to point out when things are actually pretty cool。

 when someone did something in a clever way when they made a really good choice。😊。

And if you think about talking imagine like pair programming， or if you're sitting with someone。

 you're programming something together and you're like one person's typing something and maybe you switch the keyboard over or you're just one person's typing to other person talking。

 but you're interacting with like a human in the flesh and you're working on code together if every time you opened your mouth it was to say that they did something wrong that would not be a particularly enjoyable experience so why should code reviews be any different they shouldn't if in a code review you find that they've made a really good choice then call that out。

 leave a comment and they can easily like they don't need to do anything with that comment。

 they can just hit resolve， but it makes their day a little bit better。

 but it also means that the code of view feels more balance。

 it means that they walk away feeling better about the change that they contributed and they will feel more empowered to make the changes you ask for because they recognize that they also did a good job。

And obviously you know these days we have a lot of people using AI tools to do reviews that can work really well I'm not claiming it can't。

 but it can't really substitute human review one of the reasons for this is at least for now when LLM's review they tend to do what we call zero context reviews or contextfr reviews so they review the change based only on the description of the change and the diff of the change and they sort of review that the reality is that when you review code usually most of the comments are not really about the diF there will be some obviously but the more important comments the thing the review is really therefore is to see whether this change is a good idea for the overall codebase is a good idea for the direction of the product you're building or the direction of the application。

 whether the library should change in this way whether this change is like backwards incompatible with the versioning scheme and you're not。

To make a breaking release and those things， the the LLM。

 the AI reviewing the code will not have the context for and so usually LLM based or AI based。

C reviews are a useful tool， but you should not think that just because it is happy with the code。

 the maintainer will also be before can you feed in context to AI before it reviews you can to an extent this is where at least in my experience we tend to hit the sort of boundaries of what AI is able to do of there's a reasonable number of things where it doesn't understand the problem。

Like you can give it lots of context about teaching about breaking changes， for example。

 that it doesn't necessarily understand what a breaking change is。

It's able to syntactically represent it in English， but that's more of a pattern repetition。

 but it is an understanding of this project's breaking change policy。theEven if you give it examples。

Do you see AI change， able do that。Well， so this becomes a question of like what do I think that the current AI approaches are on the path to AGI。

 which I do not， but that is a separate discussion we could have apart from this。

 they can be super useful， but I don't think it's just a matter of we just need to give them more context and then they can give us perfect reviews。

诶成 yeah。The next thing I want to talk about is education so you know we've talked now about one- way communication we've talked about two- way two-way communication now let's talk about education a lot of our noncoding time as engineers is actually spend either asking or answering questions from other people and this can be just our mentors it could be our teachers it could be Ts it could be other students that know something that we don't or they've solved the lab and we haven't and education whether it's sort of taking or receiving is something that is super useful to get better at and it genuinely is something you can get better at in fact one of the things that I wish more people would do is to learn how to get better at asking questions you can also learn to get better at answering questions but that tends to sort of be stage two stage one is how do you ask good questions in such a way that you get answers that are useful to you there's some really good blog posts that are linked in the lecture notes by Julie Evans so I highly recommend you read。

Otherwise' sort of a quick summary of what you get here。

The first is a state you're understanding for a state what you know， tell the person。

 here the things that I've figured out， here are the things that I've thought about。

 here are the things I know。Before you start asking your question so that they know what they don't need to repeat。

The second is to ask yes no questions and this is maybe counterintuitive right in general we tend to think oh we need to ask a question and then let them give us all the detail。

 but it's sometimes more useful to probe the questions specifically so that you don't end up on long tangents that you don't care about or than the turnout not to be relevant to your question if you ask yes no questions you will very quickly get to figure out which things you have understood correctly and which things you have not。

😊，So a sequence of yes， no questions can often be more useful to you than letting them give an open answer。

You'll also want to be specific about these， so you want to give us put as more detail into your yes or no question so the other person either can give a clear yes or no or can learn from your question what you have misunderstood and then be able to point that out。

Similarly， when you ask questions， you want to explicitly admit the things that you don't understand if you try to like pretend that you understand when asking a question。

 then you will not get useful answers because the other person can't calibrate to what level you're at in the different sort of knowledge buckets。

The reason you're asking a question is because you want to understand more。

And this relates to the next point which is to not accept incomplete answers。

 a pattern that I see quite a lot is people who ask questions。

 they get an answer and then they don't want to bother the person anymore。

 so even though they didn't understand the answer they go okay， thank you and then they walk away。

You should not do that because you did not learn anything and this sort of ties into if you ask yes& no questions。

 you're obviously going to ask more than one question because that's the only way you're going to get to more useful details。

And you really want to train yourself to not accept the answers until you feel like you've understood。

 or until you've clearly oversstateayed your welcome， that can also happen。

But but also remember that when you ask questions， make sure that you do some research yourself first。

 if you ask questions and you've done no thinking yourself， no googling， no searching yourself。

 then the other person， they will probably help you if you're their nice person。

 but they are going to be a little bit annoyed that you didn't do the minimal amount of work yourself。

 because sometimes the questions have obvious answers。

 like you Google it or you ask an LLM and it will just give you the answer in like three seconds。

 and that can often be a much better way to spend people's time than for all of them to come and ask the same question that had a trivially findable answer。

Yes。They also remember that these apply just as much when you're asking LLMs than if you're asking humans right。

 so LLMs also work better if you're able to give them specific questions where you tell them what to know and you don't back down just because they gave you an answer and you probe them with the S&O questions。

 all of these are good advice there as well。They also apply when you ask questions in public forums like on Sta overflow。

 if you follow these guides， you will ask better questions， you will get better answers。

 but also the people who come after you who go back and have the same question you have and find your thread on stack overflow or on a forum。

 they will learn more from the questions and answers as a result。

 so this ends up being a sort of rising tide lifting all boats kind of affair。Yeah。

Well the tail end of time here so the last thing I want to cover is AI etiquette。

 this is pretty fast， so we've seen increasing growth of LOMs and AI across all of software engineering and arguably across much of society and the social and professional norms around the use of AI。

 we haven't figured out yet， they're still evolving， they're still in flux。

 we've already covered a lot of the tactical consideration in yesterday's lecture about agenda coding。

 but there are a bunch of softer parts of them that I think are worth discussing。😊。

The first of these is that when you use AI in whatever form you use AI to contribute to your work。

 then you need to disclose that you've done so。And this is not just about sort of like it's not about shame。

 right， it's not even about intellectual honesty， it's more about setting expectations for your output and ensuring that the resulting work gets the appropriate level of review。

So if you don't disclose， you've used AI， but a bunch of the code you haven't really read or you haven't really looked at or you don't fully understand。

 then it's important that someone else knows that so they know to apply additional scrutiny to that part before it gets accepted。

Similarly， there's no problem using LMs， I've been using LMs to code for like several days now on this giant project I have to do for work that is like LMs are perfect for this task。

 I have no shame about using LMs for it because it's right for the task。

But it's also important that at the end of it， when I say here's like this giant code base I've ended up generating that I'm open about。

 I have not read all this code， right， this is the starting point for something that we will then sort of polish into something we can actually use commercially or in production。

But the starting point needs to be obviously labeled as being sort of AI assisted。

And it's also useful to say which parts you used AI for and which parts you did not right so if you just said I used AI in this project。

 that's not particularly useful to someone trying to figure out which things they should review or which things they should be skeptical of or just which things they should expect a higher quality bar for。

If you say， you know， I used LLMs to generate the test cases this for this project。

 but I didn't use it to write the actual code or I use it to generate the。

The UI front end for my thing， but the back end I wrote myself that those are meaningful distinction that is important to be open about。

You'll also have to follow the norms and expectations of the teams， companies。

 projects you work with， especially in open source。

 but also commercially you will find the different companies and different projects have different preferences and sometimes even pretty strict guidelines about when you are and are not allowed to use AI and what you're allowed to use it for and sometimes this is for really good reasons sometimes this is like we cannot use AI here because we would be violating the law like we are not allowed to have this data escape out of the confines of the company whereas if you're using like energetic LLM it might actually upload it to a cloud service that's outside of our control it's can be true for example for health data。

 financial data all of these things where that data is pretty tightly controlled and you don't want to run afo of the laws here so be mindful and sometimes it's not about the laws right it's just about being contributed to the respects to the wishes of the developers of the project you work on it can go in either side of that spectrum。

But make sure you familiarize yourself with what the preferences are of what you work with。Also。

 remember that if you use AI and LLMs to develop things， you will learn less from the process。

There is a huge learning element in doing the work yourself you get some of that from using a coding for instance like you definitely do learn from it。

 but you will learn less than if you also wrote all the code your code yourself but it's a tradeoff you're making where do you want to spend your time and sometimes you don't want to spend your time writing all the code and that's fine sometimes that code you don't think you would learn that much from anyway but should be an intentional choice and intentional tradeoff that you make rather than just I'll just let it spit out all of its stuff and I'll hopefully learn some things by prompting it you will learn some things but there are some lessons that come from writing the code yourself。

And then finally， this also comes up in interview and assessment situations。

 be that at university where you're taking exam or at a company where you're interviewing。

 there has been a sort of increase in people who want to use AI in its various forms in those kind of contexts and here it is much more debated whether that is。

😊，Like whether that should be allowed， whether that's okay。

 but also whether it means that you're no longer evaluating the person。

 you're now just evaluating the LLM here too， make sure you familiarize yourself with what expectations are set by the evaluation scenario you're using。

 like whether that's with the company that's interviewing you or with the university that's evaluating you。

 make sure you know what the expectations are。And obviously。

 if you're unsure if there's no stated guideline， then you know use your best judgment and prefer to ask again。

 this comes down to the disclose side of things where if you're using that's not inherently bad。

 it's not inherently shameful， it is just something that you need to make sure the other side is aware of so they can take it into account when they evaluate the output of your work。

Okay that's the end of the lecture today the one thing I'll say at the tail end here is we have a Q&A lecture for part of the lecture tomorrow。

 if you have questions that you want to have us answer in that Q&A session there's a link to a Google form on the lecture notes for tomorrow lecture。

 please use that to submit to your questions ahead of time because we expect that there'll be quite a bunch of them so we need to prioritize and sort a little bit we probably will not take too many live questions from the room depending on how many questions come in so please use that form if you can。

😊，Thanks so the lecture tomorrow is going to be the same length as a normal lecture I don't think it'll go longer we'll have to see I also have a plane to catch tomorrow so hopefully it doesn't go too much longer but we'll see so the first half of the lecture is going to be on code quality and then the second half is going to be on tuning。

😊，No， at 130， it was only the one lecture that was at three o'clock。

Let me double check that I'm not lying to you here， but I don't think I am。Yeah。Yep， it's at 130。

 It was just last Friday because of mystery Hunt that we had different time any any questions here in the room while we。

Cool， thanks see you tomorrow。