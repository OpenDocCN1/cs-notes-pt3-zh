# 悉尼大学【中英⚡计算模型｜COMP2022 Models of Computation】 p04 P5 Normal Forms in Propositional Logic -BV1vTe6zzENb_p4-

This is the six video in the propositional logic module for foundations of computer science。

 The topic is normal forms。 These are a very important part of automatically checking whether formulas are satisifiable or valid。

 So I will introduce the general idea and then define three different types of normal forms and work through some examples of how one can compute the normal form of a formula。

 Then I'll conclude with some discussion about how much work it is to do this in general。

 and we'll look at a particularly bad case in which it takes exponential time。By the way。

 I want to give credit for a lot of the material in this presentation to a slide set by Carlos Almeda called validityity checking。

 I've used this in addition to the references to Benari。 There's a link to it in the next slide。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_1.png)

Okay， so we'll start with a definition of normal forms in general。

 This is something you actually do not usually see。

 Typically people give definitions of particular normal forms。

 And even though there are lots of normal forms that appear throughout logic and math。

 There' is not really an official criteria that is established for all of them as far as I'm aware。

 but they do all have certain things in common。 So this definition is my attempt to say generally what a normal form is in logic。

 and I'm aggregating some ideas from a couple of sources， including that nice slide set I mentioned。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_3.png)

So if F represents the set of all well formed formulae and propositional logic。

 a normal form is a subset of F with some restricted grammar， right， In other words。

 it has a special shape in which only certain operators and expressions are allowed。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_5.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_6.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_7.png)

And for every formula A from our big set of possible formulas。

 theres some corresponding a prime where a prime is a formula in normal form。

 and either its equivalent to a or its equisisfiable with a。

 We'll discuss equi satisfiability a bit later on。 But the quick loss is that it means a is satisifiable。

 if and only if a prime is satisfiable。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_9.png)

Finally， there's some process for computing a prime from A。

 or you can think of it as transforming A into a prime， and this is called a normalization procedure。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_11.png)

Before we get into specific normal forms， it is helpful to define one additional term called a literal。

 A literal in logic refers to some atom or the negation of an atom。

 So either an atomic proposition or an atomic proposition with a not symbol in front of it。

 You can refer to a specific literal with a variable。 And here we're using L。

 And we also have a definition of the opposite of a literal written， negative L。

 And this is just the negation of whatever L is。 So if L is P， then its opposite is not P。

 And if L is not P， then its opposite is P。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_13.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_14.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_15.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_16.png)

And if you match up any literal with its opposite， this is called the complementaryary pair of literals。

Now， sometimes when people first see this definition。

 it's not obvious what we're getting out of this。 You might wonder why don't we just write P or not P。

 Why bother defining this extra thing。 The answer is that you could do that。

 But what we're doing is just creating a tiny abstraction layer that will make our later definitions a little more tidy。

 So we don't have to worry about whether some atom。 we're talking about is negated or not。 Anyway。

 hopefully this will be more clear as we go on。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_18.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_19.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_20.png)

Now， for our first actual normal form， we will start with negation normal form。

A formula A is considered to be in negation normal form。 if and only if two things are true。 First。

 only the operators and or and not are allowed to appear in the formula A。 Second。

 the not operator can only be applied directly to atoms。 There is no negating larger expressions。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_22.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_23.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_24.png)

An equivalent way of saying this is that a formula is in negation， normal form or N N F。

 If it is composed of literals， Cons， Disjunctions and conjunctions。

 I notice this is a place where we are getting something out of our definition of a literal because it already includes the idea that the knot operator might be applied to an atom。

 And we're saying here that this is the only case where the knot operator is allowed。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_26.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_27.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_28.png)

So that is what negation normal form means， and the next thing is how do we get some。

 how do we go from some arbitrary formula to a formula in N NF。

 The good news is this is always possible， So that's what we're saying here for any A that is a formula there is always another formula B。

 such that it is equivalent to A and it is in negation normal form。😊。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_30.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_31.png)

