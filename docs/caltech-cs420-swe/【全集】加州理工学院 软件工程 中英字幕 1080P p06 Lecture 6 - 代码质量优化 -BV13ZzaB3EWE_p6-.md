# 【全集】加州理工学院 软件工程 中英字幕 1080P p06 Lecture 6 - 代码质量优化 -BV13ZzaB3EWE_p6-

II this whole thing。Hi， good afternoon， everyone。We are here from De part one。

 Miguel me and Jesen and we are going to have a presentation about code quality and what we're going to learn on today's presentation lessons so we're going to learn what is code quality and why it is important and definitely will go with some other code quality tools will have some handsome experts and example of eight and then to begin my friend Jasonson will start with。

Some story， and then'm gonna to go that。So we have a gallery of bad code here。

It just examples of poorly names code， no documentation on it。

Dable names being bad that this been open。嗯就先。

![](img/282de5f04e4cc7925fae63a5298ac5c1_1.png)

嗯。对，我对。放的没。So。Here's an example of some。battle。Okay， you know it's great we're doing it live。Oh。

I have no idea wrong with this what。The jobscript there。ItWhat I was about， for example。

Third on one slide with。

![](img/282de5f04e4cc7925fae63a5298ac5c1_3.png)

早啊。This is pretty simple module。If you didn't see simple calculator here you。Hi。

 you would have to sit here and Sarah this for a while of period does。

So you have function here is called AS。And do you see。

So if you just looked at this without any documentation we kept these variable days。

 you had a difficult time kind of figure out what they all did。哦。没问题。

So what we to do to put this on code is come back and rename。All these functions and variables。So。

It死你。We response of towards to our points。我么回事。Actually， I have it right here。

So this is the same exact module， but you can see I would have renamed all the functions and。

No I did only use a fire they use or。最主选择这。So now you can see it's an add not to fact multiply the bottom。

嗯现在休息。🤧嗯。😊，598。We'll get to all what Island is。对。

![](img/282de5f04e4cc7925fae63a5298ac5c1_5.png)

But it's a link tool that will like a that roller， thatll go over your code。See y'all。

 I's tell you we can improve on。目这为事。嗯。So code quality is essential for developing， maintainable。

 readable and ever free software， basically like I said， it makes your code easier to read in all。

It identifies potential issues early and enforces coding standards use all every every language will have its own namem and conventions and stuff。

哦。We'll also show you how to integrate it with your。So。You know。吔屎。

Poor code quality is an umbrella term from multiple issues with the code base。

 code that exhibits bugggy behavior， slow implementation。

 messsy code with thigh coupling and low cohesion， aK spagheti code。

 I think we've all seen that unmatainable code and usage of obsolete libraries and frameworks。

 code repetition that leads to costly refactor。嗯，好的。So。I'm going to cover Soar cube。

 it is a piece of software that's meant to check over and check the quality of your code via setting the logic。

 well， not logic， but like setting gates that checks and verifies。

If your code meets the standards of the。Prerequisites that have been set by the person who set up the Soar Chief server so it checks for vulnerabilities。

 it smells the code and it checks the standards as said you can integrate it with your repo so that it checks that live and it also spams your email anytime somebody does something that you don't want them to it will say hey this person sent out bad code that may either be an optimize or not format standards and will either you can either set to reject that push or you can。

Allow it to go through but it's in your email a box highlighted that's just one example of what it does。

Since it's a。Server， you can have it both for local instances or you can have it running off of your own network server that you connected to。



![](img/282de5f04e4cc7925fae63a5298ac5c1_7.png)

So I'm going to run through a quick example of how to get it set up。It's very finicky only because。

It's， you can tell it's made for。Industry it's not real user friendly like the first file you get isn't even in the solar it's not as clear cut as anything like Vs code or anything where you just run an ec and everything works know you need to set this up yourself you need to set the configuration files you need to tell it what Java version you use and you can use the wrong way so we're going to manage we're going to try to manage do that here in this instance so i'm going to open up the location and this is。

The file that you will have。I hope everyone else on Zoom can see that。

 but you'll start out with a zip file， obviously it's already extracted and sonar cube 10。7。

