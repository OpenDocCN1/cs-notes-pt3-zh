# 使用-Python-和-LLVM-创建编程语言-p08-P08-Episode-8---If-Statements-+-Booleans--BV1hn5RztEt8_p8-

Welcome back to the programming language series where we're going to build a statically typed and Git Gt compiled language using nothing but Python and LLVM Today。

 we're going to tackle if statements， conditional operators and booles。

 So this is going be the code that we're going to be able to compile by the end of this episode。

 We're just have it。 We're initializing a variable。 We have our new if statements in here A equals 5。

 It's going to reassigns。 We're going to go。

![](img/1f8d0b70015acef737e03658515eb7f9_1.png)

To our variable reassignment a equals 5。 we're going to set it to 69。 nice。 If it's not。

 we're going to set it to 4，206。And then we're going to return a back and see what the program returns。

 So let me back out of here in C D end episode 8。

![](img/1f8d0b70015acef737e03658515eb7f9_3.png)

First thing we're going to need is go to our token class。

 So I'm going to add a new region into here as comparison symbols。

 We'll put it underneath equal side。So we're going to add the less than the greater than equals equals。

 not equals， less than equals and greater than equals。

So these are all the comparison operators we're going to add for right now。



![](img/1f8d0b70015acef737e03658515eb7f9_5.png)

We're going to add two new keywords， our if keyword。



![](img/1f8d0b70015acef737e03658515eb7f9_7.png)

Our else keyword。 And then we're going to add two more for true。And false。



![](img/1f8d0b70015acef737e03658515eb7f9_9.png)

Is are boolean tokens。So now that we added all of these here。

 we need to set some keywords in our dictionary。

![](img/1f8d0b70015acef737e03658515eb7f9_11.png)

So， our if keyword。

![](img/1f8d0b70015acef737e03658515eb7f9_13.png)

It's going to be equal to token type dot if。

![](img/1f8d0b70015acef737e03658515eb7f9_15.png)

Or else， keyword， token type。Do else。True。Co can type do true。Then false。Token type dot false。



![](img/1f8d0b70015acef737e03658515eb7f9_17.png)

Now， I do have a couple of Gen Z sllings that I'm going to use for if else。



![](img/1f8d0b70015acef737e03658515eb7f9_19.png)

So for if， we're going to say sus because。If kind ofces。Token type that is。And then， imposster。

For else， said token type Dot else。 Now that we have suss and impostor in here。

 we have all of our keywords set up for if else， true and false。



![](img/1f8d0b70015acef737e03658515eb7f9_21.png)

![](img/1f8d0b70015acef737e03658515eb7f9_22.png)

So we can move on into our Leer and start actually making tokens from these。



![](img/1f8d0b70015acef737e03658515eb7f9_24.png)

![](img/1f8d0b70015acef737e03658515eb7f9_25.png)

Alright，This's gonna be a little bit of code， but we will run through it。



![](img/1f8d0b70015acef737e03658515eb7f9_27.png)

So underneath our percent modulus sign， I'm going to paste in all of this。

 So we're going to do our less than sign。 first， of course， we need to handle less than or equals。

 So we check if the next character in the source code is an equal sign。

 We'll read the character and then set that to less than equals。 If it's not an equal sign。

 then we're just， we know it's just straight up less than sign。



![](img/1f8d0b70015acef737e03658515eb7f9_29.png)

![](img/1f8d0b70015acef737e03658515eb7f9_30.png)

![](img/1f8d0b70015acef737e03658515eb7f9_31.png)

And we'll return that new type same thing for equals and equals equals and for our bank。



![](img/1f8d0b70015acef737e03658515eb7f9_33.png)

![](img/1f8d0b70015acef737e03658515eb7f9_34.png)

All we have right now is bang equals。 So we don't have the actual bang operator。



![](img/1f8d0b70015acef737e03658515eb7f9_36.png)

Or the negate operator implemented yet that's going to happen in a later episode。So for now。

 I have slapped it to do， and we're just going to return back in a legal symbol for right now。



![](img/1f8d0b70015acef737e03658515eb7f9_38.png)

Now that I have pasted this in here， I'm just going to get rid of my。

 I'm just going to get rid of my equals case from before。 So we don't have two equal s cases。

 but you'll just。

![](img/1f8d0b70015acef737e03658515eb7f9_40.png)

