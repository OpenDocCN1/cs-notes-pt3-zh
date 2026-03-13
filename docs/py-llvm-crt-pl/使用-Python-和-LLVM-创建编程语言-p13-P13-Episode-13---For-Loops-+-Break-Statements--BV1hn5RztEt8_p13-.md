# 使用-Python-和-LLVM-创建编程语言-p13-P13-Episode-13---For-Loops-+-Break-Statements--BV1hn5RztEt8_p13-

4 loops and are continue and break statements。 and these statements will work in while loops as well or just any loop in general。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_1.png)

um。We're going to start off with our test dot line file which I just have a main function in here set up。

 We have a variable set to 0。 That'll be a。We're going to be implementing a very basic and generic for loop。

 so。I equals 0。 The condition I is less than， while I is less than 10。

 and then every iteration will add  one to I。If it's 5。

 we're going to break early and it's not going to print 5。

 It will just break out of this for loop entirely and go to our return statement。

If it's neither of those， we're going to print I， and then we're going to set A to I for funies。

 just。To have something else down here to return。That's basically all。

 this is our goal for the episode， and。Pretty self explanatory。 And let's go。So first thing。

 like always token dot Pi， we're going to be adding in two new or three new token types。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_3.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_4.png)

For our new keywords， we have continue es continue。Break equals break。And4 equals 4。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_6.png)

Now， down in our regular keywords。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_8.png)

We're going to add three new keywords。Like do we just added the types for。

 So our break is gonna be mapped to break。 continue， continue，4，4。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_10.png)

Now， in our gen Z safe keywords， I have three， just for fun。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_12.png)

We have yeat for breaking。 So we want to y out of that loop。 We have another one for continue。

 So we just want to go to another iteration。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_14.png)

And then we're going to dab for the four loopcause why that。

 That's all we need to do for our token dot pis。 So we'll control S。 save that。

 We'll go into our A S T。 Now， we can skip the Leer， A S T dot pi。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_16.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_17.png)

We're gonna first start with our node types。 We're going to add three more statement node types。

 one for the break statement， one for continuous statement and one for four statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_19.png)

And then we'll go down to the bottom of our statements。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_21.png)

Section or region。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_23.png)

And I'm going to start with the brake statement。 So I'll paste that in for the sake of time。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_25.png)

Break statement going to take in nothing， do nothing other than return that this is a break statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_27.png)

Same thing for the continuous statement。 you can pretty much copy paste and change this to say。

 continue continue statement here。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_29.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_30.png)

any statement not going have anything special we need to do with。 We just need to know， hey。

 there is a continued statement here。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_32.png)

Then finally， slightly more involved node will be our four node，4 statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_34.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_35.png)

It's going to take in a variable declaration。 So I'll get our test out line file down here at the bottom。

 for take a look at。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_37.png)

So we have our four sees our variable Dec variable declaration， which is just a let statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_39.png)

We have our condition， which is an expression。 So I less than 10 is our condition expression。

Then we have an action。 So what we want to do every single iteration of the loop。Right now。

 I have this set to an assigned statement， will。Make this more generic into an expression later in the series。

 But right now， we're expecting an assigned statement right here to。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_41.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_42.png)

Asign I to something， every iteration。Then， of course， we have our loop body。

 which is our block statement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_44.png)

And will set all those variables up。Then normal type function and Json function。

 And we'll just set every variable as a key value pair in our dictionary。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_46.png)

We'll save our AST do Pi and we'll move on into our parser。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_48.png)

First thing we'll do is import our three statements。 So break。Continue。

And four statements will import those。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_50.png)

We need to go down to our parse statement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_52.png)

Method。Down here below par program。 I have it in our match case。

 We need to add three more cases for the sake of time。 I will paste these in。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_54.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_55.png)

So we have our break。 So It's going to go to a parse break statement。 continue， parse continue，4。

 parse 4。First thing that we will。Iplement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_57.png)

Or we'll define all these functions first。 So we'll start with our break statement。

 We'll go down to the bottom of our statement methods region。Deaf， parse break statement， self。

We'll take in a break statement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_59.png)

All we're going to do is advance the parser past that brake keyword。

 and then return a brake statement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_61.png)

Noode。😔。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_63.png)

