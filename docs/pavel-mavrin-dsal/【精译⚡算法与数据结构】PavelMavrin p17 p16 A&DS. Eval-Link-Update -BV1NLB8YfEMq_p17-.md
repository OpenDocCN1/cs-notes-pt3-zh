# 【精译⚡算法与数据结构】PavelMavrin p17 p16 A&DS. Eval-Link-Update -BV1NLB8YfEMq_p17-

，🎼嘟嘟嘟嘟嘟嘟。🎼The。So today we discuss another work by Robert John。

 it's called Appplication of PEth compressionpression on B trees。

best skills we discuss is another data structure， which is worked something like we discussed like the union find state structure we discussed in previous lecture it's usually called union find but in this paper you call it something。



![](img/52c17ed77009a3232b54299045c9b17b_1.png)

![](img/52c17ed77009a3232b54299045c9b17b_2.png)

Evol link up data structure。

![](img/52c17ed77009a3232b54299045c9b17b_4.png)

![](img/52c17ed77009a3232b54299045c9b17b_5.png)

嗯。So it's called like this in this paper， but sometimes it is called。

 I read it in some another paper's context so justin queue up。



![](img/52c17ed77009a3232b54299045c9b17b_7.png)

![](img/52c17ed77009a3232b54299045c9b17b_8.png)

![](img/52c17ed77009a3232b54299045c9b17b_9.png)

![](img/52c17ed77009a3232b54299045c9b17b_10.png)

嗯。Change that oh we have， sorry my character off。Let's change the title。



![](img/52c17ed77009a3232b54299045c9b17b_12.png)

Goodoood point。

![](img/52c17ed77009a3232b54299045c9b17b_14.png)

Let's go。So what is this data structure， data structure works like this？Like in previous lecture。

 we have some forest of trees。

![](img/52c17ed77009a3232b54299045c9b17b_16.png)

好吸心。Something like that。

![](img/52c17ed77009a3232b54299045c9b17b_18.png)

哦。So we have some forests。

![](img/52c17ed77009a3232b54299045c9b17b_20.png)

Some forests。Some trees， trees are border so。

![](img/52c17ed77009a3232b54299045c9b17b_22.png)

Something like that。

![](img/52c17ed77009a3232b54299045c9b17b_24.png)

嗯，6是多开。白什咩。

![](img/52c17ed77009a3232b54299045c9b17b_26.png)

So we'll have some direct forms。So each tree have a root。



![](img/52c17ed77009a3232b54299045c9b17b_28.png)

These are rope。

![](img/52c17ed77009a3232b54299045c9b17b_30.png)

Yeah， and each element belongs to exactly one tree。Good。

And now we have operations each node also contains some value so in each node there is some value。

 this value is called the label in this paper， so I'll also call it label so each node contains some label。



![](img/52c17ed77009a3232b54299045c9b17b_32.png)

![](img/52c17ed77009a3232b54299045c9b17b_33.png)

![](img/52c17ed77009a3232b54299045c9b17b_34.png)

![](img/52c17ed77009a3232b54299045c9b17b_35.png)

Thanksice。Now what we want to do， we want to able to perform free operations。

 basically we want to involve link and update operations， we need free operations。嗯。Let's go。



![](img/52c17ed77009a3232b54299045c9b17b_37.png)

What operations do you need， Trust separation is link。 So Li link is basically。



![](img/52c17ed77009a3232b54299045c9b17b_39.png)

And which direction they do it and I just want to。Do it in the same direction as in this article basically。



![](img/52c17ed77009a3232b54299045c9b17b_41.png)

Makes the parent of the open。

![](img/52c17ed77009a3232b54299045c9b17b_43.png)

So this separation just makes vertex V， the parent of vertex W So we have some。



![](img/52c17ed77009a3232b54299045c9b17b_45.png)

Some tree with a root of V and another tree with a root of W young。

And this separation basically just makes this V。The parent of that。



![](img/52c17ed77009a3232b54299045c9b17b_47.png)

さ0。So this is basically link operation again again。

 it is works something like we did in the previous lecture when we make union operation Yeah like when we make union of two trees。

 we link one tree to another tree， but here we can change the order So we always want so we can swap these arguments。

 we always want this W B， the sound of this the。😊，No。Evaporation。In e evaluation。

 we want to calculateulate some sum on the path from vertex。From what to screen。

Let's look on the path from Vic speed to the root of the train。



![](img/52c17ed77009a3232b54299045c9b17b_49.png)

Or6。And that some。So this is the root of history。

![](img/52c17ed77009a3232b54299045c9b17b_51.png)

We want to take this path。And calculate some function in this path。Let's say we have。

 let's in the right pencil。

![](img/52c17ed77009a3232b54299045c9b17b_53.png)

let's scroll them something like。A0， a1， a2 and so on is key。

 So we want to calculate something like a0， something A1， something a2， something and so on。

 something a key。

![](img/52c17ed77009a3232b54299045c9b17b_55.png)

![](img/52c17ed77009a3232b54299045c9b17b_56.png)

呃。So this is some abstract operation。So this is some binary correctionation。嗯哼。

What properties you have from impression by now the only properties you want from the integration is to be associated so this is some associate associated very different difficult。



![](img/52c17ed77009a3232b54299045c9b17b_58.png)

Associative， right？This is Sam's As operation。A search means you can change the order of expression de。

 so if you have some x， something Y， something Z。You can calculate it like this or you can calculate it。



![](img/52c17ed77009a3232b54299045c9b17b_60.png)

Like this。 So a result will be the same。Oh， let's。Quite common property for a different operation。

 For example， you have for some operation for。嗯。Minimum maximum。

Some other operationss I know greatest is common divisor and so on if you watched the lesson about segmentary over。

Yeah。We had about sounds like that， we have some abstract creation。

 and we needed to be assoative to be able to perform the separations。That'错。

