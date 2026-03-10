# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p06 P6 03_关联与聚合关系 -BV1MMEjzoEhg_p6-

So another thing that I'm going to talk about for class diagram is what we call association。



![](img/ab24acf341a556a1a00437af49781e63_1.png)

So notice that objects or classes within our class diagram， they don't exist alone， right。

 Somehow they are connected with some other objects， right within within the class diagram。

 for example， thread。

![](img/ab24acf341a556a1a00437af49781e63_3.png)

![](img/ab24acf341a556a1a00437af49781e63_4.png)

Okay。May hold an account。Or song right， may hold an account。

 and then this account may be associated with a bank B A。



![](img/ab24acf341a556a1a00437af49781e63_6.png)

Okay then another guy right maybe be Fred or he's going to have this account and this account is going to be from HSBC etctera。

 etc， so notice that within the system we need to keep track all these length。



![](img/ab24acf341a556a1a00437af49781e63_8.png)

， between the instances that we have within the system。So for example。

 Fred is going to have this account and this account is from HSBC and eventually we have to keep right many links。



![](img/ab24acf341a556a1a00437af49781e63_10.png)

Okay， within the system， so instead of of of trying to represent all of this length。

 right within the class diagram， we're going to perform。



![](img/ab24acf341a556a1a00437af49781e63_12.png)

Again， in classification。

![](img/ab24acf341a556a1a00437af49781e63_14.png)

We going classify all these links together and say that we only have this association。

 ho between account and customer。

![](img/ab24acf341a556a1a00437af49781e63_16.png)

Okay， and then we going to classify all these links together and say that we have this this association is with okay。

 between account and bank。Okay okay， so again here we are doing classification because we have so many links okay within the system between the instances that we have within the classes okay so that's why we're going to classify this links together and we perform abstract or we skip some details okay and we're going simply say that customer they host accounts and then accounts they are with different banks。

😊。

![](img/ab24acf341a556a1a00437af49781e63_18.png)

可以。So this is what we call a class diagram， we have classes and associations right between the classes。



![](img/ab24acf341a556a1a00437af49781e63_20.png)

Okay so an association described a collection of length this is what we have mentioned right in the previous slide okay so we try to perform classification and then classify all the instances right of the length okay as an association。

😊。

![](img/ab24acf341a556a1a00437af49781e63_22.png)

Okay。And conceptually associations， they are inherently bidirectional okay so that means right a account they are somehow associated with a customer and a customer they may hold different accounts okay so they are bidirectional。

So that means right， for example， account is going to be hold by customer and then customer they hold different accounts。

 right it's going to be bi directional okay。

![](img/ab24acf341a556a1a00437af49781e63_24.png)

And again， in some cases， right， we may show nevigability of association with an arrowhead。



![](img/ab24acf341a556a1a00437af49781e63_26.png)

Okay， so it means right， one object may depend on another object okay but if we are talking about the requirement model。

 okay， the requirement model， we may simply use association withoutarrowhead okay because in most cases in most cases。

 the associations， they are going to be bidirectional okay in a requirement model。

In a solution model， we may use arrowhead， right because one class that we implement may depend on another class。



![](img/ab24acf341a556a1a00437af49781e63_28.png)

But when we are talking about a requirement model， usually in most cases。

 it's going to be bidirectional。

![](img/ab24acf341a556a1a00437af49781e63_30.png)

So can we have two associations between the same pair of classes， yes。

 okay as long as those two associations， they have different meanings。For example。

 one of the association means right。The people that attended okay the people that are actually the student of a university okay and then the other one is like the people that works for the university as long as these' two associations right they have two different meanings right then we can have two associations between the same pair of classes。



![](img/ab24acf341a556a1a00437af49781e63_32.png)

Okay， and also we can have like unaryasation。For example。

 some people they may married to other people and then some people they may manage。

 they may be manager of some other people and this is what we call unaryasation。



![](img/ab24acf341a556a1a00437af49781e63_34.png)

Okay， instances within a class where it's going to associate with some other instances are within the same class。



![](img/ab24acf341a556a1a00437af49781e63_36.png)

Okay。And notice that the collection of class and association names， right they may。

 they must be unique。 Okay， so when you try to come up with the names for the classes and associations。

 make sure that the names， they are unique。

![](img/ab24acf341a556a1a00437af49781e63_38.png)

Okay。So these are the different types of associations that we can have within a class to can be unary okay that means the class is going to be associated with the same class。

Okay binary right， we have an association between two classes or it's going to be tennery。

 that means we have an association between multiple classes。



![](img/ab24acf341a556a1a00437af49781e63_40.png)

![](img/ab24acf341a556a1a00437af49781e63_41.png)

