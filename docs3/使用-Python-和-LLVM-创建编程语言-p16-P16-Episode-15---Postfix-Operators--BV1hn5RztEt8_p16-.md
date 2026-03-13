# 使用-Python-和-LLVM-创建编程语言-p16-P16-Episode-15---Postfix-Operators--BV1hn5RztEt8_p16-

![](img/6af1ed99976df5c30c5bbff0fda916f2_0.png)

Welcome back to episode 16， where we finally made it to file imports into our language。

 So basic file imports。Kind of sea styles。 So we're gonna just have the import keyword。With a string。

 with the file path。

![](img/6af1ed99976df5c30c5bbff0fda916f2_2.png)

To this file。And in there， I'd just created a math that lime file in the same directory as test。

And in math dot line， I just have one function named add that takes in two integers。

 returns an integer and just adds them together and returns the result。



![](img/6af1ed99976df5c30c5bbff0fda916f2_4.png)

So in test thatt line， I'm importing it here， and then I'm going to use it only when I equals1 in this for loop。

 I'm just going print out I plus 8 equals。Percent I。

 and that percent I is gonna be I plus 8 calling that add function。 So we don't have it。

Declared anywhere in this file。 It is in a different file。 So we've imported it。



![](img/6af1ed99976df5c30c5bbff0fda916f2_6.png)

So now that we have our test dot line file figured out， we're going to move into our first area。

 which is， of course， the token。

![](img/6af1ed99976df5c30c5bbff0fda916f2_8.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_9.png)

In our keyword section of token type， we're going to add import。Equals import。



![](img/6af1ed99976df5c30c5bbff0fda916f2_11.png)

Not really add this， we can go into our token or below our token class to our keywords。

 mapping or our dictionary。

![](img/6af1ed99976df5c30c5bbff0fda916f2_13.png)

We're going to add a new one in here for our import keyword。

 We're going to map that to token dot import。

![](img/6af1ed99976df5c30c5bbff0fda916f2_15.png)

So you can type that import and in our alt keywords to make a Gen Z safe。



![](img/6af1ed99976df5c30c5bbff0fda916f2_17.png)

We're gonna give this one Gib。 We'll do Gib。So， token type。

Dot import is going to be mapped to Gib as well。

![](img/6af1ed99976df5c30c5bbff0fda916f2_19.png)

And that will be all for our token type。 We don't need our Leir。 So we go into our A S T。



![](img/6af1ed99976df5c30c5bbff0fda916f2_21.png)

Scroll all the way up to our node types。 in our statements。

 we're going to add our import statement node type。



![](img/6af1ed99976df5c30c5bbff0fda916f2_23.png)

Import statement equals import statement。

![](img/6af1ed99976df5c30c5bbff0fda916f2_25.png)

We're going to scroll down to the bottom of our statements region， underneath 4。



![](img/6af1ed99976df5c30c5bbff0fda916f2_27.png)

And we'll paste in our import statement node。 The only thing this takes in is a file path。

 So we're just setting a file path property。 Everything else is， as we usually do it。



![](img/6af1ed99976df5c30c5bbff0fda916f2_29.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_30.png)

We can save that as well and move into our parser。Go up to the very top in our statements block here。

 I'm going to import the import statement。

![](img/6af1ed99976df5c30c5bbff0fda916f2_32.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_33.png)

We're going to scroll down to parse statement function in our parsers class。



![](img/6af1ed99976df5c30c5bbff0fda916f2_35.png)

Scroll down all these functions we've made。 parse statement。



![](img/6af1ed99976df5c30c5bbff0fda916f2_37.png)

Down below 4， we'll add a new case。Token type。

![](img/6af1ed99976df5c30c5bbff0fda916f2_39.png)

That import。And we're going return a self dot underscore underscore to score parse。



![](img/6af1ed99976df5c30c5bbff0fda916f2_41.png)

Not assignment statement It be a import statement。

![](img/6af1ed99976df5c30c5bbff0fda916f2_43.png)

Function。And we're going to implement this import statement。

 So at the very bottom of our statement methods block underneath parse 4。



![](img/6af1ed99976df5c30c5bbff0fda916f2_45.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_46.png)

We're going add a deaf parse import statement。 It's going take in。

It's going to return back our import statement note。



![](img/6af1ed99976df5c30c5bbff0fda916f2_48.png)

First thing we're to do is we're going to make sure the next token is a string。 So if not。

 self do expect peak。