And final operations update。

![](img/52c17ed77009a3232b54299045c9b17b_62.png)

。嗯。And update， we'll just modify the label of the vertex R， so vertex R must be the root。

And this separation makes the point， it just update the label of the verex power。Oh。



![](img/52c17ed77009a3232b54299045c9b17b_64.png)

Yeah。Like this。

![](img/52c17ed77009a3232b54299045c9b17b_66.png)

We just applies this separation with this argument to this label。You can watch the pre on YouTube。

 The link is。Just below in the description of this now。嗯。不'错。That's all。Okay。

 is it clear by now what we want to do， we want to make the form of the destruction。

 we want some elements。Be urbanized as some trees。Each element belongs to exactly one thing。

And we want to perform these free operations， first operation will combine two trees into one big。

 so we take this vertex and just link it to this vertex， so they became one victory。Second is e。

 we just calculate the sum on this path， sum using this binary operation。

 so we have some binary reparation and we use this binary repar to calculate sum on this path。

Some of labels， yeah， so we have labels in each verex。And we calculate some of these labels。Next。

And finally， update just update the label of the roots node so we take the root of the tree and we may update the label in the root。

Mh哼m嗯哼。😊，Is it clear by now。

![](img/52c17ed77009a3232b54299045c9b17b_68.png)

This should be quite。C部没了。第一个。Now， what we'll do， we will try to。嗯。Baicallys in the next semester。

 we'll talk about link cut and obviously you can do all the separations using link cut。

In link countries， you can do all the separations in loggan time。MIf you're not。

If you don't know what is link country we'll discuss it in next semester， it will be fine， but just。

Here we will try to do it faster than in loggan time。

 so we'll try to make the separations actually faster than in logan time and the reason we will do it is because we don't have cuts in link cut trees you can link two trees and you can cut trees you can like merge to trees into one and you can like split three into two separate trees here we only need to link these trees。

So we'll be able to the it in loggenile。Let's go。그거 그거。那哼。😊。



![](img/52c17ed77009a3232b54299045c9b17b_70.png)

Here's sub direction。How can we first of we all try to apply the pathth compression。

 it is the same technique we discussed in previous lecture。🎼Sp compression。

How to apply by compression to make these functions pretty simple。 So well we call E above functions。

 So you call a。Of sound green。 So we have these products be。And you have some。So this is all。😔，Yeah。

 it's pretty hard to Google it， that's true。You might Google the article the main paper source application compressions。

Maybe， maybe it's Google that is eventually the income date， I didn't try it， but。有没出。

It's not very popular structure。嗯。哦。That's why we covered this lecture in Bos because。

Who else will tell you about these data structures？You算病。Okay。So we call evapo from this node V。

So when we call evaporation， we follow this path and calculate the function。

Like we did in union fight。And then。We will make link。

 We will make this V the sum of of this vertox R。 So after we find this sum。

We will connect this suite directly to this verortex R。

 and we basically connect all vertices on this path to this vertex R。啊。How will do it。

 We will do it by。Modifying the labels。 So now they have labels， let's say a 0， a1， a2， a3。

It faithful。So after we applied PE compression， we'll have some like。

 we have vertex R with label a form， and we have this is vertex V。Oh。And these are wonderful。



![](img/52c17ed77009a3232b54299045c9b17b_72.png)

And will change labels in such way that this sum will stay the same for example for this vertex。

 sum must be a3 plus S A4 so we just。Leave a3 here for this vertex， sum must be a2 plus a3 plus a4。

 So we make it a2 plus a3。So now when we try to calculate sum for this node。

 here it is some of these three and here it is again some of these three so the result for this node will stay the same。

And heroes make。Take one， take two。A3， and for this vertex， it will be a 0， A1， a2。A会。嗯哼。



![](img/52c17ed77009a3232b54299045c9b17b_74.png)

That's all。So what you do when you do breath compression， you follow this path。

Culate the result and then connect all these nodes on the spread directly to vertex R。

And when you find the labels in such way that the sum is the same as before。哼。😮。

Is it clear how to calculate this sum in linear time？It's quiteite easy。

 You just calculate this sum from right to left。 So first you calculate this。

 then I calculate this by a2 plus this， then this will be a1 plus this。

 this will be a0 plus this and so on so you just calculate them from right to left。

And in linear time， you can calculate all these results。Connect them directly to all。No。

 update operation is fairly easy。😡，When you make update date operation。

 you just update the value in the route。Thiss。But by now， it's very easy。We update on these route。😡。

We update where only in the route。We never update， so we can update this ver if we could update a middle notes。

 then it will be difficult。But we update only the root node。Yeah。And the route is the same。

 will never change this route。So after we apply this path compression。

 the road is the same so we can change this route if we change the road。

 we will change all the various in the same way and so on。Okay。That's the first part。

 we're going to b with compression。Now， let's remember the previous lecture。

 if we apply path compression。When we go， something like that。Then what will be the time complexity？

Well the time complexity here will be if this tree is not balanced。

Then time complexity will be something like that。We approved this in the previous lecture。

it's about logan， but not exactly。It's log n when you have small M， if you have big M。

 this is constant If M is between n and n n squared， it's something in between。嗯。E3 is balanced。

They are dream。The time complexity will be the go of alalheimma。Yep。

So these two were just proof on the previous lecture， right？If you didn't get the proof。

 not it's not that important， let's just。You can just believe in this lecture then these time time complexities are correct the proof was kind of complicated。

 we will not use that proof we will just say that this proof is correct okay so in this lecture we'll just believe then if three is non balance we'll have this time complexity if three is balanced。

 we'll have this time complexity。Okay。So in this data structure， no one。

Promise us that the tree will be balanced right so if you make some arbitrary links the tree will maybe not not balanced in the entry right。

 so if you just make these links， you may end up with some nonbal trees in that。