So in this course， most of the associations， they are going to be unary or binary associations notice that higher degree associations。

 right， they are extremely rare unless really necessary you don't include high degree associations into your diagram because higher degree associations。

 they are more difficult to understand they are more difficult to read So if you includes many high degree or tenary associations in your diagram。

 it's going to make your diagram more difficult to read and then when you try to use your model to communicate with different stakeholderss within your project that model is going to be difficult to read and that model is going to be more difficult to understand by the other stakeholderss。

 so in most cases we will simply use unary or binary associations。



![](img/ab24acf341a556a1a00437af49781e63_43.png)

![](img/ab24acf341a556a1a00437af49781e63_44.png)

![](img/ab24acf341a556a1a00437af49781e63_45.png)

![](img/ab24acf341a556a1a00437af49781e63_46.png)

![](img/ab24acf341a556a1a00437af49781e63_47.png)

![](img/ab24acf341a556a1a00437af49781e63_48.png)

Okay， so in practice， right， the majority of associations is going to be binary， okay？



![](img/ab24acf341a556a1a00437af49781e63_50.png)

So within an association， you also need to specify what we call multiplicities okay multiplicities specify a restriction on the number of objects in a class that may be related to an object in another class。

And this is how we specify multiplicity。Okay， for example， a given bank。

 how many accounts can it have？Okay， so now if we say that right， a bank can have multiple accounts。

Then we simply use0 dot dot asterisk risk asterisk risk means any。Any， and this is the lower bound。

 right，0 up to any number of accounts。 So that means it can have many accounts。 Okay， okay。

 so this is how we specify multiplicity。 And notice that this is the lower bound。

0 and the upper bound is any up to infinity。

![](img/ab24acf341a556a1a00437af49781e63_52.png)

![](img/ab24acf341a556a1a00437af49781e63_53.png)

Okay。And then given an account， okay， how many banks can it be with？Okay， for example。

 an account must be with exactly one bank right from the application domain mainly know that an account must be from one bank right then you provide the multiplicity here and say that an account can be associated with one dot dot one lower bound is one upper bound is one that means exactly one bank。

Okay， so multiplicity is an application domain constraint。

 So that means you have to get this information from the application domain。 Okay， the domain expert。

 right， some people from the application domain， they will tell you right a bank can have many accounts and then an account can be associated with exactly one bank only okay then some information that you can get from the application domain。



![](img/ab24acf341a556a1a00437af49781e63_55.png)

And this is how we specify multiplicities within a class diagram， for example。

 when we specify C1 can be associated with how many C2， were going to specify it here。

And when we specify， for example， C2 can be associated with how many C1。

 then we specify the multiplicity here。Okay， as a data B， and then when the lower bound is 0。Okay。

Then we say that it's going to be optional participation。



![](img/ab24acf341a556a1a00437af49781e63_57.png)

Okay， so that means C1 may or may not be associated with any C2。



![](img/ab24acf341a556a1a00437af49781e63_59.png)

Okay， because the law amount is zero。But if it's mandatory。

 that means the lower bound is bigger than0， then that means c1 has to somehow associated with some C2 and we say that the participation is mandatory。



![](img/ab24acf341a556a1a00437af49781e63_61.png)

Okay， ettera， et cetera。8。And then we also have to specify what we call the maximum carbonity。



![](img/ab24acf341a556a1a00437af49781e63_63.png)

Okay。And there are some special cardalities that we can use to simplify the class diagram。

For example， if the minimum card is one and the maximum card is one。Okay， for example。

 one dot dot one， okay， then we can replace it with simply a one that means exactly one。诶。

If the lower bank is zero and the upper amount is an asteriskther risk。

 okay then we can simply replace it with an asterisk risk。

 that means any okay a bank can have any number of accounts。Okay。

 so these are the two special cardities that we can use to simplify the class diagram。



![](img/ab24acf341a556a1a00437af49781e63_65.png)

Okay now let's try out this little example about multiplicities Okay so let's say from the application domain。

 you know that a student must enroll into at least one course and can enroll into at most five courses in a semester then you may say that right a student is going be associated with one up to5 courses and then again from the application domain you know that a course must have at least 10 students and cannot have more than 45 students Okay then you may say that course can be associated with 10 do 45 students Okay but now。



![](img/ab24acf341a556a1a00437af49781e63_67.png)

![](img/ab24acf341a556a1a00437af49781e63_68.png)

![](img/ab24acf341a556a1a00437af49781e63_69.png)

Let's think about it。Does it make sense？Did。ok。What's wrong with it？He， think about it。Now。

 let's say before the a row okay。In a course， right do we have like。



![](img/ab24acf341a556a1a00437af49781e63_71.png)

10 up to 45 students。No， right， before the actual， do student enroll into any courses？No。

 so that's why right， we have to relax， right， notice that once we specify these constraints within the class diagram。

 we have to always follow these constraints。😊，Okay that we specify in in the class diagram all the time all the time So now let's say before the add。

 you allowed a student to enroll into no courses。

