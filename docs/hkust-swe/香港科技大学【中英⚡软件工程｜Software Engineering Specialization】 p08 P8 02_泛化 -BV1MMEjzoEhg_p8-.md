# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p08 P8 02_泛化 -BV1MMEjzoEhg_p8-

![](img/942c67799321fb955ed85989b6e47f71_0.png)

And the next component that I'm going to cover in this lecture is what we call generalization or inheritance。



![](img/942c67799321fb955ed85989b6e47f71_2.png)

And the definition of generalization is that it's a relationship between classes of the same kind Okay。

 so we may have。

![](img/942c67799321fb955ed85989b6e47f71_4.png)

![](img/942c67799321fb955ed85989b6e47f71_5.png)

A class， okay， and then we may specialize the class into different。



![](img/942c67799321fb955ed85989b6e47f71_7.png)

Someub classes， which are of the same kind。

![](img/942c67799321fb955ed85989b6e47f71_9.png)

Okay， so now let me show you an example because it's easier to explain what is generalization using an example。



![](img/942c67799321fb955ed85989b6e47f71_11.png)

So now this is an example， let's say we are trying to build a software system for a bank and then within the application domain we have different accounts and then you can see that from the attributes right we can see that the account we have different types of accounts right for example some of the accounts they are checking accounts and then some of the accounts。

 they are saving accounts。

![](img/942c67799321fb955ed85989b6e47f71_13.png)

And then some of the actual bills， let's say service charge is going to apply to only checking accounts and then interest rate is going to applies only to saving accounts and then the operation pay interest it will only apply to saving accounts。

Okay， et cetera， etc cetera then instead of saying that we only have account okay。

 we can specialize account into two types okay， one is what we call check account and then another one is what we call saving account okay and this is what we call doing specialization top down。



![](img/942c67799321fb955ed85989b6e47f71_15.png)

![](img/942c67799321fb955ed85989b6e47f71_16.png)

Okay， that means from account， okay， we can see that there is an attribute called discriminator。



![](img/942c67799321fb955ed85989b6e47f71_18.png)

![](img/942c67799321fb955ed85989b6e47f71_19.png)

Okay， account type okay is the discriminator okay to discriminate account into two different types right。

 Sa account or check account okay， then we can do it top down right starting from account we specialize into two types of accounts Check account and save account and we perform this kind of specialization using。



![](img/942c67799321fb955ed85989b6e47f71_21.png)

![](img/942c67799321fb955ed85989b6e47f71_22.png)

A triangle。Okay using a triangle， a triangle means we have generalization。

 okay we try to specialize accounts into two types okay。

 check accounts and save accounts okay and under a check account we have the additional attribute called service charge and then under Sa account we have the additional attribute bill called interest rate and we have the additional operation called pay interest。



![](img/942c67799321fb955ed85989b6e47f71_24.png)

Okay。

![](img/942c67799321fb955ed85989b6e47f71_26.png)

And we can also do it bottom up okay， for example， we can see that we have two classes they are pretty similar to each other for example。

 account and credit card okay you can see that the attributes they are kind of similar and then the operations they are kind of similar then we can see that they are。

Kind of similar objects that we have or kind of similar things that we have within the class diagram then we can。



![](img/942c67799321fb955ed85989b6e47f71_28.png)

We can perform generalization。Okay， and then we general account and credit card。えす。



![](img/942c67799321fb955ed85989b6e47f71_30.png)

A more general class okay call account Okay and under account we have two different types of account right one is bank account and another one is credit card account Okay。

 and this is how we perform generalization or inheritence bottom up okay。

 because we see that we have two very similar objects right in the class diagram Okay then somehow we can perform generalization and then create a more general class called account。



![](img/942c67799321fb955ed85989b6e47f71_32.png)

![](img/942c67799321fb955ed85989b6e47f71_33.png)

![](img/942c67799321fb955ed85989b6e47f71_34.png)

![](img/942c67799321fb955ed85989b6e47f71_35.png)

Okay， then accounts specialize into bank accounts and credit card accounts。



![](img/942c67799321fb955ed85989b6e47f71_37.png)

Okay。And this is what we call inheritance okay and the good thing of inheritance is that we can extract the common attributes。

 relationships and also operations and put them in the superclass okay in our example。

 we say that bank account and credit card accounts right they share common attributes like account number and amount。



