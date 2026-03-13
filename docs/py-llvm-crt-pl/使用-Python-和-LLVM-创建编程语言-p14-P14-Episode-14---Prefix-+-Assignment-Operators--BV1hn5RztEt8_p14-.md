# 使用-Python-和-LLVM-创建编程语言-p14-P14-Episode-14---Prefix-+-Assignment-Operators--BV1hn5RztEt8_p14-

We' go to E 14， for this episode， we're going to be focusing on two concepts。

 We're gonna to have prefix operators。 So negative symbol and the not operator here。



![](img/69db6256f9dfb864a5ccc710bf040937_1.png)

Are going to be up one half of what we're doing today。

 The other half will be adding assignment operators。 So we have plus equals。

 minus equals times equals and divide equals。So for this initial test。

 I'm just going to use it right here in the for loop since we're expecting an assignment statement。

 So that will be our test online line file to make sure we get on track today。 So first things first。

 we'll go into our token file。We're going to go to our token type enum。And in the， let's see。

 let's do it in the symbols。Area， we're gonna to add our bank。bank， good bank。

So that's our exclamation point。I'm gonna go here to the assignment operators little section I have。

 I'm just gonna paste these in for the sake of time， but。

We have plus equals minus multiply and divide equals。So we're going to add all those token types。

 and then we can save that and move on into our Lexer。 So our Lexer dot pi。

 we need to add the case statements for those new token types we just added。



![](img/69db6256f9dfb864a5ccc710bf040937_3.png)

We'll start with the bank operator。 So right here， we had a to do statement or to do comment for our bank operator。

 So all we can have to do here is just change the legal to bank and we'll go ahead and get rid of our comments。

If you have one there。We'll save that。And now time for our plus equals and everything else。

 So up at the top where we have our plus case statement。

 we're going to do something similar to the minus sign down here。 So I'm going to control X that。

 save it。If self dot peak cha。So if the next character is an equal sign。

Then we want to save the current char that we're on right now。We wanna go ahead and advance the。

Lexer。So， read Shar。Like I can type。And then， we'll paste in。

This will change this token type  to plus equals。And then， we'll do。Or save char。

 plus the current cha。And then in the elself's statement。

 that's where we'll paste in our just a normal plus token。So for this。

 we'll do pretty much the same thing for every。One of our new assignment operators。

 So I'm gonna copy this。

![](img/69db6256f9dfb864a5ccc710bf040937_5.png)

Arrow handling。I'm going to paste it down here， change it to an eph。

 change this string right here to an equal sign。And then change the token type in the new token function to a minus equal。



![](img/69db6256f9dfb864a5ccc710bf040937_7.png)

Then at times equal， I'm just going to paste this in。 Sam as everything before。

 We check with peak char for if the next one's equal。Save it， advanceance the Leor。

 create the token and saving the literal as both the plot or the asterisk and the equal sign。

And then if not， we're just， it's just the normal。Ass， And finally， we have our divide case。

 So I'll paste that in， Same as before， just changing this to div equal and slash。 Now， that's。

 that's out of the way we can。Save this file and we can move on into our As T do pi。



![](img/69db6256f9dfb864a5ccc710bf040937_9.png)

So we'll scroll to the top to our node types。 We'll go down to the expressions section。

 and I'll paste in this prefix expression is going to be our new node type equals prefix expression。

Now we'll scroll down to our expressions region， right under call expression。



![](img/69db6256f9dfb864a5ccc710bf040937_11.png)

I'll enter down and paste in the new node prefix expression。 It's going to take in an operator。

 which is a string and the right node to that expression。 So in our test dot line。

 it will give us a minus sign。 And then the right node will be the integer 10。

 now that we have that node。

![](img/69db6256f9dfb864a5ccc710bf040937_13.png)

Set away in As T， we can save that file and move on into our parser。



![](img/69db6256f9dfb864a5ccc710bf040937_15.png)

Scroll up to the top。In our expressions， little line here will' import that prefix expression。