![](img/1f8d0b70015acef737e03658515eb7f9_41.png)

Alter that。So you can pretty much copy and paste the first one and just change the symbols and the token types for each one。

 After you have all that done， we're ready to get into our A T。



![](img/1f8d0b70015acef737e03658515eb7f9_43.png)

![](img/1f8d0b70015acef737e03658515eb7f9_44.png)

So we'll go to our AS T in our As T。 we're going to have to add two months。

 We're going to add our if statement node type。

![](img/1f8d0b70015acef737e03658515eb7f9_46.png)

Down here with our statements， let if statement。Then we're going to add our boolean。

 So our boolean literal will go down here with our lital。 Go down to the end of statements。



![](img/1f8d0b70015acef737e03658515eb7f9_48.png)

![](img/1f8d0b70015acef737e03658515eb7f9_49.png)

Start to create。 I'm going copy and paste this so you guys can pause the video and get this copy down into your。



![](img/1f8d0b70015acef737e03658515eb7f9_51.png)

Actual project， but I'll go over it。 So if statement will take in a condition。



![](img/1f8d0b70015acef737e03658515eb7f9_53.png)

![](img/1f8d0b70015acef737e03658515eb7f9_54.png)

So， in our。In our code right here， this is our condition， So a equals equals 5。

 So it's just some type of expression。

![](img/1f8d0b70015acef737e03658515eb7f9_56.png)

Of our consequence， that'll happen if condition， if there's an else block。

 this will have all the code in that else block。

![](img/1f8d0b70015acef737e03658515eb7f9_58.png)

Or it'll stay none if there's not an else to it。So everything's the same。

 So we'll set our no type to an if statement。 we'll set up our Json。



![](img/1f8d0b70015acef737e03658515eb7f9_60.png)

This right here is just in case this alternative ease of dev。 Missus actually can be none。

So I set just an in line if statement here。 Turn back none if there is not an all。

 moving on into our Boolean lip。

![](img/1f8d0b70015acef737e03658515eb7f9_62.png)

![](img/1f8d0b70015acef737e03658515eb7f9_63.png)

Copy any of these A S T nodes in the literals and just change it。

 So they're pretty much the exact same as the other。 So we'll save that。

 and we will go into our parser。 So in our parser， we need to actually import both the var nodes we created。

 So our if statement。

![](img/1f8d0b70015acef737e03658515eb7f9_65.png)

![](img/1f8d0b70015acef737e03658515eb7f9_66.png)

![](img/1f8d0b70015acef737e03658515eb7f9_67.png)

We'll go here in our， we have a precedes or precedences to add。



![](img/1f8d0b70015acef737e03658515eb7f9_69.png)

So we'll go down here。

![](img/1f8d0b70015acef737e03658515eb7f9_71.png)

Now， paste these。So we have our equals equals， and these are going to be set to our P equals precedence less than a greater than。



![](img/1f8d0b70015acef737e03658515eb7f9_73.png)

![](img/1f8d0b70015acef737e03658515eb7f9_74.png)

Of course， get our less greater precedes。 Add these six precedes to our。 Now。

 we need to go to our infi parse。 Wed add our six more to our infi。

 All of these is just going to be up for our all of our tokens that we did above in every single one of them。

 we'll call our parse infi。 We can come up to our parse prefix functions now。



![](img/1f8d0b70015acef737e03658515eb7f9_76.png)

![](img/1f8d0b70015acef737e03658515eb7f9_77.png)

![](img/1f8d0b70015acef737e03658515eb7f9_78.png)

![](img/1f8d0b70015acef737e03658515eb7f9_79.png)

We'd add three more entries。

![](img/1f8d0b70015acef737e03658515eb7f9_81.png)

1 for our if statement。So if we have an if， we have a new function pars if statement。

 If it's a true or a false， we want to parse that boolean。



![](img/1f8d0b70015acef737e03658515eb7f9_83.png)

![](img/1f8d0b70015acef737e03658515eb7f9_84.png)

So thatllturn back our literals。 The first thing we will implement is our if statements。

 So we'll comp going on to our parse。 the end of our parse statements。



![](img/1f8d0b70015acef737e03658515eb7f9_86.png)

![](img/1f8d0b70015acef737e03658515eb7f9_87.png)

Region blocks。 we'll just keep on scroll into where assignment。