So if you just apply pathth compression to theses， you will have this time complexity complexity。

That's always not bad right so this time complexity is still about logan。

 so if you just need some first data structure。Some something about loggan time you can just make these operations very simple and again how to make link operation。

 whether you make link operation， you just make this V parent of it so here just make。

Pent of w equal to being here you just update this label in this way and when you call evolveval you just follow this like path compression。

 that's all like 10 li of code， very simple。So if you just want some pretty fast data structure。

 you may just implement it。Very simple vibrations applied with compression。

And you have this time complexity。嗯。But if everything was that simple， we will not have this lecture。

😊，What we want to do is to have this time complexity。Okay。好。

Unfortunately it's not always possible we will be able to achieve this term complexity for some specific operations。

 so for some operations we will have this timem complexity and also for some special cases。豹子搞。

Can there error is something， is everything clear by now？嗯。よす。Just。Just write something in the chat。

Each 30 seconds， okay。Just。Just to keep me notify that you are all right， okay？By now。

 anything must be pretty simple。We have very simple operationss， apply plate of compression。

 puff compression is simple。😊，It's all quite simple bit。Let's try to achieve this angle complexity。

オッケーここ。The first special case， when we can easily achieve this time complexity is when you have some special integration。

 which have some。Inverse inverse values for each failure。If you have for let if for each x。

 there exists some x minus1， such that。If you have x and connected to x minus1 will be equal to0。

And0 is some billion。0 is some values that for each x， if you apply。Z x equal have。嗯哼。是よ。

However this is useful， I'll discuss some algorithms probably when you can use this。

Oh maybe I won not discuss them today。So there are a lot of different implications of this algorithm in some strange of these data structure。

 in some strange algorithms， like you can use it when you build the minimal spending tree。

When you build theminator stream。In some maximum close algorithm。あ、あの。

Do they show some applicationsifications？哎9这头地图。I know there should be some other applications。長。

So in some algorithms， you have some trees and you want to calculate some functions on these trees。

 we'll discuss such algorithms in the next semesters。

Maybe in the next some or some something will discuss。In the third semester。

 how in the fourth semester。So at some point， we will use these structures like this。

What I was talking about yeah so you have some operation and for each element there is an endorse variable so for each element you have endorse element so that this sum equal to0 simplest case is。

 for example， if you have some if。For example。If deation is。B。Then x1 is simply equal to minus x。そうか。

definitionSo if you have numbers and you want to calculate sum on the path。

 so when you're going to calculate sum on the path。You want。Then the inverse value is just minus x。

Mm。😊，So we have x plus minus x equal to zero。こ。Also， so how we will achieve this time complexity。

 we will achieve this time complexity by building balance trees so we have。We have power trees。

 cover this drill tree。The stream may be not balanced。我看一下。Let's grab some purchasees。嗯。Like， please。

It is not balanced。We will build another tree， what's called virtual tree。

This virtual tree will have all the same notes as a real train。我 have with。Oh。嗯。我 someone。W。

 stuff like。It will these three will be balancedd。So these tree will be balanced and all evolves will give the same results。

Oh。あ。Yeah。Yeah。啊。We only compare in the balances street works。

Now we can apply PEth compression to any tree， PEth compression is very simple method that you can apply it to any tree。

 it does not require the tree to be balanced， but if tree is not balanced。

 then you will have least time complexity。And if the trees balanced， will have this complexity。

 so if we just apply with compression to this tree。

We will have something like that and if we apply compression to this tree。

 we will have this temporalplex and that's what we need。Let's go。Now for example。

 let's build this for this stream， if you have， for example， if separation is sum。

 so if this separation is plus。And you have some numbers here。1。3e5。父。Let's put some labels here。

 so here will be five for this vertex， it should be free for this vertex。

 the sum should be 1 plus3 plus 5。Its form。And here it should be seven， and here should be two。そ。

If you look on how evaluations calculated in this tree， all results are the same as in this tree。

So we can use this tree instead of this string。And we will do it in such way that this tree will be balanced。

That's the plan。 So we'll， we'll kind of make some。嗯，好 cold。Something certainly like equal tree。

 so we have our tree anyway we almost something some another tree。

 which is in some case equal to our tree in case of this operation so this operation will give the same result。

But these tree will be built to be balanced。And when this tree will be balanced。

 we will apply path compression to these tree and will achieve the good time complexity。Yeah。

 at some point， we will touch the reduction。一。And in some cases， we will try not to touch the root。

 but actually if in this case rule we will touch the root now let's go。So if we have brush like this。

 so we have some indoor elements for each。啊。How can we build the tree balanced？

We were built in very similar way in a very simple way， so imagine you have some ratio link。UW。

So you have this not B。You have some tree here， this not to W。

You have some treaty and you want to link this w to this screen。

Let's see how the evaluation will change。For all nodes of history tree。

 so what will happen to the results of eva？So for these three。

 a result of evaluation is the same as before。So here， if you look on any address here， yeah。

After we make this link， this result is the same。 so here is。啊。Hes。The same。And put each rotex here。

Yeah let's，'s， it's too long。 Let's say my。 So let's say E of of。X。Equal to previous e of x。

 So if you have someor steps。Here。So this is the。The previous result of Eval this is the next result of failure。

 so the next result of Val is the same as before if you have some vertex here， see why。

And you calculate evolve from this vertex y， then before you make this link。

 you calculate some on this path， and when you make this link， you can sum on this path。

So this new value of Eval of y will be the old value。Plusus。完毕。What label of freedom？

I'll just put it。Okay。HereYou take label of verx speed。Can apply de separationation。

 so we'll get a new result in this rot。Makes sense。那。啊。Let's remember how we how we did。

We made the tree balance when we make union find structure。

 when we make union data structure union find in previous lecture we try to build the tree balanced by connecting small tree to big tree。

 yeah， so when we connect some。嗯呃。Small tree to big tree like this。 And instead of this。

 we try to do this， we try to make small tree and connect it to big tree。Mmh哼m。😊。