Save the file。And I forgot one more thing to do in AT。 We need to go to these statements。

We need to find a sign statement。Sign statement here。

 We need to modify this assigned statement to also include an operator now， so。

In the init function operator string。Goes an empty string， and then we'll add self。Dot operator。

Equals operator。Now， that should be everything we need for the A T。

 So move back into the parser after we've imported this。



![](img/69db6256f9dfb864a5ccc710bf040937_17.png)

![](img/69db6256f9dfb864a5ccc710bf040937_18.png)

We can go down to the prefix parse functions。Dictionary we have in our innate function。



![](img/69db6256f9dfb864a5ccc710bf040937_20.png)

We'll add two more entries into this。 So I'll enter down just for some space。We'll paste that in。

 We have one prefix function for minus。And then one for bank。

 And both of these are going to call the parse prefix expression function。



![](img/69db6256f9dfb864a5ccc710bf040937_22.png)

So we'll implement that。 We'll scroll down to our expressions at the very bottom。Inner down de。

 underscore underscore parse。 you'll see。 Alright， underscore underscore parse prefix expression。

Self can return that prefix expression node。We're gonna go ahead and set up the。

Prefix expression node。Wass a new instance of prefix expression。

Will set operator equal to the current tokens literal。Go ahead and advance theelir or the parser。

We're going to set the right node。Variable equal to our parse expression function。

So we want to parse an expression from this。And these next tokens。

Prescience type is going to be the lowest。Or I'm sorry。 it's gonna be prefix。

Since we've added that beforehand。

![](img/69db6256f9dfb864a5ccc710bf040937_24.png)

And then we're going return the prefix expression。Now we're going to scroll up to our helper methods。



![](img/69db6256f9dfb864a5ccc710bf040937_26.png)

Under here， let's do it above expect peak。

![](img/69db6256f9dfb864a5ccc710bf040937_28.png)

We're going to create a new function。 underscore， underscore Pe token is assignment。

 So this function is just going to tell us whether or not the peak token is one of our assignment operators。

It will take in self， it will return a boolean， true or false。The assignment。Operators。

Me a list of token types。

![](img/69db6256f9dfb864a5ccc710bf040937_30.png)

So all of our assignment operators are the equal sign。The plus equals。



![](img/69db6256f9dfb864a5ccc710bf040937_32.png)

Sign， and I'll paste in the last three， minus equal， multiply and divide equal。SoNow。

 all we have to do is return。The self dot pig token dot type。In assignment operators。

 So if this type of the peak token is one of these， this will return true。 If not， it'll be false。



![](img/69db6256f9dfb864a5ccc710bf040937_34.png)

And we'll copy this function name willll scroll down to parse statement right here in this if statement。



![](img/69db6256f9dfb864a5ccc710bf040937_36.png)

We check to see if it is an equal sign to signify that this is a parse assignment statement that we need to run that function。

Now， we can use our new helper function instead。Just to clean up the code a bit。 So if the。

The token is any of those assignment tokens or。Yeah， if any of those are assignment tokens。

 that's when we'll call this function。 Now， we'll control click to the parse assignment statement here。



![](img/69db6256f9dfb864a5ccc710bf040937_38.png)

![](img/69db6256f9dfb864a5ccc710bf040937_39.png)

Instead of skipping the equal sign here。We're gonna add our value to our new property operator on the assignment statement。

We'll set operator itself dot current token do literal。

 and then we'll add our next token to skip it after we've set this。So we'll keep the right value。

 everything else the same in here。And that should complete everything we need to do in the or the parsers so we can move into the compiler。

 Now， we'll scroll to the top， go ahead and import our prefix expression node。



![](img/69db6256f9dfb864a5ccc710bf040937_41.png)

![](img/69db6256f9dfb864a5ccc710bf040937_42.png)

AlrightWe're going to scroll down to our expressions region at the very bottom of this。

 So underneath visit call expression， we'll enter down。



