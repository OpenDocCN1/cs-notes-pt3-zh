# 非程序员的cursor完整指南（Vibe-编程-101）--BV111EgzTEi4-

Today we're talking about building apps with AI。 This is a comprehensive guide for you with no coding experience。

 you'll be able to build an app by the end of this video。

 This is going to be the most comprehensive cursor tutorial for those who want to vibe code vibecode is the act of speaking or typing into cursor composer。

 which is the smartest AI tool for coding in the world by far in this video。

 we're going to talk about this in three parts。 The first part will be the basics of cursor and so we talk about all of these different things。

 we're going to go through all of the vocabulary， everything that you need to know as someone who doesn't know how to write code to communicate with AI powered coding tools like cursor and so in this first basic section We're also just going to build an AI image generator and I want you to fully understand how relatively easy。

It is to create really cool apps。 You don't need to pay for other people's software anymore。

 The AI image generator that we create looks like this。

 And so we're gonna be able to say a man riding a bike with an Llf。😊，Hat on。

 and I will show you from scratch how I built this very quickly。



![](img/1500f029842088de157b5aeb1cb6d5d3_1.png)

And boom， so we created this AI image generator， we can copy， we can download and then in part2。

 we built this landing page and we found a library on Github that had really cool animations and we just remixed it and created this landing page and we also went through the process of deploying it and uploading it to our own domain。

 So I bought a domain a Genmate co and that is this site。

 you can visit this site and I'll show you every step of the process to create this and then finally in part3。

 we built an AI powered app and this app really targets one of my big pain points with the new open AI deep research。

 I really like how it can create 10 to 30 page reports but it doesn't have images built into it。

 which is why I wanted to create an app that allows me to。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_3.png)

paste in all of my ideas and then I could generate images for the different section so I can generate charts with AI。

 And this allows me with one click to generate charts with AI And if I want to make changes。

 I can actually talk to an AI and say mention the companies and explain these more in the chart。

 And so we use Clas API to allow us to edit these charts。

 And so now we have this chart here that we can view that automatically created by AI。

 It shows all the different companies and how they can either race competitively or prioritize safety and slowed progress and then it shows the different outcomes。

 and you can export this as a P。 And so it's just a more fun way to read the deep research project。

 Those are the three apps that we created today。 and I'm going to go through all of the basics getting started with cursor and then we're gonna build these apps and we're gonna talk about other things like。

😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_5.png)

To use Gitthub as someone who' literally can't write a line of code or understand code for that matter。

 We're going to talk about verll and deploying apps to Versll。 I promise you， it'll be worth it。

You're gonna love vibe coding。 I'm Riley Brown。 Let's dive in。 This right here is cursor。

 And you can download cursor at cursor dot com。 I downloaded it for Mac。

 And whenever you open up a new window after you have it downloaded。 This is what it looks like。

 This right here is bolt and bolt is a friendly familiar interface just like chat GT。

 you can type whatever you want。 And in a chat like experience。

 it will generate the app that you want。 except it's hosted online。 And many people love this。

 It's just a simple website you go to， you immediately type it in。

 while cursor is a tool that you download all of the project files or hosted on your computer。

 And by the end of this video， you'll understand why I think that's actually a good thing。

 And the reason why a lot of people prefer this experience over this experience is because of the interface。

 And it's just easier to get started。 But I think that you'll run into a lot more roadblocks using webbased tools than cursor。

😊，I think the cursor agent is just the most superior。

 and I think you'll understand that by the end of this video。

So the question many of you may have is how do you get to this experience within cursor。

 How do I type my idea in cursor to have it generate the files so that I can create the app that I want and I'll tell you right now。

 So when you create a new cursor window， there are three options Open project cloneone Repo and connect via SSH in this video we're going to go through this one and this one let's go ahead and start off by going over this which is basically creating your new project from scratch So if we press the open project button。

We are now taken to our file system and people might be you know confused they're like， wait files。

 I don't know where to put it， it doesn't matter， pick a place where you're not actually going to delete it and you're creating an empty folder。

 That's how you get started on cursor。 So I'm going to create a new folder and we're going to call this Let's call this new project for tutorial doesn't matter what you name it you're gonna to press enter and then open。

😡，Then what you're going to do is you're going to press command I and congratulations。

 congratulations。 you made it。To this。What this is is this right here。

 They're the same thing except this one gives you more control。 So we now have a cursor window open。

 and we're going to turn this to agent mode。Okay， so what the hell is composer。

Composer is an AI agent that allows you to create files。

 edit files and delete files and run terminal commands within your codeb and you might be thinking what do all of those terms mean so let's ask composer what is a codeb。

Answer by creating a new file called codebase。Explanation。Text file。

 And we're just going to use the agent。 And as I said earlier。

 it can create files and the code base is just the collection of files。

 and that can be found right here。So you see here it created this text file called codebase explanation and it basically created this right here。

 this is a text file and now we can read what a codebase is。

So it is all the programming files written in various languages and all of those files will show up right here。

 we can also create folders or we'll name this one folder。

 and then we can move this into that folder and we can hit moveve。

And so now we have a folder with codeb explanation。 and we have created a dot file。

Computer software doesn't run on text files。 It runs on special other kind of files that I don't know how to write。

Luckily， AI can write basically anything I ask it。 And if you learn how to prompt AI correctly。

 you can get AI to create high quality applications。 and there's a lot of controversy around this。

 but it's true。😊，Okay， so not only can we create text files， we can also edit them。

 Please make code base explanation longer，10 paragraph essay。

And we can use the agent that will say let me expand on the code base， it says it's reading the file。

 and now it's done reading the file， I'll now expand this into a comprehensive 10 paragraph essay about code bases so it can very easily change the files within your app。

嗯。So you see it shows the diff view， show it shows what it's removing and it shows what it's adding and since it's in text file。

 you actually don't see the paragraphs because dot TxT it doesn't have like automatic line breaks in order to see line breaks。

 we would actually need to change the format we can do that Can you change this file to dot M which is markeddown and this will change it to dot M and then we'll actually be able to see the paragraphs。

And so what it did is it took all of the text from the previous one and it created a new codebase explanation do MD file。

 and then it deleted the old TxT file， which is basically the same as converting it。

 we press accept and now you see the line breaks and this is in markdown and many smart people who write a lot for their job。

 actually use cursor all the time because you can use the agent to make edits。

 you can also use the chat feature within composer。

 which I'm not going to talk about as much because as a vibe coder。

 you're mostly not you don't really read the code necessarily because you don't always have to。

 In fact， I hardly ever read the code I just rely on composer but you can select this right here。

 and then you can press chat and we can say make more concise。

And you can make changes and so if you know a little bit about coding and you can actually highlight parts of the file and make changes。

 and then you can press apply and we can press command Y。

 or you can select that right there and it made the change and it gives you full precision over all of the files within your code base。

So I think you understand the basic premise that there are different types of files over here and when you work on really big projects。

 the amount of files might increase to hundreds or thousands of files depending on the size， however。

 when you're starting out it's useful to keep it as small as you can because。

It does get harder the bigger your code base is。😡，Which makes sense。

 right that intuitively makes sense as a programmer that's the same thing as a vibe coder using AI tocode that still applies。

 So now let's go ahead and generate some code files。

 So let's go ahead and open up a new composer window Now that I'm working on something completely unrelated to what we were doing previously it's good to just open up a new cursor window because all of the previous messages in your chat will affect the later chats and the longer these threads get the worse any AI model performs。

 you want to reduce the context。 So just frequently create new chats and try not to make it so long that it says previous messages above this。

 once you reach a point where it says see previous messages in your chat it's a sign that you need to move to a new chat。

 So what we're gonna to do is we're actually just going to。

Right click on this and we're going to hit delete Now let's create some frontend designs using cursor from a blank project so I'm going to delete this folder。

 We're in a brand new cursor project。 Now what we're going to do is we're going to generate a cool design Now let's use this prompt I know and let's make sure that we go to composer。

I want you to create an H TM and JS animation of balls bouncing in a rectangle。

 and they should be red， blue， green， orange， and。White， so we're now going to press enter。

 And you're like， okay， where are you even going see these balls bouncing。

 Is it gonna to pop up right here， Is it going pop up over here， Where is it， Okay。

 so it's creating a file， as we saw earlier， it createds file。

 So it created this index dot H TM L file， And if you can read this great。😊。

And it's fun once you get in the hang of it to change some of these variables。

 because you can intuitively understand what it does， right， you can change the minimum height。

 You can change the alignment so you can change this from center to left or to right。

 And here it is done creating animation do Js。 So we're gonna hit except all。

 So now we have this index do Hm file and this animation dot Js。 Now you say run it locally。

 I want to see it。😊，You could probably just say I want to see it and the agent will understand what you mean。

 So what it's going to do is it's going to create a local host server。

 So it says all use Pythons built in HtTP server to serve the files which is a simple way to view HTML files locally and so it says now you can open your web browser and visit this link right here。

 Let's go ahead and copy this。And what we're going to do is we're going to open up whatever browser。

 Chrome， I personally used Arc， and we can paste in that address and we're going to press enter and look at that。



![](img/1500f029842088de157b5aeb1cb6d5d3_7.png)

We can now see these balls bouncing around。The frame， exactly as we asked it。 Now。

 what we can do is we can say， add four more green。Balls。If you're asking， why is he doing this。

 I don't know。 It's kind of fun。 And I I like it is a really fun experience to just mess around with it and let you're just curiosity just go。

 you don't need to think， okay， how do I do this to convert it into money。

 The fastest way to not create any money from the activity of learning how to code is to think about this activity as just like utilitarian and not just exploring because all of my good ideas from this has come from just exploring and learning the possibilities。

 And so I encourage you to have fun。 So what we're gonna do now is we're just gonna to press except。

😊，And I'm going to come back over here and we're going to press command R。

 which is going to refresh this local host server， and we're going to hit refresh。 and there we go。

 it added these green balls。 Now I want you to make these balls， bounce off of each other。

 So right now they're going through each other when I want them to bounce off of each other。

And we'll go ahead and run this and now that it's done， we're going to press accept。

Now we'll come back here。 Let's go ahead and refresh this。 Let's see if it works。

Okay and you can see that these physics are not perfect right they sort of bounce off each other and that's because there's a lot of different things that we could do to make these balls bounce off of each other and make them better。

 but the point is is you're constantly changing things。

 changing variables and you should always tell cursor specifically what the problem is。

This is not doing a good job of mimicking how these balls would realistically bounce off of each other。

 They're kind of like glitching。 And it looks like the center of mass。

Is does not represent the border of the balls don't cause。The bounce。

And it doesn't bounce in a realistic way。 Is there anything you do can do to make them bounce off of each other when the edges of them touch。

 It's like when the centers get somewhat close to each other。 It's hard to explain。

 but please figure this out。 And we're going to run it。

 And if you're wondering how I am doing the voice I am using an app that is called whisper flow。

 and whisperflow allows you to speak into your computer。

 And then it creates text wherever your cursor is。 So in any app that I want。

 I can hold down the FN key and speak， and it will create that text。 And this is the icon。

 This is what it looks like。 And I haven't even gotten pro yet。 It's free。

 This is like one of the best free plans I've ever had because this app is very， very good。😊。

So now that it is done。Let's see if this works。 So we're gonna press， accept。

And now we're going to come back and we're going to refresh it。 Look at that。Check that out。

 Now they are bouncing realistically off each other。

 all from us just describing what the problem was。And now they are bouncing off of each other very realistically and there we go。

 and we're creating this little design and you could put this on your website。

 I don't know why you would create this， but the point is you can create simple one JavaScript file and one index。

 HTML file and this is a really simple and good way to get started without creating a bunch of files。

So I just opened up a new composer window I made sure agent was on and I have claw 3。

5 sonnet on as well。 I think it's the highest quality and fastest model for cursor composer and that's the one I use。

 Now we could actually abandon this whole idea of these balls bouncing off each other and what we could do is we could turn this into a landing page。

Okay， abandon everything I want you to get rid of these bouncing balls and I want you to create a landing page with no scrolling that looks like an early 200s website。

On animation， I want it to be like this retro animation website， and make it。Epic。

 no idea what it's going to do here。 But my point is， is once you create files。

 you can just say abandon everything。 Let's delete the existing files since we're starting fresh。

