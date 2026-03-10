# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p12 P12 03_领域建模-评估关联与属性 -BV1MMEjzoEhg_p12-

And then there are also some rules for you to eliminate irrelevant associations。

If some of the associations， they are irrelevant to the domain model， you eliminate them。

If some of the associations， they are at operations， again， you can eliminate them。

If there are some tenary associations， you may consider decomposing them into multiple binary associations because as I've said before。

 we try to avoid using tenary associations because it's going to make your diagram more difficult to read。

And then if some of the associations， they are derived associations。

 so for example you can use this path right A to C， C to B to go from A to B。

 or you can directly go from A to B okay if you can get the same information using this path A CB and also this path A B okay then you can eliminate one of the two paths but you have to be very careful before you remove a path in your class diagram。

 so now let's study an example from our exercises。

![](img/37d86334a39a6370b1be94e2f1bb5756_1.png)

Now， let's say we have this class diagram in this class diagram。

 we try to keep track all the transactions for different accounts and the accounts they belongs to different customers。

 Now we can see that we have a cycle in this diagram。 So can we remove one of link， let's say makes。

In the class diagram Gr。

![](img/37d86334a39a6370b1be94e2f1bb5756_3.png)

So now let's study the example in more details。And let's say this is actually the information being stored under the software system。

 So transaction T1 is actually a transfer between A1 and A2 from customer C1 and C2 Now let's say we only have the associations is against and also holds。



![](img/37d86334a39a6370b1be94e2f1bb5756_5.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_6.png)

Can we tell？Which customer initiated this transaction？

Whether the transaction is actually initiated by C1 or C2， can we tell？



![](img/37d86334a39a6370b1be94e2f1bb5756_8.png)

No， because using the information being stored under our system。

 we can actually tell this transaction is actually initiated by C1 or C2 so that's why we also need the association makes to tell us exactly who made or who started this transaction now with this association now we can tell。

 for example T1 is actually initiated by customer C1 using the additional link from the association makes。



![](img/37d86334a39a6370b1be94e2f1bb5756_10.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_11.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_12.png)

So in this very special case， we cannot remove the redundant path just because the two paths they have two different meanings okay one of the path means transaction is against which accounts and the accounts there from which customer okay and the other path means who actually initiated the transaction。

 so that's why we have to keep both the two paths。

![](img/37d86334a39a6370b1be94e2f1bb5756_14.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_15.png)

Because they have two different meanings。

![](img/37d86334a39a6370b1be94e2f1bb5756_17.png)

And again， if some of the associations they describe implementation constructs。

 you may eliminate them。

![](img/37d86334a39a6370b1be94e2f1bb5756_19.png)

For attributes， you double check whether those attributes。

 they are closely related to a class or an object within your class diagram。

 because a class should be simple and coherent。If the attributes they are not related to a class then you may eliminate them。

If some of the attributes they should be classes， then you make them classes。

If some of the attributes， they should be in an association class。

 then you should create an association class and put those attributes within that association class。



![](img/37d86334a39a6370b1be94e2f1bb5756_21.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_22.png)

And if there's some I that you can use to identify an instance of an object。

 you eliminate all the Is because Ids， right object identifiers。

 they should not be included in the domain model。 As an example， in the first exercise。

 we have Is as attributes， and we have to remove all of them。



![](img/37d86334a39a6370b1be94e2f1bb5756_24.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_25.png)

![](img/37d86334a39a6370b1be94e2f1bb5756_26.png)

Because they are not the real properties of the objects， they are simply artificial numbers。

And to make sure that our class diagram is going to be simple and also easy to read。

 we only keep the necessary attributes and ignore all the IDs。



![](img/37d86334a39a6370b1be94e2f1bb5756_28.png)

And then finally， for each class， we have to specify all the attributes， and then for each attribute。

 we have to specify the name， type and also multiplicity of the attribute。

And for each association we have to provide a name for the association， if it's a unary association。

 we also have to provide row names and also maybe multiplicity and also association class if needed。

And that's all I want to cover in this lecture。

![](img/37d86334a39a6370b1be94e2f1bb5756_30.png)