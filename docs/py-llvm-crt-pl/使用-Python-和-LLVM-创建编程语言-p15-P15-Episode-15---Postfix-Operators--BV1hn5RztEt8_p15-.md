# 使用-Python-和-LLVM-创建编程语言-p15-P15-Episode-15---Postfix-Operators--BV1hn5RztEt8_p15-

![](img/6e07942cd5e6c6af7134fd72ad745942_0.png)

Wele back to the series is episode 15， where we're going to be going over our post fix operators。

 So in the last episode， we added prefix operators。 So what comes before。

Our expressions or nodes or whatever you wan to call it。This today。

 we're going to be adding post fix。 So it comes after those。

 So we have a plus plus operator and a minus minus operator。 we're going to be adding， But you can。

 of course， add what how you see fit by seeing this template I'm about to give out。

 So that is our test thatt line file。 We're just doing what we usually do making a for loop。

 We're testing post fix operators in this for loop right here。



![](img/6e07942cd5e6c6af7134fd72ad745942_2.png)

Now that we have that， we can move into our first step as the majority of all of our episodes in the tokendo pie file。

We scroll down the symbols where we had our bank。I'm going to enter down and create a new block and post these in post fix symbols。

 We're having plus plus minus minus。 I'm also going to clean up and just enter down this bang here。



![](img/6e07942cd5e6c6af7134fd72ad745942_4.png)

And make a new section for prefix symbols。I would put the minus in here， but。Me， it'll be alright。

So we're just gonna have bang here。So that we can save that and then we can move into our lecturea。



![](img/6e07942cd5e6c6af7134fd72ad745942_6.png)

We need to handle the plus plus and minus minus tokens。 So in our case statement here。

 we can move up to pluses。

![](img/6e07942cd5e6c6af7134fd72ad745942_8.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_9.png)

Oh， literally the same thing as before， we just copy this。



![](img/6e07942cd5e6c6af7134fd72ad745942_11.png)

Paste in it here。 Change this to an e。

![](img/6e07942cd5e6c6af7134fd72ad745942_13.png)

Change this to another plus sign。Then change this to plus plus。



![](img/6e07942cd5e6c6af7134fd72ad745942_15.png)

We can do the same exact thing for minus。 We'll take this equals block right here。



![](img/6e07942cd5e6c6af7134fd72ad745942_17.png)

Pace it down。 Change it to another minus。Change this to minus minus。

And now we can handle those postfis operators in our Leer。So we can save that AS T dot pi is next。

 We need to scroll up to our node types， in our expressions。



![](img/6e07942cd5e6c6af7134fd72ad745942_19.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_20.png)

We will add the post fixed expression。 shallll paste in。



![](img/6e07942cd5e6c6af7134fd72ad745942_22.png)

So postfi expression equals postfi expression。

![](img/6e07942cd5e6c6af7134fd72ad745942_24.png)

We'll scroll down to the expressions region。Underneath our prefix。



![](img/6e07942cd5e6c6af7134fd72ad745942_26.png)

I'm going to enter down and paste in post fix。All this takes in the left node in the operator used。



![](img/6e07942cd5e6c6af7134fd72ad745942_28.png)

As the postfi， so。Pretty similar， but backwards to our prefix right here。 I'll just copy this in。

 and then we'll paste and save that。

![](img/6e07942cd5e6c6af7134fd72ad745942_30.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_31.png)

And that's all we need to do for the A S T。 So we'll move on to our parser。

Scroll to the very top in our expressions block right here。 We'll add our post fix expression。



![](img/6e07942cd5e6c6af7134fd72ad745942_33.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_34.png)

We have a couple more precedes mappings to do。 So in our dictionary right here， precedes。



![](img/6e07942cd5e6c6af7134fd72ad745942_36.png)

We'll do the very bottom。 I'll pace season for time。Plus。

 plus goes the index minus minus also goes to the index。



![](img/6e07942cd5e6c6af7134fd72ad745942_38.png)

We'll move right along to our infi functions dictionary。



![](img/6e07942cd5e6c6af7134fd72ad745942_40.png)