This is how we managed to build the balance tree in the previous lecture。We will try to do the same。

不上。So in this case。If this tree is small and this tree is big。小地服。Size of V is less than size。

Of double here。And then we will try to connect this V to w， so we'll try to reverse this edge。

So if we make。This swim。Son of this double。Then you have the different results。

 so this function will not stay the same because now in this tree。

Evolve function gives the same result， and in this tree。

 the evolve function will include this vertex up here。So we need to fix this。How will fix。These。

Very simple or same。そう。Let's start from this 3W。Yeah well say no yeah is exactly like that so in this3w we want the next the new value of this e be the old result plus vertex v so I will take this vertex v and just apply it to vertex W so this。

Label of vertex W will be。Old label of vertex W。Plus is robotox3。그。So here I make。I play this orby。

Now for this tree， the result of evaluation for each node will be like this。

 so here if you take any node in this tree， then new result of operation Eva will be the old result plus B。

So it is the same as here。Now let's hook on this tree in this tree if we take any vers x。

What is the result now now the result is we go to here， we apply V， then go to here， apply V。

 and then apply apply W and then apply V。And we want it to be the same。So to fix this。

 we will simply apply the inverse separations of this。

 so we go to 2v then to here and we want to have a reverse of this。So here we will apply。아。

We need to do it in correct order， so apply W then V。So to reverse this。

 we need to apply v minus1 and then w minus1， right？我 right。So willll be old。Label of free。嗯。

Then apply V minus1， then apply W minus1。It makes sense。So when we follow this path。

 we get this sum plus this element and we want to like neglect this element so we make this change to this node to neglect this change of this node。

 so this node contains value of this。Yeah， it's not's not this label。The change here I have level。

 here I have read input。Let's come labels everywhere。Yes。Like this。There just too many。

Too many texts in this whiteboard my whiteboard is small away。

 I'll I'll usually skip this L just say。That I apply vertex v because it's kind of what you do when when you apply deperation to labels。

 so when I print something like this， I mean the label of the vertex okay。

It's just for simplicityimistic because because my board is small。Makes sense。So你又 label分。哎。Yes。

 I apply LB to L this。So you can make  zero here， so it is than just label of w minus1。Makes sense。

Okay。Let's， let's have some examples。 So for example， you have some tree。

 you have let's click vertex with label free in the root here。And here we have vertex2。

 and in another tree， you have vertex let's say4， and here we have5 and  one。

So if you have something like this， you want to connect this。

And this tree is big and this tree is small。 So you want to change the direction of this edge。

 So you put this。哦。Here。And this and this。These three。And now you can apply this separation。

 so a new label of w will be sum of these labels， so it will be7。

And your label of these will be minus1。でへ？So yet in this three。

 the results of all operations is the same if you take some if you take this note。Here the sum is5。

You should take the signal note here。The sum of this path is also5。So tree is different。

 but the result of operation is the same。嗯哼。😊，Let's all。You know。

If we always connect small tree to big tree， the final tree will be balanced。Again。

 like we discussed in previous lecture， and when we apply PE compression to balance3。

 we will have the indoorverse a command tank complexity。9。All， I lost half of my son， that's fine。へへ。

😊，Let's。Not very popular the topic。Fine。😊，Go next， let's go next。Again you。Youre too quiet again。

 just say something。嗯。Now that's the first the first special case when you can achieve the time indoor Acrament time complexity when this function is the such that you have in element information each。

But that's not very usual case。😡，D are a lot of different binary reparations which don't have the indoor operation for example。

 one of the most popular operation is minimum or maximum。Let's。Can never era this？

If we do update on this show。to make a here， we changed the root of the tree。But how to make updates。

You find this node R。Which was so in the real training。

This vertex are was the root of the train in your virtual train。This node R may be not therapeutic。

 so it may be under here。Yeah， the road's changed。What you can do。

 what you want to do when you apply update operation to the root。

 you will change the result of operation to all three so after after you make update again the new result。

Of operation will be the old result。We have X。For each。Will be the open result plus x。

So if we want to make update， we may find the root of this tree。We take this verts instead。嗯，然。儿2。

We take this vertex。And apply a date to this route。It will give you the same result。

So if you just take this rope。And applied。嗯。Le separation to the root。

The result will be the same so for if you take any verts。If you take any vertex B。Here in here。

For this vertex， we result will be changed by this x and for this vertex。

 we result be changed by this x。So a result will be the same。So when you need to update。

 update somewhere value in the route。You take loose。Vertex R find the root of this tree。

 again by pathth compression， find this actual root， this virtual root here。

The route of in this virtual trim and apply this update to this root element。

And it will give you the same result as applying these extras。哦可 okay okay okay okay okay。아。Okay。

 that was a good question， that was a good question。Yes， we don't need to maintain the realty。

 Yes in all these other we will never need to maintain the realty。

We always will maintain all the virtual tree and we just make sure that our virtual tree is always the same as the real tree。

 so we don't need to maintain this real tree usually we just maintain this virtual tree and maintain the property of the results in this virtual tree is the same as the results in this real tree。

ok。Let's go next。Let's move next。Let's move to the maximum。啊。For maximum。

 it's a little bit more complicated。啊。So why can't we apply the same techniques here because we can change this to this？

When you apply maximum， you have this。One in this。So you want to make a link。So you have Flake。

one here and two here，So you want to make this link。You can have some some trees here。

 some some big tree here。 You can just reverse this edge。

Because you want a result for this vertex B equal to2 and the result for this vertex equal to2。

 So if you just change the。A direction of this link。So this is x。 this is y。 Well，'s V。咩人没少了。嗯。아。

Sorry this is the first time in this lecture。This will be doubly this so if you just reverse this edge。