And it will create a new retro style website。Okay it is done， let's go ahead and hit accept all。

 now we're going to press command R and there we go， we have this early 2000s Anim agent。

 welcome to the hottest animation site on the web Home animationations downloads guest book。



![](img/1500f029842088de157b5aeb1cb6d5d3_9.png)

And right now， like when I press- so what I could do is I can actually just highlight these right here and press copy and if we go back to cursor。

 if we go back to cursor， I could just paste this in right here。



![](img/1500f029842088de157b5aeb1cb6d5d3_11.png)

When I click on each of these， can you please create a different animation and within this box。

 I want something else to pop up。

![](img/1500f029842088de157b5aeb1cb6d5d3_13.png)

Let's go ahead and press accept and we're going to refresh this now。 if we press animations。

 we now have this DVD bouncing around the edge。 This is a classic。 we can press downloads。

 Obviously these aren't good。 We didn't specify what we wanted。 We can press guestbook。

 whatever we can create this little fun page right here with basically no effort。 Okay， that's cool。

 I'm done with this little project right here。😊，And I opened up a new cursor window。 Well。

 what we just did right here， and we created this by using the cursor agent。

To create all the files within it， this is two files， an H file and a JavaScript file。

And we did this by just starting our own project， then asking this AI agent to create this。 Great。

 awesome。 Now， what we can also do is we can use this second option， which is called clone repo。

 And when you press it， you'll see， provide repository URL or pick a repository source。

 And so this is Github and do not be afraid。 I was afraid of Github for a very long time。

 Github scared me。 I have no idea what the hell all of these files are， right， but you do already。

 These files right here。 are those same files that we had open to create this site right here。

 This is just two code files。 This is two code files right here and we created them with the agent。

 In fact， we can open up this project right here。 that's made up of two project files。

 And what we could do is we can actually come to Github。

 which is a place for developers to save their code。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_15.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_16.png)

And we could create a new repository and we could call this testing two files right we can just call this testing two files and we can make this a public repository。

 And so if we create a new repository at testing two files on my Github account。

 which I'll go over in greater detail later in this video。

 but I just want to show you how easy it is so we can just copy this link and we can just say I'm going to say save this project to paste that repository link that I created just by typing in testing two files enter。

I'm gonna to say I already created the repo， Please load files to this or commit。

 I don't even know the official vernacular。 I just know。

 put this on Github and we're gonna to press enter。 and cursor can actually do this。

 directly from the agent。 It says it's doing these commands。

 which we're going to talk about a little bit more。 I don't think we've seen any commands yet。

 but it is running these commands， and it's automatically going to create the initial commit。

 and now let's add the remote repository and push the code。Let's push the code to the main branch。

 I'm not doing any of this。 This is all happening automatically。 Great。

 your project has successfully been uploaded。 Now， if we refresh the page right here。

 we see that those two files that we just created on here。is now on Github。 This is public code。

 So if you were to copy this link right here to Github where we just saved our files。

 you could do this right now if you want to test it out。

 you could go to cursor and open up a new window of cursor press clone repo paste this in right here。

 press enter， and we could create a new folder called banana Jones， don't know I hit create。

 select as repository destination open。 we now created， this is basically like a template。

 And so what we did is we forked it， I don't know this is what a fork is technically。

 it doesn't matter。 The point is all of the public code on Github。

 you can just like clone it and you can start coding from that point。

 There are licenses you want to be aware of some code you can't just freely use to make money on。

 but for testing purposes you can just fork stuff。You can find cool Github reos and just fork it and we just forked our own repo however。

 there is a certain template that thousands of people have used thousands of people have used this template and what you can do is you can copy this link this is a next JS project and so we did a lot of work getting it set up so that it connects with a database which we'll talk about later and it also is connected with authentication and we put a lot of work into this template so that you don't have to waste time so if we create a new cursor window let's create a new window。

And I want to show you the process of creating a next Js project。

 And you'll notice how much bigger the code base is。 There's going to be a lot more files。

 We're going to at clone repo。 We're going paste this。 We're going to press enter。

And what we're gonna to do is I'm just gonna press select repository destination open。

 And here we have all of these files and you see this source folder， this public folder。

 the app folder， which has components which has a lib folder， which has contexts。

 all of these are different things you can do within the app and we have it pre-built with a voice recorder that you can create。

 we have it pre-built so that there's AI chat built in like chat GT like features。

 but we'll get to that later。 what I want to focus on is doing the first process。

 which is pressing command。 Now we're going to press agent。

 And so now we're going to start out from a blank template。

 The first thing that we want to do is we just want to see it because this template comes with a frontend page to start that is like your template page。

 And so what we can do is we can say run this locally。

And what this will do is this will I'll help you run this project locally。 first。

 let me check if we have necessary files and set up to run the project so it's looking through all the files it's looking through the package JSO when you're starting out。

 don't read this just focus on what you want to create and focus on what it has created and then focus on communicating what you want to cursor the best you can because this stuff will just confuse you right now it's doing NPpm install and so this is actually a terminal feature that I'll also get to later And so here it says since this project uses Firebase openaiI Anthropic deepgram。

 you'll need to set up the environment variables which'll also get to later don't be don't get flustered yet all you did was say run this locally and then it ended up with creating this document and it gave us this link right here that says HtTP。

Local host 3000。 You're gonna to press command， click。This is going to open up our template。

 So we now have a next JS app open and running。 And if you think about how long this took。

 all you have to do is paste in the link， press around this locally。

 now we're in business and let's go over some of the features within here like if you wanted to change any text in here this is a page that we created。

 this is a page within here and we can find it by pressing this search bar。 And since when I started。

 I didn't know how the code files were organized， I let the AI agent do all of that。

 And you should do that as well。 But if you just want to change text like imagine if you wanted to change this right here and you actually just wanted to use this template because you're not always gonna to use this template。

 you can find anything on Gitthub。 there's millions of different code bases that you can start from And what we can do is we can just paste this in right here and let me zoom out real quick within cursor within cursor。

 you can actually see that it says make anything you imagine and so we can highlight this and what we can do is。

Make anything you can think of exclamation point， and then if you'll notice it didn't change。

 you have to press command S， so you need to save it， command S。



![](img/1500f029842088de157b5aeb1cb6d5d3_18.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_19.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_20.png)

And here it made the change， make anything you can think of。 Okay。

 so now let's change this to make an image generation app。

 Let's just create an AI powered image generation app。 And so in order to do that。

 we're going to press new。

![](img/1500f029842088de157b5aeb1cb6d5d3_22.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_23.png)

And we're creating a new chat。 Remember， we've created zero prompts so far。

 All we did was say run this locally。 We haven't created any prompts for this project。

 Now we're gonna to do our first one。 And now we can actually start creating whatever you want。

 Let's go ahead and try it。😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_25.png)

I want you to create right now。 I want you to create a really cool looking AI image generator。

 And let's say you have a very specific idea in your mind。

 Let's go to any tool that you want to use to like。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_27.png)

Draft out a。Any tool that you can use that you can use TLR draw。 I personally use whimsical。

 and many people have actually been asking me what tool this is。 So I'm just gonna to say。

 and this is not sponsored。 These are tools that I use。 There's no sponsor in this video。

Let's go ahead and put whimsical。 And let's go ahead。

 And what we're going to do is we're going to diagram what we want to create。

 So I'm going create this rectangle。 And so this will be the site。

And let's imagine we wanted to create an app。 Let's just put。Describe image here。 and then。

 and then let's say that we wanted。 And so then let's say we wanted the images to pop up。Right here。

 And it doesn't need to be perfect。 right， we're just creating a little thing。 And we're just。

 and then in the top bar， right， let's say we wanted a top bar。 Maybe we want this to be black。

 and then we can add home。Okay， so now we can screenshot this。

 You can actually do this on an actual whiteboard and draw it out。

 The point is here is we're giving cursor。 So if you screenshot it and then you drag the image into。



![](img/1500f029842088de157b5aeb1cb6d5d3_29.png)

Csor here。 I want you to create right now。 I want you to create a really cool looking AI image generator。

 The input field will be light purple。 and I will describe the image there。 And when I press enter。

 It will generate images in a grid。 Right now， I want you to just put placeholder components instead of the images there。

 I'll add the AI features later。 I want to start off by just creating the shell。

 have a top bar that looks like this image， this is a rough sketch。

 please make it look professional and have the background。

 have dots like a grid line dots in the background that are gray and like nice and light and not to demanding。

 I really like that look。😊，So look， all we've done， paste a little sketch that we created。

 added this prompt after cloning the template repo by pastetail link and we're pressing enter。

 we've hardly done any work and the hardest part now the hardest part for a lot of people is accepting that this interface is kind of ugly。

 but if you get past the fact that cursor's interface is kind of ugly and looks like a codeb。

 then I guarantee you you're going to be like， oh my God I'm so glad I learned this。

So I'm going to press accept。Now what we're going to do is we're going to go back to our local host 3000。

 and here we go， describe your image， a monkey monkey riding a dolphin。



![](img/1500f029842088de157b5aeb1cb6d5d3_31.png)

Right and here we have the images make make no images show up until I press enter and I actually want you to mimic the loading process of these images and have like a nice little like blur while they're loading and just have them load for three seconds just to kind of see what it would look like right now I just kind of want to design this out and depending on the type of local host。

 some of these just automatically update as you make changes with next Js that does happen so it just changed without me even having to press except and I actually want to talk about that。

 There's a difference between pressing save all and accepting all it used to matter a lot more until cursor added the feature of the restore and this is one of the most important features I can't stress to you how important these features are。

 this feature is， which is allows you to create to restore from a checkpoint that you created earlier because if let's go ahead。

Look at this。And so what I'm going to do is I'm going to press accept all。

 I now just press accept all because I can always go back and I can now describe an image right。

 let's zoom in a little bit to see so we can say a man walking down the street and we can press enter and now we have this nice little animation and then boom image will appear here and let's say we didn't like those changes at all。

 what we can do is we can go back to before I asked for the previous change。And watch。

 we can actually see this live。We can press restorestore。

 it'll ask you if you want to revert the file and you can hit continue。

 and so we can see that it went back to what it looked like before， but let's say oh shit。

 I actually want to go back， great。What you can do。You can click down here and if it lights back up。

It automatically restores it to the latest， and then you can restore it back here， right。

 which restores it back， and then we can restore it back to our previous one， which was our template。

RightThis was our template。 And now if we come back down here， we click down here， boom。

 now we're back at our latest and you can always go back。 Okay。

 so what we're gonna do here is we're gonna add an AI feature。

 We're gonna add an AI image generation feature。 I'm going show you how I use As。

 I'm going show you an example。 and then we're gonna circle back and create a new project cloning a Github repo and then I'm going to talk deeper about As。

 So this is gonna be kind of a roundabout examples way of learning of all about cursor。 But first。

 let's actually just make this work right So what I want to do is I'm going to press new composer。

 We're at a good spot。 And the first thing I want to do is I want to I don't like this purple。

 I hate this purple。 Please make it darker dark blue and make update that。Across all components。

Get rid of the purple。Okay， we're going to run that。This got changed to this blue color。

 I'm going to say man， the text is dark blue， we can press enter。

 and now everything is blue and it looks better， I think。

Let's not worry too much about design that purple was just like hard for me to see。

So now we want for whatever we for whatever we type here。Whatever I type here。

 I want this to turn into images and you're like， how the hell do you do that Well。

 what we're going to be using is we're going to be using an API and so。😡，In very simple terms。

I want you to create a little info icon at the top right of this page that when I press it。

 it opens up a center peak toggle that explains what an API is。Explain this very simply。

 like concise to a beginner and use analogies and make this easy to understand。

And why not use cursor here。Okay， so now we're going to press accept。We'll come here。

 we see this info icon， press this。 Okay， think of an API application programming interface like a restaurant waiter。

 you， the customer don't go directly to the kitchen to order food instead the waiter。

 the API takes your order to the kitchen server The kitchen prepares what you ask for the waiter brings back exactly what you ordered right We are creating an app that allows a user to type in a man on roller skates。

 There are many people there are many tools out there。 you know that host。

An API that allow you to generate an image with a text input and AI is very good at taking the essential information about this technology and converting it into your own tool use。

 and you need certain things。 So the first thing that you need is we're going to need API key。