![](img/1f8d0b70015acef737e03658515eb7f9_89.png)

Do deaf partsif statement。Take in self and initialize these three variables first。 So our condition。

 consequence and alternative。

![](img/1f8d0b70015acef737e03658515eb7f9_91.png)

![](img/1f8d0b70015acef737e03658515eb7f9_92.png)

We'll go ahead， and。

![](img/1f8d0b70015acef737e03658515eb7f9_94.png)

Advanced the le surpas the actual if token。

![](img/1f8d0b70015acef737e03658515eb7f9_96.png)

We'll take our condition。So self dot parse expression。



![](img/1f8d0b70015acef737e03658515eb7f9_98.png)

Take in the precedent type of the lowest value。

![](img/1f8d0b70015acef737e03658515eb7f9_100.png)

We're expecting after our condition， we're expecting a left brace。 So if not， self do。



![](img/1f8d0b70015acef737e03658515eb7f9_102.png)

Unders corner score， Exp peak。

![](img/1f8d0b70015acef737e03658515eb7f9_104.png)

Token tight， dot left brace。Now， we're going to check to see if we do have an else block or not。

 So if self dot peak token is。

![](img/1f8d0b70015acef737e03658515eb7f9_106.png)

A token type of else。

![](img/1f8d0b70015acef737e03658515eb7f9_108.png)

So if it is， we'll advance the Leer or the parser pass that else token。



![](img/1f8d0b70015acef737e03658515eb7f9_110.png)

We're going to do this same expect peak function。

![](img/1f8d0b70015acef737e03658515eb7f9_112.png)

Were expecting a left brace。Then we're going to fill in our alternative。



![](img/1f8d0b70015acef737e03658515eb7f9_114.png)

Will parse a block statement for that alternative value。



![](img/1f8d0b70015acef737e03658515eb7f9_116.png)

And we'll cop out of this if statement， and we'll do if。



![](img/1f8d0b70015acef737e03658515eb7f9_118.png)

So that's it for our parse if statement function。So we'll go into our parse。

 should be at the very bottom。 We'll just paste。 I'll paste this in。 It's really short。

 All this is doing is seeing if the current token is a true token。



![](img/1f8d0b70015acef737e03658515eb7f9_120.png)

And this will return back an actual Python Boolean。



![](img/1f8d0b70015acef737e03658515eb7f9_122.png)

So that will set our our booley and our AS T node as well。 So if it's true。

 this will return a Python true。And then that will become our boolean。 So that is it for the parser。

 So we'll check our work with main dot pi。

![](img/1f8d0b70015acef737e03658515eb7f9_124.png)

We'll set compiler and run code if false。 Now we will Python main dot wrote successfully。

 So we'll go into our AS T dot Json and we'll pull up test dot line as well。



![](img/1f8d0b70015acef737e03658515eb7f9_126.png)

![](img/1f8d0b70015acef737e03658515eb7f9_127.png)

![](img/1f8d0b70015acef737e03658515eb7f9_128.png)

So we have our function， of course， our block statement， and we'll go into our。



![](img/1f8d0b70015acef737e03658515eb7f9_130.png)

So our let statement， then we have an expression。 the condition is a in fixed expression。

 So a equals。 if that's true， we have another block statement and we assign a to 69。



![](img/1f8d0b70015acef737e03658515eb7f9_132.png)

Nice。

![](img/1f8d0b70015acef737e03658515eb7f9_134.png)

We have an L statement as well。 So our alternatives another block statement where we assign a。



![](img/1f8d0b70015acef737e03658515eb7f9_136.png)

2，4，20，6。

![](img/1f8d0b70015acef737e03658515eb7f9_138.png)

And then we end up returning A。 So the A T is looking perfectly fine for right now so we can move in and set our parser to false。

 first thing as always， import our newly created notes or if statement and we're going to go down to the compile method and add in our if statement So case node type。



![](img/1f8d0b70015acef737e03658515eb7f9_140.png)

![](img/1f8d0b70015acef737e03658515eb7f9_141.png)

![](img/1f8d0b70015acef737e03658515eb7f9_142.png)

No type。If Sa。

![](img/1f8d0b70015acef737e03658515eb7f9_144.png)

And that's gonna call any function visit， if statement。

