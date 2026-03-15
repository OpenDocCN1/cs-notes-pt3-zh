# 【剑桥大学-•-中英】分布式系统讲座-p04-P04-Distributed-Systems-2.1---The-two-generals-problem--BV1NwQhYeEyV_p4-

Hello everybody， welcome back in the last lecture we introduced distributed systems by looking at some concrete examples such as the web and RPC which are examples of client server systems。

In this lecture， we're going to move things to a little bit more abstract and a little bit more general model。

 and we're going to talk about system models for distributed systems。

 which are descriptions of the assumptions that we make when we are designing an algorithm to run in a distributed systems。

 So a system model is very important because as we discussed。

 things can go wrong in a distributed systems， nodes can crash， networkss can fail and so on。

 and we have to be precise about what failures we are assuming are possible and what failures we are assuming are not possible。

So we're going to start this by looking at two classic thought experiments from distributed systems。

 the two generals problem and the Byzantine general's problem。

 and we're going to start now with the two generals problem。

So this is it's kind of like a military analogy so I'm sorry about that。

 I'm not really a big fan of that， but it's widely known as the two generals problems so I'm just going to stick with the convention here and so the setting of this experiment is that we have two armies。

 each army is controlled by one general and these armies are wanting to attack and capture a city。

Now， the city is well defended。 And so if only one of the Army'ies attacks at one time。

 that army will get defeated。 And so it's very important that if the two generals are going to attack。

 they attack at the same time， because then if both the armies attack at the same time。

 they know that they are going to win。

![](img/624521b93ef73a86e46dbf067ab1cdb9_1.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_2.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_3.png)

So you can see from this truth table here what happens is， okay， it'， it's al right。

 If neither of the two armies attacks， but if only one of the two armies attacks， then it's。

 it's all going to go terribly wrong。 So what we really want is that one army attacks。

 if and only if the other army attacks。 So both are armies attack together。



![](img/624521b93ef73a86e46dbf067ab1cdb9_5.png)

Now， what makes this difficult is that the two generals can't just talk to each other and agree on their plan of when to attack。

 but they can only communicate via messengers。 and so these messengers。

 there are people who run with the messengers through the forest and as they run through the forest。

 they might get captured by forces of the city。

![](img/624521b93ef73a86e46dbf067ab1cdb9_7.png)

And so whenever an whenever one of the general sends a messenger to the other general。

 that message may or may not get through。 And there's no way for the sender of the message to know whether the message got through except by receiving a response。

 And so the problem here is now this。 So imagine， for example。

 General 1 has decided to attack on 10 November。 And so he sends a message to General 2。

 saying we're going to attack on 10th November。 Are you okay where that。

 And General2 receives the message and says， yes， I'm on board。

 We're going to attack together on 10 November sends that response back。 But unfortunately。

 the response message is captured。 So the initial message to request get through。

 but the response is lost。 And so now， General  one does not receive a response。



![](img/624521b93ef73a86e46dbf067ab1cdb9_9.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_10.png)

Now， this， this is one scenario of what could happen。 Here's another scenario of what could happen。

 It could also happen that General  one sends a message attack on 10 November to General 2。

 But that initial message is lost and never get through to General 2。 And now。

 General 2 doesn't receive any message。 So he's not going to respond either。

 And the end result is also the general  one does not receive a response。

 So in both of these two cases。The only thing that General one observes is no response。

But General 1 does not know whether there's no response because the initial message didn't get through or whether the response was lost。

 But there's a big difference between the two of these， because from General2's point of view。

 in the first case， General2 has agreed to attack。 In the second case。

 General2 doesn't even know about the attack。 So they look the same from General2's point of view。

 but they look very different from General， sorry， they look the same from General One's point of view。

 but they look very different from General2's point of view。

So let's try to design an algorithm which will nevertheless get the two generals into agreement and so。



![](img/624521b93ef73a86e46dbf067ab1cdb9_12.png)

Let's think about it。 first of all， from the point of view of General  one。

 General one basically has two choices。 Either General one is going to always attack no matter whether any response is received。

Or general 1 is going to wait and only attack if it receives a response from General 2。

 So let's start with the first case。 So General  one always attacks， even if no response is received。

 So in this case， General 1 wants to make sure that General 2 is also going to attack because also because otherwise。

 General 1 is going to be in a problem， problematicmatic situation。

 So we could say that general 1 is going to send lots and lots and lots of messengers over to general 2。

 all saying attack at this time， attack， attack。And if one of those get through。

 then things are probably okay because General 2 knows that general one is always going to attack。

 So General 2 knows that it's safe。For General2 to also go into battle。

Even without responding to General one， because after all。

 General one has promised that General one is always going to attack。However。

 it could happen that all of the messengers are lost。 And so in this case。

 General 2 does not know about the attack。 So General 1 ends up going into battle alone and losers。