We're going to need documentation。And we're going to need a great explanation of the feature you want。

 and the deeper your understanding of different AI tools。

 the more fun you'll have building because I all I did for two years is test different AI tools。

 And so I can just go out and I can just connect all these tools together to create my own super cool AI tools。

 When you're just starting out， the best place to learn is a tool called perplexity。

 you can also use chat GBTs web feature。 but I've just been using perplexity for so long that I'm just going to use pro mode。

 Actually， we're gonna to use reasoning R one。 and I'm going say this。 I'm creating。A next JS app。

 you want to make sure that whatever app you're creating， you want to just specify what it is。

 because the app that we're using to generate images。

 The API has different instructions based on what language you're using。

 So we need to include that it's next JS app。 And I want a user to be able to generate。An image。

From text。I want the best。AI image。Provider API to use。 I already know。

 I'm just gonna put FAL because I know I already have my API key set up with that。

 And I think that's a really good platform for people to understand。 So we're gonna to use that。

 You don't need to include it right It's often free to test APIs。

 So you don't have to pay before you use them And you just get an API for free。

 So go ahead and test different APIs。 It's very fun。 So this one， We're gonna use FAL。

 Please give me the code examples for generating。😊，An image。Using a great high quality image model。

 explanation and code examples， this doesn't fully matter。 Basically you want a how to use it。

 your code snippet examples， because each one of these tools has a special syntax。

 I think is what it's called their' special way of writing code to access this API。

And we need to give that to cursor。 We need to give cursor the instructions on how to use the technology of whatever perplexity fine。

 And so here it's saying it's giving all of the requirement。

 So here's a solution using flux 1 pro via F AIs API currently considering one of the highest quality AI image generators available in 2025。

 here we have this full thing right here。 What we can do is scroll down to the bottom。

 We can press copy， and I'm just going to what I'm gonna do we're gonna do is we're gonna put documentation。

 So we need to put the documentation right here。 So we're gonna paste all of that in。

 We need to find an API key as well。 this f AI dashboard slash keys。

 We can click API keys right here and boom。 We can add a key。 I'm already signed in。 I have $20。

 You get $20 for free when you sign up for f， which is really cool。

 You can generate a lot of images with $20。😊，So what I'm going to do is I'm going to hit add key and I'm going to hit create key I'm going to delete this key right after this video because if you could use this key right now and drain my $20 theoretically but I'm going to delete this key right after this video and so you can actually just put your API key right here and I'm just going to say beneath this。

 put this in the right place that works then you give it documentation and then here at the bottom。

I'm going to give it the explanation。All right， our app is perfectly set up for the user to enter in text。

And get out the images， the four images that we generate in those in the places that we've created placeholders。

 So replace the placeholders with actual image generation。

 Here is the documentation for implementing F A L。 And I want to be able to just generate。4 images。

 And what we can do， if we wanted。Let's just go ahead and run this。 Let's see if this works。

Just by pasting in some code examples from perplexity。

 pasting in our API key and our instructions down here at the bottom Okay so in theory。

 we can actually see what files it created and it actually put the key in the wrong place It put the key directly in this route file so if you were to deploy this。

 this is not secure This key is not secure at all So what we need to do is actually I'm going to paste this key and say put this in the ENV file that is secure。

And since we're running this locally， this E N V file， let's say you were to upload this to Github。

In the E N V do local file， this will be secure。 This will not be shown because this key is private。

 And so anything you put in this Ev do local file will stay secure。

 So you want to make sure that in the route do T S file that uses this instead of using this key right here。

 which is my API key that needs to say private。 It's using this thing that points to it like points to file underscore API key。

 which can be found in your ENv do local file， file underscore API underscore key。

 if that makes sense。 So I'm going to press accept all， let's go ahead and see if this works。

 So we're gonna go to localhost 3000。 I'm going refresh the page， make sure everything's all good。

Now I'm going to type in a man riding a surf board in Hawaii and press En。

Local host 3000 failed to generate images。 Please try again。 So what I want to do is this is good。

 If you get an error， you can actually screenshot it。Anytime I get an error。

 I just screenshot I'm trying to grab as much information as possible。

 some other things that you can do when you run into a problem is you can press write。

 you can right click and press inspect and then you can go to console and here we have some information so we have we can copy this。

And we can actually just paste this back in， however。

I just wanted to see if this would work just with perplexities's information。

 but what we need to do is we might need to give it more useful information。

 I'm going going to give you more info on FAL image models and what we're going to do is we're going to come back here。

And we're going to go to perplexity。And I'm going to just copy this right here。

 I'm going to paste this in， need docs for image generation。 Give me inline links that are relevant。

Just links to the docs。 And so here， main FAL flux documentation。 great。 we're gonna copy this。

 Lets let's just go ahead and open it。 flux image generation。 And so we can click on this。

 So we can also see playground。 And so playground is where you can actually test things。

 So like this is extreme close up of a single eye tiger。

 And we can actually just run this directly in the app。

 And if open AI has a playground where you can test the language models Anthropic has a playground where you can test language models。

 Look at this。 this is cool， extreme close up of a tiger。 And so this one is flux pro。

 the newest version of flux maintaining okay， this is pretty cool。

 And we can change this to the word flux flux master。😊，Ran。And we can do some testing。

 And this is a good way to test different image models， text models。

 voice models in playground prior to adding it to your app。

 because it is going to basically do this same exact thing in your app。

 except the output is going to show up in your front end。 That's what you're paying them for。

 You're paying flux to do this technology to do this text to image and put it into your app。

 That's what you're paying flux for。 And so what we might want to do here。

 is we might want to just get the examples。 So if we click playground right here， we can hit form。

 We can also change this to jascript， which is what we're using。 Next Js is jascript。

 and we can actually just hit copy。 So this is the input。Result Json。

 So we're now getting the result code。 So I'm gonna paste this in right here。

 This is my code from the playground because we want to just give them relevant examples。

 We wantna make sure that that was input here is output and then here we have this Json。

 We can copy this and we can paste it in right here。 we can show the logs， there's no logs。

 What we can do is we can just run this。 So let's go ahead and run it。

 And one thing I just made changes to my environment Ev do local file。 Anytime you do that。

 it's good to rerun your server。 and I could ask the agent to restart my local host。

 That's what I normally say。 or you could come into the terminal， which scares a lot of people。

 And I think it's NPpM run dev。And this will actually open this up on 3001， and we can command。

 click on this and run it again。 And honestly， don't do that。 if that even is sort of confusing。

 you can just say rerun it because you do want to rerun your server after you make changes to your EN V do local file。

 So I'm going to press accept on these changes。I'm going to refresh the page here。

 now describe the image you want to generate， man flying a kite。We're going to run this。

This is looking good。 It should take a little while to load。You know。

 the loading indicators aren't great。 Okay， fail to generate images。 you know what。

 not everything is that easy。 let's just copy this and we're gonna to paste this in and we're saying I'm still getting errors with FAL。

 please fix them。

![](img/1500f029842088de157b5aeb1cb6d5d3_33.png)

All， let's restart this。Now， let's test this again。A man with sunlasses wearing a shirt that says。

Csor is lit。 Come on， Come on。Please AI gods。 Yes， there we go。 cursor is lit。 Okay。

 how do we download them。 Okay， so let's actually， that site seems like a good thing to do。

 You please create a option to for on all the images to one click download and one click copy。

 this should be on the top right of each one as little icons。

 don't have text have icons just allow me to copy a download the copy icon should have a slight little animation when I press it。



![](img/1500f029842088de157b5aeb1cb6d5d3_35.png)

And so here we just created a basic front end for an AI image generator。

And you could use this for various purposes。 This could be for graphics， for Instagram。

 for YouTube thumbnails。 You can train your own model。

 There's a ton of different things once you start adding many different features。

 So here it's loading。 Let's see if this works。

![](img/1500f029842088de157b5aeb1cb6d5d3_37.png)

Okay， I don't see it updating on the front end here。Let's try this again。

 just refresh this page here。 We'll paste this in。 We'll run that same prompt。And hopefully。

 when these images pop up， it will show the ability to okay， weird。 we got this error。 So remember。

 when you get an error， when you get an error， let's go ahead and we're gonna go to cursor。

 let's just open up a new chat， say， when the image is loaded， I got this error。

And this happened after I tried to add the copy and download buttons so as you can see here and when you work in next JS and we're in Next JS you do get more errors because the codebase is just bigger so anytime you get an error you just copy the whole error and you paste it in try to describe exactly what's happening to the best of your ability and then yeah。

 see if it fixes it so what we're going to do here is we're going to now paste in a man with a zebra。

Okay， it's done， as you can see here， now it has this weird components。However， it does have it。

 So if I press copy， it gives that little animation and we can download。

 we can download and we can download and we can download。

 I could ask cursor to fix this part right here。 but I actually don't want to continue with this project。

 I want to go over how to use Github repos。 I want to use a repo， I've never used before。

 and how I navigate using a new Github repo as a starting point for one of my internal apps or an app that I want to make money on。

 And so let's go ahead and focus on that。 we're gonna to clone a repo create a project that we're gonna actually going to deploy this one on the Internet。

Okay， so let's pause for a second and recap what we've talked about so far in this video。

 so we've been over cursor and we talked about how to download cursor on cursor。 com。

 and then we went over the different parts of cursor like the composer all of your files within your codeb and then where you view the files and we also talked about how you can ask composer to run it locally。

And then you can view it in webVi on local hostst， and then if you get an error when running it on your local host。

 like we created the AI image generator and we got a few consecutive errors。

 this is going to happen every single time that happens you want to copy the errors in your console and you do this you can press right click on the website anywhere and you're going to press inspect。

And then at the top， at the top， there's going to be some a tab that you're going to press。

 It's going to be console。And there you can find information。 So if we're on the website。

 we can click inspect and then。Up here， you press console and you'll see the errors right here。

 and you can paste those errors into composer and you say， hey， this is not working。

 this or that happened。 Here the errors。 Here you go， and it will then。Right。

It will generate new code。 So the process is you speak or type， and in order to speak。

 I use an app called Whis flow， and it just allows me to type faster because I can just do speak the built in Mac。

Beach to text is just not very good。 cursor composer will then generate the code。

 and then it gets applied to the codebase， whether that means adding removing。

 or editing code files and then if you click on a code file you can see them here and you can make changes directly but since we are software composing or vibe coding we are just focusing on using AI and that's what makes these tools so revolutionaries。

 we have an AI agent who can make these decisions so we can just focus on our end goal and this is just a brief overview。

 we haven't really talked about planning we have not yet talked about using As at a very deep enough level and we haven't talked about databases right if you were to refresh the last app that we created all of that data is gone So we're going to talk about that later so for the rest of the video I am going to divide the rest of the video。

In two parts， the first part is going to be， we're going to just create some design。

 So we're going to do some static pages。 And then we're going to build an app。

We're going build an app with database， authentication。And we are going to deploy it to Ver cells。

 So we're going to put it on the Internet。 We're not just going to run it locally。

 We're going to give it a domain on the Internet。And then we are going to give it a custom domain。

 And this will allow you to create an actual app that your friends can sign into。

And this is step one， you want to learn how to do this before you learn about payments。

 I suggest building apps for yourself before you try and build apps for others focus on that so let's start off with designs this is something that I'm really I've been obsessed with recently and I think a lot of things that we do in society。

 people are going to start doing it a lot more and making little websites and really cool personalized websites。

 things like resumes。So things like resumes。Are getting a lot easier to create。 And it's very cool。

 It's a cool way to stand out。 Things like link trees。 If you're a creator。

 you know that linkree is massive and being able to find relevant links。

 It's somewhat like a resume in a way where you can find all of the interesting things about you。

 And then landing pages。 This is a great place to get people to convert to sign up for your newsletter to sign up for your app to sign up for whatever。

 And just like simple websites。 The design is very fun and very easy to do。

 I just really think this is a great place to start。 So let's talk about design。 Gu what。

 We're going back to perplexity。 I want to make a really cool landing page that has really elegant and fun animations。

😊，And I want to use a new library and test out new simple frameworks for animation。

 I want you to suggest simple pub reos that I can use right now to try out different to test out different types of animations。