You want a result for this vertex be equal to1， and for this vertex results should be equal to2。

And you obviously cannot do it right， You cant put some values here and here。

 So maximum here is 2 and maximum here is one because this maximum includes this vertex。

 so this maximum will be greater than this maximum。So we will apply。Different。Alreadio。ho。Let's go。

Let's start some simple properties， so let's look on some properties of maximum function。

 which will allow us to make first algorithm。Let's see。 So if you have some note， you have some note。

Yeah。哦。And the label is X。Let's look on the path from this node to the root。그。

So let's look at this path。Oh no no，'s much their it not not enough。

We need function that we have some total ordering。啊。

So maximum is defined when you have some total order of rope elements in your group。

 so we will we will use this。Let's see， so imagine you have this ver。Let's look on this map。

First observation。If all vertices on this path， So if all these vertices are less than x less or littles。

And then。What can we do？We can just ignore these ver when we calculate something inside this subject if you take any ver here。

And try to calculate result for this vertex， you can just ignore all these vertices。

Because youll follow this。You follow this path， calculate maximum here。Then you meet the objects x。

And all vers here will be less than x， so when you calculate maximum。

 you can go here and then ignore all this。So you only need this part of this pattern。

That's just a observation。Second observation。Let's have something like this opposite if you have verex X and not all of them are less than x so at some point you meet。

Nortex y。And y is greater than x。We get a greater art。🤧嗯。

And if you move from x to the root and on this path， you meet another vertex。

 which is greater equal than x。X。What can we say about this vertex X？Okay， any ideas， let's。

Let's stop here for a little。What can we do about this value x？当你です。Any ideas？嗯。Oh。

So you missed the beginning Okay。We just started today。诶。Most complicated stuff will we just。

You missed the first part， what we boom。That's too bad。

What we want to do we want to be able to calculate the maximum and the path from the ver to the root。

 that's the current state。We can mo all this up all to why。啊。Yeah。

 we can always apply path compression I want to change this label actually， what I want to do。Yeah。

 we can always apply path compression because it is true。

 we can apply path compression and we make these notes directly away。The more interesting part it is。

The most interesting part that we can actually， we don't need this label X anymore。Yes。

 we can change this x to y actually。So we can change this x to y。And the result will be the same。

Again， if you take any vers in this sub。You follow this path。

 this x will never be the maximum of this path。😡，Because for each path， this y is greater than x。

So this x will never be the maximum on this path。こ。That's all。That's all we need。Hem。

 now what smoked like a lot of them。The algorithm works like this。Again。

 we have a real tree and we want to build some virtual tree which have the same。

How the same results of evolve function。啊。Now it will be a little bit more complicated。

We will transform our tree into some sequence of trees。So we have in real trip。

We have some tree with some rootpower。In our virtual tree。It will be transferred to not one tree。

 but is serious of three。So we'll have this vertex R。And some tree。Here well have another three。

Scor R1。Yes。So each tree in the real tree will be transformed to a series of trees in the balance tree in the virtual tree。

Okay。In this tree this theres is a somewhere we have some something our one is here。

 our2 is here so these trees contain the same set as this one tree。All， these fruit trees。

Contain some vers from this laundrying。그가。好多人。哎。And now we will maintain the following property。

First property。Each of these small trees will be balanced。So all these three are built。

And we will connect them in a short order。 So these labels。In the road wordss。Will be sorted。

 so this label will be less or than this， this。I compare only labels in the root。

 so I have these three roots。Label in this route is greater doesn than label in this route。

 label in this route is greater on this route and so on。Inside these trees。

 there might be some different verse。I don't care about inside of these trees。

Car on only these routes。We have some example， let's have some examples， we have some vers。

 let's say。嗯。啊。What's sync on something like？And they have some values， let's say。我哋。1，5。阿佛。嗯，死吧。

So we can transform them into something like you have vertex A。哦。Here we have verx P。嗯。For example。嗯。

嗯。嗯。嗯。Here in my first vertex C。응 흐 하。What they want。Does let like these， for example。

Is it the same tree， not exactly？So we have this。 let's make this dashed。We have free one。

I have the same labels， no that's boring， you may change the late labels。

 you care only on the results。嗯嗯哼。Oh。This'sけ just。To make it more interesting， let's add F here。

 so we can add F here。嗯。Let's make it like this， we will add F here。And up by seven here。嗯哼嗯哼。

Clear enough。Okay， we have this tree in our real tree， we transformed this into a series of trees。

 so we have three trees one， two in three trees， these roots are sorted。嗯哼。

So this free is less or than this， this4 is less or than this。And this。

A set of trees contains all the elements from this one big3。So we have the same six vertics here。

And the result of gival function is the same， so if you take any。Elements， well have to E。

Calculate result of Eval from here so we follow this path so result will be 7 if you take this E calculate result of Eval you follow this path but result will also be 7 so a result of eval should be the same and the set of verses should be the same。

嗯哼。😊，And each of these three must be balanced。Okay， I lost another half of my viewers。

Anyones still alive？嗯。Okay。Just bring something in chat just。

They'll make it look like something interesting in scrapping。Go， now。That's the plan。

 so we will for each three， we will make something like that。Yes。

 I want the result for this f be equal to 7， so I need to change this label to7 to have the result of e function be equal to 7 yes。

不可以。So labels are different， but the result of evolved function is the same because that's the plan。

Well let's go， so how do you calculate the evolve function， so evolve function is very simple。

So when you calculateate the evil function， E。So you have some vers V。Okay。What you do。

You simply calculate the evolved function as before。

 but you calculate the evolved function not to the root of the tree。

 but only to your local root to the root of your small of the。So you follow the path to the root。

 but only to your local a something like that， so you inside of this tree。Let's make it like this。

So this is the real room， this is your local room。When you calculate E function from this vertex。

 you may follow not the whole path to this root， but only path to your local root。