Whatever version is already pushed out， I'm going to open PowerShell。Because， I mean。

 I could do it through Git， but I don't remember the commands to do it to Git since I did it through PowerShell myself。

嗯。So we're going to navigate to。That。Directory。Once it decides， there we go， take that input。Okay。

 so。Before doing this。You want to tell it。What Java version use？嗯。And there's a command for that。

Thank。Yeah on my notes that I can't access right now。那个能。嗯。And that command would be。Well。

 first you have to find。The location of the Java instance。That you're going to be using。

 or I should say double version， it's still going to be an SDK。So oh yeah， that's another thing。

 it has to be the SDK， the links on the PowerPoint slide on the backgrounds。So。I believe it's under。



![](img/282de5f04e4cc7925fae63a5298ac5c1_9.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_10.png)

It's going to be under your drive。In your programs file， that's where it lives in your user profile。

They can find that program file。了解这东西发过。Ne needs to be in theflow， ourflow as。没见。Yeah。嗯。Oh wait。

 I'm ahead of myself， I didn't need to go into the user profile。

 it's in program files under the Java program。And here's the J JDK will be using。嗯。

We don't need to navigate exactly the where it is。That's why the autofill on this exists so。

With the command。嗯行。嗯。叫个。And the JDK location。This。

This command will tell it to look for this specific version of the JDK and run the instance office。

So it's been applied and set。Oh well， I mean， yeah。

 I need to get rid of I need to actually name the file what it's called and。

Make sure that is not there。There。And once that's running。We can now finally begin to。

Sign our server up。So we'll navigate to Sunar tube， we're already in the file from when I started。

请紧少。We're going to list out what's in it。So we're going to go into the bin。Once in the bin。

 we're running on Windows， so we're going to go into Windows。And within。

This file is the batch file that you can start the server instance on so。We're going to run that。

If it allows me to in possible。There you go。Now you can tell it where the JEK is for Java on the properties folder of sonar itself。

 but I had like a 5050 win rate on that， whether or not it would actually tell where it is it's currently executing right now。

 but this is an I3 computer so it might take a moment。Okay， so yeah。

 you see it starting the instance。Srings。So from here。

 it actually lists the HttP of the sonar server， so you would use that to connect to。

The sonar cube interface locally through your computer。So I know it's not done yet。喂。

I'm going to preemptively plug it into the browser。



![](img/282de5f04e4cc7925fae63a5298ac5c1_12.png)

一到是先是谁世好。

![](img/282de5f04e4cc7925fae63a5298ac5c1_14.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_15.png)

And I'm going to check back on status。So I'm pretty sure elasticasticSe that process is looking for the JDK。

 which we pointed to earlier。When it finds it， it's going to start running it。And。

We'll then be able to access so， okay， there we go。And。In a start。你咋个工。



![](img/282de5f04e4cc7925fae63a5298ac5c1_17.png)

Let's see if it works。

![](img/282de5f04e4cc7925fae63a5298ac5c1_19.png)

Okay， it did not launch。And you could take the time to debug that but。

It might be blocked by the firewall， but since it's a local client， I don't think it is。

 I'm going to run through though。嗯。嗯。And see if my is still able to run。嗯。



![](img/282de5f04e4cc7925fae63a5298ac5c1_21.png)

Okay， that instance also doest wrong。But there is a backup， I do have some videos pointing out。

Of what it should look like。

![](img/282de5f04e4cc7925fae63a5298ac5c1_23.png)

So。

![](img/282de5f04e4cc7925fae63a5298ac5c1_25.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_26.png)

I'm going to mute the audio because I really only care about the interface itself。

 which you wouldn't be able to run unless you have that process。



![](img/282de5f04e4cc7925fae63a5298ac5c1_28.png)

Active on the computer。啊。So。

![](img/282de5f04e4cc7925fae63a5298ac5c1_30.png)

呢首嘅少。

![](img/282de5f04e4cc7925fae63a5298ac5c1_32.png)

There's on the problem with all name。

![](img/282de5f04e4cc7925fae63a5298ac5c1_34.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_35.png)

