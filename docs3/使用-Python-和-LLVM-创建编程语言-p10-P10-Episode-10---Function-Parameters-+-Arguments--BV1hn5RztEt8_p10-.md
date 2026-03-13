# 使用-Python-和-LLVM-创建编程语言-p10-P10-Episode-10---Function-Parameters-+-Arguments--BV1hn5RztEt8_p10-

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_0.png)

Welcome to episode 10， where we're going to be adding function parameters and arguments to our function callings for user to find functions。

And soon enough， our built in functions。 But for right now。

 this is what we're going to be compiling and running today。

It's just pretty similar to the last episode。Except we're going return and add our our calling of our add function。

 And it's going to take in two parameters that are integers， and we'll declare their types as well。

 when we declare the function。 And it's gonna return an integer。 And it's going return A plus B。

 That's it。 First thing we're gonna to do is we're gonna have to add a new token， which is our comma。

 So we'll go to a token dot pi。 So once we're in token dot pi， we'll go down to。

 we'll say right by the colon。To comma equals comma。 And That's all we'll do for token。

 So we'll go move on into our Lear now。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_2.png)

We're gonna scroll down and add the comma to our。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_4.png)

Next token function。 So add a new case。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_6.png)

Self dot new token。Took a type that comma。Not just the current character。That's it for the alir。

 Pret easy。We'll move on to the A S T。 Now， for the A T， we're going to add a new。Kind of a special。

 like helper。Noode。We we'll just make a new section down here Helper。

 we're just gonna to call them per function parameter node。

I implementment this right underneath the program class， Malay region。Helpers and region。

The only reason I'm putting the function parameter node here is so we can use the typing in telecent down in the function。

After we modify this。So just for the sake of time， I'll copy and paste this。

Function parameters is just going to take in a string name and a value type string。

So that is just the A and then the int。 that's all it's going to take in。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_8.png)

Then same as everything else。 The type in the Json functions。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_10.png)

Now that we have this node implemented， we'll scroll down to function statement。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_12.png)

We're going to change the type of this parameterss function， to a list。Of function parameters。

Just for typing psych， and we're going to start off with our parser。

 we're going to import our function parameter node。 So from As T import function parameter。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_14.png)

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_15.png)

So we' can add another line here just for the helper nodes as we create them。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_17.png)

We need to go to our parse function statement node。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_19.png)

So， I'll take。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_21.png)

Or our parse function statement function。Down here in the。

Statement dot parameters will get rid of this。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_23.png)

Expect peak， we'll get rid of this to do。And we're going to set this equal to self dot underscore corner score parse。

Function。Parameter。It's going to be a new function。 we'll create。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_25.png)

So we'll create that right below this function， just for ease of use。So paste that in。So。

Be a list of our function parameter note。Go ahead and get a variable for that。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_27.png)

Function parameter empty list。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_29.png)

First thing we're gonna check is if the next token。Is a right parentheses。If so。

 that means we don't have any parameters。 So we'll just return back our empty list。

 So if self thought or squish core peak。Token is。Token type dot， right parentensheses。If it is。

 we'll go ahead in advance to that right parentheses。

And then we will return back our empty list of pms。If it's not。

We're going skip over our left parentheses by calling our next token。functionction。

We're going to get the first parameter。We're going to initialize that class。

The name is going to be our self dot current token。 not literal。 We're going to expect a colon。

 So if it's not a colon。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_31.png)

If not， expect peak token type。 colon。We' return none。 make sure we have an error route for that。

We're going to skip over that colon with our next token function。

 We're going to set our first parameters type， the first parameter dot value type。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_33.png)

It's going to be equal to the current tokens literal。 So that's going be this inch right here。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_35.png)

Now we're going append this function parameter to our parameterss variable。Appendned first per。Now。

 we're going to loop through and get all the rest of the parameters that were passed into this function or declared with this function。

So while self dot underscore underscore peak。Token is。Tokentype。t coa。

So while the next token is always a comma。 So there's still more to parse。

 we're going to call the next token function twice to skip over the comma。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_37.png)

Advance to our next parameter。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_39.png)

So parameter function parameter， make a new class。Self talk current token， not literal。

So we'll grab this colon， Exp Pete colon again， and we'll paste it in here。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_41.png)

