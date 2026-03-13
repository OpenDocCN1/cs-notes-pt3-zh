# 使用-Python-和-LLVM-创建编程语言-p17-P17-Episode-17---Exporting-to-EXE--BV1hn5RztEt8_p17-

![](img/d9a399c36f623dc4b4b25799137c12d1_0.png)

We'll come back to episode 17， where we're going to be working on exporting our language to an E a standalone E X E file that you can give to your friends or release and put it on Github so that other people can download and add your languages E X E to their path and use it as if。

You had any other language， pretty much。

![](img/d9a399c36f623dc4b4b25799137c12d1_2.png)

So for right now， the first thing we're going to do is in our terminal。 So in our terminal。

 we need to install another package。 So Pip install。Pie installer。 This is the。

One of the easiest libraries to compile up your Python code into a standalone executable。Well。

 press in turn。 make sure that's all installed。 Once that's installed， we can。



![](img/d9a399c36f623dc4b4b25799137c12d1_4.png)

Make this terminal a little smaller， and we can move into our main dot pi file for first time in a little bit。



![](img/d9a399c36f623dc4b4b25799137c12d1_6.png)

Up here， we can add another import from Argparse。Import。Argument， parser。



![](img/d9a399c36f623dc4b4b25799137c12d1_8.png)

Name space in our debug flags。 Make sure everything is set to false。All of our debug。

 you can keep run code when keep that one true。Then we're gonna go back up to our。

New function named parse argumentsgu。 So this is going to allow us to pass in arguments into our E。

 X E。 and' just going to help us。Kind of structure it。To be an easier time。



![](img/d9a399c36f623dc4b4b25799137c12d1_10.png)

AndThis is gonna return our name space that we imported。ItsArg parser variable。

 It's going to be an argument， parser。

![](img/d9a399c36f623dc4b4b25799137c12d1_12.png)

![](img/d9a399c36f623dc4b4b25799137c12d1_13.png)

Make an instance of that argument。 parser will enter down。We'll set a description here。

So you can put your whatever you want here I just put my name of this language and whatever version it's going be。

 So we'll make that one。Very much alpha versioned language。

We're going to add some required arguments to this， so。Our our par or class dot add argument。

First one is gonna to be file path。It's gonna be the type。Of a string。

And our help text for this argument is going to be path to your。Entry。Point。Lime file。What example。

Main dot line。

![](img/d9a399c36f623dc4b4b25799137c12d1_15.png)

We're going to add one more argument underneath under this。 So ourrc parser add argument。



![](img/d9a399c36f623dc4b4b25799137c12d1_17.png)

This will be a debug flag。Dash dash debug。

![](img/d9a399c36f623dc4b4b25799137c12d1_19.png)

Action。It's going to be store true。

![](img/d9a399c36f623dc4b4b25799137c12d1_21.png)

So if the user adds this flag， it's just going to resolve to a boolean true。



![](img/d9a399c36f623dc4b4b25799137c12d1_23.png)

And the help text is gonna be prints。Internal debug information。



![](img/d9a399c36f623dc4b4b25799137c12d1_25.png)

So the debug stuff that we've been using。Last thing is we're going return the yard parser dot parsars function。



![](img/d9a399c36f623dc4b4b25799137c12d1_27.png)

Next thing， we're going add another one here underneath run code。 we're going call it prod。Debug。

A bully animal will set that to false。

![](img/d9a399c36f623dc4b4b25799137c12d1_29.png)

By default。Go ahead and get rid of this code thing here to clean up。

We're going to do a little bit of housekeeping here。 So above our reading from the input file。



![](img/d9a399c36f623dc4b4b25799137c12d1_31.png)

We want a new variable as。Equal parse arguments。

![](img/d9a399c36f623dc4b4b25799137c12d1_33.png)

It the first thing we do。If Args dot debug。

![](img/d9a399c36f623dc4b4b25799137c12d1_35.png)

We want to set that pro debug flag the true。 So this debug here is this。 Our file。

 We're going to make a file path variable equal to tests， not test。



![](img/d9a399c36f623dc4b4b25799137c12d1_37.png)

Or test， slash test dot line。If。As dot file path。So if we did pass in fire or file path into our E X E。

 we're going to set file path equal to。Arg do file path。So this one's just going to be our default。

 the one we've been using down here。And if we added an argument with one。

 we want to set that variable with it。And we'll use in our open function。

We'll use that whatever that resolved file path is from here。



![](img/d9a399c36f623dc4b4b25799137c12d1_39.png)

I will scroll down。We add a couple of things here， so。In but we'll have our program in between this。



![](img/d9a399c36f623dc4b4b25799137c12d1_41.png)

First things can be our parse start time。

![](img/d9a399c36f623dc4b4b25799137c12d1_43.png)

So float for the time， that time。And then we'll copy that， paste it below。

 This will be E T for end time， time。 time。

![](img/d9a399c36f623dc4b4b25799137c12d1_45.png)

Will check the errors。 if pars or debug。Will write that A S T， as well。