This is a set of video， which it's what we just did， we ran it。their instance was successful， though。

 the specific JDK versions that I just went over。And this is what that interface looks like it's dated because this is what it looked like three years ago。

 but it looks similar as it is currently。On screen。Now。Under here you will see projects， issues。

 rules， quality profiles， quality gates and administration under each corresponding tab。

 that's where you would tweak the settings for the gates。

Obviously you can see that it has integration for Gitlab。

 GitHub and I think they added Azure recently and he bucket was I guess prominent three years ago。

 I don't know if they support that anymore。

![](img/282de5f04e4cc7925fae63a5298ac5c1_37.png)

We're going to go back to this slide。This video is an instance of the quality analysis。

 which well reference in a bit。So。This is a g of what customizing the quality gates should look like。

If it runs。This for center。是的。But essentially what you would do here is。Navigate under the projects。

No not under projects This is the modern bar I got this working on a local instance on my desktop at home as you can see it's the httP address mentioned earlier and you would go under the。

诶。The quality gates up here in this part of the banner。嗯。And you get to set custom values in like。

Coverage is one attribute you get to set it's just saying like。

How much of this code was checked or was able to be checked by sonar cubes？嗯。And。

There's also another attribute where it checks the， I believe。

 the optimization of the code and you can also tell it a template for what the code should look like。

不是。你食佢。那拜不行。I just feel if we will put in sense。So integration with the CICD。



![](img/282de5f04e4cc7925fae63a5298ac5c1_39.png)

What you would do on your GithHub？

![](img/282de5f04e4cc7925fae63a5298ac5c1_41.png)

And since GitHub always runs， can I will actually be able to go over what you would do。

To see if I can open up a on queue the instance。

![](img/282de5f04e4cc7925fae63a5298ac5c1_43.png)

Let get a around。我马 show。

![](img/282de5f04e4cc7925fae63a5298ac5c1_45.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_46.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_47.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_48.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_49.png)

there you go。This is what it running with GitHub looks like。

But I wanted to go to the previous slide because I'm pretty sure it had something I wanted to show。嗯。

There we go。These are the quality profiles that are preset based on whatever language you have set。

So I'm going to see if I can present to the front slide。😔。



![](img/282de5f04e4cc7925fae63a5298ac5c1_51.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_52.png)

这能不见来。

![](img/282de5f04e4cc7925fae63a5298ac5c1_54.png)

So。Through Git you'll be able to set a YMl file UM it will set the properties of the action like through GitHub actions and run the configuration based off what you said it as based on what you put into UM you can。

Identify whether or not you use the mevyn or any other code quality。Review method。

 these are established， I believe in the industry。And they。

Are just different ways that SoarQ would check for that quality？嗯。

The reason why I mention it is because。On the slide I want to present。



![](img/282de5f04e4cc7925fae63a5298ac5c1_56.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_57.png)

嗯。系 so。We covered this a bit of code already， that's the someone I had opening it up。Viual studio。哦。

Let's see so you asked what a letter was， a letter is a tool that analyzes code to detect potential errors both styllist admissions and violations would code the same。

I also checks text for all our syntax， now enforcement error detection and improve consistency。

 as you see it like a my roller。Or that's where it gets its name。

Oh the different name conventions so every language kind of has its own it's set up by the community and kind of。

By language。They're not exactly enforce， but it's good to have some type of standard so everybody can look at something be like。

 oh I know exactly what that variable is just based on its own。我哋就 case。So like I said。

 different languages have their different naming conventions。

 Python uses Pe is that as pronounced Pe style online， which is snake case。

 which is lowercase underscore second part of the word Pascal case where you have the capital letter。

 then you thenote the second word by another capital letter， and youve got screaming and snake case。

 Java， you have Campl case， Pascal， and also screaming case。哦。Ohm sorry。

 it's just when it's all caps separate about underscores。That's used from all constants。

you can go to that website havetPython。org。If you click on， I'll bring you to this。

And as you can see， they have a bunch of。Different all categories you can look at just to see what the guidelines are。

But just the key parts are your ination rules instead of tab and they want you to do four spaces。哦。

