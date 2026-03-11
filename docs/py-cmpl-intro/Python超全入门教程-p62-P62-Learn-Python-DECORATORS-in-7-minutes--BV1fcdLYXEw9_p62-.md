# Python超全入门教程-p62-P62-Learn-Python-DECORATORS-in-7-minutes--BV1fcdLYXEw9_p62-

What is going on， everybody。 So today， I got to talk about decorators in Python。

 A decorator is a function that extends the behavior of another function without modifying that base function。

 We pass the base function as an argument to the decorator function。 For example。

 Let's say we have a base function of get ice cream， and you can pass in a flavor of ice cream。 Well。

 some people might want sprinkles on their ice cream。 and others may not。

 They might just want plain vanilla， Well， we could add sprinkles by using a decorator We're extending the behavior of a function where we get ice cream where we're adding sprinkles。

 but we may not want to change the base function because some people don't like sprinkles。

 Think of decorators that way。 We're adding something to a base function without changing it。

 Here's how to create a decorator。 Let's start with the base function。

 We will create a function to get。😊，Ice cream， there will be no parameters for now。

All we're going to do is print the following message。Here is your ice cream。 and for fun。

 I'll add an emoji。 I'll add an ice cream emoji。

![](img/460272a5d085c620652be12f9c399d3e_1.png)

![](img/460272a5d085c620652be12f9c399d3e_2.png)

To call this function， all I got to do is call the get ice creamre function。Here is your ice cream。

Here's how to create a decorator。A decorator is a function。 will'll need to define it。

Define add sprinkles。Our decorator function is going to have one parameter。A function。

But we'll just rename it to funk for short。 We're going to pass a function to our decorator function。

Within our decorator function， we will define an inner function of wrapper。Currently。

 there's no parameters， we'll set that up later。Within this wrapper function。

 we will call the function that we receive this parameter。



![](img/460272a5d085c620652be12f9c399d3e_4.png)

Then we will return our wrapper function。Up until this point， we've been returning values。

 but now we're going to return an entire function。

![](img/460272a5d085c620652be12f9c399d3e_6.png)

Here's the basic form we like to create a decorator。To apply a decorator to a base function。

 preceding that function。You're going to add at the name of the decorator。



![](img/460272a5d085c620652be12f9c399d3e_8.png)

So add sprinkles is a decorator， the base function is get ice cream。



![](img/460272a5d085c620652be12f9c399d3e_10.png)

Within our decorator， how do we want to add sprinkles exactly， Currently。

 our decorator doesn't do anything。

![](img/460272a5d085c620652be12f9c399d3e_12.png)

Here's what happens。

![](img/460272a5d085c620652be12f9c399d3e_14.png)

We just print。 Here is your ice cream。 Let's say that before we're given our ice cream。

 we'll print a statement that we add sprinkles。

![](img/460272a5d085c620652be12f9c399d3e_16.png)

Within our decorator， imagine that we're replacing calling function。With this print statement。

Let's create another print statement where we add sprinkles before it。



![](img/460272a5d085c620652be12f9c399d3e_18.png)

I will print the following message。You add sprinkles， and I'll add an emoji。



![](img/460272a5d085c620652be12f9c399d3e_20.png)

How about Confetti？That could resemble sprinkles。

![](img/460272a5d085c620652be12f9c399d3e_22.png)

Okay， let's see what happens。You add sprinkles， Here is your ice cream。



![](img/460272a5d085c620652be12f9c399d3e_24.png)

We're decorating our base function of get ice cream with a decorator of add sprinkles。



![](img/460272a5d085c620652be12f9c399d3e_26.png)

![](img/460272a5d085c620652be12f9c399d3e_27.png)

We're not modifying the base function。 We're extending it。Now。

 we have a nested function of wrapper within our decorator。 It is necessary to have this。 Here's why。

 So I'm not going to call the get ice cream function quite yet。So nothing should happen。

If I was to remove this wrapper。

![](img/460272a5d085c620652be12f9c399d3e_29.png)