At the very bottom， I will tape， or I'll paste in。These， again， for both of our tokens。

We're going to create a parse post fix expression that are both mapped to these postfi operators or tokens。



![](img/6e07942cd5e6c6af7134fd72ad745942_42.png)

So I'll copy that name。We will scroll down to our expression methods underneath prefix。

 This is going to be a very simple function， parse postfi expression。



![](img/6e07942cd5e6c6af7134fd72ad745942_44.png)

Take in self。And a left node。Type expression。And we're gonna set that to post fix。



![](img/6e07942cd5e6c6af7134fd72ad745942_46.png)

So what we're gonna do is just return a new post fixed expression object。



![](img/6e07942cd5e6c6af7134fd72ad745942_48.png)

Where the left node。Equals the left node we took in， and the operator is equal to the current tokens。

 thought literal。

![](img/6e07942cd5e6c6af7134fd72ad745942_50.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_51.png)

Now that we've done that， we have one last thing to do。

 We need to go to our statement methods to our four statement。



![](img/6e07942cd5e6c6af7134fd72ad745942_53.png)

Instead of our assignment statement here for the action。

 we want to do this a little more generalized。

![](img/6e07942cd5e6c6af7134fd72ad745942_55.png)

In parse expression。

![](img/6e07942cd5e6c6af7134fd72ad745942_57.png)

We're going to set this to the precedence type， dot lowest。We're going add in another next token。



![](img/6e07942cd5e6c6af7134fd72ad745942_59.png)

Fingcao。And everything else can stay the same。 Now that we're not allowing assignment statements in our for loop。

 We need to go into our for statement。 We'll save parser at first。



![](img/6e07942cd5e6c6af7134fd72ad745942_61.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_62.png)

We need to go to our four statement node in the A S T。 So I just control， clicked that。



![](img/6e07942cd5e6c6af7134fd72ad745942_64.png)

In here， we'll just set this type to expression。

![](img/6e07942cd5e6c6af7134fd72ad745942_66.png)

That's all we need to do for that。 Just for typing sake， you could keep that。

And it would still work fine， but。To save me some annoyance later。



![](img/6e07942cd5e6c6af7134fd72ad745942_68.png)

I will get rid of it。That's everything for the parser and our A T again。

 So we'll go into our compiler now。

![](img/6e07942cd5e6c6af7134fd72ad745942_70.png)

Always， first thing we do is import what we've been working on。 So in our expressions。

 we' Li post fix expression。

![](img/6e07942cd5e6c6af7134fd72ad745942_72.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_73.png)

In our visit or expression visit methods down here in our regiongian block expressions。



![](img/6e07942cd5e6c6af7134fd72ad745942_75.png)

Scroll all the way to the bottom。We're gonna create a new function under here。 de。

 is it post fixed expression。Take self。And we're also taking in a node of that post fix。



![](img/6e07942cd5e6c6af7134fd72ad745942_77.png)

And this won't return anything at all。We're gonna break up our node。 So left node。

Should always be an identifier literal。We going do node dot left node。



![](img/6e07942cd5e6c6af7134fd72ad745942_79.png)

That's something we also need to check。 So post fix here。 we're to change this expression。

 This needs to be an identifier literal。

![](img/6e07942cd5e6c6af7134fd72ad745942_81.png)

Which we can't do because it's down here。 All right。

 so we're just gonna pretend this says ident literal。 and we're going to go with it。



![](img/6e07942cd5e6c6af7134fd72ad745942_83.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_84.png)

Don't worry about it。 Real software right here。

![](img/6e07942cd5e6c6af7134fd72ad745942_86.png)

And we're gonna take the operator。As a string， and we're gonna break it from our node。

 node dot operator。

![](img/6e07942cd5e6c6af7134fd72ad745942_88.png)

Next， we need to make sure that this node actually exists。 So if self dot E And V dot look up。

Left node dot value。

![](img/6e07942cd5e6c6af7134fd72ad745942_90.png)

Is none。 So if this just returns None。 We want to app an error。 So I'm going to paste this in。