Because all these vertices are less than Europe。All these notices。Less or equal than R。

So you don't meet them when you calculateva from this vertex。

 you might go only up to this vertex and don't go here。嗯哼。😊，But because of this book。

That so that's how you make the E function， you just follow the breath to your local root。

EachEach this small tree is balanced。So when you apply path compression to this pathth。

 you will have inversea mountainan complexity。Because you only apply path compression to the balance trees。

 each of these trees balance。So when you apply path compression inside this tree。

 you will have indoor acroman complexity。simple everything， I told you， I told you that is simple。啊。

Now let's talk about links we need to talk about links and updates。😡，First， let's talk about updates。

Updates。Link will be fun， yes， not very hard， but kind of fun。Let's first make update。Okay， in this。

In this method， we will not change the root， so this route will be the same in the virtual tree as in the real tree。

So when we make update date， we will change the label of this root node。

What will happen So you have something like that and then you change the label of this root element。

The problem will happen that this。Inequations will be not satisfied anymore。So you have please。

Sequence what's having dashed。Let's have them dished。不。So when you apply update to this verex？嗯哼。

So you have some new label will be old label loss， no maximum maximum in these。Of R and X。

My production is maximum。Yes。Before we apply the inspirationsperation。We have this property。

After we apply the separation， the label will be increased。So when we increase this label。

 this is an equation may be not satisfied。So let's calculate the new label of the root。And then。

Find all the children， actually if the root is changed， then it will be equal to x， right？

So maximum is equal to r or x， so we either not change the root or we change it to x。

 So if it's less than x we will change it to x。 that's what happens。So， if we。

Make it equal to x for simplicity。土。Let's make the label of the root equal to x。Now let's find。

All the elements。Which are less。Ortle not doesn't matter what the。

Let's find all the elements less or equal than x。嗯。Now what can we do again。

 like we discussed before， if you have some element and above。

 you have some element greater than this element， you can change this label to x。

 so we'll find all the rules less or equal than x and change them to x。やます。



![](img/52c17ed77009a3232b54299045c9b17b_76.png)

Okay。😊，We can do it， the result of amount function will be the same， right？And now what we'll do。

 we will merge these two trees into one big tree， so we'll take all these trees and merge them into one big tree。

So we will take all these trees。So we have some small prints。And merge them into one big。

I can without this， we don't want to touch the root only these batteries。

So we take these fruit trees。And merge them into one between with something like that。Oh。嗯哼。😊。

So we take these three trees， notch them into one big tree。And everything else is the same。

So that's the final state。That's how we apply operational。Update。Again。

 we update the value in the root。Then they find all the small roots less than x。

Change their levels to x。Actually， it's not important that you may not change label to x just for simplicity。

Yeah， and then merge these two trees into all these trees into one and when we merge these trees into one big tree。

 we apply the same heuristics we connect small tree to big tree。嗯哼。😊，Yeah。

 we march all this small tree to the big tree。So this three is still balanced。That是 one。Let's see。

Okay。That's all quite simple Again， let's talk here， let's talk about time complexity。

Why did we merge the updated node string into。To make tank too good。

We need to merge this threat because if we don't merge them， each time we apply up。

 we need to find again this not and change these labels again。

We want to be amortized time complexity small， so if we make long operation。

 so we find many roots and change a lot of labels， we want to compensate this time complexity here by decreasing the potential and decreasing the potential is just decreasing the number of trees。

So if we find cagere。If we find K3， then time is K。But。Delta phi will be minus8。

It feeds the number of notess。Number three。嗯 가 가 가 가开门。

So we find this K3 spend K time bound to compensate it in the final time complexityes here。

I want to decrease the potential。So I will merge all these trees into one big tree。

 so total number of trees will be decreased by K management one。This will compensate ten。ふ。It's。

 it's almost all。Now we just need to make links。哦不是。So。过 quite well。Yeah， that's very it click here。

Li。So what's going on when we make link operation， so we want to merge these two trees。

 so we have this verx V。We might double you son of fear。So let like have the sx v。我s。

M use different colors for V and W for。To make it more visual， let's have thepherv。

And it contains some number of trees。Oh。So we have this set of trees and we have another set of trees for Vers Ws。

Thescript is W。Yes。嗯哼。や。えない貝 のォンと どうです？I want to connect this W to this view。

 make this be parent of this W。Updates are constant time amized yeah。Yeah。

 updates these have a constant time， that's right。All term complexities will be called inside evolved section。

Again， like in union find the structure when you make union you have time is constant complexityes here here here we have updates kind of the same you make updated data you have time。

Qustant and complexity yeah。Can be nord or most almost once in the expression Yes。

 each node is northd exactly once， so if this node is merged to another node it became is sum and it forever likeen link cut or liken linkable is in union find like an union find。

When you emerge to trees， they emerge forever。やと。And then you apply path compression， yeah。

Then here you have one big tree。This tree is balanced and you will apply pet compression inside this tree。

So now links， you want to be able to link this W to this again。

That's kind of trickying because you have a lot of trees here， a lot of trees here。

 you can just link them。So what you will do， you will merge something to something。Let's see。

Let's look on the total size of all nodes here。 So let's look on total number of nodes here。

And total number of notess here。Total number in all these small trees。

 So let's look on all nodes in this set of trees and all nodes in this set of trees and look which is smaller so let's look where we have a smallest number of nodes。

There are two possible cases。え。This tree is small， this set of trees is smaller than this set of trees。

 or these set of trees is small。Let's try to solve both of them。For example，衣。

Size of W is less than size。Of size of W is the total size of all these notess。

 So we'll keep track on total size of this notes。 So this size。Is size of W。

 So there's total number of nodes in all these trees， not only in this small chain。

But in all these trees， okay？And the same here and the same here。

So size of V is the total size of all these small trees。