![](img/942c67799321fb955ed85989b6e47f71_39.png)

And also as they share the common operation balance right then we can put all these things right in the superclass and they will be shared in by the subclasses Okay。

 so for bank account we have account number amount balance， the operation deposit and withdraw。Okay。

 and for credit card account right we have two attributes right account number amount and also balance the operation balance and also this additional operations for credit card so this attributes and operations right they are shared by the subclasses。



![](img/942c67799321fb955ed85989b6e47f71_41.png)

Okay and this is the get thing of inherance right you can define all the attributes and operations and also the relationships just once。

 and then they will be shared by all the subclasses。

Okay and by putting the attributes or by defining the attributes and operations in just one place。

 okay again we reduce redundancy of description and promote reusability of descriptions and also simplify modification of descriptions because if we want to somehow modify the things that we have in the supert okay then we just we just modify the supert or superclass。

 or if we want to modify a particular。

![](img/942c67799321fb955ed85989b6e47f71_43.png)

![](img/942c67799321fb955ed85989b6e47f71_44.png)

Type of of or a particular subtype of class okay then we just simply modify that particular subclass we don't have to touch the other things right then it's going to help simplify modification of descriptions。



![](img/942c67799321fb955ed85989b6e47f71_46.png)

And this is another example of inheritance we can define additional properties under the subclasses okay。

 for example， checking account， we have a service charge， saving account。

 we have some additional properties Okay now let's say we define another withdrawal operation under the subtit。

OkayAnd we can see that we also have the withdraw operation under the supert then notice that if we define another withdraw operation here under the subt。

 okay it's going to override the withdrawal operation that we have defined it in the supert。Okay。

 that means if an account is a check account， then it's going to use the operation under。嗯。

The subtype to perform withdraw rather than using this operation under the super type。Okay。

 so that's what we mean by overriding okay， overriding means right if we define the same operation again in the subtype。

 we're going to use the operation defined it in the subtype。In this example。

 we define withdraw again in。The subtype， then we're going to use the withdraw operation under the subt instead of using the withdraw operation under the supert。

 and this is what we mean by overriding the method of a super class operation。



![](img/942c67799321fb955ed85989b6e47f71_48.png)

![](img/942c67799321fb955ed85989b6e47f71_49.png)

Okay。And this is what we mean by single inheritance and then we can have multilevel of inheritance right for example。

 let's say we have another type of account which is like checking and saving together okay then we can simply apply another level of inheritance and then we say that we have checking and saving accounts。



![](img/942c67799321fb955ed85989b6e47f71_51.png)

![](img/942c67799321fb955ed85989b6e47f71_52.png)

Okay。And notice that discussion of multiple inheritance is beyond the scope of this course and in your project or in in your exercises。

 you may use multiple level of inheritance but try to avoid having like more than three or four levels of inheritance because if you have more and more levels of inheritance it's going to make your diagram your class diagram more difficult to read and more difficult to understand so to keep your model simple and also make sure that all the other stakeholders they can easily understand your model。

 try to limit okay try to limit the level of inheritance to only two or up to three levels。

Okay don't use like four or five or even six level of inheritance It's gonna to make your diagram very difficult to read So now what if we have this special situation。

 let's say Pg student they can enroll into like zero up to three courses and then usually each student they can enroll into one up to five courses Okay then again instead of saying PG student they enroll into some courses and use the student they enroll into some courses we can simply say student they enroll into some courses Okay but now we have to relax the requirement because Pg student。

 they are going to enroll into zero up to three courses use student they are going enroll into one up to five courses Okay then we have to relax and then say that student they enroll into zero up to five courses then some of you may say right we miss the information about like Pg student is gonna be zero up to three courses and U student is gonna be one up to five courses notice that again in a class diagram。

 you can also put you can always you can always put a no。



![](img/942c67799321fb955ed85989b6e47f71_54.png)

![](img/942c67799321fb955ed85989b6e47f71_55.png)

![](img/942c67799321fb955ed85989b6e47f71_56.png)

Beside and say that， for example， PG student is going to be zero up to three courses and then usually students is going to be one up to five courses you can you can always provide additional information using a note。



![](img/942c67799321fb955ed85989b6e47f71_58.png)

And in generalization， we can have what we call abstract class。

