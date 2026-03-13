# 使用-Python-和-LLVM-创建编程语言-p09-P09-Episode-9---Calling-Functions--BV1hn5RztEt8_p9-

Rance， so episode 10 is going to deal with。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_1.png)

Function calling and how we're going do this is this pizza code is what we're going to be compiling by the end of the episode。

We're just going to have our main function， and it's going to return whatever the test function returns。

 So that should just return our 69。And how we're going to make it our call functions is how usually a lot of other languages do it。

With our parentheses。 So all we're going to do is implement a new AST node for the call expression。

 that's basically just going to be this。 and then we're going to add some new parser functions for if we encounter this left parentheses。

In this certain context， that means we're trying to call something instead of。Trying to do math。

 And we'll move into our A S T。 First thing we're going to add is our call。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_3.png)

Expression。Those call expression， node type。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_5.png)

And we are going to go down to the expressions。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_7.png)

Create a new class。Call expression， Inherit from expression。Make our knit method。And I'll paste this。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_9.png)

These functions in here， for the sake of time。So we have our function。

The function variable is just gonna be an identifier literal。

 just pretty much the name of that function。And then any arguments that it has for right now。

 we're going to have no arguments。Ed no abilities to pass in arguments or parameters。

 That'll be coming in the next episode。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_11.png)

So that's all we'll take in。In these arguments just going to be a list of expressions。

And then the type， which is the call expression that our Json is same as everything else。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_13.png)

So we'll save that and go to the parser。We'll import our call expression。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_15.png)

We're going to go down to our precedes mapping。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_17.png)

And add in our left parentheses。And we're going to map that to the call precedence type that we've already set up before in our。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_19.png)

![](img/d33bc1c40be3f2bd2c963d796c889bd8_20.png)

Enumeration。I'm going to scroll down to our infi parse functions。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_22.png)

We're going to add a new and fixed parse function token type dot left parentheses。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_24.png)

We're to call any function。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_26.png)

Parse call expression。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_28.png)

So we'll scroll down to our the bottom of our expressions。 here's all our statements。

 and now here's our expressions。 So go to the bottom。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_30.png)

![](img/d33bc1c40be3f2bd2c963d796c889bd8_31.png)

Make our function parse call expression take in self。

 and this will return back our call expression node。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_33.png)

Go ahead， and make。The instance of our class。Passen function。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_35.png)

We go function。Now， I forgot to add this in here。 when the， this function is called。

 they're going to be passing in a variable。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_37.png)

And that will be of type expression。 So pretty much will be a identifier literal that goes into here。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_39.png)

![](img/d33bc1c40be3f2bd2c963d796c889bd8_40.png)

And then for our arguments。Expressional arguments， we're just gonna enter in our。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_42.png)

EmpP list for now put a two on here for the next episode。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_44.png)

Then if not， self done， underscorecorner score， expect peak。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_46.png)

Tookken type dot right print。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_48.png)

So if there is not a right parentheses。After the left one。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_50.png)

We're going to throw an air pretty much。 So we're return none out of that。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_52.png)

And after that， were return expression。Now， this bit of code will be removed after we get to creating our parse parameters of parse arguments function。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_54.png)

So this is just temporary for right now。So that we have that out of the way。

 we can go into main dot pi。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_56.png)

We can set compilerr and run code to false。 We can set parser。Do you bugged it true。

And then we will let me go into the right episode。We will run the file mine made not pi。

So we got compiler objects。 That's fine。 We're not worried about that。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_58.png)

Read about this AS T debug。 So go in the JO file。We'll put test that line up over here。

first ones are function statement tests。And it just returns back 69， then our next one。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_60.png)

Our main function。 And here we are。 So we're returning a call expression。

And the name is in test or the functions test。 and the arguments are blank。

 So there's nothing in the arguments， which is perfect。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_62.png)

So the AS T is done for now。 So we'll get out of that。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_64.png)

We'llGo ahead and set the part， the compiler debug to true set false back to or pars debug back to false。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_66.png)

Then we'll move into our compiler。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_68.png)

First thing import， call expression。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_70.png)

We will go to the compile visit method。😔，And downown here in the expressions， will add a new case。

 node type。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_72.png)

That call expression。 we'll make a new visit function for that。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_74.png)

Pass in the node。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_76.png)

We'll scroll all the way down to our visit expressions。 So in fixed expression here。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_78.png)

And right below that。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_80.png)

We'll do de。 visit call expression。Self the node。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_82.png)

Call expression node。We're going to turn back none。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_84.png)

TheFirst thing we're gonna to do is take in get our name of our function。So， node。Not function。

 do value。 Since this is an identifier literal。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_86.png)

To get our prams。List expression。No dot arguments。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_88.png)

This is gonna be empty for now， so we won't use it。

We're going just set two variables here for later as and types。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_90.png)

And we'll add it to do here。 We won't use those yet， but we'll keep them for now。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_92.png)

We're going to do a match statement on the name。This is where if we're trying to call a built in function。

 we would。 This is easy place to put， like， we'll put our。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_94.png)

Kays print F in a later episode。Here， but for now。We're going to do the underscore for just anything。

 whatever this name is for now。We're going to grab our function and our return type。

From our environments， self。 E and V。lookup。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_96.png)

So we're going to look for that function。We're going to set our return variable。

To self dot builder dot call。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_98.png)

I call that function with the as declared above。Nowo。😔，This call， whatever this。

 this function returns。We will return it back from here。

 So well return from the call expression and the return type as well。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_100.png)

Now， we need to scroll down to resolve value and add our call expression case into here。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_102.png)

Case known type dot call expression。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_104.png)

And then all this does is called the function we just set up So visit。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_106.png)

Call expression。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_108.png)

Pass in that node。 So that's all that's gonna do。 Now。

 we'll go back to main becauseuse that should be everything we have to do for the compiler。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_110.png)

Go ahead and run this。

![](img/d33bc1c40be3f2bd2c963d796c889bd8_112.png)

With our compiler debug is true。And we'll investigate this I R bring test that line up， as well。So。

 all right。 So we have our test function returns 69 in here。 If our main function。

 that's calling the test function。 And then it returns whatever the test function returns。

 So that's perfect。 So we can run。Our code as well。ho。

Now that we run that and we can see our program returns 69。 so we can plus。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_114.png)

![](img/d33bc1c40be3f2bd2c963d796c889bd8_115.png)

Another God number。Then here we go。 And now our program is returning。

 So we're able to call these functions。 Now we're able to call these functions。

 The next thing up will be adding parameters to these functions。So， we could have a。For a add。

 then A and B。Turns back an integer， and this will return a plus B。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_117.png)

And then we could call the add function with one and2 here in this wood。Just resolve。

 It would just add those numbers together and then return back the answer。

 So that's what we're going to work on next is these adding arguments and parameters to functions。

 Thank you for watching。 We have the discord in the description below。 If you have any questions。

 comments or concerns。 I saw a couple people had some issues。With some of the prior episodes。

 we were able to， I was able to help them out in the discord。

 So definitely join that if you're running into any issues。Thanks for watching。 We'll see。

 I'll see you in episode 10 for function parameters and arguments。



![](img/d33bc1c40be3f2bd2c963d796c889bd8_119.png)