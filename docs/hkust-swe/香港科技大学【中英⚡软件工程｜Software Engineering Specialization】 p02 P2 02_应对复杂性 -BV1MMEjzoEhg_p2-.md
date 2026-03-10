# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p02 P2 02_应对复杂性 -BV1MMEjzoEhg_p2-

![](img/2284416b5c4537047637b347dd7b90ff_0.png)

So to deal with complexity， the first thing that we have to do is to choose the appropriate design goals at the very beginning of the project。

 let's say if you want to build an online transaction handling system and you have to make sure that your system has to be efficient and also reliable and notice that it's often impossible to achieve all of them simultaneously all of them at the same time because of the time and budget that you have for the project and notice that some of the design goals right they may be conflicting with one and another so that's why it's not possible for you to achieve all the design goals at the same time。



![](img/2284416b5c4537047637b347dd7b90ff_2.png)

![](img/2284416b5c4537047637b347dd7b90ff_3.png)

![](img/2284416b5c4537047637b347dd7b90ff_4.png)

And to choose the appropriate design goals， you need to clearly understand the client's design goals at the very beginning of the project if the client tells you that I want the system to be efficient and to be reliable。

 then those has to be the design goals that you choose for the project。



![](img/2284416b5c4537047637b347dd7b90ff_6.png)

![](img/2284416b5c4537047637b347dd7b90ff_7.png)

And then you need to priorize the design goals for a given project and then base the development around these design goals again。

 you have to choose two or three or four most appropriate design goals right at the very beginning of the project。



![](img/2284416b5c4537047637b347dd7b90ff_9.png)

![](img/2284416b5c4537047637b347dd7b90ff_10.png)

And having clear design goals is going to reduce the complexity of designing the system because you know exactly what you need for your software system。

 so eventually when you design the system it's going to be much easier。



![](img/2284416b5c4537047637b347dd7b90ff_12.png)

![](img/2284416b5c4537047637b347dd7b90ff_13.png)

![](img/2284416b5c4537047637b347dd7b90ff_14.png)

And to deal with complexity， another thing that we can do is to apply modularity and also incremental development。



![](img/2284416b5c4537047637b347dd7b90ff_16.png)

Because there is a limit to human understanding when we are building a large software system。

 then we can apply an approach which is called divide and Conre to divide the large software system into many smaller pieces。



![](img/2284416b5c4537047637b347dd7b90ff_18.png)

![](img/2284416b5c4537047637b347dd7b90ff_19.png)

And instead of handling the large software system all at once。

 we're gonna build these smaller pieces， smaller modules， one at a time。

 Okay and the definition of a module is a part of the system that is make sense to consider separately and notice that this modules is going to interact with each other because one module may be using some of the functionalities or some of the operations from the other modules。

 So that's why they interact with each other。

![](img/2284416b5c4537047637b347dd7b90ff_21.png)

![](img/2284416b5c4537047637b347dd7b90ff_22.png)

![](img/2284416b5c4537047637b347dd7b90ff_23.png)

Okay， and another approach to deal with complexity is to use information hiding。

 so when we try to access a particular module， we are only allowed it to access the module or interact with the module via interfaces。

Okay，So by using an interph， we achieve both abstraction and capsulation at the same time。



![](img/2284416b5c4537047637b347dd7b90ff_25.png)

![](img/2284416b5c4537047637b347dd7b90ff_26.png)

OkaySo what are the definition of abstraction and encapsulation abstraction means with steep details So when we try to use a module。

 we don't have to actually understand what's inside the module that means the sourceco and the implementation within the module。

 we only have to understand how to use the interface That's it and encapsulation means if we want to maintain a particular module okay or when we want to modify a particular module。

 then it's going to be just within this module， we don't have to touch the other modules。



![](img/2284416b5c4537047637b347dd7b90ff_28.png)

![](img/2284416b5c4537047637b347dd7b90ff_29.png)

![](img/2284416b5c4537047637b347dd7b90ff_30.png)

Okay。So that's what we mean by abstraction and encapsulation。

 so the good thing with abstraction is that a module can be used by only understanding the interface。

 but not the actual implementation within the module。