So we call this the negation normal form of a。 The way that we know B exists is that we have an algorithm that tells you how to produce it from any A。

 This is called the normalization procedure。 and the basic process is just to repeatedly replace any sub formulas in a that are not allowed with sub formulas that we want using the following table of equivalences。

 Now， this assumes you have already eliminated operators like the projection and the exclusive or。

 but it is not do hard to do this。 You can do it using the equivalences back on slide 30。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_33.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_34.png)

If you happen to be using Nand and nor operators in your formulas， you need to replace them， too。

 But again， this is straightforward， and it follows from their definitions。 In any case。

 once you have done that， this little table of equivalences will get you the rest of the way。

 you just replace all the implication symbols with the equivalent expression not a or B。

 And you use de Morgan's laws to move negation symbols inward wherever they are applied to expressions。

 And， of course， you can always eliminate double negations whenever they show up。

 So a nice thing about this procedure that is worth pointing out。

 is that the time it takes grows linearly with the length of the formula。 So that is not too bad。

 Our next normal form to discuss is conjunctionjunctive normal form。 So in this case。

 if a is some formula， we say it is in conjunctionjunctive normal form。

 if and only if it can be expressed as a big conjunction of big disjunctions of literals where。😊。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_36.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_37.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_38.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_39.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_40.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_41.png)

Our term L sub I J refers to some literal。 I will come back to this expression and break it down in a moment。

 But first， in case it is helpful to hear another version of that and equivalent definition is that formula A is in conjunctionjunctive normal form。

 if and only if a is a conjunction of disjunctions of literals。 Okay。

 so just to make sure the notation is clear here。 The big conjunction symbol and big disjunction symbol work like generalized sum and product notation。

 They work the same way as if we're expressing the products of sums of some terms where they range over various indices。

 I and J。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_43.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_44.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_45.png)

In other words， we can expand this big V out to the disjunction of J different literals， for example。

 L sub 1 or L sub 2 or dot dot dot up to L sub J。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_47.png)

And then we do the same thing to expand the big wedge out to a conjunction of eye different expressions。

And we can add the subscript of the expression to the individual literals if we want to have a unique index for everything。

 so this would be 1，1，12 up to 1 j， and the next would be 2，1，22， up to 2 J， etc ceter。

 until we get all the way to I1， I2， all the way up to Ij。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_49.png)

So that's what this expression expands to。 and hopefully it is clear that this just means the same thing as some conjunction of disjunctions of literals。

 some conjunction， all this of disjunctions of the literals。

 The only thing I think might be a little confusing about the way we've expressed this is that we do not actually require each of these expressions to have the same number of literals in them。

 the number can vary from expression to expression。 So in the first one J might be5。

 there might be only five literals in that one second one might be 10 etc。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_51.png)

I'm spending a little bit of extra time writing this all out because I'm not sure whether everyone is seen this big wedge or big V notation。

 but once you're familiar with it， I think it's a nice。

 compactact way of saying what we're trying to say。 Also。

 I think you'll quickly get a sense of what is conjunctive normal form and what is not after you've seen a few examples。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_53.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_54.png)

Now， just to add two more useful terms， the constant formula false written here as the bottom symbol is considered the empty disjunction。

 In this context， we think of it as a disjunction that has no literals in it at all。

 We'll come back to this later to say more about it and why that is the case。 But for now。

 just keep in mind that its something that exists。 And then finally。

 the inner disjunctions in this expression are called clauses。 So putting that together。

 if I say I have an empty clause that means one of my disjunctions is actually a contradiction。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_56.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_57.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_58.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_59.png)

Now， again， having given you the definition of conjunctive normal form。

 the next thing to do is explain the normalization procedure。 So again。

 we can do this for any formula in propositional logic and the procedure is as follows。 First。

 you compute the negation normal form。 You already know how to do that。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_61.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_62.png)