![](img/69db6256f9dfb864a5ccc710bf040937_44.png)

![](img/69db6256f9dfb864a5ccc710bf040937_45.png)

We're going create a new function visit， underscore score visit。Prefix expression。Takes in a self。

 and the prefix expression node。And it's going to return back a tuple of I R type values， the first。

Element and A IR type as the second element。So we're returning this。

Pretty similar to how the call expression does it。Because this function is going to be called in our resolve value function down here。

We'll implement this function first before we call it。

So we're going break up this node into an operator。VVable， we're gonna break it again to a node。

So this would be an expression node dot right node。

We're going to resolve the value of this right node。 So right value。Right type。

Wes self dot underscore underscore score resolve value。 And we're gonna pass in that right node。

 as the expression。

![](img/69db6256f9dfb864a5ccc710bf040937_47.png)

We're going to set the type variable to none。We're set a value variable to none。So， if。

Is instance built in Python method。If this right type here is the IR float type。

We're going to set type equal to IR dot float type。



![](img/69db6256f9dfb864a5ccc710bf040937_49.png)

We're going to do a match statement。 So match the operator that we're using。



![](img/69db6256f9dfb864a5ccc710bf040937_51.png)

If the case， it is a negative symbol， or to set value equal to。Calling our builder。Dot F Mo。

So this is going to be float multiplication。We wantna multiply the right value。Times。

 we're going to create a new constant value in L L VM。The I dot constant。It's gonna be a float。

Type constant， and the second parameter will be negative 1。0。 So if we see this。

 we're just gonna multiply whatever this value is by negative1。And that will flip the case。

 so that will turn it negative or if it's your。Putting a negative on a negative number。

 Those will cancel out and make a positive。

![](img/69db6256f9dfb864a5ccc710bf040937_53.png)

Last case here， we have our bang symbol。And that value is just going to be an IR dot constant。

It's going to be an int type 1。 So a boole under or a bit。And that's gonna be 0， so。

0 is gonna be pretty much equal to false on that。 So we're falsifying and not operator。LF。

The right type。Is an int。 So I heard an int type。We're going to set the type variable。

So you have an IR int type， and it's going to be a 32 B inchcher。

We're going to do another match statement。Very similar to what we did up here。

 So I'm gonna to go ahead and copy this， paste it。

![](img/69db6256f9dfb864a5ccc710bf040937_55.png)

Instead of F mole， we're going to use just regular mole。 instead of float type。

 we're going to change this to int type。And there will be a 32 B integer。

 and we'll get rid of this decimal in 0。So it's going to do the same thing as floats。

 except we're dealing with integers。 So we have to slightly declare constant differently and use a different function。

Now， down here in the case statement， we can use something on the builder， self dot builder， dot not。

And we can pass in that right value and it'll do pretty much the same thing as we're doing here。

 At the very end， we can enter down in return， value and type。From this function。

And I willll copy that function name。We'll scroll down to resolve value should be right below it。



![](img/69db6256f9dfb864a5ccc710bf040937_57.png)

To our expressions， we'll add in case。Noode type dot prefix expression。

Then we're going to return a self dot visit prefix expression call。

And we're going to pass in that note。So we can save that。 We'll move on to our final thing。

 So we need to go to our visit assigned statement and our statement methods。

' just try to figure out where that is。 There it is。Alright。

 we're gonna modify this function slightly heavily。So we're gonna add in between name and value。

 we're gonna bring out our operator as well that we've added。 So node dot operator。

We're gonna go ahead and move this。Below here。We're gonna go ahead and get rid of。



![](img/69db6256f9dfb864a5ccc710bf040937_59.png)

We're going tab those to the left one and we get rid of the else。Under this if statement。

 we're gonna just add one more line just to return directly out of this function。Here。

 I'm going just for the。sake of not having the same。Names right here。

 I'm going to change this to right value。This one， the right type。

I'm change this to be called var pointer。Underscore， lookup name。