We do have a lot of new stuff to add into this compiler。

 So we'll go down to visit our if statement function。

 So'll go to the bottom of all of our visit statements。



![](img/1f8d0b70015acef737e03658515eb7f9_146.png)

![](img/1f8d0b70015acef737e03658515eb7f9_147.png)

Underneath the sign。So de is if statement self。

![](img/1f8d0b70015acef737e03658515eb7f9_149.png)

Takes in a node of the type it。 We're going to grab all of our variables from our node。

 So our condition consequence and alternative。

![](img/1f8d0b70015acef737e03658515eb7f9_151.png)

![](img/1f8d0b70015acef737e03658515eb7f9_152.png)

First thing we'll do is we're going to test our actual conditions。 We'll name it test。



![](img/1f8d0b70015acef737e03658515eb7f9_154.png)

And then this will be our type， but all'll just said as an underscore because we don't need it。



![](img/1f8d0b70015acef737e03658515eb7f9_156.png)

Self dot resolve value。And will'll pass in our condition。

 This will resolve whatever our condition equals out to。



![](img/1f8d0b70015acef737e03658515eb7f9_158.png)

So if the alternative is none， that means we don't have an L statement。 So we want to use。



![](img/1f8d0b70015acef737e03658515eb7f9_160.png)

Something a little new。 If you have used Python a lot。

 you've seen this same thing that we use for opening our。



![](img/1f8d0b70015acef737e03658515eb7f9_162.png)

![](img/1f8d0b70015acef737e03658515eb7f9_163.png)

File， but this width statement。So， with。Self。Thought builder。Dot if then， So as you can see。

 there is a if then in an if else statement in。

![](img/1f8d0b70015acef737e03658515eb7f9_165.png)

![](img/1f8d0b70015acef737e03658515eb7f9_166.png)

On the builder， we're using， So after we pass in that test。We'll just call ourselves to compile。

 and we'll compile our consequence。 So generate that。



![](img/1f8d0b70015acef737e03658515eb7f9_168.png)

IR code for that。So if there is an alternative， so why an else statement here。With。Self dot builder。

 dot if else。Test。And we'll break these variables out from that function。First one will be true。



![](img/1f8d0b70015acef737e03658515eb7f9_170.png)

The next one will be otherwise。So I have a little bit of a comment I'm going to put in here just to help visualize what's going on。



![](img/1f8d0b70015acef737e03658515eb7f9_172.png)

![](img/1f8d0b70015acef737e03658515eb7f9_173.png)

So the this is just creating a condition branch。 So if this condition is true。

 it's going to branch to whatever our consequence or if block。Coode is。

In the actual execution of our code。 And if that condition is false。

 it's just going to jump or branch straight to the else branch of this tree。 So we're going。

 I'll keep this here。

![](img/1f8d0b70015acef737e03658515eb7f9_175.png)

Just so you guys can see this。 So with true， if this is true， so true is actually a value。



![](img/1f8d0b70015acef737e03658515eb7f9_177.png)

We're to compile our consequence。

![](img/1f8d0b70015acef737e03658515eb7f9_179.png)

Function so far integer types first， we'll go below this。 I I need to come back to this。 I apologize。

 I forgot this was even a thing。 So I'll come back to this p symbol。



![](img/1f8d0b70015acef737e03658515eb7f9_181.png)

![](img/1f8d0b70015acef737e03658515eb7f9_182.png)

![](img/1f8d0b70015acef737e03658515eb7f9_183.png)

But we're going to paste in these cases。So every single one of these comparison operations for integers in particular。

 make sure this is our integer， if statement。

![](img/1f8d0b70015acef737e03658515eb7f9_185.png)

![](img/1f8d0b70015acef737e03658515eb7f9_186.png)

It uses an ICMP signed， so you can create one of these， paste them all and just change these symbols。



![](img/1f8d0b70015acef737e03658515eb7f9_188.png)

And these will do our comparison operation and return back and we'll move into our。



![](img/1f8d0b70015acef737e03658515eb7f9_190.png)

Floats now， I'll paste these。 you guys can pause and copy them as well。 All of them use the FCP。

 So float compare ordered。

![](img/1f8d0b70015acef737e03658515eb7f9_192.png)

![](img/1f8d0b70015acef737e03658515eb7f9_193.png)

And you could just copy or make one of these copy paste for all the other comparisons and enter in the symbols on this function as well。



