# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p07 P7 01_关联类 -BV1MMEjzoEhg_p7-

Hi， in this lecture， we will talk about some additional components that you can use for drawing UMl class diagram。

 so now let's start with an example。So let's say we want to build a system to keep track student enrollment information and we have a set of students and then we have a set of courses and then we keep track which student enroll into which courses for example。

 Mac androll it into Com 3111 Com 3021 and also co 3311 now let's say if we want to also keep track and attribute like grade then where should we store the grade so there are different options that we can use。

O呃。

![](img/ab1d2df44cad5d43f38b011396050b14_1.png)

The first option is that we may store grade as an attribute under student。Okay， for example。

 for a student， we stored a grade for column 1212 and also called for column 2012。Okay， is this okay？

No， this is not okay because we don't know exactly how many attributes that we need right for a particular student so this is not okay so this is the problem right we don't know how many great attributes that we need for each student。

So option number two is that can we use a multi value attribute for grade？Okay， for example。

 under the student， we have an attribute called grade， which is like an array。

 okay then we can store multiple grades。Right under a student。Okay， is this okay。No。

 this is also not okay because we don't know which gray maps to which cause。 Now。

 understood that we just have a set of grades。 but we don't know exactly which gray maps to which calls。

 So this is this option， right option number two is also not okay。😡，Okay。

 then let's talk about the next option， which is using an associate class Okay so this is another component that we can use for drawing UMl class diagram Okay so whenever the association has properties then we can model the properties of an association using attributes under the association for example。

 when student enroll into a course， then we try to keep track the grade and we keep track the grade under the association and this is the situation。

 for example， macro enroll it into con3 111 and then he get an a plus then we start this attribute under the link between Mac and con3 11 as another example。

 let's say Jason okay。

![](img/ab1d2df44cad5d43f38b011396050b14_3.png)

Takes co 3 P1，1， and then he gets an A。Okay， then again， we store a grade A under this link okay。

 then think about it is this option okay？I would say no， okay， why， let me give you an example， okay？



![](img/ab1d2df44cad5d43f38b011396050b14_5.png)

So now let's say we are using this model。 Okay， we have a student。

And then student enroll into different courses。Okay。

 and then we try to keep track all the grades using an association class and roads in。

And then we try to keep track the attribute great。Okay， using this association class。

 then under student， right， we may have many students。😊，For example， we may have Kenne of。

We may have Gibson。We may have de men。And also， we may have a Dave。Okay。

 they are all the students within the university and then we have different courses。For example。

 we have co 1001， we have co 31，11， we have co 3311， etc cetera， et cetera。 Okay。

 now let's say we have this kind of situation。 let's say kind of enrolls into Com 31。

11 in the previous semester。

![](img/ab1d2df44cad5d43f38b011396050b14_7.png)

Okay， then he failed。Okay， we try to start a great field using association class。



![](img/ab1d2df44cad5d43f38b011396050b14_9.png)

Okay，Then now let's say he takes CO 3111 again in the semester。Okay， and now this time he。

 he get an A plus。

![](img/ab1d2df44cad5d43f38b011396050b14_11.png)

Now using this model。Okay， can we store this kind of information？16。No。

 so now let's say we have a pair of instances。 let's say Kenne of and co 31，1。

1 being connected using an association using a link。 Okay。

 then notice that this is what you have to keep in mind。 Not that once a pair of instances。

 they are related。 They are related。 Okay We cannot。 okay。

 we cannot relate the same pair of instances using two different links。 Okay。

 so now we can only keep track one of the two links， right， but not both of them。 Okay。

 maybe we can simply keep track the most recent link， Okay。

 which is like Ken of enrolls into co 311 again in the semester and then he get an a plus。



![](img/ab1d2df44cad5d43f38b011396050b14_13.png)

![](img/ab1d2df44cad5d43f38b011396050b14_14.png)

so this is what we can keep track， okay， using this particular model。Okay。

 and this is the restriction of this model。Okay， so again。Keep in mind， once they're related。

 they're related， we cannot relate the same pair of instances using more than one links。



![](img/ab1d2df44cad5d43f38b011396050b14_16.png)

Okay， okay， so this is not allowed。 Okay， and then we have to remove one of the two links。



![](img/ab1d2df44cad5d43f38b011396050b14_18.png)

Okay okay so if you want to keep track all the historical information， for example。

 Kenneth enrolled it into Con3 111 in the previous semester and then he failed and then he takes it again in this semester and he gets NA a plus this kind of information you cannot now store it using this particular model so now how do we fix the problem because using this model is not allowed it to have a student to enroll into the same course multiple times through the association class androlls in。

😊，Then we may have to use a more complicated model。

 which is this one So now student they are not enroded into different courses。

 they are enrollded into different offerings of the course So what do we mean by offering So now let me try to draw the example so we may have different students。



![](img/ab1d2df44cad5d43f38b011396050b14_20.png)

![](img/ab1d2df44cad5d43f38b011396050b14_21.png)

And we have also a set of courses。And then we relay students and courses together using offering。

Okay， now student they are not taking courses， they are taking the offering a particular offering of a course。

 okay， and then we try to keep track grade。RightOf a particular offering。

K students they enrolls into different。Os Okay， so what do I mean by offeringing Okay， so Kenneth。

 we may have like a set of students like Kenneth。Gbson。And then Dave and then maybe Desmond。

Okay and then we have a set of courses maybe column 3111 and also column 3311 etca。

 etcter so under a course we're going to have different offerings in different semesters okay so that means we may have column 3111 in for 2019 and also come 3111 in spring 2020。



![](img/ab1d2df44cad5d43f38b011396050b14_23.png)

![](img/ab1d2df44cad5d43f38b011396050b14_24.png)

Okay， and they are different offerings of Conre 111。Okay， now using this model。

 it's possible that Kenneth emrolled into Conre 11 in 4019 and then he gets anF。



![](img/ab1d2df44cad5d43f38b011396050b14_26.png)

![](img/ab1d2df44cad5d43f38b011396050b14_27.png)

Okay， then he emros intoum Com 311 in spring 2020 again， and then he gets an A plus。Okay。

 so now we are relating students and courses to gather through offerings。Okay。

 and by using this model， we can keep track all the historical information， for example。



![](img/ab1d2df44cad5d43f38b011396050b14_29.png)

Kenneth。Erolls into Com 3111 in 4 2019 and he gets NF okay and then1if also enrolls into Com 311 in spring 2020 and then finally he gets NA+ Okay so now using this more complicated model we can actually keep all the historical information and we allow students to enroll into the same course multiple times through different offerings in different semesters。



![](img/ab1d2df44cad5d43f38b011396050b14_31.png)

![](img/ab1d2df44cad5d43f38b011396050b14_32.png)

![](img/ab1d2df44cad5d43f38b011396050b14_33.png)