![](img/ab24acf341a556a1a00437af49781e63_73.png)

![](img/ab24acf341a556a1a00437af49781e63_74.png)

And also you allow a course to have no students just before the。

 then somehow you have to relax the constraints。

![](img/ab24acf341a556a1a00437af49781e63_76.png)

Okay， and just say that right， a student may enroll into zero up to five courses and then a course may have like zero up to 45 students。

 then some of you may say right？

![](img/ab24acf341a556a1a00437af49781e63_78.png)

![](img/ab24acf341a556a1a00437af49781e63_79.png)

![](img/ab24acf341a556a1a00437af49781e63_80.png)

Then from from the model， how do I know that like after the a。

 a student should enroll into at least one course and also a course should have at least like 10 students notice that in UML we are allowed aance。



![](img/ab24acf341a556a1a00437af49781e63_82.png)

![](img/ab24acf341a556a1a00437af49781e63_83.png)

Okay so now you can draw a little note here， say that after the a drop。

 we should have like at least 10 students in a course and then here you should say that right a student should enroll into at least one course right after the a okay but if we talk about the multiplicity that we have to follow all the time we have to relax the requirements and we have to make it like a student can enroll up。



![](img/ab24acf341a556a1a00437af49781e63_85.png)

![](img/ab24acf341a556a1a00437af49781e63_86.png)

![](img/ab24acf341a556a1a00437af49781e63_87.png)

can enroll into zero up to five courses and a course may have like zero up to 45 students just because right。

 before the a， we may have no student in the course and student may enroll into no courses before the a。



![](img/ab24acf341a556a1a00437af49781e63_89.png)

![](img/ab24acf341a556a1a00437af49781e63_90.png)

And for Uniary association， we also have to specify what we call Roine。



![](img/ab24acf341a556a1a00437af49781e63_92.png)

Okay， usually the row name is going to be kind of obvious for binary association。😊。

Okay because if we say like a person they work for a company。

 then one side right the role should be employee and the other side， the row should be employer。

 so that's why just because right it's kind of obvious for binary association， the row names。

 it's going to be kind of obvious for binary association， so we may skip them for binary association。

 okay but unitary re association， we have to provide the row names right on the two sides。



![](img/ab24acf341a556a1a00437af49781e63_94.png)

![](img/ab24acf341a556a1a00437af49781e63_95.png)

![](img/ab24acf341a556a1a00437af49781e63_96.png)

OkayJust to make sure that we know that one side is going to be the boss and the other side is going to be the worker okay why because eventually when you store the data okay within your system。

 instead of simply saying that we have a link for example between join and Frank and then between Sarah and Bill okay we also need to provide a label or the row name saying that a join is the boss and Frank is actually the worker okay for the boss。

😊。

![](img/ab24acf341a556a1a00437af49781e63_98.png)

![](img/ab24acf341a556a1a00437af49781e63_99.png)

Okay without doubt this this labels okay without the row names。

 we only have the link okay then we cannot determine who is actually the boss who is actually the worker okay so that's why for unary association it's always required to provide the row names under the class diagram okay but for binary associations or tenerary associations。

 we may skip them。😊。

![](img/ab24acf341a556a1a00437af49781e63_101.png)

![](img/ab24acf341a556a1a00437af49781e63_102.png)

![](img/ab24acf341a556a1a00437af49781e63_103.png)

Okay。😊。

![](img/ab24acf341a556a1a00437af49781e63_105.png)

And then the last type of association that I'm going to cover in this lecture is what we call aggregation or composition。

😊。

![](img/ab24acf341a556a1a00437af49781e63_107.png)

Okay。So composition， we use a hollow diamond。Okay， then if we are using a hollow diamond。

Then the multiplicity on this side is going to be  zero up to one。

Okay0 up to one okay that means a disk may be associated with zero computer or one computer if it's a hollow diamond okay and when we are using a hollow diamond。

 okay， we have a special meaning okay， it means that it's going to be part of something， for example。

 the disk is going to be part of a computer okay when we have the meaning part of okay。

 we're going to use a diamond。

![](img/ab24acf341a556a1a00437af49781e63_109.png)

Okay， okay， and if it's hollow， okay， then that means right the multiplicity that we have on this side。

 okay on the computer side right， it's going to be0 do1 that means a disc。😊。



![](img/ab24acf341a556a1a00437af49781e63_111.png)

It's going to be associated with zero up to one computer when it's zero， okay， when it's zero。

 when the lower bound is0， that means the participation is going to be optional。😊。

That means the disk can exist alone without a computer。 Okay。

 that's what we mean by optional participation。But let's say if we are using a filled diamond。

 then the multiplicity becomes 1 dot dot1。Okay， so a ro is going to be associated with exactly one building。