Everyone line has a character limit just so it doesn't extend too far where you have to scroll re page you see the rest of the code。

啊。And for blank lines， it's the space in between your functions and different lines。

Pyent is an example of a Lint tool， it's deals with Python。

 as you can tell about the P prefitx the Li。Yeah， like like you said， 100 times already， it's。

Checks for errors， code and standards and it smells the code。

 which means it can look at the code and kind of。I understand analyze it without running the code。嗯。

Yes。So to install pipeline。哦。You open up your terminal and you run pi M。

This supposed to be a give okay， so our gifts are kind of broken in presentation mode you can see use that command right there and'll install。



![](img/282de5f04e4cc7925fae63a5298ac5c1_59.png)

You are。呃，跨我。And that's what it should look like when you install it。是。I'm sorry。哦，你说咗。Im sorry。

 this had you installed pit my better。 I gotta have myself。Oh。

You have to have P install to install a Pi。This part right here is shown that I had Python 3。

96 installed， then you installed that's my benefit thing。Now we install our pilot。

Use P to install pilot， like I said。And this is what it should look like。我全 install it。

And then tells you upgrade it， but back worth that。嗯。

And an alternate version is if you open up visual code。

 you can add extension called P and what's cool about this is that you can I'll show an example later but it'll highlight exactly where your code's messed up and it'll pop up with the error code you can click on itll bring you to the documentation。

 explain what's wrong with your code。Here's a short short little class ahead its just adding two numbers。

I run piloty just to see where I'll explore just on what four lines of who。 so if you grant it。

 I have 10 and 20 in there you have 30， which should be a result。So this is where I check use file。

And we can see I scored at 2。5。It two。八 of。So it tells me right here this mono doctoring。

 this function meing and having the constant result doesn't conform to their standards。You know。

 like I said， you can go to the website right here。

I'm not going to give this a laptop so it's the last lead。

And make move so that you change the device but each working we are so sorry we like these device had perfectly for those daily version 17 plus。

So，那 this word。I was interesting sorry was demomo will not be able。

 but others be able to work properly on this。I think I' no， no， no， I have some gifts later on there。

真的谢谢啊，谢谢。😊，哦，十分钟没两太度。对。

![](img/282de5f04e4cc7925fae63a5298ac5c1_61.png)

嗯。

![](img/282de5f04e4cc7925fae63a5298ac5c1_63.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_64.png)

You don't conquer that。

![](img/282de5f04e4cc7925fae63a5298ac5c1_66.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_67.png)

![](img/282de5f04e4cc7925fae63a5298ac5c1_68.png)

I believe I have a picture of it， so I'm not going to go you that we're on a new laptop I thought can。

四得。No， okay，你 never。Yeah， I didn't control out it doesn't pop up。



![](img/282de5f04e4cc7925fae63a5298ac5c1_70.png)

That's good。No， I have a picture of it later on。Just that you going right now。Yes， broken。



![](img/282de5f04e4cc7925fae63a5298ac5c1_72.png)

O。So。As you can see， you have your oh oh I think you can't see the entire itself。是。



![](img/282de5f04e4cc7925fae63a5298ac5c1_74.png)

喂啊，O。screenIn a screen screen live。I know that's just sharing with the Zoom let's just go back to this。



![](img/282de5f04e4cc7925fae63a5298ac5c1_76.png)

That's what that's what it was on before right oh yeah， okay。

 I haven't had a picture and we'll be fine。Now where's the PowerPoin。Is that more okay？

So this is the website， as you can see you have a fatal error warning convention rera or rera and information if you go back to our error code。

嗯，嗯 the7。

![](img/282de5f04e4cc7925fae63a5298ac5c1_78.png)

You can see the prefi right here， C0114， the C telling us， it's a hub。



![](img/282de5f04e4cc7925fae63a5298ac5c1_80.png)

It's a convention error。Yeah， I forgot y'all can't see my mouse anymore。

We used the website and I went down and found the Eric code C0114 and then it'll even show you an example of what he's looking for it's look for dos。

 which is inosing triple quotes。And that's like in Java doc when you just explain what a function or method does。