Where in a self do error is aend， a compiler error。

 and that this identifier has not been declared before it was used in a post fixed expression。



![](img/6e07942cd5e6c6af7134fd72ad745942_92.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_93.png)

Make these errors a lot better， but。

![](img/6e07942cd5e6c6af7134fd72ad745942_95.png)

That should do the job for now。We'll enter down after the if statement will take in a var pointer。

And the underscored for the type。 and will'll look up in the E And V。



![](img/6e07942cd5e6c6af7134fd72ad745942_97.png)

The left node value， again。We're going do get the original value。By loading that pointer。

 sub self dot builder dot load。

![](img/6e07942cd5e6c6af7134fd72ad745942_99.png)

Or pointer。We're gonna do it。 We've done a lot。 We're gonna do a value variable set it to none。



![](img/6e07942cd5e6c6af7134fd72ad745942_101.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_102.png)

Match case on the operator。We have only two cases。 We have our plus plus。



![](img/6e07942cd5e6c6af7134fd72ad745942_104.png)

And are minus minus， and they will be the exact same pretty much。 So if is instance。

Original value dot type。Is an integer。 So I an int type。



![](img/6e07942cd5e6c6af7134fd72ad745942_106.png)

We want to set value equal to self dot builder， do addd。The original value。

 and we're going to add it to a new constant。It's going to be an integer 32 type， Ida in type。

And we're just going add one to it。

![](img/6e07942cd5e6c6af7134fd72ad745942_108.png)

L if is instance that original value， type。 If that's a float。 So I a float type。



![](img/6e07942cd5e6c6af7134fd72ad745942_110.png)

We' going need the same thing， except with the float。Function。 So F that。



![](img/6e07942cd5e6c6af7134fd72ad745942_112.png)

The original value， we're going to add a new constant。Which is a float。



![](img/6e07942cd5e6c6af7134fd72ad745942_114.png)

We're gonna。Add one to the original value。Now， for the minus minus， it's the same。

 except instead of adding or subtracting。 So we'll use sub and F sub here。

 and everything else is the same。

![](img/6e07942cd5e6c6af7134fd72ad745942_116.png)

![](img/6e07942cd5e6c6af7134fd72ad745942_117.png)

Now， finally， after we've done that， all we have to do is create a store instruction to set this new value here。

To be equal to the。

![](img/6e07942cd5e6c6af7134fd72ad745942_119.png)

Variable were that set this pointer。So self dot builder dot store。Or restore that value。

 new value in the variables pointers location。

![](img/6e07942cd5e6c6af7134fd72ad745942_121.png)

Finally， we're going go up to our compile methods right around the very top。



![](img/6e07942cd5e6c6af7134fd72ad745942_123.png)

We'll scroll down to the expressions section， and we'll call our function that we've been working on。



![](img/6e07942cd5e6c6af7134fd72ad745942_125.png)

New case， node type， dot post fix expression。And all that's gonna do is call our visit method。

Visit post fix expression， and we pass in that node。



![](img/6e07942cd5e6c6af7134fd72ad745942_127.png)

So that should be everything that we need to have post fixed expressions。

 So go to our test dot line file， go to our terminal， Python， main dot pi。



![](img/6e07942cd5e6c6af7134fd72ad745942_129.png)

Just scroll on up。

![](img/6e07942cd5e6c6af7134fd72ad745942_131.png)

Looks like it worked。 Since we're breaking here at 5， it should never get to 5。

 which it never does 0。 It's adding one each iteration。 We can prove that with the print statement。



![](img/6e07942cd5e6c6af7134fd72ad745942_133.png)

So it looks like it's working to me。Now that we have all this squared away。

 our next episode is going to be on actual importing of files。

 So we'll be able to import a math file and use functions from that file and also declare import statements at the top。

 It's going to be very basic。But it will get the importing job done。 And I should have some。

Better ways of importing， But I haven't been able to find any information on。Actually。

 importing things or any tutorials。 So I think it'll be a really good video。

So thank you very guys for watching， and I'll see you in 16。



![](img/6e07942cd5e6c6af7134fd72ad745942_135.png)