Second， we'll refer again to a table of equivalences that you can use to repeatedly replace sub formulas that are not in the right form with ones that are the first set of equivalences you need are the ones that express the distributive laws here。

Then after that， we can simplify any conjunctions with contradictions by replacing them with a constant false。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_64.png)

Likewise， we can simplify any disjunctions with contradictions by simply dropping the contradictions。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_66.png)

And then we have analogous implications that we can do with a constant true whenever it appears in conjunctions or disjunctions。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_68.png)

Now， notice that the last four rows of this table are super easy and straightforward。

 The only real work that you're doing after you've gotten the formula to negation normal form is just repeatedly applying the distributive laws。

 This can sometimes be a bit complicated， but the rest of the substitutions are really just included here for completeness。

 They are things you probably do not have to look up in a table to make this a bit more concrete。

 I'll walk through an example soon in which we start with a formula。

 change it to negation normal form and then change it again all the way to conjunctive normal form。

First， though， I want to also mention another normal form。 and this is disjunctive normal form。

 It is the duall of conjunctive normal form， meaning that instead of a conjunction of disjunctions。

 we say a formula A is in disjunctive normal form， if and only if it can be expressed as a big disjunction of conjunctions of literals。

Clearly， this definition is very similar to the definition of conjunctionjunctive normal form。

 but just with the order of the symbols reversed。 and we can describe it without writing it in symbols。

 but just saying that it is a disjunction of conjunctionctions of literals。

 We're just going to be focusing on conjunctionjunctive normal form。

 but to some extent that's just an arbitrary choice。

 it would be possible to use DNF instead if we wanted to， and it really would be very similar。 Okay。

 so now， as promised， I'll work through an example where we start with an arbitrary formula and convert it to conjunctive normal form。

 We'll start with this formula A， which is P implies Q。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_70.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_71.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_72.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_73.png)

P implies P。 So at first， this has only implication symbols in it。

 and we're going to need to get rid of all of those。

The first thing that we'll do following our normalization procedure is find the negation normal form of the formula A。

 we start out by just repeatedly applying the equivalentence we need to eliminate all of the implication operators。

 And that is A implies B is equivalent to not A or B。 The first time we use it。

 We're considering everything in this parentheses here to the R A。

 And the B is just our P on the other side of the implication symbol。

And so the not a is just this whole expression negated， and the B is， again。

 the P on the other side of our or symbol。 Next， we do the same thing with the inner expression。

 The part in parentheses is， again， the A。 And so we have a implies B。And therefore。

 this first part of the expression just becomes negated。The second part stays the same。

 and our implication becomes an or symbol。 Then the last time we just have P implies Q by itself。

 So use the same rule again to replace that with not P or Q。 Now。

 all of our implication operators are eliminated。 So what we have left to do is move the negation signs inward。

 So they are applied only to literals。We can do that using de Morganorgan's Law。

 so we distribute the neation and flip the center operator， so our not P becomes P。

 our or becomes and and our Q becomes not Q。Then we go through the same process again with this outer negation symbol。

 we first apply it to this whole expression and then also to this P。

 So we get the whole first expression negated。And our P becomes not P， and our or becomes an and。

 that gets us to the next line。 And then finally， one more application completes the procedure。

 We bring our knot symbol into this P。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_75.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_76.png)

And the not Q and our P becomes not P R not  Q becomes  Q and R and becomes an or。

 So now we have a formula in negation normal form。 And from there。

 it is not very far to get to our conjunctive normal form。

 We just have to use the distributed property expressed by the equivalentence A and B or C is equivalent to A or C and B or C。

 And you have to recognize that this expression we're working with has the same structure as the equivalentence we're applying。

 It has a conjunction in parentheses that matches our A and B。

 And a disjunction that matches up with the C。 So that means we can distribute the P using this rule and we end up with not P or Q or B and not P or P。

 And if we went one step further， we would see that this turns out to be autotology。

 It is true and true So the whole thing is equivalent to the constant formula true。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_78.png)