那听减少啊嗯。你睇嗰啲。I don't think that oh， okay， I' see no， oh， oh， that a laser pointer。Yeah， okay。

 that's cool， all right。All right， moving on。

![](img/282de5f04e4cc7925fae63a5298ac5c1_82.png)

So I went back to our simple method we had adding our simple code we had I just said， hey。

 this module demonstrate create a simple function for adding two numbers。啊。

So a doc ring is a special type of document， like I said with like Java doc where you're just explaining what that method does。

And given that I got a 2。5 out of 10 last song by just adding that little doc string。

 what do y'all think we're going to score next， how many points y'all think we went up？Three over。

 anything under over。All right， we went up 2。5 points so we're walking five out of 10。

So just by adding that one little do ring but I think we could do better so this time we're going to use visual studio code。

Like oh， the extension to see what that has to offer。And like I said， you can just hoverger over。哦。

The v name。And then you'll pop up with the see zeros 116 error code and they'll ask if you want to go to the website andll bring it right to the error code。

So when I clicked on that， it brought me to here。And like you can see I showed you an example of bad code and good code。

 it was the same thing Im interested to send all the doctrines， explain what's going on。So。

I added you had two numbers A and B return the result。And it tells you。

It's going to return to integer and it takes into integers。So I mean， this is pretty simple example。

 given it's just an addition method but。So that last the last code we had。Wait， not bad。

So we went up another 2。5 points to 7。5 out of 10 this time。

And on our chests and our last code or last error it's given us is the constant name result doesn't meet the upper case requirements for all a constant。

But there's a way around that。If you want to， if you want to say hey。

 I want to keep your result lowercase because I like it that way。

 you can put in this little common violent dis equals invalid name and whatever you put right here。

 whatever I you put right there is on it north。So。Let's see， so if I run into again。

 it's just going to ignore that and give me a perfect 10 out of 10。Nothing。Yep， perfect 10 out of 1。

did you I'll put it in this little comment right here， I don't know if you can see it。

It's just saying hey， ignore ignore this line， ignore the error in this line for all invalid name because those same result needs to be all caps so instead of naming it result in all caps we all。

Add it underscore added numbers， whatever， you could just put， hey， ignore this for me。嗯。No。

 just on that one line。You can oh what's up yeah， you can go in and configure like pile in and say。

 hey， these are my standards adhere to these standards instead of PeP eight。

I didn't really get a chance to dive into that too much。But are。

I will one day because I thought that was pretty interesting just to be like， hey。

 for this project specifically， I want this name and convention for these types of variables。

Or I want this much space in between methods， to that answer your question or avoid answering your question rather？

so yeah now we had the code all cleaned up we got a perfect 10 out of 10 Okay I forgot to point this out it shows you what you scored on previous run so you can say hey I scored a 7。

5 at this time I got plus 2。5 I got a 10 out of 10。So warrant doc strings。

 you can use a help function inside Python by running Python and saying， hey， from example。

 which is my class name import add numbers the function。

And you can put in help and then the function name you want help with and it'll pop up。You'll pop up。

 tell you what what you put in the doctrine so now you know， hey。

 this is a function that takes into two numbers as you get returns a result。嗯嗯 two more啊O。

You want to go with that video first？Sure。So let me go back to the。

Video where it wasn't working properly sitting up， your fine yeah。



![](img/282de5f04e4cc7925fae63a5298ac5c1_84.png)

Okay， so。As described before。You can set different ruless to。

You can set different roles to what it sees and it will check the individual lines and compare it to what is expected based on formatting options。

This will be specified in the aforemention of ue douml and you you would push that to a repo so what that would look like is。



![](img/282de5f04e4cc7925fae63a5298ac5c1_86.png)

Is actually on the next slide， this is what it looks like with Github actions with CicCD integration it will run。

Check it and if it fails， it'll give you an error with a code that you can later debug based on what parameters you predefined it with。

 it will tell you what exactly the error was and from there you can go on about fixing it。嗯。

Now this happens automatically with every push and pull。😡，Every single time， like for example。

 if when we were doing our capstones， let's say it wasn't just the documents we were sending over。

 it was actual code we were pushing out to production。