We're gonna to get rid of the store instruction。We're going replace it with a new variable original value。

 orig value。Equals a builder call self dot builder to a load。

 And we're going to load that load that variables pointer。

 So we're going to load whatever values at that pointer。



![](img/69db6256f9dfb864a5ccc710bf040937_61.png)

If the is instance of the original value dot type is an int type。 So I R dot int type and。



![](img/69db6256f9dfb864a5ccc710bf040937_63.png)

The right type is also， or and it's a float type。So if they're mismatched。

Or to set org value equal to self dot builder dot S I T。O， FP。So it's。

 this is just a conversion to a integer to a float。We're going to pass in the original value。

And we're going to pass in a new float type。

![](img/69db6256f9dfb864a5ccc710bf040937_65.png)

We're going to pass it。 also do another if call， if is instance。Worriig value。

We're going to actually help copy this and paste it here。



![](img/69db6256f9dfb864a5ccc710bf040937_67.png)

So a rig value dot type is a float。And the new value is an int。We want to use the same function。

 except we want to convert the right value to a float。



![](img/69db6256f9dfb864a5ccc710bf040937_69.png)

Now we'll enter down a little farther。We're going to set a value。Variable equal to 9。

 We're going set a type variable equal to 9。

![](img/69db6256f9dfb864a5ccc710bf040937_71.png)

We're going to create a new match statement based on what operator we have。



![](img/69db6256f9dfb864a5ccc710bf040937_73.png)

I'm going to write two of these， and then I'm gonna to paste the rest'cause they're pretty。

Almost exactly the same。For add our case statement for our equal sign。

That just means value equals right value。 That's it。If we have our plus equals operator。

We want to have an if statement， if is instance。

![](img/69db6256f9dfb864a5ccc710bf040937_75.png)

The original value。Type that type。Is an int type。 So I are an int type and。Is instance again。

The right type isn't in type， as well。We want to set the value equal to a builder。Sefttop builder。

Add instruction or the original value。Is getting added against the right value。



![](img/69db6256f9dfb864a5ccc710bf040937_77.png)

Else， if it's not， they're not integers， we want to use the floating point。

 So value equals self dot builder。Not F add for floats。The original value and the right value。Now。

 for the rest of these， I'll paste these in。

![](img/69db6256f9dfb864a5ccc710bf040937_79.png)

Go over them。So we have minus equals， which is using the sub and F sub functions。



![](img/69db6256f9dfb864a5ccc710bf040937_81.png)

Multiply equals mo and F mo。

![](img/69db6256f9dfb864a5ccc710bf040937_83.png)

Divide equals S and F。 And then I added a default case just to say it's unsupported。As well。

Temporary error。 Cat right here。

![](img/69db6256f9dfb864a5ccc710bf040937_85.png)

Now that we're done with that， we can get on the outside of this match statement。



![](img/69db6256f9dfb864a5ccc710bf040937_87.png)

We're going to make a variable pointer。A second one for underscore equals self dot environment dot look up。

We're going to look up the name。And then， we're going to store。So self do builder。 store。

 we're going to store the value to that pointer。And that should be everything we need to do for assigned statements。

 Now， we can pull up this test dot lime， run Python main dot pi。



![](img/69db6256f9dfb864a5ccc710bf040937_89.png)

![](img/69db6256f9dfb864a5ccc710bf040937_90.png)

And we see here。That everything is starting to print， as we want it to。



![](img/69db6256f9dfb864a5ccc710bf040937_92.png)

So。That's how you add。The assignment operators， we have our negative right here。And we have。Our。

Prefix operator right here。 And we can see that's working from not false。

 So be true is printing out to the console。thank you for watching。 And next episode。

Willll be on post fix operators， so。Mostly useful right here in a four loops。

 you'll be able to add plus plus minus minus， or you can add your own after that。

So that'll be the topic of next。 Thank you for watching， and I'll see you in 15。



![](img/69db6256f9dfb864a5ccc710bf040937_94.png)