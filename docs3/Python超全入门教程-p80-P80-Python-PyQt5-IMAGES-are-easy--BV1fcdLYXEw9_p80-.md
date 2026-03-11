# Python超全入门教程-p80-P80-Python-PyQt5-IMAGES-are-easy--BV1fcdLYXEw9_p80-

What is going on， everybody。 In today's video， I'm going to show you how we can add images to Pi Q T 5。

 You will need an image to work with。 me。 I'll be using my profile picture for my YouTube channel。

 Feel free to take a moment to find a picture of your own may be a profile picture of yourself。

 We will need the following imports。 Q label。 The most common and straightforward approach to displaying an image is to add an image to a label in order to display it。

 Then we will need this other import。😊。

![](img/f0597931941f80aaa4093f39764426b1_1.png)

![](img/f0597931941f80aaa4093f39764426b1_2.png)

![](img/f0597931941f80aaa4093f39764426b1_3.png)

From。Pi Q T 5。 That's the package。 Then the module of Q T G U Y import the class of Q Ps map。

 The class of Q Ps map。 It's used for handling images and provides functionality for loading。

 manipulating and displaying images。 We will load our image to a Q Ps map object。

 Then add this Q Ps map object to a label in order to display it。

Within our constructor of our main window。We will create a label。

Label equals called the Q label Conor。Then， pass in self。Self refers to the window object。

 Our window will be the parent widget。 Our label widget is one of its children。

 Once we have our label， we'll set the geometry of the label。Label dot set geometry method。

 We have to pass in X and Y coordinates。As well as a width and height of the label。

For the coordinates， let's say 0 for each。 The label will appear in the top left corner。

For the width，250 is good。And the height， 250 as well。



![](img/f0597931941f80aaa4093f39764426b1_5.png)

Here's my window。 The label is going to appear in the top left corner。 However。

 there's nothing added to the label。

![](img/f0597931941f80aaa4093f39764426b1_7.png)

That's where the widget of Q Ps map comes in。We will create a Pix map object equals called the constructor of Q Pixmap。

We have to pass in a string that represents a relative file path or an absolute file path to our image。

 My image is right next to my main Python file。 I just need the file name。

 The name of my image is profile underscore P。 and this is a Jpeg。



![](img/f0597931941f80aaa4093f39764426b1_9.png)

![](img/f0597931941f80aaa4093f39764426b1_10.png)

![](img/f0597931941f80aaa4093f39764426b1_11.png)

When I run this， we don't see our image。

![](img/f0597931941f80aaa4093f39764426b1_13.png)

We have to add the Pix map object to the label。 We have to set it。 Here's how。Take our label。

Use the Ac Pixmap method。And pass in our Pix mapap object。



![](img/f0597931941f80aaa4093f39764426b1_15.png)

And now we can see the image。However， the image doesn't scale according to the size of the label。



![](img/f0597931941f80aaa4093f39764426b1_17.png)

To enable that， we have to call the following method。Take our label called the set Scd。

Contents method， then pass in true。Our image will now scale to the size of the label。

If we were to change the size of the label， let's say it's 100 pixels。

It will scale down even further。Or I could even increase it to 500。



![](img/f0597931941f80aaa4093f39764426b1_19.png)

So now the image takes up the entire width and height of the window。



![](img/f0597931941f80aaa4093f39764426b1_21.png)

Let's set that back to 250。

![](img/f0597931941f80aaa4093f39764426b1_23.png)

There's a few tricks that we can do with positioning of the image。We've set our label with an image。

 We can move the label within the confines of the window。



![](img/f0597931941f80aaa4093f39764426b1_25.png)

Currently， it's set in the top left corner。But here's a few tricks that we can do with positioning。

With our label。We will set the geometry again。So the top left corner is0，0 for the coordinates。

We could pass in 250 and 250 again for the width and the height。But if we were to change that here。

When we initially createate this label。We would have to manually change that here as well。

I think it would be better if we were to get the current width and height of the label。

 Take our label， called the width method to get the width。Same thing applies with the height。



![](img/f0597931941f80aaa4093f39764426b1_27.png)

Label， dot height method。And that should work fine。

Let's say we would like to take our image and move it to the right side of our window。



![](img/f0597931941f80aaa4093f39764426b1_29.png)

Here's how。With the X coordinate。We're going to access self。That means our window。

Called the width method。

![](img/f0597931941f80aaa4093f39764426b1_31.png)

Here's what we have currently， we can't see the label。

It was placed outside of the confines of the window。



![](img/f0597931941f80aaa4093f39764426b1_33.png)

Let's subtract our labels width。Label dot width。I'll put each of these arguments on a new line just to help with readability。



![](img/f0597931941f80aaa4093f39764426b1_35.png)

So now our image is right justified within our window。



![](img/f0597931941f80aaa4093f39764426b1_37.png)

For the bottom right corner， we will take the second argument。Access self dot height。

That's the height of the window。 that we're instantiating。Minus our labels height。



![](img/f0597931941f80aaa4093f39764426b1_39.png)

And our image is in the bottom right corner。

![](img/f0597931941f80aaa4093f39764426b1_41.png)

For the bottom left corner， we will set x to be0。Now here's the tricky part。

To have our image placed in the center of our window。

We will take the width of the window minus the width of the label divided by two for integer division。

 we'll be using double forward slashes。We need our pixels to be whole integers。

 So we're going to be using integer division and not standard division。

We will round to the nearest whole pixel。Then we will do this with the height， as well。

And now our image should be in the middle of our window。Al right， everybody。

 And that is how to add an image to your Pi Q T5 application。



![](img/f0597931941f80aaa4093f39764426b1_43.png)