![](img/1f8d0b70015acef737e03658515eb7f9_195.png)

So that's all we need for the infi expression function。



![](img/1f8d0b70015acef737e03658515eb7f9_197.png)

We now need to scroll down a case statement into this。 So below identifier。

 paste in bully and little Try here again is just for intelligenceence。 You don't need this at all。



![](img/1f8d0b70015acef737e03658515eb7f9_199.png)

![](img/1f8d0b70015acef737e03658515eb7f9_200.png)

But this will return a constant with the type and it's going to return one if the no dot value is true。

 if not， it's going to set that constants value to 0， and then it' will return back that as well。



![](img/1f8d0b70015acef737e03658515eb7f9_202.png)

![](img/1f8d0b70015acef737e03658515eb7f9_203.png)

Alright， so that's pretty much implemented here。 We do need to implement a couple more things for our actual bulloleanance。

 So actually registering the true and the false。

![](img/1f8d0b70015acef737e03658515eb7f9_205.png)

So up here in our very top of our compiler in our tight map， we're going to add the bull。



![](img/1f8d0b70015acef737e03658515eb7f9_207.png)

Type some IR dot bull。

![](img/1f8d0b70015acef737e03658515eb7f9_209.png)

Int type 1， sorry。At the bottom of our init method。



![](img/1f8d0b70015acef737e03658515eb7f9_211.png)

We're going to do a new function we're going to call is self underscore underscore initialize。

Builtins。

![](img/1f8d0b70015acef737e03658515eb7f9_213.png)

We are going to declare that function right below the in。



![](img/1f8d0b70015acef737e03658515eb7f9_215.png)

So initialized builtins just takes itself and won't return anything。



![](img/1f8d0b70015acef737e03658515eb7f9_217.png)

This function is going to have a function within it， just for fun。



![](img/1f8d0b70015acef737e03658515eb7f9_219.png)

So in itbuoleys。This will turn a tuple。Of first value being a global variable。



![](img/1f8d0b70015acef737e03658515eb7f9_221.png)

IRt global variable。 the second value will be an IRt global variable， as well。



![](img/1f8d0b70015acef737e03658515eb7f9_223.png)

So this is where we're going to actually build our constants for true and false within the LL VM IR code。



![](img/1f8d0b70015acef737e03658515eb7f9_225.png)

![](img/1f8d0b70015acef737e03658515eb7f9_226.png)

First thing is， we're just going extract this Boolean types。



![](img/1f8d0b70015acef737e03658515eb7f9_228.png)

It's an IR type。For our tight map。First thing we're going to do is our true variable。

 So I'll paste these in for the sake of time。

![](img/1f8d0b70015acef737e03658515eb7f9_230.png)

We're going to create a IR dot global variable passing in the module。

 and it will be our Boolean type。

![](img/1f8d0b70015acef737e03658515eb7f9_232.png)

And the name of that global variable or global constant pretty much is our， is true。

We make our initializer。And I are constant。So it's going to be initialized to one， which means true。



![](img/1f8d0b70015acef737e03658515eb7f9_234.png)

And we're going to set that to be a global constant。Now， you can copy paste the same thing。



![](img/1f8d0b70015acef737e03658515eb7f9_236.png)

And just change everything to false。Variable， so false here。

 And we're going to change this number to 0， because that represents a false boolean type。



![](img/1f8d0b70015acef737e03658515eb7f9_238.png)

![](img/1f8d0b70015acef737e03658515eb7f9_239.png)

And this is also a global constant。And from this inner function。

 we're going to return our true variable and our false variable。 So we're going to return that tuple。



![](img/1f8d0b70015acef737e03658515eb7f9_241.png)

Now， lower down in the initialized built ins function。



![](img/1f8d0b70015acef737e03658515eb7f9_243.png)

We're going to grab out our true variable， and our false variable。From R in it。Bole's function。



![](img/1f8d0b70015acef737e03658515eb7f9_245.png)

And we are going to define these in our environment so we can't name a variable true。

Or a function true。 These are。 This is gonna to be a reserved keyword。So the name is true。

The value will be our true variable。And our type will be the true variable， that type。

And you can copy， paste this again for false。

![](img/1f8d0b70015acef737e03658515eb7f9_247.png)

It just changes to false， false variable， false variable that type。