Okay， that means right a ro， the participation is going to be mandatory。

 that means the room has to somehow associated with a building okay the room cannot exist。

 cannot exist alone without a building okay that's the difference between a hollow diamond and a field diamond okay hollow diamond means part of okay field diamonds also mean part of okay but hollow diamond means the participation is going to be optional okay and field diamond means the participation is going to be mandatory okay that means Rome。

 the existence of Rome okay depends on building。When participation is optional。

 that means existing of， for example， hot diskk， does not depends on computer。😊。



![](img/ab24acf341a556a1a00437af49781e63_113.png)

Okay， okay， and we use。Ecation or composition only when we want to specify the meaning part of， okay。

 when something is really part of something， we use education or composition。



![](img/ab24acf341a556a1a00437af49781e63_115.png)

![](img/ab24acf341a556a1a00437af49781e63_116.png)

And when the participation is optional， we say that we have aggregation， we use whole diamond， okay。

 when the participation is going to be mandatory， okay we use a filled diamond。😊。



![](img/ab24acf341a556a1a00437af49781e63_118.png)

![](img/ab24acf341a556a1a00437af49781e63_119.png)

Okay， that means comp。That means composition。

![](img/ab24acf341a556a1a00437af49781e63_121.png)

Okay， some of you may ask， how do I know whether we're going to use a whole diamond or field diamond。

 Okay， one way to think about it is going to be this way。 Okay。

 think about when you destroy a computer。Okay， do you destroy audit hard disk？



![](img/ab24acf341a556a1a00437af49781e63_123.png)

Okay， let's say right， if you destroy all the computers， you also destroy all the hard disk， right。

 then you have to make it fill diamond because the existence of Had disk right depends on computer。😊。

Okay okay， but let's say right when you when you destroy a computer， you may keep all the hard disk。

 you may still keep all the hard disk right， then you have to make it hollow okay because existence of hard disk right does not depend on a computer in this case we have to make it filled okay just because when we destroy the building it's kind of natural that we can to destroy all the rooms。

😊。

![](img/ab24acf341a556a1a00437af49781e63_125.png)

Within the building， okay， so that's why we have to make it filled。Okay。

 to denote that the participation is going to be mandatory， okay。

 just because when we destroy the building， we can also destroy all the rooms。😊，Within the building。

 okay， that means the participation of Rome。It's going to be。

That means the participation is going to be mandatory。Okay。

 so that's another way to think about whether we have to use hollow diamond or field diamond when we are talking about aggregal composition。



![](img/ab24acf341a556a1a00437af49781e63_127.png)

![](img/ab24acf341a556a1a00437af49781e63_128.png)

But be very careful when you're using application or composition。

 don't replace every single has or have kind of associations with applicationss or compositions。😊。



![](img/ab24acf341a556a1a00437af49781e63_130.png)

Let me give you an example。😊，Kenneth has a bank account。



![](img/ab24acf341a556a1a00437af49781e63_132.png)

But bank account is not part of me。It's not something that like inside my body。

 okay then you should not make it like part of Kenneth， okay。

 so you should not use educational composition between like person and account right because like account is not part of the customer。



![](img/ab24acf341a556a1a00437af49781e63_134.png)

![](img/ab24acf341a556a1a00437af49781e63_135.png)

![](img/ab24acf341a556a1a00437af49781e63_136.png)

![](img/ab24acf341a556a1a00437af49781e63_137.png)

Okay， okay， so that's why you have to be very careful， okay。

 and the decision to use education is a matter of judgment。😊。



![](img/ab24acf341a556a1a00437af49781e63_139.png)

![](img/ab24acf341a556a1a00437af49781e63_140.png)

Okay， and it's also a design decision。

![](img/ab24acf341a556a1a00437af49781e63_142.png)

And it's not wrong to use association rather than aggregation in your project or in your assignment okay if you are using aggregation if you provide more meanings right in your in your diagram because whenever we see a diamond we know that something is going to be part of something you provide more semantics in your diagram okay but it's not wrong to simply use an association between two things right to replace aggregation or composition so that's why it's important that you think twice before you use aggregation or composition in a class diagram okay。



![](img/ab24acf341a556a1a00437af49781e63_144.png)

![](img/ab24acf341a556a1a00437af49781e63_145.png)

![](img/ab24acf341a556a1a00437af49781e63_146.png)

![](img/ab24acf341a556a1a00437af49781e63_147.png)

![](img/ab24acf341a556a1a00437af49781e63_148.png)

Think about whether something is really part of something before you use a diamond。

 okay within your class diagram。

![](img/ab24acf341a556a1a00437af49781e63_150.png)

![](img/ab24acf341a556a1a00437af49781e63_151.png)

And that's all I want to cover in this lecture。