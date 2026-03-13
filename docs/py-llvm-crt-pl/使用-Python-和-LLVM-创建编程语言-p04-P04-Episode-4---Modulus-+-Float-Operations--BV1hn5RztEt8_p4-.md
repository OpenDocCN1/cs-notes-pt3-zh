# 使用-Python-和-LLVM-创建编程语言-p04-P04-Episode-4---Modulus-+-Float-Operations--BV1hn5RztEt8_p4-

![](img/559ac134b563798179047329d0da9ff6_0.png)

All right， We'll come back to the program language series where we're gonna build a statically typed and Jit compiled language all using Python and LLVM light。

 Last time we set up the compiler for most of the operations that we needed。

 but we do need to come back in really quickly get the。Modulus operations up and running。

 And we need to add all of our float operations as well。

 So this will be kind of a short bridging video into the next section of the series where we're going to start implementing。

More of our language features。 So we can get on with this and get into our compiler class。



![](img/559ac134b563798179047329d0da9ff6_2.png)

We're gonna pretty much stay in the visit in fix expression method for right now。



![](img/559ac134b563798179047329d0da9ff6_4.png)

![](img/559ac134b563798179047329d0da9ff6_5.png)

We need to add another case。

![](img/559ac134b563798179047329d0da9ff6_7.png)

Right here for the modulus operator， which is our percent sign。



![](img/559ac134b563798179047329d0da9ff6_9.png)

And we'll set a value equals self dot builder。Dot S Re， So like sine integer remainder， pretty much。



![](img/559ac134b563798179047329d0da9ff6_11.png)

![](img/559ac134b563798179047329d0da9ff6_12.png)

We'll set that with our left value， and our right value。Now。

 we'll go ahead and add exponent the exponent case here， but we'll put slap it to do here。



![](img/559ac134b563798179047329d0da9ff6_14.png)

There's just a couple issues I'm having off camera。

 getting this to actually work in the way I'm intending it to。

 So this will come back at a little bit later of a date。 Now， we need to handle the floats。

 So we're gonna add another。

![](img/559ac134b563798179047329d0da9ff6_16.png)

![](img/559ac134b563798179047329d0da9ff6_17.png)

If statement on to this， So L of in instance。llDo the right type。



![](img/559ac134b563798179047329d0da9ff6_19.png)

And'll meet I R dot float type。 If the right type is an IR float type and。



![](img/559ac134b563798179047329d0da9ff6_21.png)

The left type is a float type。

![](img/559ac134b563798179047329d0da9ff6_23.png)

We want to set our type variable。

![](img/559ac134b563798179047329d0da9ff6_25.png)

To iron upload type。We will not make a new match。And what can we can go ahead and let's do match on the operator。

Case will do the plus sign first。

![](img/559ac134b563798179047329d0da9ff6_27.png)

Value equals self top builder dot。 So since we're adding floats now， instead of the add function。

 we'll use the F add function。

![](img/559ac134b563798179047329d0da9ff6_29.png)

![](img/559ac134b563798179047329d0da9ff6_30.png)

Lets to the left value， adding it to the right value。



![](img/559ac134b563798179047329d0da9ff6_32.png)

Make our new case with the minus sign。I can self top builder， F sub。Left value。 right value。

And we'll add another case， multiply。

![](img/559ac134b563798179047329d0da9ff6_34.png)

Into a value equals self dot builder dot。F multiply。



![](img/559ac134b563798179047329d0da9ff6_36.png)

What value。And right value。

![](img/559ac134b563798179047329d0da9ff6_38.png)

Next one will be our division。

![](img/559ac134b563798179047329d0da9ff6_40.png)

Value equals self dot builder dot F div。

![](img/559ac134b563798179047329d0da9ff6_42.png)

Left value。 and our right value。

![](img/559ac134b563798179047329d0da9ff6_44.png)

Next case will be our modulus operator。

![](img/559ac134b563798179047329d0da9ff6_46.png)

So value equals self dot builder， dot F Rem。

![](img/559ac134b563798179047329d0da9ff6_48.png)

Left value。 right value。Now， we'll go ahead and put R to do for the exponents。

 Hopefully in the next episode， I can have that。

![](img/559ac134b563798179047329d0da9ff6_50.png)

![](img/559ac134b563798179047329d0da9ff6_51.png)

As well。But that is it for the modulus operators in the。

Float operations so we can go ahead and go to our tests in our compiler test。



![](img/559ac134b563798179047329d0da9ff6_53.png)

![](img/559ac134b563798179047329d0da9ff6_54.png)

In our main dot pie file。We are setting this to compiler dot line。



![](img/559ac134b563798179047329d0da9ff6_56.png)

So5 times 5，5 plus 5， we know works。 So let's add float。 So 4。

20 for no apparent reason at all times 5。We can go ahead and Python main not pi that and check out our IR code。

So it looks like we're having a issue here with， oh，4。20 times 5。 So we do not have。

Floats time integers implemented yet。 So we need to make this a float as well。 So 5。1。

And then here we go。 So floats are a little weird。 It's got the hex add。Of these floats。

But we are multiplying floats together。 So that's great。嗯。Let's do a。Modulus operations。

 We'll do modulus on。Flos first。 So in our IR file， we'll go ahead and split this。 So in I R file。

 we have the F Ram。 So that's good。

![](img/559ac134b563798179047329d0da9ff6_58.png)

And then we'll do our integers now， just to make sure these works of 4 modulus 5。

S Ramm 4 integer 4 and 5。Okay。😊，So thank as for watching moving on to episode 5。

 we're going to get into the meat potatoes of our language。

 and we're going to start implementing more language features。

 I'm still not sure if I'm going to do functions or variables first。

 I think I'm going to do functions so we can get the printf out of the way。

 and we can execute our program and start to see all this multiplication and arithmetic operations working in action。

 So thank you for watching。 I will see guys in episode 5。



![](img/559ac134b563798179047329d0da9ff6_60.png)