![](img/d9a399c36f623dc4b4b25799137c12d1_47.png)

Keepep the compiler here。

![](img/d9a399c36f623dc4b4b25799137c12d1_49.png)

For the compile step， the actual function call will make two more time tracking variables。



![](img/d9a399c36f623dc4b4b25799137c12d1_51.png)

Filr start time。Time that time。

![](img/d9a399c36f623dc4b4b25799137c12d1_53.png)

Compilr end time。Float。Time that time。So we're just taking when it starts， when it ends。

 we can calculate how long it took。

![](img/d9a399c36f623dc4b4b25799137c12d1_55.png)

![](img/d9a399c36f623dc4b4b25799137c12d1_56.png)

So down here in the output steps， we have our module of things good here。 compiler debug， great。



![](img/d9a399c36f623dc4b4b25799137c12d1_58.png)

Viler errors， great。Our run code function。

![](img/d9a399c36f623dc4b4b25799137c12d1_60.png)

We'll scroll down a little bit。 Everything's looking good here。At the very end of this E T。

We're going to set up our pro debug flag。 So if that's running。



![](img/d9a399c36f623dc4b4b25799137c12d1_62.png)

If that said the true。

![](img/d9a399c36f623dc4b4b25799137c12d1_64.png)

I'll paste these in。 We're going to add two more print statements。

One's going to tell us how long it took to parse in milliseconds and how long it took the compile。

Milliseconds should be it for everything for the main dot pi file。



![](img/d9a399c36f623dc4b4b25799137c12d1_66.png)

![](img/d9a399c36f623dc4b4b25799137c12d1_67.png)

So we'll scroll this thing up a little bit， make it bigger the tu。

We're going to run a command for P installer to compile our Python code into an E X E。

 So we'll call P installer。Dash， dash1 file。 So that's what's going make it stand on。

We to make the name of that file， dash dashed name， the name will be limeme。Now。

 if you wanted to add an icon， you can。 I'm not going to do it right now。

 but you could add in this So dash dash icon。And then a file path to get to that icon from this folder here。

So you can add assets and then add your ICO file， and that will give your EX E this icon。

 I'm not going to use this for right now。ButFeel free to do that。And then finally。

 the entry point file， I want to compile So main dot pi。

 We're going to enter that in and let it compile。

![](img/d9a399c36f623dc4b4b25799137c12d1_69.png)

![](img/d9a399c36f623dc4b4b25799137c12d1_70.png)

Might take a minute or two。All right。 Now that that's compiled。 we can make this term a little bit。

 You'll see that a couple folders have been made。 Also a little file lime dot speck。

 It's just something for the P install module。

![](img/d9a399c36f623dc4b4b25799137c12d1_72.png)

![](img/d9a399c36f623dc4b4b25799137c12d1_73.png)

![](img/d9a399c36f623dc4b4b25799137c12d1_74.png)

But we have disked and build。What were。Pretty worried about is the disk folder。

 which is where our lime dot E， X， E is。So I'm going to create a new file in this disk。

 call it main dot line。

![](img/d9a399c36f623dc4b4b25799137c12d1_76.png)

We'll take this test right here。 Yeah， we'll take this test right here。

And we will put it in our main dot line file。 I'll go ahead and get rid of the import for now。

 I don't feel like copying that over。And we'll just do I plus 8 here。

So that'll be a good main file for us to watch。Now that we have this main file figured out。

All we have to do is just go back to our terminal and make it a little bigger。

We'll run C D disk to get that disk folder。We'll do dot slash lime。 Ec。

And pass in main dot lime is our file path。AndThen run it。we go。 And under a millisecond。

 we've done this。 I plus 8 is 9。And now you have any X E that you can use。

 You can add this file path to your。Environment variables。On Windows。

So that you can use the lime command anywhere。In your computer。But I won't go over that Quick。

 That's a quick Google search。 Just look up how to add an E X E。To your path。

Varis your environment variables for whatever operating system you you're using。

Probably going be the first link。 so I'll let you guys handle that。But。😔，One last thing。

 if you do have this in a github， which you probably should。

Create a new file if you don't have already， Add a gi ignore。And you'll w to add your。Build。😔。

Directory to this ignore， So build slash star。 So everything in that build folder。

The disk slash star。 So everything in the disk，'cause you don't wantan to upload these E Xs or all these build things that don't matter to Github。

So make sure you guys do that if you desire。But thank you guys for watching our next episode。



![](img/d9a399c36f623dc4b4b25799137c12d1_78.png)

I still have to try and implement， but a。Helpful viewer has made me aware of a way we can create a static。

 make this statically compiled， rather than gi compiled。 So I'm going add that as our next episode。

Ass a little bonus episode onto this。 So if you wanted to statically compile your language to its own EX E。

 your own programs， EX E。That'll be coming in the next one。 So thank you guys for watching。

 And I will see you in the next episode and series。



![](img/d9a399c36f623dc4b4b25799137c12d1_80.png)