And I want these to be lightweight。Great for landing pages。 Please list these out right now。

 And so what I'm doing。And let me break down this prompt。 What I'm doing right now。

 I'm trying to use get as a entry point to create a fun landing page。

 And I think this is a really great way to learn the same way that people on midjoney。

 they use what are called S reps， which is represented by dash dash S， R， E F。Right。

 if you type in dash dash SREF。You'll find that there are a bunch of libraries of different Sfs and that kind of points to a different style and a lot of people who do graphic design come to these sites be like okay。

 I want to create designs that have this vibe or this vibe and when you're generating images you put in this Sf and that gives you images in that style and I think of Github thats I think of Github in a very similar way where like you can use Github for inspiration and so we have this animated landing page。

 Giapp Sherry do Js， no idea what this really means and before I learned about coding and learned how to use Github none of this was available to me but now we have these AI models that it can search through a bunch of different projects that people have uploaded to Github and we can just surf through them without having to know how to code and we can get explanations using。

嗯。Using perplexity。 And that's awesome。 And so here we have this right here， Here's the repo。

 And we can click on this repo。 And you can look into it。 But for me， I'm just gonna。

 I actually noticed that that repo only had one star。 So please find popular ones。😊，Okay， so。

Here's one called anime JS。 And so let's find the Github link。 Here it is。 Let's click on this。 Okay。

 this one looks very popular And look at that。 That looks cool， right。

 And so we see these really cool animations。 All right， you know what， this looks fun。

 Let's go ahead and try this。 So we're gonna copy this link。 And let's go ahead and open up cursor。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_39.png)

And we are at a new window。 Let's go ahead and just clone this repo。 And we can create a new folder。

 and we're gonna create a， let's call these one page。Projects and we're going to hit create。

 and we're going to hit select as repository destination， and we're going to create a landing page。



![](img/1500f029842088de157b5aeb1cb6d5d3_41.png)

Okay， so this GitHub repo is open and it's called anime。

 we have some files here that are loaded on the left。

 The first thing that I noticed is we have documentation and I'm seeing examples here。

 and so this are layered animations。 this looks like some stuff that we might be able to use at the very least we can use these examples to make sure that cursor creates animations with this new library correctly。

There's a lot of different libraries out there and this anime thing that we just downloaded。

Is a library that might be something that Claude is really familiar with， like Python。

 Claude is trained on tons of Python data， but it might not be fully familiar with anime。

 I have no idea。 But what we can always do is type in examples and just tag the file and say。

 look at these examples。 and then make sure you correctly create like keyframe， speed， stagger demo。

 I don't know。 You can use this as examples。 And so that's very useful to know。

 What I want to wonder is I'm just gonna go ahead and ask composer。I'm going to say。

 can you please tell me。If。I'm able to run locally， anything from the documentations folder。

I'm wondering if we can run that index do HTMLm file to see what's in there。

 and I'm just going to go like this at documentation， and we're just going to tag the whole folder。

And we can run this and yes， you can run the documentation folder looking at the files here。

 it is generating the command and this command is on the terminal and it's running it and then it should give me a link where I can run this locally by the way。

 so these commands right here when you're using agent mode。

 when you first see one of these you're probably going to get like an accept or reject these in your terminal because this is the terminal right here。

 you can see the integrated terminal， you can find it right here， however。

 they show up right here when you're in the cursor agent mode。

And there is a setting within cursor that allows you to bypass the accept and reject。

 and it automatically accepts them。 And that's the mode that I have on。 And it's called Yolo mode。

And if you go to general features and then scroll down to Yolo mode。There enable Yolo mode。

 I recommend starting with that because I don't even fully know what things I should accept or reject so yeah。

 I just have Yolo mode on。And so let's go ahead and get out of that。

 And here it says that it is running on local host。 So I'm going to copy this。



![](img/1500f029842088de157b5aeb1cb6d5d3_43.png)

What I'm going to do， I'm going to open up a new tab。



![](img/1500f029842088de157b5aeb1cb6d5d3_45.png)

And we're now running this。 It is just a gray screen。 So I'm just gonna to say that。

 and we'll see if there's something's wrong。 Let me see。

 let me check the structure of the main index do HDl file。 I see the issue。

 The documentation is trying to load some resources from paths that don't exist， Got it。

 So now it's automatically running these commands， you can pop them out into the terminal。

 if you want to see them。 Sometimes that helps speed up the process。 Okay。

 so now we're running it on this new folder。And so we can type in logo hostst slash documentation slash examples。

 so we can click on these。

![](img/1500f029842088de157b5aeb1cb6d5d3_47.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_48.png)

Got it。 That's cool。 Okay， really cool。 So this is one of the animations you can create in this library。

 And now we're。😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_50.png)

Checking this out。 See， And this is why I love Github so much。 I just downloaded this code online。

 And now I'm getting so many ideas。 Let's decide what our project is while we're going through these。

 I want to create， recreate the lovable landing page。 right， idea to app in seconds。

 except we're gonna make it sick。 We're gonna add some extra things to it。 and it's gonna be awesome。

 I just thought of this as a good starting point。 This is the app that we'll try and create。

 We're just gonna to use theirs as an example。 Let's do that。 But let's use these from the library。

 Let's just keep going through this。 Oh， wow， that's sick。 Actually， That's insane。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_52.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_53.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_54.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_55.png)

Okay， so the first thing that we're going to do is we're just going to screenshot this app right here。

 Let's go ahead and just get this whole page。

![](img/1500f029842088de157b5aeb1cb6d5d3_57.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_58.png)

What we're going do is we're gonna copy this to our clipboard。 Now。

 what we're going do is we're going to open up cursor。



![](img/1500f029842088de157b5aeb1cb6d5d3_60.png)

And we're going to say the following。 So let's close this up real quick。Cllosed documentation。 Now。

 what we're going to do is we're going go into composer agent mode。 And we're going to say。

I want you。To create a new document that is a landing page for my app。

And I want you to start off by making it look like this。Except where they mention app。

 I want you to say design。 This is going be an idea to design tool and。

It's an agent that creates designs。For you， and it's going to be awesome。

I'm going to paste that picture in here， Call it。Agenimate the agent who animates your ideas。

Build this site。This landing page， except I want you to use。

Some cool animations in that just around the app that match the examples in the。😊，And so yeah。

 we'll see how it does here， so here it says let me create a modern landing page。

 it's creating an index。 HTMLtm file and this will likely be added over here and there it is。

And so we can take a look here。 and it is 236 lines of code。And let's see if they ran it cool。Okay。

 so we're going to accept this。 Now Im going to say run this locally。 Let's see what it does here。

So it's now running this command， our servers now running on local hosts 3000。 what we can do。

 Let's go ahead and come over here。

![](img/1500f029842088de157b5aeb1cb6d5d3_62.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_63.png)

And we are going to go like this。 And here we go。 idea to design in seconds。 your superhuman AI。

Design partner， dart creating today day for free。 Okay， I like it。 I don't like the orange。

 Let's first specify， change the orange to like a dark like a red pink， all instances of that。

And idea to design in seconds。嗯。Okay， features pricing about how did lovable look。Okay。

 so we're gonna need like some sort of logo。To go right here。 And let's just get rid of these。

Right here， these sections are ugly。 get rid of them。

 And here I want you to create a really cool animation and use anything that you need from the examples folder as inspiration to create the illusion that。

😊，You can animate anything with just your ideas and you can use an AI agent to create your animation。

Let's go ahead and press， accept。Now we'll come back over here。 We're going to press command R。



![](img/1500f029842088de157b5aeb1cb6d5d3_65.png)

And here we go， okay。I like the idea that it has here。 I actually sort of dig this。

 Let's go ahead and upload this right here。 Okay， I actually really like this idea。

 Instead of just having like it being typed out to the talk。

 Can we actually make the typing look more like。😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_67.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_68.png)

Real， let's actually put perplexity on。

![](img/1500f029842088de157b5aeb1cb6d5d3_70.png)

Dark mode。Okay， let's use this right here。 And I included an image。

 ignore the buttons and everything in there。 Please make it look like that as you type just like a clean input field。

 except make it way。Taller and include the animation。

 like and make the components that it's animating like really， really cool。

 And if you need to make a different file and then render it in index study Hml。

 go ahead and do that。 I know the index Hm L file is getting larger。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_72.png)

Allright， let's take a look。 Okay， make it float。Now， spin it。Not bad。Let's make it more all right。

 kind of ugly， but I like the idea。 I'm going to go ahead and screenshot this。



![](img/1500f029842088de157b5aeb1cb6d5d3_74.png)

There's too many like pills or backgrounds of components。

 It should be just that like light gray that's in the background。

 and then there should not be those two containers around the text field。

 nor should there be a new black container around the animation。

 And let's choose something else for the animation。

 like make it like a really cool component like a full component。

 come up with some realistic changes to like a full component。

 make it look like a computer component and then say change the aspect ratio and then have it change from a horizontal rectangle to a vertical rectangle。

 And so just focus on cleaning up just this component。Okay， let's go ahead and accept this。



![](img/1500f029842088de157b5aeb1cb6d5d3_76.png)

Now let's go back to our design here， Age gen toimate， we're going to refresh。



![](img/1500f029842088de157b5aeb1cb6d5d3_78.png)

Nice， I like this back to horizontal。 Okay， so let's refresh it。 What does it do here。

 It's a little underwhelming。 Make it horizontal。 Make it a black to blue gradient with a call to action。

😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_80.png)

Then， reflect。

![](img/1500f029842088de157b5aeb1cb6d5d3_82.png)

That change then for the next one， which is make it hover and make it glow and have a。White glow。

Behind it so we can fully customize this。All right， let's go ahead and accept all now command R。

 and here we go， let's make it horizontal and make it a black to blue gradient。All right。

 that got cut off。 So it's starting off on this。So it's starting off on this one。

 also make them faster， so make the typing speed faster and then also make them loop so that they should never stop。

Okay， this is cool。 Let's go ahead and hit， accept。And we're going to hit refresh， okay。

 so it's not perfect。We screenshoted it， we're putting it back into cursor composer。Okay。

 I want you to take a really close look at the component that has the typing and the changing components。

 I need you to make sure that the previous change is held there。

 All of this seems like an endless rotation And so you should change the last animation to the first one and make that match in the prompt。

 So it's like a continuous clean flow。And yeah， we can just ideate， we can take all of our ideas。

 and we'll watch it go to work。Okay。Let's see。 Okay， that looks a little bit better。

 I get vertical and hover good， now rotate it。Okay， not bad。 Stop rotating and make it big。

 Shake it up。 All right， al right。Okay， that's not a bad rotation。 I feel like that's pretty smooth。

 Please change the font to popins。 And then I want you to add another component that shows the assembling of components。

 And I want you to use examples from this。 And if you as remember earlier。

 we started going through some of these documentations。 And so here's this transforms demo。



![](img/1500f029842088de157b5aeb1cb6d5d3_84.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_85.png)

And。This is in the files， so in the examples， there is this transforms demo and match。



![](img/1500f029842088de157b5aeb1cb6d5d3_87.png)

The color of this site。 Let's take a look and see what it did。 So let's go ahead and accept this。

 We're gonna press command R。 So we still have this。This is Wack。

 I literally can't see anything on this。See how small it is down at the bottom， what's going on here。

Can you please make this？😔，嗯。This new one make it。These circles go into the middle and then flash out to like a really clean red component that looks like a section of a website。

Wow， in white， I want to add text to that。And then I want you to get rid of that gray background that's behind it。

 Just have it on without any background that red stuff。

 and then move that up above the component that shows the typing to edit the animations。

 just have the header text on that。 and then also rotate everything down。

 you in in your recent changes。 you moved everything too far up。 And now it's off the screen。

 So we're now typing these in。 We're making changes。 We're just vibbe。

 like this is the essence of vibe coding。 we're using this package that we learned。

 We found this example in the documentation。 And I like it a lot。

 And it's like takes all the like your idea shoots it into the middle now， shoots it out。Okay。呜。