![](img/6af1ed99976df5c30c5bbff0fda916f2_50.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_51.png)

Token type， dot string。Or turn none。

![](img/6af1ed99976df5c30c5bbff0fda916f2_53.png)

We're gonna set a statement variable， equal to。

![](img/6af1ed99976df5c30c5bbff0fda916f2_55.png)

Go ahead and add typing to。Equal to a import statement class where the file path is equal to the current token dot literal。



![](img/6af1ed99976df5c30c5bbff0fda916f2_57.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_58.png)

Or make sure there's a semicolon。 So if not， self do expect peak。



![](img/6af1ed99976df5c30c5bbff0fda916f2_60.png)

Token type。

![](img/6af1ed99976df5c30c5bbff0fda916f2_62.png)

Dot semicolon。Return none there。

![](img/6af1ed99976df5c30c5bbff0fda916f2_64.png)

If all is good， we will just return that import statement。



![](img/6af1ed99976df5c30c5bbff0fda916f2_66.png)

Really short on the parser。 So we'll go into our compiler。



![](img/6af1ed99976df5c30c5bbff0fda916f2_68.png)

Scroll to the very top。First thing will import our import statement node。



![](img/6af1ed99976df5c30c5bbff0fda916f2_70.png)

Next， we'll go up here to the top。 We'll import the O S package so we can。



![](img/6af1ed99976df5c30c5bbff0fda916f2_72.png)

Have Fpath access。

![](img/6af1ed99976df5c30c5bbff0fda916f2_74.png)

And then below this environment import will add two more。 So from our Lexer file。



![](img/6af1ed99976df5c30c5bbff0fda916f2_76.png)

Import our Leer class。And from our parser file， we import our parser class。



![](img/6af1ed99976df5c30c5bbff0fda916f2_78.png)

In our initialized method for the compiler， we'll scroll all the way down under here。



![](img/6af1ed99976df5c30c5bbff0fda916f2_80.png)

Im paste this in with the comment。 So this is just going keep a reference to our parsed pallets。

 So anything that's been imported， it's gonna keep a reference to its program node。



![](img/6af1ed99976df5c30c5bbff0fda916f2_82.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_83.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_84.png)

It's just a dictionary with a string in the programme node。

 So the palette's name or what I'm calling in this language， pals， people would say modules。嗯。是。

Stuff like that。 Yes， packages。

![](img/6af1ed99976df5c30c5bbff0fda916f2_86.png)

Whatever you're calling it， I'm calling em pallet's limes。Now we scroll down to the compile method。



![](img/6af1ed99976df5c30c5bbff0fda916f2_88.png)

Add a new case under four statement for our node type import statement。



![](img/6af1ed99976df5c30c5bbff0fda916f2_90.png)

We're gonna have a new function， underscore underscore visit。Import。Stment。



![](img/6af1ed99976df5c30c5bbff0fda916f2_92.png)

We'll pass in the note， as well， for that。So I'll control。

 click on four statementca we need to probably go below this one， which we do。



![](img/6af1ed99976df5c30c5bbff0fda916f2_94.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_95.png)

So below the four statement visit function。We need to create our visit import statement functions。

 self。

![](img/6af1ed99976df5c30c5bbff0fda916f2_97.png)

Take in the import statement note。

![](img/6af1ed99976df5c30c5bbff0fda916f2_99.png)

And this will not return anything。

![](img/6af1ed99976df5c30c5bbff0fda916f2_101.png)

First thing we'll break apart our node。 So all we have is a file path。



![](img/6af1ed99976df5c30c5bbff0fda916f2_103.png)

There's no dot file path。Now， we need to make sure that we haven't imported this before。



![](img/6af1ed99976df5c30c5bbff0fda916f2_105.png)

So。If self dot global parsed pallets。Dot get。The file path。



![](img/6af1ed99976df5c30c5bbff0fda916f2_107.png)

Is not none。

![](img/6af1ed99976df5c30c5bbff0fda916f2_109.png)

So。If something exists， there's a key with that file path。



![](img/6af1ed99976df5c30c5bbff0fda916f2_111.png)

If it exists。

![](img/6af1ed99976df5c30c5bbff0fda916f2_113.png)

That means we've already parsed this before。 So we'd need to。Air out or a warning， I guess。



![](img/6af1ed99976df5c30c5bbff0fda916f2_115.png)

So I will print that little warning in here。 So print live warning。

 this file path is already imported globally。

![](img/6af1ed99976df5c30c5bbff0fda916f2_117.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_118.png)