So if this total size is less than this total size。Then we will do the following。

 we will take all notes here。And connect them directly to me。So it will'll take。Noord V。

So here we have the same drink drink。Drink。These are the same。

Now we'll take all these notes and connect them directly to V。ち to。To to to to。中。

One of them is value。Like this。Now， later， we will prove that it will give us the good content complexity。

 okay？Now， what happens if the opposite if this size is greater than this size？嗯。

So if size of W is greater than the size of it。Then we will do kind of the opposite。

 we will take all small trees here。And connect them to the。So again， we take this V。it let's make it。

等 the。We take this V。Take all the nodes in this set of nodes and connect them to this B。

 so we have three。And then take this whole chain and connect this chain directly to Ri。嗯。

Something click。 here we have W and through here。Yes。都没生。那走那最好管。Again， let's see what's going on。

 what's going on， so you want to connect this W to this view。嗯哼。And you won a result of this。

How的 gold。A result of this evolve function should be the same。

So if you call E function from some node from here。

So you need to follow this path to vertex W and then to vertex phi。Here you will do the same。

 you go to the vertex to your local root， you don't need this W and then to vertex v。

 so this vertex v will be added to all pres for all vertics in this set。And for each vertex here。

 the path will be the same sorry for all vertices here， the path is the same for all veres here。

 well add vertex V。The same here for all vertices in this set， we will add vertex v to this pair。

Or all heres here。YeahYes yes。I almost thought， at some point， when you do this。

 you may again break this property。So you need to make the same procedures here。Yes。

 you also need to find all the nodes here which are less than B and apply the same expression as here。

嗯。Okay， again， for all veres here， if you take the path from vertex to the root。

 this V will be added to this path。And for all ver here。

 the path will be the same so you follow the path to your local route and the same。

Each note can be root almost one。Yes， in this big tree， yes。

 the three is also changed almost one year， so if one vertex is not a root anymore when you merge this to trace。

 this w is not a root anymore， so it will stay not root。

Until the end of the algorithm time so if some vertex is stops being the route。

 then it is not route until the end of organ。So the life of is realex。Is like this。 So at some point。

 this vertex was the root of the tree。 So。 So let's see some vertex V。

 So it's that as a root of the tree。 Now， at some point。We merger it to something。

 so this vertex is not a root， but it is local root。Okay。And then at some point we make this merge。

 so this vertex v is not a local route， so it is inside something。あ。

So this is the typical life of a note in this data structure。It start as a root。

Then at some point we merge it。So it became some local route。

And then we merge this tree to some another tree and it became just some internal Goths。啊哼。酷。

This could happen during the linear process when you burn this these trees and when you glue these。

 yes， when you do this， you make all these notes， not local rules。 so now they are not local rules。

 So this is one single balance tree。 So here we have just one single balance string。

 And here we have one single balance tree。嗯哼。So when you make the operation。

 these vertices are not local roots anymore and heroes。W。

That's almost all now we just proof that this three is balanced。没错。This one。

The ammartized time of link is also CSs， ammartized time of link is also constant because when we travel to lot some pathth。

 we also decrease the number of three CS per yes amort time of link is also constant。呀翻落翻落去。

What we forgot to prove， we forgot to prove that the final trees are balanced。嗯。

How to prove that tree are balanced and quite simple。 Well， look， how do we construct these trees。

Let's look on。Here， so when we apply update operation or the symbol。

 when we make the link and combine these trees。When we apply something like that。

 we take the number of。Small trees in this chain and merge them into one using wait。

 so it connects small tree to be trim。Let's hook on these edges， let's call them good edges。

I need more colors。I'm not sure if it's green is is visible。Let's call these edges good edges。Msible。

 quite tough。So let's say these edges are good edges。Right。you cant read this。What is good。

 good edge has a simple， very simple property。If you have a good edge from x to y。

So if this edge is good。诶。Then the size of y is at least twice more than size of x。No。

 let's prove that when we apply de separationation， all these edges are good。No。

 that's quite obvious because when we make this separation， we connect small tree to big tree。

 so even a time we connect small tree to big tree， the total size of this tree is at least twice bigger than the size of this small tree。

So when we connectect all this， all these edges will be good。这 is this this。ね。But that's simple。

 right？Now let's talk about other edges。Not all edges in this data structure are good。For example。

 when you make something like that？So， when you。Then you make this link。

And you want to connect all the trees from this。Set of trees。Do the verex speed。

It may happen then this vertex v actually connects some small trees， So you have some。

So when you do something like that， you might have some vertex v。Wehi have some small tree。

But you have big big big trees Nick here， so these trees are big and this tree is very small。

And when you apply this， W， so so the total size of nodes here is pixelix。You have this W。

 you have one big tree。Again， the total size of W is less than total size of V。

So we make this procedure。嗯哼。But the size of this small tree is greater than the size of this small tree。

 So we may connect this big tree。 So this small tree of W maybe be bigger than this tree of。Maybe。

So it might happen so in this case， we will connect big tree to small tree。Sometimes we do it。嗯。

Did I lost all my oh actually， the number of yearss has actually increased，'s that's strange。

I forgot the word， I forgot the word。미디가在。That's，'s difficult for me。

I know how to pronounce its a medire， right？에。包啦宝宝。바람 빡 똥 빡빡。I will check my背包。Sory。嗯。

Mijo means not quite good， but good enough， sounds selected。

So we will say that we have mediare edge if we have the following property。

If we have two meocre edge，2，2 meocre edge one by one， so if we have。X， then y， then Z。And we have。

The base two meteority。Then if we have two millibars and y by one， then size of。

Is at least twice size。Thanks。And I claim that all edges here are metegri So if you work on these edges。

 they all are mecr so all edges here areidte all edges here。あすみろ。So basically。

 all edges we create on these operations are always good， so if you apply two edges like this。

 you will increase the size of the trademark mode at least twice。Well let's prove this。

 it's clearly not that not that far so what happens if you have situation like this。

 if you have situation like this， it means how can it happen？One sorry。

