# Python超全入门教程-p33-P33-Python-default-arguments-are-awesome--BV1fcdLYXEw9_p33-

yEvery， today， I'm going to explain default arguments。

 Deult arguments are a default value for certain parameters。

 The default is used when that argument is omitted when you invoke a function。 In the last topic。

 we discussed positional arguments。 today， we will be examining default arguments。

 Then in future topics， we' examine keyword and arbitrary arguments。 Let's begin。

 Let's define a function to calculate net price。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_1.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_2.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_3.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_4.png)

There will be three parameters， an original list price。A discount， if there is one。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_6.png)

And sales tax。We will return a net price， and heres the formula。List price times。

1 minus our discount percentage。Times。One plus our sales tax。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_8.png)

Maybe I'm buying a PlayStation 5 for $500。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_10.png)

I will pass in 500 for the list price。 Well， I can't actually execute this function without also passing in an argument for discount and tax。

 Perhaps the discount is 0， and the sales tax is 5 per cent，0。05。 Well， this would work。

 And I should probably put this within a print statement。 so you can see it。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_12.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_13.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_14.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_15.png)

There we are。 My total is $525。 The list price of $500， No discount and 5 per cent sales tax。 Now。

 suppose that maybe 90% of the time when we're executing this function， most of the time。

 discount is 0。 and our sales tax is almost always the same。

 What we could do to make this function a little more flexible is to set these two parameters to have a default value in place of sending in three arguments。

 we can pass in one， then set our discount and our tax to have a default value。

 So I will set discount to be 0。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_17.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_18.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_19.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_20.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_21.png)

And tax to be 0。05， meaning 5%。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_23.png)

So this function would work。 Our total is 525。 And that's assuming that our discount is 0 and our tax is 5 per。

 The nice thing about using default arguments is that let's say that somebody has a discount。

 Well this function would also accept up to two additional arguments。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_25.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_26.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_27.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_28.png)

So， let's print。Our net price。500， and our customer has a coupon for 10% off。

 I'll add a second argument of 0。1。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_30.png)

If we're passing in an argument for our discount， we'll use whatever is passed in rather than the default。

 Our total now is $47250， or maybe this time。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_32.png)

They are not paying sales tax。 I will set the sales tax to be 0。Now， the customer's total is $450。

 So that's kind of the nice thing about default arguments。 It makes your functions more flexible。

 and it can reduce the number of arguments， especially if the arguments that you're passing in tend to be consistent。

 Most of the time， people don't have a discount。 and almost everybody is paying 5% cent sales tax。

 Why pass an arguments if we don't have to。 Let's cover an exercise。 We'll create a count up timer。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_34.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_35.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_36.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_37.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_38.png)

We will import the time module。 We will define this function。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_40.png)

Define count。There will be two arguments。Start and end。For x and range。Start。Coma， and。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_42.png)

Within the range function， the second argument is exclusive。

 so I'm going to add one to the end of our time。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_44.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_45.png)

Then， I will print。X， to make this thread that's running the program sleep。

 you can access the time modules sleep method， Pass in one for one second。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_47.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_48.png)

Then outside of the for loop， let's print the word dumb。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_50.png)

To invoke this function， I need to pass in two arguments。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_52.png)

A start time and an end time。 I'll set the start time to be 0， the end time to be 10，10 seconds。

So we start at zero， then we will increment by one every second。I'll speed up the video。

 I think you get the idea， but we'll stop at 10。Let's assume that most of the time a user would like to begin at 0。

 Well， we don't necessarily need to pass that in as an argument。

 Let's set our start parameter to have a default value of 0。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_54.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_55.png)

We only need to pass in one argument， but we do have a problem。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_57.png)

Nonde arguments should follow default arguments。 So if you use any default arguments。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_59.png)

You'll want to be sure that there are after any positional arguments。 so let's reverse these。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_61.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_62.png)

And that should work。So now when I run this program， it's assuming we'd like to start at zero。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_64.png)

But we'll need to pass in an ending amount of seconds。 When do we want to stop。That works the same。

 But now we do have the option of starting at a different number。 This time， let's end at 30。

But we will begin at 15。We're beginning at 15。 Then we will count to 30。I'll speed up the video。



![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_66.png)

There we are。 Are't everybody So in conclusion。 defaultult arguments。

 They are default values for certain parameters。 The default value is used when an argument is omitted。

 They can make your functions more flexible and reduce the number of arguments you have to pass in。

 especially if those arguments are consistent most of the time。 So those are default arguments。

 And in the next topic， we will discuss keyword arguments。 And， well， yeah。

 those are default arguments in Python。

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_68.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_69.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_70.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_71.png)

![](img/4c1bb0f301ca3e307a1ee0fc96b39fd0_72.png)