That's kind of clean every time that there is。A new component that it pops up because right now it's on a loop where it circles to the middle and it pops out with a component。

 I want you to change the component every time it comes out。 So now it's horizontal。

 And then I want it to be a vertical component。 And then I want it to be a component with a square in the middle that has like animating or a rectangle in the middle that has like animations going through it。

 And yeah， keep the top bar the same。 and the the outboard the same for all of them。

 So it should all look like a Mac window。 Okay， let's see。Boom， I dig that。

 So that's a good first animation。 Let's see the second one。Alright， I dig it。 I like it。

 It's a cool design， simple， easy to understand。 That one's a little bit much。😊。

And then it should loop， okay。Cool， I actually like this。

 And then this can be about like editing your。😊，Animation。

 and so I think we should add a component between this。 Let's go ahead and say that。

 So let's open up a new composer here。嗯。Let's screenshot。This， okay， that's good。

 In between these two sections， I want you to make a testimonials section。And I want you to add like。

 this should be like， and there should be spacing in between the top of this component and then the bottom of this new component。

 And I'm gonna give you an image of the style to follow。 And then we should go back to lovable。

 I liked their section。 I guess theirs was a little bit lower。



![](img/1500f029842088de157b5aeb1cb6d5d3_89.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_90.png)

Use this except come up with ones for like creating designs， so it should be a very similar idea。

 but just like focus mostly on designs。All right， let's see the changes here looks good。

 Love by design innovators。 change this to。Blue text。What else here， Let's， let's see how it looks。

Like this。I mean， this is pretty solid。I like it。 And it's like narrow， as it gets skinnier。嗯。

I think。Between these sections， add a line like a white line that doesn't go that far across just a little line break。

Make it。Look， cool。 this separates。The sections。Okay， so this is coming together。

 Take a look at this。 So here's our app。And we can scroll down， loved by designers and innovators。

 and we have this edit section， I do want to add a few more things。For this bottom section。

 can you please add a title section that says edit your animations just by typing。

And please add a white line break between this section and the one above it。 very similar to the。

 the other line breaker。 Okay， so now we're gonna hit accept。 let's refresh this and looking good。

 Love by designers。 nice。 Where's my header。Where's the header that says edit your animations with typing right here。

We do have this line break， Please add a footer at the bottom and I want to be to scroll down to get to the footer。

 so a good amount of spacing between the last component and the footer Okay there we have it and we have loved by design innovators and edit your animation just by typing and this looks pretty good and we added this footer So let's say that we're done and we're like。

 okay let's go ahead and put this on the Internet we just vibe code at this we had a good time going through the motions using cursor now we want to put this on the internet And so the first thing that we should do is we need to go to GiHub。



![](img/1500f029842088de157b5aeb1cb6d5d3_92.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_93.png)

And on Github， create an account。 And I think we talked about it earlier。

 but we created a Git repository。 and we need to do that again。 So this repository name。

 I'm going go ahead and make this public so you can see my code。 If you go to my profile。

 I'm going call this a。Engenimate。And I'm going to say a Genimate landing page， make this public。

 and we're going to hit create new repository After we create the repository。

 we are going to click copy。

![](img/1500f029842088de157b5aeb1cb6d5d3_95.png)

Now we're going to go back to cursor and in a new composer。

 we are going to paste in this link and say。Push。嗯。

I created a new Github repo at this link right here。 I just initiated it。

 and I want you to push this code to that and it is a public repo。

 Let's put it on Github and when you say before you do this you might need to say I want to sign in on Github please help me do that and the agent will actually help you do it So you need to set up an account on Github the first thing you're going to do is set up an account on Github and then tell the agent you want to set up your Gitthub account and it will take you through the steps to connect cursor to Github because I have these connected So all I need to do is this and I can just run this and it will actually push our code to Github and you'll be able to fork it and use it immediately within your own project to use it however you want to use it。

 So it says now let's stage all the files， let's push the code to the Github repository。



![](img/1500f029842088de157b5aeb1cb6d5d3_97.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_98.png)

Here， this is what we want to see。 We want to see that files are being uploaded。And we wait。Great。

 I've successfully pushed it。And all we need to do， I believe， is press command R。



![](img/1500f029842088de157b5aeb1cb6d5d3_100.png)

And there we go， here is our code。And we are now on Github。 Now what you're going to do。

If we want to put this on the Internet， there's a lot of apps you can use to put it on the Internet。

 We're going to deploy it to ver， and。What were going to do。

 since we've already pushed to have GiHub， we can import the a Genimate landing page that we've created because when you sign into Versell。

 you'll sign in through GiHub so we can press import。Framework， other root repository。

 Let's just hit deploy。 Let's see what happens if we do this。

 So we are using verll to put it on the Internet。 They're going be hosting right now。

 we're using local host， but we need a provider to host it。

 So other people can go to the site or app and use it。

 And it costs money based on how much it's used basically。

 And so what we want to do is we want to get it to successfully upload。 However。

 there are some requirements。 So what I'm going to do is I'm actually gonna copy this link。

Right here， yeah， so the project name I'm going to copy this and I'm going to go back to cursor and I'm going to say I just tried to deploy this app to Verll and I got this error and the error message popped up on versll and it said this right here。

 please fix this and prepare this project for deploying on Verll and then do it。



![](img/1500f029842088de157b5aeb1cb6d5d3_102.png)

And so cursor can actually communicate directly with Verll。

 And again you might have I forget how the sign in process works。

 but just say you want to sign in verll to your cursor agent and you will figure it out。

 I remember I did it when I was first starting out， it wasn't too difficult。

 And if you could always ask perplexity if you run into any problems。

So I've made the necessary changes。嗯。Okay， do it now directly and give me deployed link。

I know for a fact， you can。Yes， you can've。Done it。 You've helped me do it many times。

Sometimes it doesn't think it can， but it can。Yeah， I apologize for my oversight。 You're right。

 We can use the versll CI to deploy directly。 Let's install。 Alright， cool。

 and then it's gonna ask you questions here。 Just press， I just press enter， no。

 link to different existing project。 No what's your project name。I think if you just press enter。

 okay， now you have to type something in landing a gen in what directory is your is it located。

 just press enter and now this is loading。 And so now this is being pushed to verll。

 It's building we'll see if it succeeds。 says great。 your project is a success。

 and then it gave us this link right here， you can also inspect the deployment there。 Okay。

 so let's paste this in and there we go。 idea to design in seconds powered by design innovators nice。

 great， so this is deployed at this link right here， a Gen landing page do verll do app。

 so that means you could type that into your web browser and you should still be able to it。

 I don't think I'll change it by the time you watch this video。



![](img/1500f029842088de157b5aeb1cb6d5d3_104.png)

But you can now see this app or site on the Internet， which is what we want。

 We're building this app for other people to see as well。 So， yeah， you can see it。

 but you might be thinking， wait， I hate that domain， right， I want to choose my own domain。 Great。

 Let's go over that process。 Let's go to a website like nameche。

 You can also use Godaddy or wherever you buy your domains。 I personally buy my domains on nameche。

 And before this video， I purchased 1， just like thought of one that would be fun。

 And I thought a genimate was a cool name。 It was $11。 It's pretty cool。 So I bought it on。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_106.png)

Name cheap。 It's where you can buy domains。 You can simply type in。

Names of websites you want to buy and you can buy domains on nametu。 I bought a Genmate dot com。

 I am going to go to advanced DNS settings， so。What am I gonna do， Okay， yeah。

 so I'm going to go after I bought the domain， I'm simply going to select the I'm gonna click on dashboard。

 And then what I'm gonna do is I'm going to hit manage on a Gen do com。

 And then what I'm going do is I'm going to press advanced DNS。

 Then I'm going to delete these right here。 Now what I'm going do is I'm going to go to Verll。

 and I'm going to bring Verll。 I'm going bring Verll side by side So I'm actually going just I'm going go back to Versll's homep page here we have a Genimate landing page。

 We're gonna click on this We're gonna click on settings。 I believe。And we're gonna click on domains。

 and we're gonna to click edit。 and we're gonna click， and we're gonna use a gen。Dot com。

And this is production， no redirect save。Wai， I did。Something wrong。 I added it M after there we go。

 Okay， save Now it says set the following record on your DNS provider。 And so this is an a value。

 And so all this means is it's a type a name at value 7，6621。

21 What we're going do here is we are going to go to on name cheap we're going to pass add new record right here。

 add new record And this is going to be an a record and the host is going to be at。

So a at and then this value right here。And then we're going to press， save changes。 Okay。

 and then I realized we actually need to add a C name。

 So I just asked cursor what I need to do to add a C name。 And here it is。

 So we need to enter C name record with a value of this。

 So we're gonna add a C name with a value of this。

![](img/1500f029842088de157b5aeb1cb6d5d3_108.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_109.png)

And then WWW， so WWw。And we can hit enter。And we should be good。 So let's refresh this。

 And so all we need to do now is we need to type in a genmate。 And here we go。

 It is on the Internet at a genmate do com deployed on the Internet clean website right here。

 And so we did it。 We did some really cool design work in my opinion I don't know about you。 Okay。

 so before we move on to a more complex project with databases， authentication， more AI features。

 I just want to do a breakdown of what we've done。 So let's really think about what we've done in this last section。



![](img/1500f029842088de157b5aeb1cb6d5d3_111.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_112.png)

We went to perplexity and we explored perplexity， which is an AI powered search engine basically and we just looked for any open source GitHub reos that have cool animations。

 cool libraries that make cool animations and so we did that we found this GitHub link it was called anime on GitHub and it had like really cool animation examples and the animations are really cool and so we basically forked this project。

And we did that by simply pasting this link into cursor。 So all we did was ask a question。

Find a link， paste that link into cursor， and then it loaded all the files from that link。

 So it's like a starting template in cursor。 and you can see the files in the left window。

 and then we iterated on it。 We asked it to create new files and to use examples from the files that were in this Github repo and it used the examples and it created a pretty cool design if we go to a gen to do co。

 we can see that I don't know if I would have created this without that one example that we used。

 and I just think these are like pretty cool animations。

 obviously we didn't spend that long like 30 minutes making this but I think this site looks pretty good for just like and then here it says now rotate it and we created some pretty cool rotations and we use this random Github repo as inspiration which is pretty cool。

 And so and we were running it locally just by asking composer。 you just ask composer。

 run it locally。😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_114.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_115.png)

So that's how we could see it in the local host so every time we made changes to the code。

 we could see it on this web view once we were done， we deployed it or we committed it to Github。

 we posted it on Gitthub， I don't even know the vernacular I just know that if I say put this code on Github after creating a repository cursors like yep got you fam and then it uploaded the code to Github we can go to Gitthub right now and we can see that we have created if we go to our repositories which are just like the projects that we create we can see this a Genimate landing page and here we see all of our code。

 we just ask cursor to make this and then we deployed it to Verll and you can always just ask cursor for all of the instructions on how to deploy a verll depending on the type of code you have this process might be a little bit different。

 but with AI if you just ask AI how to deploy it you will you。Can get it deployed to verll。

 And once you get it on verll， it'll give you this like app domain。

 So I'm pretty sure it was like verll dot agenimate dot verll do app or something like that。

 And then we used nameche。 I bought a Gen do com for fun。

 And then I connected that domain to the verll deployment。

 And so they're basically hosting the code so that any time anyone can go to it and use the app。

 They are hosting it。 So that's kind of the overall thing that we did。

 So now we're gonna do a very similar process I'm not going start off by finding a repo。

 We're gonna start off with our template once again。

 And now we're actually gonna build an app that not only not only can you go and see the app in local host。

 We're also going to add。😊，A database， which means as the user。

As and so it'll be like an internal company tool that will allow you to do something important。

 And each member of your team will be able to sign in。 And so it's gonna have a database。

 meaning the work that they do on this app will be saved to their profile。

 So it's gonna have a database。 it's gonna have authentication。

 because in order to store the data in the right place， you need to have authentication。

 So it knows what users signing in。😊，And yeah， we're going to do a database authentication。

 We're going to have multiple。AI features and we're going to do this same process again。

 except we're going to create a useful tool and so I wanted to in this video I really wanted to get some repetition and do many projects so you can see it get practice doing different types of projects because the only thing that will make you better at this is finding ideas and taking action and trying to get to the final outcome。

 we are going to be focused on the outcome I want to talk about the problem that I want to solve with my next app and the problem that I want to solve is somewhat niche It would help me and I think it would help a decent amount of other people I'm not saying it could be a millions of user app but my problem is that I love the new deep research feature from chattPT Currently it is only on the $200 per month plan and it generates full research reports after thinking for a very long time。