![](img/1f8d0b70015acef737e03658515eb7f9_249.png)

Now that this is set up， this is going this function is going to branch us into our built in functions as well。

 in any other reserved keywords you want to add your language。 This is how you would。

Initialize them here。So later down the line， when we get our print f function。

 this will be where we first set up that actual。

![](img/1f8d0b70015acef737e03658515eb7f9_251.png)

![](img/1f8d0b70015acef737e03658515eb7f9_252.png)

Global pointer to that function。So we can go into our main dot pi file now。

 make sure our compiler is set to true。

![](img/1f8d0b70015acef737e03658515eb7f9_254.png)

![](img/1f8d0b70015acef737e03658515eb7f9_255.png)

pier debug is said to true， and we'll run that。Program again。

 we'll look at our IR code and we'll bring up our test line as well。



![](img/1f8d0b70015acef737e03658515eb7f9_257.png)

So right off the bat， first two new things you'll see is true and false up at the very top。

They're declared as a constantsance， and they can be used everywhere and true and false cannot be changed that we compile our error and a bunch of other errors down the line。

We define our main function， of course， in our entry block。We set our variable， equal to 5。

This is where we compare so that I， we're going to load that a， and we're going to compare。

A see if it's equal to 5。And this is where our branch is， so。Depending on what this。

Comparison equals。 if it's true， we're going to jump to the main entry if block。If not。

 if it's false， we're going to jump to the main entry else block。So our maidenry。

 if restoring that 69。Into a。And it's gonna jump to the end if block。For the else。

 we're storing a equals 4，20。 And then we're going to jump to end if as well。

 And this is where we load a and then return a back。So the IR code is looking pretty good。

 So I think we can go to our main dot pi。

![](img/1f8d0b70015acef737e03658515eb7f9_259.png)

![](img/1f8d0b70015acef737e03658515eb7f9_260.png)

Bring that back。We go to our main dot pi， and。

![](img/1f8d0b70015acef737e03658515eb7f9_262.png)

Set our run code flag to true， as well。

![](img/1f8d0b70015acef737e03658515eb7f9_264.png)

Run that。And as we can see， we do have an a statement。 So a equals 5。

 So it reassigned the variable A is 69 and return it back。 And here we are。So I can set this to one。

 So a equals one， so it should set。For20， here we are perfect。If a is not equal to 1。

 This should take us to 69，3 technical difficulties。 I completely forgot about。



![](img/1f8d0b70015acef737e03658515eb7f9_266.png)

![](img/1f8d0b70015acef737e03658515eb7f9_267.png)

The not equal statement in here。 So if you caught that good job。



![](img/1f8d0b70015acef737e03658515eb7f9_269.png)

We're going to set not equal here。 We're going set not equal here。



![](img/1f8d0b70015acef737e03658515eb7f9_271.png)

And we're going to test that。

![](img/1f8d0b70015acef737e03658515eb7f9_273.png)

So， that'll work。 Alright， so we will copy this down into our floats。



![](img/1f8d0b70015acef737e03658515eb7f9_275.png)

When we use RF FCP ordered。

![](img/1f8d0b70015acef737e03658515eb7f9_277.png)

![](img/1f8d0b70015acef737e03658515eb7f9_278.png)

That will be our integer type as well。 Okay， so after that technical difficulty， you can now see。



![](img/1f8d0b70015acef737e03658515eb7f9_280.png)

That。Main dot pi is now a is not equal to 1， So it's going return to 69。 So we not equal to 5。

 So a is 5。 so we can get 4，20。 So our if statements are conditional operators in our booles are now implemented。

 So feel free to play around with those。 If you do notice any bugs， please hit me up on discord。

 and I can make a patch video out。 I think we're all good， though now。



![](img/1f8d0b70015acef737e03658515eb7f9_282.png)

If you have any questions， comments， concerns， please put in the comments section or join our Discord and link us in the description。

Below this video in our next episode， we're going to be going into function calling。

 So we're going to actually have。

![](img/1f8d0b70015acef737e03658515eb7f9_284.png)

External functions， such as like an add function。Or a test function that returns something。

And we'll turn it back， and then we'll move on to episode 10， which is function parameters。

 So thanks， guys for watching。 And I will see you in episode 9。



![](img/1f8d0b70015acef737e03658515eb7f9_286.png)