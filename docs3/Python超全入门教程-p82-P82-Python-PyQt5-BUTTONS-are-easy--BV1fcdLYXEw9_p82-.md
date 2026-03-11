# Python超全入门教程-p82-P82-Python-PyQt5-BUTTONS-are-easy--BV1fcdLYXEw9_p82-

Today， I'm going to show you how we can create push button widgets in Pi Q T 5 to begin。

 we will need the following imports。 Q， push button。



![](img/b2915c83b39b7a7a9f25533af61ae851_1.png)

As well as cube label for this demonstration。During the previous topic on layout managers。

 within our constructor for our main window， we defined a method of initialize UI for user interface。

 Let's be sure that we're calling that method within our constructor Within this method is where we'll be handling managing the user interface。

To create a button， we will call the push button constructor。Normally when creating widgets。

 we would want to prefix that widget with， then follow the name of the widget。 for example， button。

However， I'm going to demonstrate what happens when we don't do that， because without self。

 we're declaring a local variable。 We'll get back to that in just a moment。

 Let's create a local button object by calling the Q push button constructor。

We can pass in some text， such as click me。We will add this to our window。

 self self refers to our window object。Let's set the geometry of the button button dot set geometry。

We could use a layout manager， but I do want to keep this lesson as simple as possible。

 So let's pick some coordinates。 I've picked the following。

For the X and Y coordinates 150 and 200 for the width 200 and the height 100。



![](img/b2915c83b39b7a7a9f25533af61ae851_3.png)

Here is our button currently。 The font is a little small， so I'm going to set the style sheet。



![](img/b2915c83b39b7a7a9f25533af61ae851_5.png)

Set style sheet。I'll just increase the font size。 We could use Q font。

 but that might be overkill for this demonstration。Let's just say the font size will be 30 pixels。

Now we can read it。So we have our button。We're going to be connecting our button to a function。

 but we need to define that function。 We'll do so within our main window class。

So we will define a function of on click。There are no parameters beside self。

When we click on the button， what would we like to do？Let's print a test message。 Let's say， button。



![](img/b2915c83b39b7a7a9f25533af61ae851_7.png)

Clicked， and that's it。When we click this button， nothing happens。

We have to set up a signal and slot for the button。 Here's how。



![](img/b2915c83b39b7a7a9f25533af61ae851_9.png)

We will take our button。Dot list a signal。 A signal is emitted when a widget is interacted with。

 We have to list the type of signal。 So the signal we're looking for is clicked。

When we click this button， we will perform a slot in action。 We will take the signal of clicked。

 Connect it to a slot。 Connect is a method。The slot will be self dot。

 the name of the method on click。

![](img/b2915c83b39b7a7a9f25533af61ae851_11.png)

When we press this button， we perform this slot， this method of on click。

Each time I press the button。

![](img/b2915c83b39b7a7a9f25533af61ae851_13.png)

We perform that action。Not only should we print a message for this demonstration。

 let's set the text of the button。So we have button， Dart， set， text。😡，Let's change the text to。

Click。So this actually isn't going to work because we're not prefixing self。

Let me demonstrate what happens。We print button clicked， but then we have a problem。

 We have an exit code。 Our program was interrupted。

Button is considered local to our initializer method。

Our oncl function doesn't recognize what our button is。

That's why we're going to prefix our button with self。

So it belongs to the class of main window and not this method。

 Any instance of button we're going to prefix with self。



![](img/b2915c83b39b7a7a9f25533af61ae851_15.png)

And now this should work。The text on my button is going to change when I click it。Click。😡。



![](img/b2915c83b39b7a7a9f25533af61ae851_17.png)

You don't have to do this。 But with my personal coding style。

 whenever I create a variable or an object within a class， Id like to do so within the constructor。

 Even pie charm is giving me a warning。

![](img/b2915c83b39b7a7a9f25533af61ae851_19.png)

![](img/b2915c83b39b7a7a9f25533af61ae851_20.png)

When we declare this button， I'm going to move it to the constructor。

And let me just rearrange everything。Self dot button equals a Q push button widget。

Within my initializer method， that's when I like to rearrange everything and style it。

We can also disable buttons when we click on them。To do that， we will take self dod button。

Called the as。Disabled method， then pass in true。

![](img/b2915c83b39b7a7a9f25533af61ae851_22.png)

When I click the button。

![](img/b2915c83b39b7a7a9f25533af61ae851_24.png)

It will be disabled。 I can no longer click on it。For the last part of this demonstration。

 when we click on our button。Let's change the text of a label。

Let's declare self dot label within our constructor equals a Q label。The text of the label will be。

 hello。We will add this label to self the window。 When we set up the user interface。

 let's set the geometry of the label。Self dot label。Dot set。Geometry。

We couldn't use a layout manager， but just to keep things simple， I'm going to set some coordinates。

1，50 for x 300 for y。 The width will be 200， and the height 100。



![](img/b2915c83b39b7a7a9f25533af61ae851_26.png)

Let's change the font size。

![](img/b2915c83b39b7a7a9f25533af61ae851_28.png)

Self dot label。Dot set， style sheet。I will set the font size to be 30。



![](img/b2915c83b39b7a7a9f25533af61ae851_30.png)

Maybe 50。

![](img/b2915c83b39b7a7a9f25533af61ae851_32.png)

Better。All right， within our on click function。Let's instead take self dot label。

 dot set text method。Then pass in some new text to display。We're saying hello。

But when we click the button， let's say goodbye。

![](img/b2915c83b39b7a7a9f25533af61ae851_34.png)

So now， when I click the button， we will change the text on a separate widget。 My label。

 which now says goodbye。

![](img/b2915c83b39b7a7a9f25533af61ae851_36.png)

So with buttons， you need a signal that's connected to a slot。 The signal is an event。

 The slot is an action that this widget is going to take when this signal occurs。And well， everybody。

 that is an introduction to Push buttons in Pi QT5。



![](img/b2915c83b39b7a7a9f25533af61ae851_38.png)