And the one thing I don't like about it is it's just too much text。

And so I want to be able to export it with cool images every once in a while。

 So I want to create an app that allows me to just come in here after it does all of this research because it's just so like look at how long this is。

 and I want to be able to copy and paste this research， copy it。

 paste it somewhere and then be able to add in like a for each section。😊。

Add in a graphic and as we've been talking about recently。

 we've talking a lot about ja and HTML graphics this video。

 that's how we created our landing page and we could easily take this information and generate a chart。

 generate cool quotes cool animations to actually make it more fun to read so that there's a lot more images and things like that。

 So I think that would be a fun project to work on and yeah。

 I'll show you let's go ahead and let's just let's dive into this。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_117.png)

The first thing I want to do is I want to come up with just some ideas on what these charts will look like。

 so create a chart using examples to show how many programmers will exist in 2030 from now 2025 from 17 million programmers to 100 million。

 make it elegant。And cool。 Okay， so I'm just trying to get an idea of what it'll look like。 I mean。

 look at these charts。 like we could have it automatically generate these charts to show different ideas。

 And this is just really cool。 So yeah， let's just send it。

 And so what I did here is I just pasted this image into bear。😊，To bear note。

 and I'm gonna to just get a screenshot of this。 And now what we're gonna do。

 I'm gonna copy that to my clipboard。 Now let's just list out our idea at a cursor。

 So we're gonna go to cursor。 Okay， let's get started on our project And we've done this process before。

 We're gonna start using our react native template。

 and all we do to do that is just go to cloneone repo and we're gonna to paste in a link from Github I have it pinned to my clipboard app that I use so I can just immediately access it。

 I use it all the time and we're gonna press enter and we're going to I'm going create a new folder and I'm going call this deep research view and I'm going to hit select repository destination。

 and we're gonna hit open。Now， what we're going to do is we're going to press command I to open up composer。

 We've done this before。 Remember， and we're going to hit agent。 My idea for an app is。



![](img/1500f029842088de157b5aeb1cb6d5d3_119.png)

And again， so here is just a quick outline that I created of my app idea。

 And I actually had to think about this for a second because I'm going to do this in steps。

 So the steps will be to allow the user to paste in a link right paste in an deep。Research。诶。

Markdown report， right， It's just text and markdown format。

 And then this will automatically load blank， blank animation canvases。

And I want to be able to click on those canvases。And paste my own code to create those animations。

 And you might be thinking， wait， why wouldn't you use AI to generate that And then also like why wouldn't it happen automatically And Ive found that when you're using AI features。

 figure out how to get it so that you can just paste it in and then you can basically use AI to create the process of pasting it in right because we want to solve this in steps right we want to solve these being able to be rendered right these cool animations to be rendered in a markdown format right and we can paste in the code for each one and then we can add the AI features that where you can click on the code describe the image and then AI will look at the page for that section and create a chart for you but I think the best first step would just be to do it manually and I think we can do it relatively quickly and then we can figure out how to use AI to generate these animations based on。



![](img/1500f029842088de157b5aeb1cb6d5d3_121.png)

A list of examples。 So let's go ahead and get started。 We are starting from this template。

 And remember this。Template right here， built in， right。

 This template built in has the ability to sign in with Google。

 And so we can actually set up the database and the authentication right from the beginning。

 And in this case， I'm actually going to do that。 for my idea for an app is。

 I'm going to paste in that text that I just showed you。

 And then I'm also going to paste in that image that I took。😊，Like this。

 which is like the bare note that shows how it's a markdown file with a cool chart。

 The user should immediately。Have to。Sign in。With Google， if not signed in。

 they should not be able to add。The report。Paste。In markdown。Okay， so we're pasting that。In there。

 And it's going to go to work。 And while that works， we actually need to set up our database。

 And this process is actually simpler than it looks。 And we are going to be using Google Firebase。

 There's a lot of different database providers you can use。



![](img/1500f029842088de157b5aeb1cb6d5d3_123.png)

I think Firebase is the best to use when you're starting out because it's the easiest， in my opinion。

 And Claude really understands the documentation of Firebase。

 It just understands how to use Firebase because it's probably in their training data a ton。

 And so what we're doing here is we're allowing the users to sign in and add data to but you need to hook it up via an API very similar to how we set up the image generator API earlier。

 We need to connect basically， I think of this like a Google cloud for the app。

 That's basically all a database is。 And so we need to create a project on。



![](img/1500f029842088de157b5aeb1cb6d5d3_125.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_126.png)

Firebase Google dot com。 That's what I've done so far。 Go to Google Firebase Google do com。

 It's free to get set up。 And if you used it for your internal team， it would be free for a while。

 It's it doesn't start getting expensive until you have a lot of users or you have a lot of data uploaded。

 And so let's go ahead。 We're gonna type in our project name。 And we're calling this deep research。

 visual。 I forgot what we call。 it doesn't matter。 We're gonna hit continue。

 And then it's gonna ask us to enable Google Analytic。 I'm not gonna do that right now。

 that adds an unnecessary step that we can always go back and add that later。 And so this is loading。

😊，And。Basically， what we're doing is we're setting up a Google cloud the same way you have your docs and you have your spreadsheets in your Google cloud。

 We're setting that up for the project。 If you go to my app and sign in。

 this is where the data will be stored。RightThe data will be stored on Google Firebase。

 and you can think of the database as anything that you would put in a spreadsheet like text like dates。

 links， URLs， things like that。 We'll go in the database。 And you can see here。

 we can build a lot of different things right here。 We can create a firestore database。

 We can create storage。 We can create authentication。 And we're gonna to do that in just a second。

 But what I want you to focus on is right here， we're creating a web app。

 So we need to actually create a web app。 And we need to get Firebase keys for this app。

 And so I'm just gonna to call this visual， It doesn't matter。 Reg the app。

And what this is going to do here is this is going to give us some API keys。

So there are six keys that it just created for me。 I'm covering these up because you need to keep these separate。

 always keep your API keys private。 And so it gives you an API key in off domainoma project I storage bucket message sender I and app I do not don't look into these。

 you don't need to worry about that for now if you're just getting started。

 you just need to paste these keys into the template that we've created for you。

 and I'll show you exactly where you need to do that。 So below the keys。

 there's actually this copy button And what I'm gonna do。Is I'm going to come back。

 I'm going to come into our composer and say here。Are my keys Put them where they need to go。

In ENV file， format them properly， please， now。 all right。

 now I'm going to paste them and run this prompt。 I'm going to do it off camera because I want to keep those keys private。

Awesome， so it added my keys into this Ev。 local file， which is great， so now we are connected。

 the API keys are connected， but there's one final step that we need to take。

 we need to actually go and create the database and these are only a couple clicks so we're creating this database。

And what we're doing is we are going to create a database here。

 we're going to hit next and we're going to hit start and test mode， create Once that is done。

 it should look like this。 This is where your data will be stored。

 then you're going to hit build again， you're going go to storage and then you're going to press this button and you want to upgrade the project。

 So once you set up this payment account this。I'm pretty sure you will not get charged for this。

 And you can create like a maximum budget。 You can literally make it $10。

 I'm just gonna say $30 for this。 This is once you like。

 really start update like uploading a ton of things to storage。

 They basically just want you to create like a payment account for it。

 And so we're just gonna continue。 And we're just gonna hit link。Billing account。

 And we're gonna to hit done。 Once it's done， it should look like this。 final step。

We need to add authentication。 This will allow people to sign in with Google for any site that you come to and you're like。

 sign in with Google， That's exactly what we're doing right now。 You're going to get started。

You're going to hit Google， you're going to hit enable。

 you're going to hit whatever your default email wherever you created this account with will be this support email for the project and just hit saveve Once you do that we are done with this page we can go back to cursor for the rest of the time Okay so we ran that first prompt and then we said to put the API keys where they need to go for the Firebase。

And so now I'm just going to ask， please run this locally。And。

You could also go into terminal and type in NPM Run dev to run it。

 But let's just go ahead and make sure everythings set up properly。 and when in doubt。

 just use the agent because it has access to every feature on cursor。So please run this locally。

Then we're going to click on this link， local hostst 3000， and here it is。

 so welcome to Deep Research。View， we can just press sign in with Google。And this should work。

 We should be able to sign in with whatever email we want。괜태 you。We've created this account。And okay。

 so it just has an input mark down。And。I want to be able to paste in this link right here。

 So let's just go ahead， and I'm going to paste this in。To our app。And look at this。

 We now have this right here。 We have， obviously， it's not perfect。

 This seems to be some like weird coding formatting， which is fine。 That's cool。 I like it。

 This is good。 And then it has these add。😊，Animations， and so if we click animations。

 we can paste our anime animation code here， create example code right here。

 And I'll copy it and paste it in there。 createate a doc that I can copy。The whole thing。

 and past it in。Okay， we need to test this again， so we need to go to cursor composer the same thing that we've done earlier。

 you need to go back to localhost， you need to paste it in。Okay， hopefully it fixs the error。

 what we can do is we can give it one of the code snippets that it suggested for us。

 so we'll click add animation and let's go ahead and paste in this one。Save animation。 There we go。

 We have a very simple animation there。Okay。This is cool。 This is cool。

 I can very easily see how we can create the app that we want here。

 Let's actually go to a new composer window。 I'm going to paste in this text。 And I'm just gonna say。

 please give me。😊，Another one that summarizes this first section。Add here。To adhere to proper。

Foratting and sizing rules， just give it to me in chat， not in code， in the code base。

And so we're just going to tell the agent， okay。Whoops， I didn't paste in。This。

 we'll paste in this right here。Becauseuse we want it to summarize the cursor composer。

 Welcome to cursor， your favorite companion。 Okay， yeah， we're going need to make。Some。

Changes to this。 But that's okay。 So we can actually， oh， it still goes。 We can remove this。

 So like if we remove it and hit save animation， oh boy。😊，Okay， that might be a problem。

 but let's just pacee in， hit save animation。Okay， now it just says， welcome to cursor。

 your friendly animation companion， make it more fun and more light movement。 Have a。😊。

Placeholder logo for cursor， and。Make it。In the center。And then， have。The key topics。

 like going across the bottom of the screen， like a ticker of like a stock show at the bottom。

 I don't know。 Oh wow， Oh， wow。 This is long， okay。Chill bra。Let's copy this。Now let's come here。

Paste in the new one， save animation。Okay， welcome to cursor， Realtime help。 Okay。

 so we can make these better。 We can make these better。 Okay。

 so I just spent like 20 minutes trying to get these diagrams to be consistent。

 and I just didn't like it。 I wanted I want to spend like4 or five hours trying to find like really good examples for animations。

 And I can always add it in。 However， I am using mermaid diagrams。

 And for mermaid diagrams are these diagrams that are a lot more predictable。 And so I can go。

 for example， I can go to Clad。 for example， this is a mermaid diagram。

 And this one doesn't look that good。 I can say I can pace this in， create a simple mermaid diagram。

😊，Choose the type。And create。诶。1 in plain text here in the chat。 Okay， so here's the the text。

 This is a very simple mermaid diagram。 This one's gonna be very small， but you can paste it here。

 Save diagram。 And this is what it looks like。 The subject desires the object。

 the subject imitates the model。 and the di。 it's actually way better。 make a longer one。

That shows more features of of his theory。 use your training data， not what I pasted memetic theory。

 And I actually think that looks pretty good。 You can actually change this。 So like， you could。

 you know， imitates。You know， it changes that right there。 And so here we can copy this one。

s click this， save diagram。Okay， so this is a lot。i。Because we can't even like really see that。

 So like sacred violent cycle， scapegoat mechanism。 But anyway， it still works， right。

 This would take a little while to analyze。 But the point is。

 we can actually create these mermaid diagrams。And it's pretty cool。 Okay。

 so I'm going to show Claude this example right here。 I'm actually going to do it on this one。

 Let's pick a good section， okay。😊，I'm going to paste in that earlier one。

 this is a simple mermaid diagram。 and what I'm going to do is I'm going to screenshot this right here。

Im to paste it into clo。 Now I want to use the clo API on these。Placeholders for mermaid diagrams。

 I want there to be a button that uses AI to generate a mermaid diagram for that section。