Our continuous statement is exactly the same， except we returning continuous statement notes。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_65.png)

And then below that， we'll start with our parse。4 statement。Take in self。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_67.png)

4our statement is the return type。We'll go ahead and set up our for statement node here。

 So we'll initialize a new object。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_69.png)

First thing， once we hit this four keyword， the next token that we're expecting is a left parentheses。

 so。If not， self dot expect peak。Token type dot left paren。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_71.png)

We're going to return none。Next thing we're expecting is our let token。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_73.png)

So if not， self dot underscore， expect peak。Token type dot left forin。Turn none。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_75.png)

Now， the reason we're doing a or sorry， let。 reason we're doing an expect peak for the let is because that we know from our A T。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_77.png)

That we're expecting a let statement。 So we want to verify that that we're going to actually have a let statement to parse。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_79.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_80.png)

So once we have that verified， we can set the state the four statements of our declaration property。

E could the self dot or Sish floor parse let statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_82.png)

So that's going to parse this whole statement right here。Before the semicolon， of course。Now。

 we need to skip。The semicolon， so。Skip semilon。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_84.png)

So now we're here on this eye。Now， we're expecting a condition。So statement that condition。

And that condition is always going to be a expression。 So we'll use our parse expression function。

With the lowest。Precience type。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_86.png)

After this expression， we're going to be expecting a semicolon here， so。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_88.png)

I'll paste this in。For the sake of time。We can also might as well go up here and expect it as well up here。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_90.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_91.png)

So。Expect token type semicolon after the let statement。

 expected again after the expression for our condition。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_93.png)

And now we are expecting an assignment statement。 So statement dot action。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_95.png)

Is self dot parse assignment statement。Now， after this assignment statement is done。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_97.png)

We're going to be expecting。 We may have to come back to this。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_99.png)

But we're going to be expecting a left brace。 So I'm going to put this here。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_101.png)

I take this with a grain of salt。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_103.png)

'cause I'm not sure where this parenthesesis is gonna be consumed at， so。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_105.png)

Just right now， we'll put this here。 We may come back to it。

But after we've verify that there is a left brace， we're going do statement dot。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_107.png)

IfI can type statement dot body is we're expecting a block statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_109.png)

So we're in to parsel block statement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_111.png)

And then we have our for loop fully parsed。 So we'll return back that for statement， we。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_113.png)

Have been building out in this whole function。 not all three of those functions are implemented。

 The last thing we have to do is implement the compiler for it。 So in our imports， we'll import。

 break， continue。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_115.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_116.png)

And4。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_118.png)

We are going to go down to in our in function of the compiler underneath initialized builtins。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_120.png)

We need to keep references of where our break points and continues are for during the codes。

 we know when to。Break out in some of our functions。 So self dot break points。

It's going to be a list of blocks。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_122.png)

IR blocks。And then we'll have a self dot continues is another list to my our blocks。

We'll set those empty lists to start。 Ill put a little comment here， just for。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_124.png)

Fun sake。Now we can scroll down to our compile method in our match case， in our statements section。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_126.png)

We can add our three cases， our break continue in4， in the visit functions for each。 We can go ahead。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_128.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_129.png)

Type those out or call those right now before we implement them。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_131.png)

Now， we'll go to the bottom of our visit methods statements underneath the wild statement we did last episode。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_133.png)

And I'll go ahead and paste in our break statement， and our continue。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_135.png)

So we take in nodes， but we don't really use them。 And all we're doing is branching。

To this specific block， that was the last added break point。

That's all we're doing is branching to that block on both of these。 So for continues break points。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_137.png)

For our four statement， we'll do de on our score score， visit4 statement。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_139.png)

Self， and then we'll take in that force statement node。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_141.png)

Since this one's going to be a lot more involved。We'll go ahead and declare out some variables to break up our node class。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_143.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_144.png)

For decoration， condition， action and body。We need to create a new environment。

 specifically for this for statement。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_146.png)

So we'll add， we're going to save the current environment we're in to a variable。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_148.png)

And then we're going to create a new environment。Or the parent is that previous one。

 We're going to create a child environment for those four statement block。Specifically。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_150.png)

And then we're going to first compile the let statement of our decoration。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_152.png)