Well， we'll end up calling this function as soon as we apply the decorator。

We're not even calling the get ice cream function at all。

 We only want to execute this code when we want ice cream， not whenever we apply the decorator。



![](img/460272a5d085c620652be12f9c399d3e_31.png)

![](img/460272a5d085c620652be12f9c399d3e_32.png)

![](img/460272a5d085c620652be12f9c399d3e_33.png)

That's why we need that wrapper function。We'll get ice cream and add sprinkles only when we call that function。



![](img/460272a5d085c620652be12f9c399d3e_35.png)

Then at any point in my program， if I call the get ice cream function。



![](img/460272a5d085c620652be12f9c399d3e_37.png)

Then we get ice cream with sprinkles。Let's apply more than one decorator。

We'll create a decorator to add fudge。Define， add fudge。We have one parameter， a function。

 which we will rename as funk。We need an inner wrapper function。

This is so that we don't call this function when we apply a decorator。



![](img/460272a5d085c620652be12f9c399d3e_39.png)

I will print。You add fudge。Close enough， we'll add a bar of chocolate。

Then call the base function that we receive。Then we need to return the wrapper function。All right。

 given our base function， we can apply more than one decorator。Let's say that。

 after adding sprinkles。

![](img/460272a5d085c620652be12f9c399d3e_41.png)

We will apply the decorator where we add fudge。

![](img/460272a5d085c620652be12f9c399d3e_43.png)

So， now。We have the following output。You add sprinkles， you add fudge， here is your ice cream。



![](img/460272a5d085c620652be12f9c399d3e_45.png)

So with decorators， you can apply more than one decorator to a base function。



![](img/460272a5d085c620652be12f9c399d3e_47.png)

What if your base function accepts arguments， For example， when we get our ice cream。

 we need to pass in a flavor like vanilla。

![](img/460272a5d085c620652be12f9c399d3e_49.png)

I will set up one parameter of flavor。I will convert our print statement to be enough string。

Here is your at a placeholder。Flavor of ice cream。Let's run this and see what happens。



![](img/460272a5d085c620652be12f9c399d3e_51.png)

All right。 We have a type error。

![](img/460272a5d085c620652be12f9c399d3e_53.png)

Our wrapper function isn't set up to accept arguments。

What you'll see within Raper functions is that they'll have parameters of args。



![](img/460272a5d085c620652be12f9c399d3e_55.png)

And quarks to accept any number of arguments and keyword arguments。



![](img/460272a5d085c620652be12f9c399d3e_57.png)

Then when you call your base function。In this case， get ice cream。



![](img/460272a5d085c620652be12f9c399d3e_59.png)

We will also set this up to accept any number of arguments and keyword arguments。



![](img/460272a5d085c620652be12f9c399d3e_61.png)

Let's do that within our ad fudge decorator， too。Our wrapper function will accept any number of arguments and keyword arguments。



![](img/460272a5d085c620652be12f9c399d3e_63.png)

Same thing goes with the base function。

![](img/460272a5d085c620652be12f9c399d3e_65.png)

And now this should work。You add sprinkles， you add fudge， here is your vanilla ice cream。



![](img/460272a5d085c620652be12f9c399d3e_67.png)

Or any other flavor of your choosing。

![](img/460272a5d085c620652be12f9c399d3e_69.png)

Like chocolate。You add sprinkles， you add fudge， here is your chocolate ice cream。



![](img/460272a5d085c620652be12f9c399d3e_71.png)

All right everybody。 so those are decorators。

![](img/460272a5d085c620652be12f9c399d3e_73.png)

Theyre a function that extends the behavior of a base function。 In this case， get ice cream。

 Decators extend a function without modifying it。 If you would like to apply a decorator to a function。

 you precede that function when you define it with at the name of the decorator。

And you can apply more than one。

![](img/460272a5d085c620652be12f9c399d3e_75.png)

And well， everybody， that is an introduction to decorators in Python。



![](img/460272a5d085c620652be12f9c399d3e_77.png)