And we define abstract class using italic okay you can see that this accounts here is in italic that means this class is an abstract class okay and the definition of abstract class is that an abstract class is a class that has no direct instances so that means we don't store any instances here under accounts okay or the instances they are either checking accounts or saving accounts okay we don't have any instances stored under this class account。

Okay， and that's what we mean by abstract class Okay。

 and abstract class we use it for modeling purpose Okay。

 so from this class diagram we know that check accounts and save accounts is under an abstract class call account right。

 so they are all accounts。Okay， so you can get some additional meaning right from this abstract class。

 but we don't store any instances under this class call account。Okay。

 we have audience instances under checking or saving， but not accounts。



![](img/942c67799321fb955ed85989b6e47f71_60.png)

几。And another thing that we need to define for generalization is the destroying coverage。Okay。

 and the coverage can be either overlapping or disjoint。



![](img/942c67799321fb955ed85989b6e47f71_62.png)

Okay， so what do we mean by overlapping right in this example， we can see that players。

 they can be either playing tennis or soccer。and we make it overlapping that means some of the players they are playing tennis and soccer at the same time。

 so this part right the screen part right some players they may be playing tennis and soccer at the same time and then if that's the case right then we have to put the constraint here saying that this generalization cons is overlapping。

Okay。Sometimes it may be disjoint。That means it's not overlapping right。

 so some of the we have accounts。Okay， and then we have different types of kind。

 right personal and business and they are disjoint。

That means we don't have an account which is like both personal and business。Okay。

 I's going to be disjoint， it's either personal or business， but not both of them at the same time。



![](img/942c67799321fb955ed85989b6e47f71_64.png)

Another constraint that we can specify for generalization is what we call completeness coverage。



![](img/942c67799321fb955ed85989b6e47f71_66.png)

It can be either complete or incomplete。

![](img/942c67799321fb955ed85989b6e47f71_68.png)

Okay， so now let's say under your university， we can have like UG student or PG student。Okay。

 and these are the only two types of students that we have within a university okay。

 then we can simply say that within the university。

 we only have UG andPG students and they are complete。😊，Okay。

 we do not have another type of student okay， we only have UG and MPG students， that's it。Okay。

 if we make it incomplete。For example， trees can be either this type， that type or the other type。

Okay， if we make it incomplete， then that means we may have some trees which are not of these free types。



![](img/942c67799321fb955ed85989b6e47f71_70.png)

![](img/942c67799321fb955ed85989b6e47f71_71.png)

Out of these three types， then we're going to use the coverage constraint incomplete。



![](img/942c67799321fb955ed85989b6e47f71_73.png)

And for example， for players we may specialize into tennis and soccer and then some of the players they may be both tennis and soccer players at the same time。

 then we make it overlapping。Okay， and we make it incomplete because in this diagram there may be some other types of spots that we have not specified in the diagram okay。

 we may even have like I don't know swimming and also and also some other types of spots okay。

 then we have to make it incomplete。for three， it's going to be destroyed and incomplete。😡。

And for courses， it's going to be overlapping and complete because we only have like either UG courses or PG courses。

 So that's why it's complete。 Okay， and it's overlapping because is some of the courses。

 they may be for both UG and PG students。Okay。For university students， we have two types， right。

 UG or PG， it's going to be this， it's going to be either UG or PG。

OkayAnd we only have these two types of students under the application domain。

 so it's going to be complete。Okay， okay， so based on what we call the coverage types， okay。

 we have to specify the constraints， right for generalizations。



![](img/942c67799321fb955ed85989b6e47f71_75.png)

Okay。So now let's study another example。😡，Okay， for let's say we are trying to pay tuition fee within a university and there are different types of methods。

 okay， cash， credit card or debit card。Okay， then for payment。Sit going to be overlappingcomplete。

 disjoint completelete， overlapping incomplete or disjoint incomplete。

I will say it's going to be overlapping because you can pay part of your tuition fee using cash and then another part of your tuition fee using credit card okay。

 it's possible okay so I will say it's going to be overlapping and is it complete。

I would say no right because there are some other ways that you can pay your tuition fee。

 for example you can use internet banking right to pay your tuition fee so it's not limited to cash credit card and debit card only so that's why for this example I would say the coverage constraint is going to be overlapping and it's going to be incomplete。



![](img/942c67799321fb955ed85989b6e47f71_77.png)