next one should be a colon。 if it's not， we want to head out。If it is a colon。

 we're going skip over it because we don't care about it。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_43.png)

We're going to set our value type our parameters type to the current token not literal。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_45.png)

And we're gonna。A pen。The new parameterm to our list。So after that。

We're going expect there to be once。The next token is not a comma in this while loop， this will end。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_47.png)

And then we're expecting a right parentheses。Expect peak。Token type dot right perin。If it's not。

 we' return none， we return our he。At the very end of this。

 we'll return back all of our parsed parameters。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_49.png)

So that is a pretty big function。 But all it's doing is going， starting at this left pre see。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_51.png)

Psing each function parameter node until it hits the right parentheses。 and it's going to air。

 and it's going return back。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_53.png)

And allows to keep parsing our function。Now we need to move on to our expressions。

 So when these are being called， So our call expressions。

 when we have our parameters or arguments being passed into that。

 So we can scroll down to our parse call expression function。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_55.png)

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_56.png)

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_57.png)

Down here。So this is where we left that to do。Now， we're going get rid of this。 If not。

 all the way up here to。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_59.png)

The expression to arguments equals。And we're going to call new function， called self。Repon score。

 parse。Expression list。This will be a token type dot right parentheses。

 That is the token we're looking for to end our expression less Pre much。

 This will get reused later down the line for other things， Unlike our parse function parameters。

 which is kind of。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_61.png)

Centralized to our functions only。 So we'll implement this function right below call expression。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_63.png)

So it'll take in our self， in our end token。So be our end token type。

Return back a list of any type of expression note。First thing。

 we'll go ahead and declare our list of expressions。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_65.png)

We set that to an equal list or a empty list。 We'll go ahead and check if the peak token or the next token。

Is our end token type in our case right now， our right parentheses。

 which means we don't have any arguments to。Parse over。So we're going to skip over。

Our left parentheses with our next token， And then we'll return back our empty list。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_67.png)

We are going to hit our next token as well to skip over our left parenthees if we do， in fact。

 have some arguments to parse。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_69.png)

We're going to go ahead and append to our e list。Not a pent。Self do parse。Expression。

We' going to do our president's type of P lowest。Now， we'll do our while loop again。

 similar to our function parameters， self dot underscore our corner score peak。Token is。

So while we still see comm， So there's still more arguments to parse， we'll add two more next tokens。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_71.png)

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_72.png)

Skip over our unwanted tokens。And then， we will append。To our E home expression list。

Our parse expression， precede type dot P lowest。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_74.png)

So I'll keep doing that until we run out of comm。Once we run out of commons， we want to make sure。

That。Our next token is our ending token。 If not， something's wrong with our syntax。Or our grammar。

 So we need to return back none and throw our error in this function。V end， we return our E list。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_76.png)

Of expressions。So now that that's out of the way we can go to main dot pi。

 we can set our compiler and run code to false。Seent our parser debugged true。We'll go ahead， and。

Run our file。We got a bunch of pile errors， but that's fine。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_78.png)

We're looking， we're interested in our AS T。 so we'll go to AsT。 Json。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_80.png)

Now'll get the the lime file on the side。 So with these， we have our add function。 of course。

 we have parameters。 This is where our function parameters are getting parsed。 So they look correct。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_82.png)

Our body looks fine。 We go to our main。To our return statement， we're returning a call expression。

Calling the ad function。In the arguments of that。Addd function are just our integer of one and integer of 2。

 So that's parsing correctly。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_84.png)

So we can get out of here and move into our compiler。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_86.png)

First thing we'll do is import our function parameter。My AS T。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_88.png)

We're going to first fix a couple things in our visit function statement。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_90.png)

So it's on line 114。Visit function statement。This will not be identifier literals any more。

 This will be a function parameter list。And now that this is our function parameter。

 this will not be a P dot value， this will P dot name。

So that's just gonna that fixes everything to use our new function parameter node instead of our identifier literal nodes。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_92.png)

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_93.png)

Now we have PRm types。We can get rid of this two flag。Self thought type map。P not value。

P dot value type。For P in parameterss。So this is just gonna get the LL VM type for each of our parameter types and put them into a list。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_95.png)

