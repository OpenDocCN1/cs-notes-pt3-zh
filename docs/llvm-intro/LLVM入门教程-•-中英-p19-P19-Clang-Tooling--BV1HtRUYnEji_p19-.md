# LLVM入门教程-•-中英-p19-P19-Clang-Tooling--BV1HtRUYnEji_p19-

Hi， I'm John Qua， I'm an undergrad student at UFMG and I currently developing a project at the compiler's lab using the claim library In the previous video。

 I explained what an AST is and how claim uses it to represent your code。



![](img/4fb2a053d98aee2561a3567417a3601e_1.png)

![](img/4fb2a053d98aee2561a3567417a3601e_2.png)

![](img/4fb2a053d98aee2561a3567417a3601e_3.png)

I talk about the ASC in this video again， so if you don't know what it is。

 I suggest you watch the previous video on the series。Today。

 I will talk about some of the different ways we can use Kang as a library to build our tools。



![](img/4fb2a053d98aee2561a3567417a3601e_5.png)

There are multiple interfaces we can use to build our tools in the official claim documentation9 Ver 12。

 they described three ways to write our tools。Lip cling。Liip tooling and claim plugins。

Our focus in this course will be claimed plugins， but I'll try to give a brief overview of the others as well。

The goal of this overview is not to make you able to write tools in each of these interfaces。

 it's just so you can have an idea of when to use any one of them。



![](img/4fb2a053d98aee2561a3567417a3601e_7.png)

First of all， Liplain。Documentation describes it as a stable high level C interface to click。



![](img/4fb2a053d98aee2561a3567417a3601e_9.png)

What this means basically， is that you can expect a program you wrote in a previous version of the library to keep working in future versions。

This is in contrast to some of the other interfaces where changes from one version to the next can be quite drastic and force it to rewrite your tools in order for them to keep working。



![](img/4fb2a053d98aee2561a3567417a3601e_11.png)

Lipplain allows you to traverse the ASC using something they call cursors。According to the dos。

 they allow you to iterate through the AST without needing to learn the details of the claim AST。

 but on the downside， you don't get full control over it。



![](img/4fb2a053d98aee2561a3567417a3601e_13.png)

![](img/4fb2a053d98aee2561a3567417a3601e_14.png)

Liip Kang does not expose all of the information kept in the AST。

 The reasoning behind it is quite simple if we remember the goal of Li Kang。To be stable。

The less it exposes the AASD in its API， the less it's likely to be affected by changes made to Kang。

 So if you need to use the ASST more in depth， you might want to consider the other interfaces Kang provides。

Next we come to Liuneune Lipuneunes API allows you to take full control over the EST。

Lip tooling runs frontend actions over code。Front end actions act as the entry point to our tools。

 that is， that's where you write the code you want claim to run for you during compilation。



![](img/4fb2a053d98aee2561a3567417a3601e_16.png)

They are implemented as an abstract class and claim。

 which other classes implement such as AST Fronend action。

 which allows us to write actions that depend on traversing the claim AST。😊。



![](img/4fb2a053d98aee2561a3567417a3601e_18.png)

When we look into claim plugins， we'll see that he uses a kind of action called plugin AST action。

 which actually implements AST frontend action。

![](img/4fb2a053d98aee2561a3567417a3601e_20.png)

That being said， lip toollling is not as stable as lip playing。Finally。

 we come to the main topic of this course， claim plugins。



![](img/4fb2a053d98aee2561a3567417a3601e_22.png)

As I have mentioned before， claim plugins run plugin AST actions over code。

 This means that claim plugins are actually a kind of tool you can build using Li tool。



![](img/4fb2a053d98aee2561a3567417a3601e_24.png)

We've also seen that plugin AST action implements anotherclass called ASC frontend action。

 which in turn implements front end action。😊。

![](img/4fb2a053d98aee2561a3567417a3601e_26.png)

![](img/4fb2a053d98aee2561a3567417a3601e_27.png)

And then in the next video， we will finally implement our first claim plugin。

 and then we'll see exactly how to implement these classes。😊。



![](img/4fb2a053d98aee2561a3567417a3601e_29.png)

For now， what's important is to know that when we write claim plugins。

 we are writing programs that run plug AST actions over code。

 What this means is that claim will read your code， parse it into an AST。

 and then give this AST to your plugin AST action class。



![](img/4fb2a053d98aee2561a3567417a3601e_31.png)

![](img/4fb2a053d98aee2561a3567417a3601e_32.png)

Clean plugins being part of lip tool also give you full control over the clean ASC。



![](img/4fb2a053d98aee2561a3567417a3601e_34.png)

There's another neat little thing in claim， which is the ability to register your plugin。

Don't worry about the details， as this will be covered in the next video as well。

 but basically what this does is allow you to compile your plug into a shared library and then make claim run it just by passing an argument at a command line。

 something like this。Again， we'll see what each piece of this line does in detail in the next video。

 but basically this line calls claim and asks it to run the plugin you registered as your plugin over the program in the file example that see。



![](img/4fb2a053d98aee2561a3567417a3601e_36.png)

![](img/4fb2a053d98aee2561a3567417a3601e_37.png)

That plugin dot S， O file is the so called shared library where your plugin has been compiled。



![](img/4fb2a053d98aee2561a3567417a3601e_39.png)

Finally， claim plugins are also not as stable as the claim。



![](img/4fb2a053d98aee2561a3567417a3601e_41.png)

So to summarize what we've seen today， Leplan is a very stable library that allows you to build some interesting tools that do not depend on having every detail of the ET available。

😊。

![](img/4fb2a053d98aee2561a3567417a3601e_43.png)

Lip tool， while not being a stable zip claimang allows you to access pretty much everything that Kang saves in the AST when par your code。



![](img/4fb2a053d98aee2561a3567417a3601e_45.png)

And clk plugins are one way of using the lip tomen and has some specific features such as the registry and others willll see in more detail in the next videos。

😊。

![](img/4fb2a053d98aee2561a3567417a3601e_47.png)

Today， we saw some of the options we have if we want to write playing tools and some of their strengths and weaknesses。



![](img/4fb2a053d98aee2561a3567417a3601e_49.png)

In the next class， we will finally start building our first claim plugin。

 I'll introduce the bare minimum we need to get our plug up and running before we jump into more interesting stuff。

😊，Until then， you can email me with any questions， suggestions or comments。



![](img/4fb2a053d98aee2561a3567417a3601e_51.png)

Thank you。😊。