![](img/2284416b5c4537047637b347dd7b90ff_32.png)

Okay。So this is going to reduce the complexity of understanding the system because you only have to understand how to use ins instead of understanding the content。

 that means the sourceco and the implementation within the module。



![](img/2284416b5c4537047637b347dd7b90ff_34.png)

Okay， so an interface also provides encapsulation， so if you want to change a module。

 you have to only change that particular module without affecting the rest of the system okay and this is going to reduce the complexity of maintaining the system because when you maintain the system when you want to change something。

 you only have to touch one thing but not the other things。



![](img/2284416b5c4537047637b347dd7b90ff_36.png)

![](img/2284416b5c4537047637b347dd7b90ff_37.png)

![](img/2284416b5c4537047637b347dd7b90ff_38.png)

![](img/2284416b5c4537047637b347dd7b90ff_39.png)

So now by applying modularity and also incremental development。

 that means you chunk the large software system into smaller pieces and then you handle one small piece at a time and then also using interfaces for the modules for the smaller pieces then it allows more productivity in team development because one team is gonna to be just responsible for one small thing and then just because people they are focusing on one small thing instead of a large software system。

 then eventually we may get fewer bucks in system development。



![](img/2284416b5c4537047637b347dd7b90ff_41.png)

![](img/2284416b5c4537047637b347dd7b90ff_42.png)

![](img/2284416b5c4537047637b347dd7b90ff_43.png)

![](img/2284416b5c4537047637b347dd7b90ff_44.png)

![](img/2284416b5c4537047637b347dd7b90ff_45.png)

And also more maintainable software and also more reusable software and resulting in more predictable software development。



![](img/2284416b5c4537047637b347dd7b90ff_47.png)

Okay， and this is going to reduce the complexity of cost and time estimates for developing this system。



![](img/2284416b5c4537047637b347dd7b90ff_49.png)

So another way to deal with complexity is to provide training to software engineers。

 so what do engineers do？

![](img/2284416b5c4537047637b347dd7b90ff_51.png)

So engineer， they apply scientific knowledge， for example， mathematics， phs。

 and then develop solutions for some technical problems。



![](img/2284416b5c4537047637b347dd7b90ff_53.png)

And then engineers， they have to design materials， they have to choose the appropriate materials。

 structures， and also system while consideringring some limitations， okay， for example。

 the time and budget that you have for the project。



![](img/2284416b5c4537047637b347dd7b90ff_55.png)

Okay。So what do we have to do as a software engineer？

 So there are two things that we have to do as a software engineer。

 One is programming in the small that means coding。

OkayAnother thing is programming in the large that means software engineering so apart coding there are many things that you have to do within software engineering for example。

 you have to talk with users in terms of the application you have to communicate with your client and also communicate with your users。



![](img/2284416b5c4537047637b347dd7b90ff_57.png)

![](img/2284416b5c4537047637b347dd7b90ff_58.png)

![](img/2284416b5c4537047637b347dd7b90ff_59.png)

![](img/2284416b5c4537047637b347dd7b90ff_60.png)

And then also translate the vague requirements into something that's going to be more precise。



![](img/2284416b5c4537047637b347dd7b90ff_62.png)

And then you have to build models of a system at different levels of abstraction so that when you communicate with your client。

 when you communicate with your users， you can use your models to communicate with different stakeholders within your project。



![](img/2284416b5c4537047637b347dd7b90ff_64.png)

![](img/2284416b5c4537047637b347dd7b90ff_65.png)

![](img/2284416b5c4537047637b347dd7b90ff_66.png)

And also you have to use and apply several software development processes。

 and we're going to talk about different development processes in one of the upcoming lectures。



![](img/2284416b5c4537047637b347dd7b90ff_68.png)

![](img/2284416b5c4537047637b347dd7b90ff_69.png)

And also you have to choose the appropriate design okay and also make design trade offs。



![](img/2284416b5c4537047637b347dd7b90ff_71.png)

OkayAnd work as a team。OkaySo this is going to reduce the complexity of building the system。



![](img/2284416b5c4537047637b347dd7b90ff_73.png)