We need to create two blocks for this for statement。

 one's going to be the entry into the for statement and one's going to be otherwise。

 So when that condition up here resolves to false， it will go to the otherwise。

 And if it's still true， itll loop back to the entry block and run the code again。So， for。

Loop intrigue。Almost exactly the same as our while loop self without builder dot dependendned basic block。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_154.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_155.png)

We'll do a format string in here， for loop entry underscore。We'll use our increment counter function。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_157.png)

And now， for our for loop， otherwise。Do the same thing。 Self do builder， pen based block。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_159.png)

F string for loop， otherwise underscore， and we'll do our counter。

Variable since we incremented it in the first one。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_161.png)

Now we need to keep track of our break points in our continuous block。

 So if we happen to use a breaker continue。The code can。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_163.png)

Or our visit statements up here can then get that block since it's going to be the last one that we added。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_165.png)

And then branch to that block。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_167.png)

So self dot breakpoint， dot append。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_169.png)

For loop， otherwise， so if。We do hit a break point。

 We want to go to the otherwise block becauseuse we're leaving the forlo。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_171.png)

For continuous self do can use append， we're going to put the entry block because if we use it continue。

 we want to go back to the start of the for loop。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_173.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_174.png)

And evaluate the condition。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_176.png)

Now， we'll branch off with the builder。 self dot builder dot branch。

 We'll branch to the entry block of the for loop。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_178.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_179.png)

We're gonna position at this have our builder positioned at the start of that entry block。

for loop entry。And now now that we're in the entry block， we're going to compile the body。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_181.png)

Then we're going to compile the action。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_183.png)

And then we're going to resolve or test the condition expression to see if it's true or false。

 So test underscore equals self dot。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_185.png)

Resolve value。We're going to pass in our condition expression。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_187.png)

Now， similar to the while loop， we're gonna do a self dot builder。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_189.png)

Dot C branch。 So condition branch。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_191.png)

The condition is test。 If it's true， we want to branch off and go back to the entry block。

 If it's false， we want to go to the otherwise。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_193.png)

Now， once the for loop is finished， we want to。Set our position。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_195.png)

Builders' position at the start of the otherwise block。And then， our for loop is。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_197.png)

Finally compiled so we can get rid of our break points。 So we'll go ahead and pop。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_199.png)

Our break points list and our continues list were just pop what we appended earlier。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_201.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_202.png)

Right here， and we'll just get rid of them。 So we'll take them off。

And then that should be everything for our。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_204.png)

4our loops， and continues and breaks。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_206.png)

So we'll go ahead and do our Python main dot pi。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_208.png)

Now， this is probably the issue that I was pointing out in the parser。 We may have to come。 Okay。

 so in the parser， I added some expect peaks。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_210.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_211.png)

Functions for semicoons。

![](img/dc94e1841bbf497ba6534dc3dc3b4751_213.png)

What we really need to do is make sure your parse 4 statement looks like this。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_215.png)

So we're expecting leftpre then expecting let， parsing the let statement。

 Then we're going to use the next toteken function to skip the semicolon。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_217.png)

![](img/dc94e1841bbf497ba6534dc3dc3b4751_218.png)

Part of the condition。Make sure that the next one is a semicolon。 Now。

 we're gonna skip the semicolon again with next token。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_220.png)

And then go into the assignment statement。And then we have one more issue here， with the continues。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_222.png)

I'm having a little trouble。 Something must have changed with my LVM light since I wrote this code。

 So for right now， I will come back later and implement the continue block。

So we'll go ahead and take that out。For now， we'll come back to that。

 I'll make sure to put on my discord。 if I find my solution。 or if you guys can blatantly see it。

 please let me know on my discord。The link will be in the description。But we should be able to。

Do Python dot main do pi。And here we are。So goes all the way print to four。

 and then it breaks out perfectly and the program still returns 4。So all right。

 So four loops and brake statements are implemented。

 The continuous statement is majority implemented。 There is a issue in the compiler for it。

 if I find a solution， I will post it in the Discord or make an updated video as well。

But thank you guys for watching。The next episode is going to be on prefix operators， so。

We're going have we're going be able to finally do negative numbers and。Be able to go， like not true。

Soth， thank you guys for watching。 and I will see you in episode 14。



![](img/dc94e1841bbf497ba6534dc3dc3b4751_224.png)