This would either stop it or just flag the code that we pushed that was bad。And prevent。

 I guess the next crowd strike I don't know why that happened with technology like this。

 but I guess with proper application in use case， it's preventable。And that would help。

With just the management aspect of it， because in a production to scale where you have like a company of 1000 people。

 each person is producing like 10，000 lines of codes code a day。

 you don't have the time to sit there and review each individual line of code。

So this will check if it breaks anything， if it has any in processes that。

Interrupts any other process that is essential for production in whatever project or app it may be you could also get it running off of。

Existing CIs and CDs。Through organizations， but that's an enterprise feature that is that I wanted to explore。

 but it's a lot on that paywall， it's like $100 something dollars。But anyway， I'm kind of。

Going on a tangent now。Part of the criteria for our。

Part of our motivation for experience on our cube for this project is because we're expected to use this for raspberry Pis you can you'd have to use Dbn I was planning on emulating it with raspberian and showing it from there how you would push code from a directly from a raspberry Pi。

😡，Because we would be， I mean， push from a computer to Raspberry5 because we'd be using that ideally to push the code through our kiosk so we'd be able to manage it remotely and it check。

Automa so it'd be streamlined and quick anything else you want to add。你好。It's a shame。

That I couldn't get it to run because literally every interaction with this program is through the web interface I'll see if I can add that I will definitely add that to the resource and I'll put an example like a detailed example through the workshop this time I'll just focus on the local running of it instead of focusing on the CICD aspects of it because I feel like while it's important。

To do the CICD aspects of it， you need to at least get it running obviously there's issues with getting this to run。

To begin with that's all I have from this part if you have any questions about so rRCq feel free to ask now I know I was a bit。

Vague in what it does because I can't really access it but。

It is it is a large tool it is on the scale of a setting up your own server you could dwell 30 plus hours into it into this I I mean I did sleep over this trying to get it to work so。

If you have any questions， I guess， just ask。And don't be afraid to ask our podcast in future by the time。

We get things rolled out， and we'll be able to answer it。

Am I trying to set it up inside the swing lab， what's the swing lab setup should be able touch it on someone raspberry pies。

 maybe？So like， oh， like the。The gate control itself and set the properties of the gate control yeah。

嗯。But yeah there's a lot of aspects to sonar from just curriculum。

 it has components of networking because it has HTP protocol which you can set up it's local hosted so it has technically virtualization。

 which is an aspect of OS， it has all these other things that we did go over and you wouldn't need to know in detail。

So what's the difference between the Sar thing and the the lit Well。

 sonar CQ is for my understanding， not just local， but it's also serverside。

 so it interacts directly with a repo。So from what I saw from JC at pilot local from what I saw from Jason's part of the presentation。

 the L is good for quick。Get it done check yourself and then push it out you would layer it probably for the best optimal use case makes and some thanks yeah。

Ser。So okay， like so far we have gone through what is code quality and why it is important and then we have gone through even we have some technical ear。

 we just had some experience of sonarch and then Jason to here going through pilot now I will go through。

8。哦，我要我住是老家。Prettier， what is prettier， prettier？😡。

Is a tool right so it's an opt code formatted which is supported by many language and integrated on most editors so the formal definitions is free here is a very powerful open code formatted that ensure a constant code style across entire code base improving readability and maximizing format formatting related merges conflict it takes gear of formatting code automatically regardless of the original style which allows the developers to focus more on writing the logic of the code rather than worrying about a style and inconsistency。

So。Priterary is supported by multiple language like Javascript， Python， S ML， CC S， Jason， GraphalQl。

 type script， Motown， YaL and。Many of those are just the examples for now and why why we need pretty ch so your code is formatted and ona like you write code and then they have like a lot of errors then once you save it but we have to first install Al that video and then once we save that the wrong formatted code it will automatically format like correctly you know like not logically but synly if we we didn't have like the semi column on the end they're going put your semi columnlon by itself and then。