So that means this first option of General 1 always attacking is not really great。

 So let's consider the alternative， which is that General 1 does not promise to always attack。

 But General 1 will only attack if it receives a positive response from General 2。 And in this case。

 General 1 is safe because General1 knows that it will only go into battle if General 2 is going into battle。



![](img/624521b93ef73a86e46dbf067ab1cdb9_14.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_15.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_16.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_17.png)

But now， if you think about it from General2's point of view， now， General 2。

Knows that the that General  one will only go into attack if the response from General 2 to General 1 gets through。

 because after all， General 1 is waiting for that response from number2。

 And so now the General 2 is in exactly the same situation as General 1 was in the first option。

 And that is， either General 2 must commit to always attack in which case he risks being alone in the battle。

 or General 2 will wait for a response from General 1。 But now， you know， General 1 has to reply。

 And so you end up with these potentially infinite chains of， yes， yes， I'm going to attack。 Okay。

 I'm going to attack if you attack。 Yes， O， I will attack。 But only if you also attack。 Yes， yes。

 already said， I'm going to attack and so on。 And so they have to send each other back in forth these messages。

 you get actually an infinite chain before there's any certainty that they actually both going to attack together。



![](img/624521b93ef73a86e46dbf067ab1cdb9_19.png)

And so what is this is called in distributed systems。

 the problem of having no common knowledge so there's no knowledge in the system that one node knows and the other node knows that the first node knows it and the first node knows that the second node knows that the first node knows it and so on。

 So you can construct these arbitrary chains and the end result is just that no matter how many finite sequences of messages we send back and forth。

 we never actually have absolute certainty that general one is going to attack。

 if only if General 2 is going to attack。 So you can build up gradually increasing like probabilistic certainty may be。

 depending on your assumptions of whether messengers get captured or not。

 but it's actually impossible to reach complete certainty here。



![](img/624521b93ef73a86e46dbf067ab1cdb9_21.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_22.png)

Now。Let's take this abstract thought experiment and apply to a concrete example。

 So we had in the last lecture， this example of an online shop making an R PCC request to a payment service in order to charge a credit card。

 and really what we want here is that the online shop dispatches the goods。

 if and only if the customer pays for the goods。

![](img/624521b93ef73a86e46dbf067ab1cdb9_24.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_25.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_26.png)

Because you can imagine， you know， if the online shop dispatches the goods。

 but the payment service does not charge the credit card。

 then the shop is unhappy because the shop has just given away some goods for free。



![](img/624521b93ef73a86e46dbf067ab1cdb9_28.png)

If the， if the online shop does not dispatch the goods。

 but the payment service does charge the credit card。

 then the customer is unhappy because the customer got charged without receiving any goods。

 So really， what we want is something that looks extremely similar to the two generals problem here that the online shop dispatches the goods。

 if and only if the payment service charges the card and。



![](img/624521b93ef73a86e46dbf067ab1cdb9_30.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_31.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_32.png)

As you can imagine， the RPC between the online shop and the payment service looks very much like the messengers running through the forest in the two generals problem。

 which is to say that the messages might get lost， either one or the other might get lost。

 and so it is actually not possible for the online shop and the payment service to achieve dis certainty that one action will happen if and only if the other other action happens。



![](img/624521b93ef73a86e46dbf067ab1cdb9_34.png)

Now， in practice， actually， of course， online shops do work。

 the reason they work is because there are a bunch of secondlevel safeguards then which ensure a reasonable outcome。

 So for example， if it turns out that the payment the card got charged but the online shop doesn't actually have the goods in stock anymore。

 then the online shop will just send an apology email saying， oh sorry， actually we're out of stock。

 we've refunded your card And so that way is fine。 And so this it's possible to get out of a situation because the charge is actually a revoccable action。

 it's possible to refund the charge and therefore it's possible to get back into into a safe state where neither the goods dispatch nor the payment has effectively happened。



![](img/624521b93ef73a86e46dbf067ab1cdb9_36.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_37.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_38.png)

Or another option is， you know that the payment service may or may not have charged a card。

 And so the online shop， then when the network is is repaired and the messages can get through again。

 then the online shop checks with the payment service saying now。

 did you actually charge that card or not， because I never heard back from you whether you charge it or not。

 And so what will probably happen is that the payment service will always go ahead and charge a card because even if it's not certain that the online shop is going to dispatch the goods。

 because in this case， it's fine because the payment could get refunded if necessary。

 So that is the way in which this online shopping problem is not actually exactly the same as as the two generals problem。

 But nevertheless， the two generals problem does illustrate this issue of uncertainty that we have in a distributed system when we're not sure if the messages got through or not。



![](img/624521b93ef73a86e46dbf067ab1cdb9_40.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_41.png)

![](img/624521b93ef73a86e46dbf067ab1cdb9_42.png)