# 【EDUCBA】AWS Elastic Beanstalk与云项目的持续集成⧸持续部署 ｜ AWS Elastic Beanstalk & CI⧸CD for p25 03_02_03_API实现 -BV1zXcKzNENN_p25-

What is the difference between potent post API put API requires an ID on which a particular document should be stored but post API does not require an ID it stores a particular document on the ID of its choice so lets see the implementation of both。

Firstly， well create an index with。Aviation 1， I'm taking this as the index name。

 That is a table name， according to the SQL database， and we will create。People。Disreet。Now。

 adding indexes into it that is adding that data into it firstly put。



![](img/0fb28192d4ee7010da2e6a6effb7a861_1.png)

A P usage document with I1， we can take any idea of our choice on which it can store that particular row。

Or document。 these are the columns。

![](img/0fb28192d4ee7010da2e6a6effb7a861_3.png)

Firstly， airline， that is which airline we will use， we will take。

This is just the sample data you can add your data according to your choice。

 I am just adding randomly so that we can move to the next step also。Pategory。

 that is what is the exact category that is is it domestic or international。



![](img/0fb28192d4ee7010da2e6a6effb7a861_5.png)

How source that is， is the particular flight is going from with with source。

 Let's just take it mobile。 This is a single road， which we are creating。Our destination。

Total flights。How many flights from Mumbai to Delhi are going on a single date。 Let's take it 7。



![](img/0fb28192d4ee7010da2e6a6effb7a861_7.png)

De。We'll talk about a single date on in our project。You can take any date of your choice。

ItDoesn't matter。An average rate。That is up to you Also， whatever price this is as a sample data。

 I am taking it by my own。 You can do it， according to yourself。

Run it as it has created the index with version and result is created successful。

Now in case of both CP。Lets let us just also see will change here only end we will see that how it works。

😔，Now we have seeing the implementation of post APII in post if you are providing any document document ID。

Then it is fine。 But if we will remove this document。

 I D and change certain things as a strange domestic mum by2 go4 and see if it works or not。 Now。

 here the I D is this。It provides its own default I。But it doesn't work that for put API。



![](img/0fb28192d4ee7010da2e6a6effb7a861_9.png)

If we see that this particular thing in put API。Then we can see that it is providing the error that you have to provide a particular I D to that。



![](img/0fb28192d4ee7010da2e6a6effb7a861_11.png)

Now， if I change that particular I to2。And run it。

![](img/0fb28192d4ee7010da2e6a6effb7a861_13.png)

Yes， it is created。Now， the put API and post API difference is quite clear to you Now。

 if you are implementing it then you will see the changes now we will create some of some more of the data from the single thing2 is created now creating the I3。



![](img/0fb28192d4ee7010da2e6a6effb7a861_15.png)

![](img/0fb28192d4ee7010da2e6a6effb7a861_16.png)

Now， change the airline also。You can put your sample data according to your choice。

 Im seeing it again and again。Cartman。I'm just not changing the data as I want the data to be shown of this particular data。



![](img/0fb28192d4ee7010da2e6a6effb7a861_18.png)

Lets just enter 4 to54 data，2 more data。So that we can have different data and we can see that in Kiana also a dashboard。



![](img/0fb28192d4ee7010da2e6a6effb7a861_20.png)

![](img/0fb28192d4ee7010da2e6a6effb7a861_21.png)

We are only using this particular sample data。

![](img/0fb28192d4ee7010da2e6a6effb7a861_23.png)

Because we want our final output to be stored in our dashboard。

 so we should have a variety of data for that。Okay。I think we created 4 to 50 let add two more。Yeah。

是。Yeah。不。Yeah。

![](img/0fb28192d4ee7010da2e6a6effb7a861_25.png)

Okay， we have created various data。You should always note that here index is a table name and document is to address a particular row of a table after using potent post APIpis now let us talk about the functionality of gett API also。



![](img/0fb28192d4ee7010da2e6a6effb7a861_27.png)

![](img/0fb28192d4ee7010da2e6a6effb7a861_28.png)

Now， firstly to fetch all the index present， that is we how many index are present we should fetch all the data using gett API Now for that we will use gett underscore gath underscore。

So to get flashlash cat， slash indices。Here we can see that yellow part is the how many index are present in here。

 We have aviation one， people 1， aviation countries data。 there are lots of。Indexes present in here。