Do everything and then we just talk about the constituencies reading ra once our code is fine and then return it like clearly we can read it out and then we can just go through the code line by line and find it out if anything is wrong and the main important thing we just talk about Mars conflict now for these k pause project I think like we need to have lot of common time for the code and everything so whenever we mark and then let's say if I make some mistake and then Jason he try to mark it and that mistakes that will automatically have like correct format of the code so that we will not have either on our main code later on。

Right so let's have an example on this one， so when we see this is just Jesen file like there is so many arguments passes through this line。

 so when we see only this line。yeah' a laser pointer yeah when we see only this line you know like some some might feel like overwhelming feel like oh my God what is this so long and then I just try to excuse for this little longer too I could not make it but sometimes we have to go and then scroll all these printprints all the way in and then again come back that will be like too headache when we work on large coding thing so like what it does like after I save this one and then like that thing went。

Like this now okay it's this exactly same thing but they just break the line and then now we can read it really easily and then have like everything on the same page we don't have to worry about is scrolling right and left and then we don't have to worry about if we miss something or not。

😊，So other reason are like。Unified code style you know they avoid avoid need picking and then's like for myself like I was thinking to hear some big story but I think we are just running out of time but it is very much helpful feel rushed so take your time don't feel quite pressured if you need go a we do like last time people have to leave they can leave I don't want you to feel pressured to so like even it's very much good and scale kind of thing when we work in a group but for example like I work myself for I don't like I'm a transfer actually like they call here Java 1583 and something like that but I used to be in different university then we called it I forget to code name like C 153 or something like that but actually it was just teaching a Java and while typing like in the beginning I used to make a lot of mistakes like forget about。

Semicolon forgetting about like those cur brackets and then you know like even those continuously writing on one line that was like two is headache and then once these things I introduced with these things it was back and then when I put this on my visual code it was like so nice I don't have to worry about them as like once I control as like I used to say that code。

That was like will formatted and make program used to run without any syntax ear。

 you know logical layer is different part even I'm talking about logical E is different thing。

And then that build up my confi， you know， once that happened like before when I was doing my program wasn't runninging properly and I was like oh my God like Im spending a lot of time and it's not runninging and my like confident in label was down but once that part was soldd you know like most of the time in that class sleep we used to have。

Syntax eat rather than logic eat right and then once this part was off and then my concrete was boost it and kind of thing right and then every we talk they're going to save me a lot of time。

And things like easy it's very easy to add like I know like we are presenting on the same thing but sonar and everything was so hard just to install and run。

 but on this one is locally and it's very easy to install and then like and very easy to use。😊。

And clean up existing code base so that's we talked about those things for new line and kind of thing also。

Even though p is one of the few tools that fully automated enforcing a style guy。

 while it may not formatted every single line exactly the way we might prefer。

 don't you think unique benefits like time saving and consistency and then era correction sense？

Make it like worth of using these things。What what do you guys think Yeah I spent a lot of time trying to augment myself so't be really good Yeah like I feel too like it's worth using it or installing in our device and then coding it accordingly。

Right then the most common very good part of this one is like it is supported by most of all the editors that we used it。

 you know， like we use subline， we use view most of the time those are like。

We can download the extension and then we can just do this one even in V quarter code right a lot of us we have that one and then webstr me too when I was looking details into it。

 I just found this webstr like I don't know， but it says it's building on that one it might be a more useful can go ahead and have a little bit more explorer on it but。

That is built in support so rest of us we have to go and do it so while installing yeah I know like it's going to be a little bit problem。

 but let me try heat。And then do it once again if I can open it。



![](img/282de5f04e4cc7925fae63a5298ac5c1_88.png)

嗯。n。Religence here。Thisiscaled。External display is disconnect。



![](img/282de5f04e4cc7925fae63a5298ac5c1_90.png)

Oh go on I go back to it， just share your screen。

![](img/282de5f04e4cc7925fae63a5298ac5c1_92.png)

你边两讲到西。

![](img/282de5f04e4cc7925fae63a5298ac5c1_94.png)

I think。Let know yours screen shareff。Yeah that's how it looks like the website is like really simple and then so we can try it if we need something on like we can try online too for just to take and kind of thing but。

😊。

![](img/282de5f04e4cc7925fae63a5298ac5c1_96.png)