Then we'll return out。Now， if we haven't imported this before， we're going to open up that file path。

 So with open。

![](img/6af1ed99976df5c30c5bbff0fda916f2_120.png)

O dot path， that absolute path。

![](img/6af1ed99976df5c30c5bbff0fda916f2_122.png)

Do an F string tests， slash slash file path。 Now for you， you can make this more generic。



![](img/6af1ed99976df5c30c5bbff0fda916f2_124.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_125.png)

But everything that Im going use in my test is going to be in this directory。

 So I'm going to go ahead and。

![](img/6af1ed99976df5c30c5bbff0fda916f2_127.png)

Tell it here in the source code。 But you can alter this and get rid of it， if you want。



![](img/6af1ed99976df5c30c5bbff0fda916f2_129.png)

This is gonna be a read。 We're gonna read， function this。



![](img/6af1ed99976df5c30c5bbff0fda916f2_131.png)

As F。

![](img/6af1ed99976df5c30c5bbff0fda916f2_133.png)

In the pallet's code。So the string is going to be the result of us reading that file。 So F dot read。



![](img/6af1ed99976df5c30c5bbff0fda916f2_135.png)

Now， we do similar to what we do in the main function to run our code in the first place。

Where is set a variable L。To an instance of our Leer， So where the source is the palette code。



![](img/6af1ed99976df5c30c5bbff0fda916f2_137.png)

We're going to have the P variable for our parser or the source or。

It's an instance of our parser where the Leir is the one we just made。



![](img/6af1ed99976df5c30c5bbff0fda916f2_139.png)

![](img/6af1ed99976df5c30c5bbff0fda916f2_140.png)

We're going to get a program node out of this。This program equals P dot parse program。



![](img/6af1ed99976df5c30c5bbff0fda916f2_142.png)

If the length。Of the errors in the parser。Is greater than 0。



![](img/6af1ed99976df5c30c5bbff0fda916f2_144.png)

We want to print。F。

![](img/6af1ed99976df5c30c5bbff0fda916f2_146.png)

Arror with imported palate。And we'll put in the file path in there。



![](img/6af1ed99976df5c30c5bbff0fda916f2_148.png)

For error in the parser's errors list。

![](img/6af1ed99976df5c30c5bbff0fda916f2_150.png)

We want to print the error。

![](img/6af1ed99976df5c30c5bbff0fda916f2_152.png)

And then we'll just call the exit function， just。Break out of our compiler here。



![](img/6af1ed99976df5c30c5bbff0fda916f2_154.png)

Now， if everything' is good， we want to compile。Self dot compile that program。



![](img/6af1ed99976df5c30c5bbff0fda916f2_156.png)

Or node equals program。 So since we're using the compile method here。Ay inside of our compiler。

 whatever scope or environment that we're in right now。

 That's where all of these functions and variables will be declared， to。



![](img/6af1ed99976df5c30c5bbff0fda916f2_158.png)

So that's why we're calling， we're compiling that node program into our already compiled。Environment。



![](img/6af1ed99976df5c30c5bbff0fda916f2_160.png)

And then once we've finished compiling， we can set our global parsed palettes。At the file path index。

Equal to our program node。 So now， for whatever reason。

 if we need to get a specific reference to this。Imported code at this file path。

 we have a program AST that we can draw from。And that's pretty much it。



![](img/6af1ed99976df5c30c5bbff0fda916f2_162.png)

We can save that。 Go into our test dot lime file。 We'll make this terminal a little bigger。

 and we'll run Python， main dot pi。

![](img/6af1ed99976df5c30c5bbff0fda916f2_164.png)

And after 1 millisecond we have right here， I equals 0。Goes along the loop。Now I equals 1。

 So now we're printing。 I plus 8 equals 9。 So I plus 8，1 plus 8 equals 9， so。I'll put 500 here。

 and this should be 501。 We run it again，5，01。So importing is now working。

 so you can add any functions here。 It's more of a globalized import system。

 which you can modify and ad or I can make some new episodes later on about it。

For this sh getchi started。But thank you guys for watching our second to last episode for right now。

Is gonna be up 17 is where we're gonna。I'm going to show you how we can export our full language to an E。

 X E so that way we can add it to our path variable and install it as if。This was a。

A professionalized language that you've installed like Python or Goling or anything like that。

thank you guys for watching， and I will see you in 17。



![](img/6af1ed99976df5c30c5bbff0fda916f2_166.png)