Now scrolling a little bit down underneath where we set。

Our previous builder and set our new builder for the function。 We need to do a couple of things。

Such as the first thing will be。Storing the pointers。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_97.png)

To each parameter。So we need to allocate all of the memory for our parameters in the function。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_99.png)

So we'll have a prams printer list。It's for I， and then a type。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_101.png)

And we'll use our en nuerate function so we can get the index out of it， is where I comes out。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_103.png)

We'll enumerate through our pram types。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_105.png)

As we can see up here is just our L VM type mappings。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_107.png)

In our for loop， we' set a variable pointer。Do the self dot builder dot allocate。The LLVM type。

 we will self。 we will store it now。 So self dot builder dot store。

A function dot as at the index O that we're looking at in parameter types。

And we'll store it at that pointer。Then we will append this pointer。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_109.png)

To the list above。Next thing will do is。Add all of the parameters to our environment。So， we will。

Add adding the parameters。To the environment。Previous N V self not E And V here。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_111.png)

And then， underneath。The self dying， as we set our new function environment。We're going to do for I。

Common x。And enumerate， or needs a couple pythonic things。 We're in a zip。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_113.png)

The Param types list with the Para names list。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_115.png)

So just kind of combining them together， zipping them together so we can loop through them both at the same time。

We're going to set a type variable to the parameter。Types， I。We're going to grab of the pointer。

From Bram's pointer， I。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_117.png)

And then we are going define that in our。Environment。So， the x1。Tupple will be the pointer。

 and the type。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_119.png)

So we're defining that parameter in our environment or each parameter in our environment。

Then we're moving on to the rest of our code where we define the function， compile it。

And then set everything back to normal after it's been compiled。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_121.png)

Last thing when you do is go to our call expression functions， So visit call expression。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_123.png)

First thing is we need to fix this。 This is going to return a tuple of I R dot instruction。

If exppel in I R dot type。We have our name and our parameters， and here's our as and types empty。

Lists said W， get rid of this to do。If the length of parameters， the parameterss is greater than 0。

 So if there are parameters to go through or args。For x in parameterss。We are gonna。Grab the。

The parameter value in the。Perarameter type。From our resolve value function。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_125.png)

So resolve x。Or our parameters value。We're going toend to our arguments， this value。

Then we're going append to our types。This type。And that is absolutely it for resolving these variables for our functions。

 we're going to call。This function。From our environment， by that name。

And we're going to pass in the as and that we just set up here。

 And that's gonna go through the rest of the function for the call expression。



![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_127.png)

And this should be it。To go into our main not pie file again。We'll set parure to false。

 We'll set compiler to true。Go and run that。 And looks like we are。Getting some type of an error。

 So let's look through this 3 hours later。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_129.png)

Okay， the。Air here。Was a little weird， so。On in our visit function statement。

In where we set our previous environment。We set the parent to our previous environment variable。

And then， in here。X， I needs to actually be x1 since x is a tuple。 So we want the。

First index of that tuupple。 So X1， not X I。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_131.png)

And then we run that。 Everything should。 There should be no errors。What investigate our IR code。

So in our main function， we are。Calling the add function with the one and 2 as the arguments。

 Then we return back whatever the result is。In our ad， we're storing these two parameters。

 We're allocating our types， them are loading them。

And then adding them together and returning them back。

And that's where So everything's looking pretty good here。

 We go into main dot pi and set run code to true。 Sa that。And then program return 3。Now。

 we can add 50 plus 50。Should be 100 cool。We can go ahead and add a new function。Be an。And。

And we at pause a minus B。Put semi column for funds。 So we'll add this just make that sub 50，50。

She equals0。Now， I don't know how negative is gonna hold， but they'll see。Now， wait hold on。

 let's dumb。So 50 and then 20 here。 will this give us negative 30 by chance。 Okay， yeah。

 we don't have negative numbers implemented yet， but hey。We sure can get him。But yeah， all right。

So that is adding parameters to our function。 so you can now call functions with any amount of parameters。

We'll see you guys in episode 11， where we're going tackle adding strengths to our language。

 and finally， the print dev function。

![](img/93fee7ca9a35ce8b29b816ec2ebfb1f0_133.png)