All right。At this point， we've said what conjunctive normal form is。

 We've said every formula has a C And F equivalent formula。

 and we also have a normalization procedure that shows you how to derive it。

 So the next natural question to ask is， how long does this take。

We know that it only takes a linear time to get to the negation normal form。

 So how much more time to get from there to the conjunctive normal form。 Unfortunately。

 as you can guess from the title of this slide， this is the bad news。 in the worst case。

 the transformation can take exponential time。 And if something takes exponential time to do。

 that generally means we really can't do it， except for a very， very small cases。 On the other hand。

 not every case has the worst case behavior。 So we really want to know a little bit more about when this procedure exhibits its bad behavior and what is causing it。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_80.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_81.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_82.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_83.png)

The summary is that when we apply the distributed property。

 we end up making a complete copy of part of the formula。 So remember。

 the equivalents we're using is some variation of A and B or C is equivalent to A and C or B and C。

 So notice we started with 1 C。 and we ended up with 2。If it happens that we have to keep doing this。

 our formula length can roughly double each time。 And therefore。

 the CF of a can be exponentially larger than a。 Again， this doesn't happen every time。

 So we just want to know when it does happen。 So here is an example。 So consider the formula。

 P1 and Q1 or P2 and or you， et cetera up to P N and Q N。 In other words。

 this is a big disjunction of N different conjunctions。

 each of which has two variables when we go to apply the distributive law of this。

 We end up copying the whole right side of the formula in the first step。 Remember。

 this is our A and B， And this whole thing is our C。 And actually it's not just the first step。

 something similar happens at every step。 So what we end up with is this giant formula in which every clause has one literal from each of our original N clauses。

 So each。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_85.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_86.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_87.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_88.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_89.png)

Cuse has either a P1 or a Q1， and then a P2 or a Q2， et cetera all the way up to n。 And in fact。

 we end up with a clause for every possible selection。

 So since we have two choices for each of n different slots， we end up with2 to the N clauses。

 Now we started with n clauses each with two literals。 So two times n literals。

 Now we're ending up with two to the n clauses each with n literals。 And if that happens。

 obviously this is going to cause some problems。

![](img/9f2a53abda4cf05b71c9184ee46f04ca_91.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_92.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_93.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_94.png)

Luckily， there are some ways of getting around this problem。

 They are a little more involved than what we've done so far。

 and we're not going to go too much further with this in this class。

 but I will leave you with a basic strategy for escaping this exponential worst case behavior。

 which involves another version of C NF called definitional C NF。

 The idea is that we give up on equivalent formulas。

 And instead we produce equi satisfiable formulas。 I said earlier in the video that we would talk about equi satisfiability。

 So here's the definition， a formulas A and a prime are equisisfiable。

 if and only if a is satisifiable exactly when a prime is satisfiable。 So that's it。😊。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_96.png)

Now， the basic idea of definitional CF is that before we compute the CF， we do some preparation。

 We define new propositional variables， and we replace our problematic sub formulas with these new variables to get rid of the worst case scenarios we were trying to avoid。

 Then we have to add some statements that relate the new variables to the formulas we replaced。

 And the purpose of these is to guarantee that our new formula is satisfiable if and only if the previous formula was satisfiable。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_98.png)

![](img/9f2a53abda4cf05b71c9184ee46f04ca_99.png)

And then finally， we compute the CNF of this new formula。So this works。

 But the cost of doing it is that we have a reduced ability to draw conclusions about the formula that we actually started with。

 Usually， the goal of computing a CF is to try to automatically determine whether the formula is satisifiable or valid。

 But in this case， we have to give up on one of these。

 We won't be able to determine whether the formula is valid。

 We can still say whether it is satisfiable， though。

 So there are cases where that is definitely helpful。😊，Okay。

 so this is as far as we're going to go with normal forms。

 we'll come back to these when we actually look at algorithms for automatically determining whether a formula is valid and you'll see then how this fits into the overall procedure。



![](img/9f2a53abda4cf05b71c9184ee46f04ca_101.png)