And we are using aviation one。Now， secondly， to fetch all the details of a particular document。 well。

 if you have to find all the details like I and everything。



![](img/0fb28192d4ee7010da2e6a6effb7a861_30.png)

So we will use， okay。

![](img/0fb28192d4ee7010da2e6a6effb7a861_32.png)

Aviation1。Underschool dog。And give the name of any I D， which you have entered during the put API。

 Lets to say 3。 See if we can have the data or not。 Yes， we have this。

 It is of I D 3 sequence number， primary temp and all the information of this。 Now， if you want。



![](img/0fb28192d4ee7010da2e6a6effb7a861_34.png)

![](img/0fb28192d4ee7010da2e6a6effb7a861_35.png)

To fetch only the data entered in a particular document， then we only use get API as。



![](img/0fb28192d4ee7010da2e6a6effb7a861_37.png)

Gt aviation1。Flash， just a source。That is underscore source of any idea of your choice。Lets see4。

 Okay， we got the data and there is no any other information。

 just the information which you have entered in the put API is present。

There is one more usage of get API that is to fetch all the data of a particular index。

 all the data we have entered in the index aviation1 during the put API we will fetch all the data of that。

 how we will use it。Aviation1 again。Search。Qury， column。And then， finally。Mat all。

Let's see if we get the data or not。

![](img/0fb28192d4ee7010da2e6a6effb7a861_39.png)

You can see that you get all the information。

![](img/0fb28192d4ee7010da2e6a6effb7a861_41.png)

And each data，1 by one。On the basis of I D， I D1， after that， we have entered this one with I D。

 we have entered that using the post API if you remember in our previous video， I D 2。



![](img/0fb28192d4ee7010da2e6a6effb7a861_43.png)

![](img/0fb28192d4ee7010da2e6a6effb7a861_44.png)

3。7，4，5。This is the all of the data which we have entered using our put and post APIs so get is clear to you。

Now， moving forward towards the delete API。 now， finally deleting the data data on the basis of document。

 So how do we do that。

![](img/0fb28192d4ee7010da2e6a6effb7a861_46.png)

Delete。Aviation 1。And score dog。Let's just delete that random。Id。Which we have entered from post API。

 we copy it。

![](img/0fb28192d4ee7010da2e6a6effb7a861_48.png)

And put it over here。 Let's see it gets deleted or not。Deleted successful。



![](img/0fb28192d4ee7010da2e6a6effb7a861_50.png)

Let's see it。It comes in all the A concept。You can see that it is not present now。In all the API。

 that means it is deleted。

![](img/0fb28192d4ee7010da2e6a6effb7a861_52.png)

Okay。Now， if you want to delete a particular index， similar thing delete and the index name。



![](img/0fb28192d4ee7010da2e6a6effb7a861_54.png)

We have created random indexes。Let's see if we can delete this particular index or not。



![](img/0fb28192d4ee7010da2e6a6effb7a861_56.png)

Error， I think it has not found any。Index with the name people。We can find the index using this API。

 Lets see if we have any other index。

![](img/0fb28192d4ee7010da2e6a6effb7a861_58.png)

![](img/0fb28192d4ee7010da2e6a6effb7a861_59.png)

Okay， we can delete this index also。 So we take the name again， copy it。And delete。Index， not found。

I think。😔。

![](img/0fb28192d4ee7010da2e6a6effb7a861_61.png)

Okay， we'll take another index Also。 Let's take people1。I think this is not the index。



![](img/0fb28192d4ee7010da2e6a6effb7a861_63.png)

O， acknowledged and true。 it has deleted。Oh， yes， there's no people run out here。

That means it is deleted。Okay， there is also。

![](img/0fb28192d4ee7010da2e6a6effb7a861_65.png)

There is also another API with the name head。Whi just gives the information of the presence of document in a particular index how。

Let's see its implementation。 Also， it just give the information only。

The if that particular document is present or not。Let's see1 if it is present or not。

You can see that yes， it is present。 we have already entered the index one。

documentcument with the ID1 also if we enter any random number for example， this。

 let's see if it is knowledged or not。

![](img/0fb28192d4ee7010da2e6a6effb7a861_67.png)

No， it is giving the error that means this index is not present。



![](img/0fb28192d4ee7010da2e6a6effb7a861_69.png)