And what it should do is it should look from because these are placed right below the headers。

 And so it should look from header。From the current header that you're working under to the next header。

 And that's where it should get the information from。

 And so that's what it should use as the input prompt to generate a mermaid diagram。

 And the output should only be a mermaid diagram。 And what I'm going do。

 So now we want to use the Cla API。 And so for those of you who've never tried Cla。

 this is Cla right here。 we can create a new chat。 we can say hi， And this is Claude。

 But we want to access this technology within our own app。

 which means you should either go to perplexity and say give me examples or type in Cla documentation platform。

 And this should so we're looking for the documentation。 And so I'm just gonna copy the docs for Cla。

 and we're gonna to paste these in。 So docs for Cla paste that link right there because cursor can actually access this。

You can also add documentation。 Maybe we've done this earlier in this video。 I forget。

 But this is a really good thing to learn。 You're going want to go to features。

And you want to go to docs。 We're gonna add a new docs。

 And we're just going paste this in right here。 And then we're gonna name it。 Claude API doc。

 confirm and。And instead of just pasting that link from now on， we can just type in Clade API docs。

 and it's actually indexed all of these so it can go through and itll look exact it'll look for what it needs to find right here So docs for Clade。

API docs。嗯。And API key， Im past， I'm going run this。

 I'm going to paste my API key and then run this prompt。

We also need to create a key on console do anthropic do com。 And this is where I can get a key。

 I can press create key right here。 I'm not going to do it on film because I want to keep everything private。

 And so now it's installing this anthropic package。 Hopefully， this works properly。

NowWe are watching it load in real time， and I'm gonna to hit accept all。

 I'm gonna say put API key in E V dot local because I saw that it didn't。

 It actually put it directly in the code instead of putting it in this secured EN V dot local file。

 So we need to do that。 I guess I could have just put it in there manually。

 but I'm trying to show that you can just do everything from cursor composer。

And so I want to test this， and I want to make sure nothing goes wrong。

 or I want to know if something goes wrong。 when when you first set up an AI feature。

 it's likely that something goes wrong。 There's just so many docs， so many things to deal with。

 But here， what we're going to do is we're going to hit generate with AI。 and let's see。

And so what it should do。Oh。Okay， syntax error in text。We can see it， right？ Oh， okay， so it added。

 I like this。 We can actually add this。 I think we just need to get rid of these， this。

 I believe this will work。 maybe， Okay， Yes， why is it so small。 We can fix this。

 We'll figure it out。😊，Oh， okay， so we can hit generate with AI。 We do multiple at once。

 So the API route worked。In its first go， except it generated。These with these weird。

 which we actually need a copy。 Okay， please make sure in the AI prompt that this formatting is removed and we can paste and so it is so at beginning this is added and then at end。

This is added so we can run that based on those changes。 let's see how this does。

 So let's choose a new section， historical examples of memetic rivalry generate with AI。 Okay。

 so it's working。 However， these are really small。 They're not being shown full screen。Okay。

 this one is。So the vertical ones are shown full screen。

 but it seems like the horizontal ones are not。Some of these are being shown full screen。

Some of them are way too small。 Can you please look into this and try and fix it。Alright。

 this is starting to look really good。 like triangular structure of desire。Like。

 I actually really like this for whatever reason， this one has a syntax error。

 but what we should actually do here。Is we should have， first of all。

 we need to have a button to view them。 I want a button at bottom right of these charts。

To allow me to see the mermaid diagram full screen。

And then have a little X to exit out and go back to scrolling down the the， the kind of the。

 the article。 And then I also want to have an edit chart。After the chart was already generated。

 I want there to be little edit icon beneath it。If pressed， it allows me to change。

 so add a new AI prompt using Clade to change the existing code and the output should be the full code of the mermaid diagram with the changes that I said。

 only the output， only that output。 Okay， let's see。So。We can generate a chart for this one。Okay。

 and now we can。嗯。So we can press this。嗯。The full screen feature should be a modal that pops up full like almost full screen that like pops ups for so I can look at the mermaid chart full screen。

And then， the edit feature。啊。哦啊。So。No， okay， it didn't get that one。 Okay。

 so now we can view it full screen。 That looks good。 Let's see if it works with a bigger one。

 Let's just start generating these。Yeah， I like this。 We should make this animation cleaner。

 syntax error。 We keep getting a syntax error on this one。 No， no， no， what's going on here， Brah。

 What happened。Show me what is the syntax error。Maybe it's cause I tried to do multiple at a time。

 Okay， so now we can view this full screen。 That looks cool。😊，Nice。Now what we can do。

 and now this edit button just lets me edit it。 Let's create a new page because this context is getting quite big。

 And I'm just gonna screenshot this right here。 So it knows the full screen feature within the mermaid diagrams where is working pretty well。

 But the little edit button at the bottom right。 I actually want a little chat field to pop up when I press it。

 That's not to actually edit the text directly。 I still think you that feature should be allowed if I just click directly on the chart itself。

 It should let me edit the code manually。 But what this feature allows me to do is it allows me to edit it。

 And so it should be a little chat bubble that pops up where I can say make it shorter。

 or I could say make it longer， or I could say change this to a pie chart。 or those types of things。

 You understand， let's give this the test here copying this。 We' gonna paste this in again。

In our app。We'll paste this right here。 Okay， let's go ahead and generate with a okay。

 And so we can view this full screen。It's not full， full screen， but that's okay。 Medic theory。

 medic desire。 Okay， so now we have this like chat feature。 make this a vertical flow chart。Send。

 wait， I've updated the diagram。Did you。Oh， what the。Wait， hold on。 hold on。 Okay。

 I don't think it's working perfectly。 I don't know why it's not rendering right away。 syntax error。

 classic。 Okay， cool colors here。 I like this。 I want to incorporate these colors so we can view this。

😊，But now we can hit chat， we can say expand on these， keep these colors。 I've updated your request。

 okay。So what happens if I click on this？Save， okay。

The changes aren't immediately should as soon as these changes are made。

 it should update the mermaid diagram。 Basically， I have to click on it。

 hit edit and then save again after I've asked for changes。 I want it to just happen。

 It should automatically update。This is when I'm using AI chat to。

 when I'm using AI chat to edit the mermaid diagram。 Okay， let's give it a try。

 Let's just do it with a fresh one。Right here， let's soo chat。

 we can say make this vertical right now it's horizontal。Sen。Boom， there we go。 Look at that。

 So now we can generate a chart here， wait。Generate with AI。 And we're generating for this chart。

 Okay， so memetic desire， rivalry， double blind， oftenane rivalry， Memetic doubles， memetic crisis。

 undifferiated conflict。 So I don't fully know what that means。 we can hit edit here and now say。

 please include。Additional。Additional explanation on what。These mean。Wow， that's crazy。 Okay。

 we need the mark down to render better。Okay。I want you to change nothing except for the markdown or like the formatting of the paragraphs。

 like the headers。Should be more， they should be bigger， right， You know。

 if you look at something like bare note， the headers are bigger than the rest of the text。

 I want something like that。 And in that way， the formatting should be better and more clear about the division of sections。

Alright， so this is actually starting to look pretty good。 The headers are looking solid。

 They're massive。 but like， I like it。 I like the way this looks。

 just like the font and everything looks good。 Well， that's huge。 Actually， that's crazy， okay。😊。

Let's actually go like this。The input markdown should be in the same column as the output。

 except the input should be a drop down that I can place it in and then close it。

 so it should start with me placing it in the input markdown and then the preview should load below it rather than side by side because I want to get rid of this like I just want this to be I want this to be one column。

Okay。Input markdown， we paste it there and we can actually just copy this text right here and what we can do is we can go to this search section。

 we can paste this right here。 We can look for input markdown。

 and what we can do is we can say paste。Your deep。Research。Here， and then this will say。

 paste your deep research here。 and then。The generate with AI buttons。

 The components don't make them like those green buttons to generate with AI。

 where make that just like a nice light gray text with no background when it's empty instead of having that big green button。

 I don't want it to be too to intense。 But while it's loading。 I want you to have like a nice like。

Effect over that component。 And like it should。It's almost like a moving gradient。Over that section。

 Okay， so now let's go ahead and let's test this out。 So major tech companies， open AI， Google。

 this is an AI competitive landscape， a game theory perspective。generateenerate with AI。Wow。

 that's a fire chart。 Look at this。Obviously， we can make this look better。But。

So the game theory perspective is they either competitive or cooperative strategies we have to be like that okay。

So they race ahead or they can cooperate for safety。 Let's generate with AI for this section。

And so this should take into consideration。Competition versus cooperation。

And there is a syntax error。Oh my Lordd。This one's massive， but it worked。

But I don't want to use that as a good example。 This is great。 I love this。😊。

I want this format for all of them。Okay， based on that problem。

 can you update the prompt with as few changes as possible to fix this issue。

 but also I want you to make sure that this problems actually fixed and then the second example that worked above。

 I want that style for all of them like those colors and so just suggest to the AI to use those colors。

Yeah， this is just like pleasing color palette， in my opinion。

 compared to like some of these other ones。 Yeah， like， this is so lame。Okay。

 here's what we have so far。 And then we're going to actually add the database。

 And this does this process does take a while。 Sometimes it's a battle。

 This is not the easiest project， but it's also not the harvest。 But anyway。

 so as soon as we finish a deep research report。 right， I had AI， it thought for five minutes。

 and it gathered 17 different sources and。😊，I want to see better visuals。

 Like I want it to look good。 And so I can just copy this。

 We can take it to the app that we just created， which is local hosts 3000。 There we go。

 Let's go ahead and refresh this。 So this is what it will look like to start。 We'd sign in。

 and then we could paste this here。😊，And here we can generate diagrams。Now I want to。

 as a user who's been signed in， I want to be able to save it to my profile。

 and I want these to be saved as reports and reports should include everything That's on this page。

 including the diagram data， including the including the input text and the output text。

 I should be able to come back to this page as my user as the user signed in and I should be able to access this。

 And since I'm already signed in through Google， this shouldn't be too difficult to save the database。

 Please figure this out。 I'm actually not going enter it in here。 This is a big ask for the AI。

 we want to make sure it as as much context as possible。And I'm going to run it。 actually。

 please create a profile button at the top right that I can press where I can view all of my saved reports。

So basically what we're doing here is we want this， right， we want to be able to see our documents。

 our reports， right these are all the documents that we've saved。And we don't want to just lose them。

 And so that's what we're doing right now。 And so it just got done fully loading。

 And it immediately gave us this error。 So we're gonna copy this。 and we're going to say。Error。

 please。Fix。啊。Oh。Let's go， all right。So let's see， let's see， all right， so wait。

 let's go do open AI， Open AI， Open AI， copy this， go back to this， paste this here， that load。

 save report okay。啊。二位。So back to reports。Okay， so this view report。哈。Call on。Okay， but this， okay。

 So， okay， I okay。咪 see。Okay， so we're here， and the first thing that we can do is create a report。

And so what we can do is we can paste that in。And then we can generate with AI and let's just generate three charts。

 I don't care if they fail for now。 Okay， that's cool。 We have multiple charts。

 let's hit save report。So we saved the report。Okay。When I generate charts and then I save the report。

 the charts are not in the report that I saved， they're not in the right place。

And we can actually go ahead and take a look at this right remember we did Google Firebase。

 that's where this is saving。 So let me show you what that even what that means here so we can actually go to Firestore database and we can see that there's a report and this is the data that's in the report。

What's this？ And so we can see that data is being stored if we go to authentication and we click users。

 we can see that I am one of the users in here。 So as people use your site。Or app。

 their name will be added here。It when they log in and then in the Firestore database。

 this is where the reports are being stored。And so we're trying to get the proper charts to be stored as well。

 and so we'll see how cursor decides to do this。And we'll hit accept。 Let's take a look here。

 I'm going fully reset this。 so I'm going to make a new report。And I just like。

 every time when I'm doing this testing， every single time I'm going back。