I have explained more on this video right， how to install it and then。How to do it。

 So let me try to play this one， hopefully that。Oh and when I save this file。

 pretty will automatically format this code， so I won't have to worry about things like semi Collins。

 cur braces， new lines， and spacing， etca。So install Preier and VS code。

 go ahead and click on the extension button down here。



![](img/282de5f04e4cc7925fae63a5298ac5c1_98.png)

Yes。God。对。

![](img/282de5f04e4cc7925fae63a5298ac5c1_100.png)

So。现该对海。

![](img/282de5f04e4cc7925fae63a5298ac5c1_102.png)

买不这，I don't know。What' going to do is going install pretier and when I save this file you automatically like semi call correct braces new lines space etc so install prettier and V code go ahead and click on the extension button down here once you click on and type in prettier and it should be the first result so I click on and you just make sure the one by prettier with a bunch of downloads it should have nearly to a million downloads install and will say this extension is enabled globally now you work for prettier to automatically format your code when you save by the couple of settings you have to set up so go ahead and type in command comm and that will bring up the settings and the first thing you want to type in is formater。

Now once you type that in there a couple settings you want to look at first one default formater should say prettier all right if this is not then pretty will not be your default formater and the other thing format on save should be checked and this tells prettier to automatically format your code when you save the file right so make sure that's checked and then the next thing what we can do is actually type in prettier and this will bring up the prettier settings for the extension now there's a ton of settings that you can adjust you know you can set you know whether you want double quotes a single quotes and you know for example arrow functions here include parentheses around a so arrow function parameterr there's a bunch of things that you can set and we're not going go over all the settings in this video but feel free to fool around a bit and adjust the settings to whatever you want or whatever code style guide that you're following there is one setting though I want you to pay attention。

If you scroll down， you'll see a setting of that says pretier acquire config and this should be checked and it's recommended to be checked by the prettier documentation and all this really is is it requires a a big file to be the root of your project in order for prettier to work。

It is very important to have because if you were to ever import someone else's code and this was not selected and you hit save it would actually format you know all the code to whatever settings you have via code so that's not recommended as it would you know maybe your the code you're importing already has certain formatting rules that it's following and your you basically just you know set everything to whatever you have in the settings so make sure that this is selected okay and again。

 this just forces you to create a config file and works for prettier to work all right so when to go ahead and close out of the settings and remember like I said you need a config file for it to work so if I were to save right now this would not automatically format even though I have installed createfig file go ahead and create a new file and the root of your project call it。

year。RRC。All right。Now in the prettier RC which is the config file just put an empty set of curly braces now normally you would see settings in here for the prettier extension。

 but because we have installed Vs code you can simply set specify the settings and Vs code and you don't have to put anything in here but you know if you were to import someone else's code they might have a config file and they would just give that to you so you can follow the same formatted that they did so go ahead and for now just put a set of cur empty curly braces in here。

AndNow if we go back to test。js and we save the file。

 you can see that it automatically formatted the code， so it's not ugly as heck。

We all see that how it was all messy and then later on it was but obviously and then we just have that really nice code。

 but I just want to make sure sometimes like myself like whenever I open the dot STM file and kind of thing because that's not fully formatted they might need something thing so we can have another extension and call33 dot ignore it so that will help Austin like。

To filter it out or either to implement these functions on this extension file or not。

 let's say we have Java dot Java extension and then do JS extension and then that will work only on that one。

 but if that criteria saw any file extension with SDM that will not auto format it on that time。

So like if we have any questions。Yeah。Oh， by the way， it's 10 minutes past Tom， so if you got to go。

 you can。And definitely we are part one i'm repeating this again and then if you guys need any help down the road about like connectinging it syntactically we are always there then like Michael said we're can post it on our fault and then and the resource resources section just to make sure like whatever we have this on that one。

哎对你。

![](img/282de5f04e4cc7925fae63a5298ac5c1_104.png)

It capable problem。嗯。Right right， part two。Okay。No bad to， yeah。

 we stay here and so I get that thermal。😊。

![](img/282de5f04e4cc7925fae63a5298ac5c1_106.png)