So how can you have two mediocre edges one to each other？Next to each other are you。

What's something like that soup。You had vertex x， then at some point you merge something to something。

 so this x became the sum of this y。So you have this vertex X。嗯哼。😊，Then at some point。

 you merge this x to s vertex y。 it means that you have。So these vers echo。

Let's look on both of them， it doesn't matter which。

hi which part do like let's let's see with this song in this song you have。啊。Yeah。

 so you have something like why and something something。Then you have something and here you have X。

嗯哼。😊，And then you apply this separation， you apply this separation if size of w is less than size v。

 so if you apply this。You will have x the sum of y， right。As well as all these other all these other。

We just what thisper。And here， size of x。A size of y is greater。Then， size。Ohax。But the。

This size is different size， this is like subsize， this is size of the small tree。

 and this is the size of the off element。你系。This different sizes。Okay， this called subs in this。

Paper was gold。To。嗯。哦。So size is the total size of all elements in the whole set and subsize is size of this small tree。

So when we apply this x， when we link these to two sets。The X became the sum of y。No。

This y should became the sum of Z。How can it be， because at some point we link this set to something which contains graphic set。

So we have that。And something。And we have this， we have Yx。呃，Something， something， something。

 something。And we link them。I want this Y， this X。And this aha I want them a sorry。I need。

 I need this dashed register just right。ど？This age is not dashed。

It's a little bit too complicated like this。So， here we have some trees。And here we have some trees。

Then you apply a link operation， so you link these two trees。

So this X became the sound of y because you apply the expression。

 Yeah well like this x is San is one of these trees， so X became the son of y。

So here x is the sum of white some trees。Now， you have this wife。呃。

It may be a summer from other something。And then again。

 you link this to this and you apply a like this， so this， all these trees became the sum of this as。

So you have a that。That here you have。W。第个还有。有X。护。You。And all these vertices。

Also became the son of this that because you， when you make this link， you take all this。

Trees in this chain and connect them all directly to the。

 so we take all these nodes here and connect them to vertex species。그 갈 없지。Now now let's look here。

 so here we apply this separation because size of y is greater than size of x， so this size。

Is greater than size。Okay。我天。嗯哼。😊，But it doesn't matter， size of Z should be greater than size of y。

 but it doesn't matter。啊。We take this Now let's work on all these small trees When we make the separation。

 all these small trees are now here。So， here。All these small trees。

 so total size of all these small trees are greater than size of x。

And now when we apply the second inporation and make this why the child of that。We take all this。

 so we take this。We take all of these trees。And make them separate sounds of this z so we we connect them when we connect this y to Z。

 we also connect all these trees to that。 So now these trees became here。嗯。

And now when we calculate the subsize of z。We include all these notes。

So here are the subsetsies of that。Is at least twice bigger than subsize of x。No sub size啊。

For x is not better because x is not。그。Subsize the size of small tree and size is the size of the whole set。

 right？That。A little bit。嗯。Diffic difficultか。Let's all。And now here， forgot say。

All these notes are children in this small tree， so here we have this this。Small small tree。

 small tree， this small tree includes all these trees from here。So after second link operation。

 these trees will be merged into one big tree。So for this verex Z。

 total size of this small tree is at least twice bigger than size of this x。嗯哼。😊。

That so that's why if you take two mediocre edges one by one。

 then the size will be increased at least twice。Not because if you make two link corporations。

 you will link all these into one degree。The same thing here。Here if if you apply the separation。

 it means that the size of this W is greater than size of thisV。

And when you apply the second link operation， you will merge all these small trees into one。

 so again you can do it by yourself， it's just the same。不'错。And so finally。Simple observation。

 if all edges in your tree are either good or mediocre， then your tree is balanced。

If for good edges it's obvious， yeah， if you have good edges。

 then you have balance trees right because time each time the size is increased twice。Yeah。

For meoc it's kind of the same， but that。Constant is not two buds。The square rootド。手续嗯。

let's prove the focus on number。Of nodes。Withft rank。

K is at most n divided by squared root of2 power。Okay。-1。哦。喂。30万对。嗯。Okay。And finally。

 let's focus this property is a little bit different from what we had last time last time we proved that time complexity will be in our Sacrament if we have properties something like that more than N。

But actually does't matter。You may have the same proof， but you have different constant。

 so this constant here only affect the constant factor of your time complexity， not the asymptotics。

So we'll just use the same proof as we did on the previous lecture for these on the number of nodes and have the same time complexity。

 but it's also be inverse second time complexity there。哼。Not basically all。

Thank you for watching again。I'm not sure if I want to have lecture。Till the February。 But if I will。

 I will。And notify you in the code for block。I hope it was helpful I'm not sure why youre washing this。

😊，I like this because its kind of little more complicated stuff。

 so when you learn something about algorithms and first。First， you think that algorithms are simple。

 so you have some simple algorithms like you have。I don't know the extratra。

 you have some simple data structures like Q stuff like this。

 and you kind at some point you kind of think that all algorithms are pretty simple。And。あなの。

I like then something is a little bit more challenging。

 so some algorithms are a little bit more challenging than just regular。

algorithms you use on you will never， I believe you will never use this audience in the code。

 but now actually for this algorithm， I think it's possible to use the code this。Yeah。

 I think it works actually pretty fast。All operations are simple and complex these goods。

 I believe it has good standard and good constant factor， so you may be。

have chance to use it at some point， but。I'm not sure。

 usually you have much simple algorithms in your。In the context， because during in the contest。

 you have such limited time。Okay。Okay， so thank you for watching again， see you。In February。

 thank you。嗯。So if you have any ideas about future lecturers， just let me know。ok见。Right here。