And refreshing the local host， because if it made a change to how things are saved。

 and I'm using something that's been saved previously， the logic might be completely messed up。

 And so we want to completely do things from scratch。

 Like you want to start your process over when testing it in my opinion。 I've just。

 that's one thing that I've learned。 So like allow yourself to refresh every time you make a change。

 It'll just help you in the long run。 Let's go back to local host。 We' paste this in here。

 I like the way this animates in now。 And we can close this。 Let's generate， and we'll go down。

 We will generate。😊，And generate。 And once these load， we have these three charts here。2 and three。

 Now， let's go ahead and hit save report。 Let's see if they're here。

It doesn't appear as though they are there。No， that's in the response。Yeah。

The mermaid diagrams were not there when I saved them。

 At least they did not show up in the view where I can view the report。 Allright， testing again。

Sometimes you just got to test things over and over again， Go to go to local host， gotta paste it in。

 Let's generate。With AI， generate with AI， generate with AI， just the first three。 All right。

 this is interesting。 First mover advantage， Multipolar trap。Okay， interesting。Okay， AI Ra。 Okay。

 cool。 Now let's save the report。Yes， there we go， nice。Cool， we did it。 Okay。

 one more thing I want to add on the save on the。Report at any given time。

 I want to be able to export it as a P D F。 So the entire report gets it。

Export it as the entire component that is the report like below the input field that shows like all of the markdown and all of the mermaid diagrams in it as well。

 I want to be able to export it as a PDFF。All right。

 it generated this code now it says it found some errors。

 and so let me fix the type issues with they react to print。Okay。

 so here it is and we can actually just export this and now it's like it made a change where it's like checking to see if everything is like rendered properly and then it downloads and there's a lot of I've done this before there's a lot of different things that you can do to make the formatting proper。



![](img/1500f029842088de157b5aeb1cb6d5d3_128.png)

So like obviously like not a lot is fit on each page， but you know。

 we still got a PDFf created and it has those charts rendered within it。

 And so that's pretty cool and if we go back to reports we can see all of my reports Obviously we can rename and I can add an edit button and a delete button but for my sake right now we've created this app that has a database set up to it and we can go。

 let's go back to home。 One thing that we should add can you please add a persistent top bar to this app that allows me to just access the key pages via icons。

 The top bar should have home and the reports。

![](img/1500f029842088de157b5aeb1cb6d5d3_130.png)

And like， pool。So now we can go to my reports， we can go back home which creates a new report last thing I'm going to do before we're done with this is say。

Create a title in that same。Top bar。 I want you to name it deep visual。 Okay， you know what。

 this is really bothering me。 So Im just w to change it。 my O CD， please for the dropdown。

 please put the past of your deep research here right aligned and in line with that little carrot thing。

 Not below it。 I do not like the way that looks at all。 Oh my God， Okay， that's so much better。

 isn't it。😔，Okay。Now we can say， paste your deep research here。 We can。 now we can。Paste this。B。

It's going to load it up in this clean fashion， and we can begin generating images with AI。

 Obviously， if I was doing this， I would probably have it automatically generate images。

So the user just like immediately gets value and we can save this report we can save this report like this。

 and we can also export them as PDFs， not only this。

 but we can actually chat and we can actually change these include the companies here。

 let's see if this works。 All right， it included it。 look at this micro Open AI， Google Deepmin。

 Me Microsoft Anthropic and others。 that's really cool。 So we created this。 now what we're gonna do。

😊，Now what we're gonna do is we all want to upload this to GiHub So what I'm want to do and we're gonna make this one private so on GiHub we can create a new repository I'm going to make this one private we're gonna call this deep visual and we're gonna create a new repository and we've done this multiple times so far if you're skipping ahead then you haven't seen this yet。

 but all this does is this allows us to save it to our Github profile so the code is updated into this central location。

 I'm making it private so if I'm on a different computer or if I have a team member we can actually download this code and work from this place in the app or in cursor。

 we can download this code here and all we have to do is we can just copy this。

 open up a new composer window and say commit this to this Github repo that I just created so I already created this repo please upload my code to this repo I really。



![](img/1500f029842088de157b5aeb1cb6d5d3_132.png)

No the proper vernacular for this， I know that's not right。But cursor will do it for us。

 and once it's done。It's basically just said congrats。 it's， it's successfully uploaded。

 We can refresh this。 And here， all our code is right here。 Now we want to put it on the Internet。

 And were， we want to use versll again。 So we're going to put this on the Internet。

 This is going to be harder because we actually need to upload。😊，Our environment variables。

 because we have API keys that we need to have secure。

And so what we're going to do here is we are going to go to now I。

 now create a verll project using the C， I think。We can force it to use verll here。

 using the CI and deploy it to verll。And。嗯。Yeah， I think we can just say this。Okay， it's going great。

 The Versll CI is already installed。 Now let's deploy your project。

 So now we're basically just gonna say set up and deploy。

 pick whether you want to use your business or personal。 Let's just run it like this。

 link to existing project。 No what's the name of your project。😊，Deep。Visual enter。

What do you want to modify these settings。 No， I honestly couldn't tell you why some of those settings are the way they are。

 I just know that I've talked to AI before， and they told me to do that。 And so I do that every time。

 I wish I had more information for you。 I could have looked it up beforehand。 but I don't know。

 So just do what I just did。 in my work。 And so it says it's building。

 but I think we're gonna have to go enter our environment variables。 And so。

I'm going click on this right here。 And this is going to take us to it's show showing us that it's building。

 but I'm pretty sure it's going to fail because we haven't yet entered our environment variables。

 because we need to do that。 So I think we need to go to yeah。

 And so if you're on the project deep visual here。 We need to go to settings。

 and we need to go to environment variables。 And I want， I need to paste in those keys。



![](img/1500f029842088de157b5aeb1cb6d5d3_134.png)

Here， right I need to paste those keys in here。 So what I need to do is I need to go to cursor。

 And we're going to open this up。 And now what I'm going to do is I'm literally going to go to E And V dot local file。

 And again， I don't want to press on this because you'll be able to see what you'll be able to see。



![](img/1500f029842088de157b5aeb1cb6d5d3_136.png)

My keys， which I don't want you to be able to see the keys that I'm using。

 So I'm gonna open this up and I'll show you what I did。 Okay。

 so if you copy the entire EV do local file， which is the place where you keep all of your API tokens。

 and you just come into where it says key and press command V。

 It'll automatically load all of them in this format right here and you can press save。

 And that's what I did。 I did it off camera because I wanted to keep it safe。

 So go to your do EV file， copy the entire thing with all your keys， come to key， press command V。

 paste it in， hit save。

![](img/1500f029842088de157b5aeb1cb6d5d3_138.png)

And all of your keys will be loaded， so that's really cool。 And so I added my environment variables。

 please deploy。😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_140.png)

And so now it's trying again， and you can always keep track of it so you can click on this little link right here。

 we'll open this up。

![](img/1500f029842088de157b5aeb1cb6d5d3_142.png)

And this will allow us。 This is the site that it will be loaded on。 And if we go back to cursor。

 If we click on this top one， this will actually show us the build status。

 So here we see it's building， building， building。

![](img/1500f029842088de157b5aeb1cb6d5d3_144.png)

![](img/1500f029842088de157b5aeb1cb6d5d3_145.png)

And there we go。 So it says status ready。 And now we can press on。

 I think we can just press this domain right here， Deep visual。 And here we're gonna sign in。

 now here is an important part。 watch us when I click on this Nothing happens。

 We're getting an error and this error is happening because we actually need to go back to our authentication we need to go this authentication。

 Remember back at the beginning when we were setting up this project and we did sign in method we turn Google on。

 and it's automatically set up to allow your local host to sign in to whatever app you're building。

 but it's not set up for the deployed one。 So we need to go to settings and we need to go to authorized domains and so we need to go back to verll。

 So we need to go to back to verll So yeah， we're gonna open this link up right here and this link we need to copy and we need to put this into the authorized domains So we can paste。

😊，Doomain right here。And now this is going to authorize the authorization to work within Firebase。

 Let me try to explain this again。 What allows us to sign in is authentication through Firebase do Google dot com。

 And we need to authorize the， we need to authorize this。

 We need to authorize that the domain that we just。Created。Deep visual top for sale dot app。

 local host is automatically authorized when you start out。 I didn't have to do anything for this。

 So let's， let me show you。 So I'm going gonna go back to this right here， and we refresh the page。

We can hit sign in with Google， and it works。 And I'm going to sign in。

 I think I made an account with this one。 But yes， so here we can either paste。

Our deep research project。Yeah， we can paste this in right here。And the。

 the app works just like normal。And we can generate images with AI， We can edit them with AI。

 And this is the app that we created。 and it is on the website， deepvisual verel do app。However。

 I'm not gonna set up a custom domain for this one。 since we've already done that。

 that process is relatively simple。 And you can see here。And you can see here it's race or cooperate。

 And so we can actually edit this， right。 And so we see Deep Mind， Google， Microsoft。

 We can actually copy this。 We could say， please make， please。😊。

Include the company names and show and explain concepts。Further。And so we can use AI。

 it's now going to go in and edit this graphic， there we go， competitive moves。

And now we can do that。 So that's pretty cool。 And so we can use AI to edit these。😊，chartts。

 and then we can come up here and we can press save report。

 and this now is saved to our reports and we can export the PDF。

 So the PDF of this was just it's about to be exported。 There we go。So we can come right here。

 select it， here is our PDF report and obviously we didn't generate charts for the whole thing。

 so it's not amazing， but we can see and we could honestly make this a lot better。

 but I don't think it's a bad start。If we go to back to reports。

 I have not edited the title of all of them， but here we have all of the reports that we've saved so we can go back to this one and it'll have the same charts loaded。

 we could probably add something like comments to this but for now I think this is pretty solid like we created this app that allows us to generate with AI we can continue to generate these with AI and that's the app that we created and it's on the internet and you can sign in with a different account as well if we go I actually didn't add a sign out button I don't think I could sign out Oh it's there they added it for me。

 we can sign out， we can sign in with Google and we could sign in with a different account right And so when I sign in with a different account。

And I go to my reports。Nothing's there right， no reports yet because I signed in as a different user right create a report and if I were to save anything here。

 we can also write， we can say hello there。This is a banana。Split。And we could go ingredients。

And then we can generate with AI。 I'm pretty sure it's just gonna this is all the context it has。

 hello banana split ingredients。 And there you got that kind of shows you how how this kind of works。

 and then we can hit save report And then if we go back to our reports。

 we'll see that we have this and we could obviously make this way better。

 we could have AI generated titles for now， I don't care too much about that。

 I wanted to show how we've set up the database if we go back into the database right we go to the firestore database We'll see all of the reports。

 We can see the authentication is right here， we can see that there are now two users for the app。

 one of my emails and the other one of my emails and storage。

 we have nothing in here yet because we're not actually storing images or videos。

 the charts that are saved are saved as mermaid code。 And so yeah， that's the app that we created。

 That was a long video。 we created a clean landing page for a Genmate co。

 you can find this online if you want to check。😊。

![](img/1500f029842088de157b5aeb1cb6d5d3_147.png)

out and I believe the Github repo is public。 so I'll paste that below。 and yeah。

 we just found a random Github repo that had cool animation styles。

 and so we used that library to bring our own ideas to life obviously we created the deep research image creator which allows us to export and save reports and yeah。

 we can export them as PDFfs pretty cool。 We also dove deep into the basics of cursor。

 we talked about how cursor composer has two modes it has normal and agent and you need to just use the agent mode because it has access to the terminal has all the commands basically anything that you need to do cursor has access and it can create it can edit and it can delete files also that you can create an app and you can upload it to GiHub and then deploy it to the internet just like we did with a Genmate。



![](img/1500f029842088de157b5aeb1cb6d5d3_149.png)

And just like we did with this link， this is a deployed link on the internet as well。

 and we could set it up to our own custom domain and so yeah， if you guys want to dive deeper。

Hop into my community software composers。 We have a lot of really fun stuff planned here。 Right now。

 we have， we have 10215 members， and we are going to be creating a lot of really cool。

 free resources in software composers。 If you want to learn more about cursor and creating apps to make money for your own internal tools for design and for whatever project you want。

 just because you like it and you think it's fun。 So join the community if you want to see what we have in store because it's awesome。

 Anyway， I'll talk to you guys later。 This was a long vi。😊。



![](img/1500f029842088de157b5aeb1cb6d5d3_151.png)

Peace。