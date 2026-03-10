# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p09 P9 03_类图总结 -BV1MMEjzoEhg_p9-

![](img/8f0b697c3efd138eb332552c4a97b53a_0.png)

And for UML diagrams， you can also specify some additional constraints， for example， balance right。

 let's say we are trying to store this additional constraint under our class diagram， for example。

 balance has to be bigger than or equals to 100，000。



![](img/8f0b697c3efd138eb332552c4a97b53a_2.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_3.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_4.png)

Okay， then you can either specify the constraint beside the operation right for checking balance。

 right， let's say when we check balance， the balance has to be always bigger than or equals to 100。

000。Okay， or you can put a note aside and say that for preferred saving accounts okay balance has to be bigger than or equals to 800。

000 okay and notice that again in class diagram we can always use a note okay to provide additional information。



![](img/8f0b697c3efd138eb332552c4a97b53a_6.png)

Okay， okay。So and a constraint is actually a statement that can be tested to be either true or false okay。

 so in this example balance it's going to be either bigger than or equals to 100。

000 or not bigger than or equals to 100，000。

![](img/8f0b697c3efd138eb332552c4a97b53a_8.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_9.png)

And it should be enforced by the system implementation once we apply this constraint okay in our implementation。

 somehow we have to enforce okay this constraint。

![](img/8f0b697c3efd138eb332552c4a97b53a_11.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_12.png)

And then there are some additional constraints that we can provide in a class diagram。For example。

 we can provide ordering。Okay， for example， student they may be waitlist for different courses and then the order is going to be first in first out。

Okay。Maybe right， we have。Persons， right， which are members of a committee。

And also we may have a person which is chair of the committee then we can say that the chair is going to be a subset of the members。



![](img/8f0b697c3efd138eb332552c4a97b53a_14.png)

Okay。An exclusive or okay， that means we're going to follow either this path or that path。

 but not both the two paths Okay， so an account is going to be either。

H by a person or hold by a company， but not both of them at the same time。

 So that means we' are going to follow this path or the other path。

 but not both at the same time Okay again， it just means that in that kind it's going to be hold by either a person or a company exclusive or okay either this or that。

 but not both at the same time。

![](img/8f0b697c3efd138eb332552c4a97b53a_16.png)

and this is a little summary of what we have covered in this lecture and also in the last lecture。

 okay we have covered how to define classes and also associations between classes。



![](img/8f0b697c3efd138eb332552c4a97b53a_18.png)

We have covered how to specify。A and also composition and also we have covered how to define generalization。

And also how to define or provide， the generalization constraints。Okay。So we have。



![](img/8f0b697c3efd138eb332552c4a97b53a_20.png)

Define all these elements and also the constraints。

 So these are the things that we have covered in this lecture and also in the last lecture And this is an example on how to use a class diagram to model data requirements within an application domain okay for example。

 within the application domain。 we have different items。 We have different orders。 we have invoice。

 we have accounts and we have some VIP etctera， etc cea and these are all the things that exist okay in the application domain Okay then we capture all them in a model and then we use this model okay to capture all the data requirements okay these are the things that we have to store within the system data requirements for an application domain。



![](img/8f0b697c3efd138eb332552c4a97b53a_22.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_23.png)

Okay，And we can also use a class diagram to model a program。



![](img/8f0b697c3efd138eb332552c4a97b53a_25.png)

Okay， and we will talk about it in one of the upcoming lectures on how to use CM to model a program。

So let's say in a program， we have different clients and we have event handler and we also have a GuUI handler。

 okay， we can use a class diagram to model a program。



![](img/8f0b697c3efd138eb332552c4a97b53a_27.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_28.png)

Okay， and as I've said in the last lecture， some of the classes in your program may depend on some other classes then we can use dependence okay again we will talk about that when we talk about how to model a program in one of the upcoming lectures and that's all I want to cover in this lecture。



![](img/8f0b697c3efd138eb332552c4a97b53a_30.png)

![](img/8f0b697c3efd138eb332552c4a97b53a_31.png)