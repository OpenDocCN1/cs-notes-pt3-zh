# 【Amazon Web Services】AWS云基础 ｜ The ABCs of AWS： Learn the Basics of the AWS Cloud p14 03_01_05_n-is-for-amazon-neptune -BV1MnrHBCEmT_p14-

This is AWS ABCs。 Today's letter is N， and the service is Amazon Neptune。

 It's true that database options were once limited with relational databases being the default choice for most applications。

 However， modern application demands can sometimes strain relational databases。

 depending on the use case。 especially when you have highly interconnected datas。

 where the relationship between the data is just as important as the data itself。

 using a relational database for these sorts of use cases can require you to write complex queries and it also can lead to performance issues as the data size grows。

 Gph databases like Amazon Neptune can be a better fit for certain applications and can provide better performance。

 Gph databases are optimized to store and query the relationships between data。

 So whenever connections or relationships are at the core of the data that you're trying to model。

 graph databases can be a great choice。 For example， social media。



![](img/80e14e91e44dc828fb1c09caaaaf01ca_1.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_2.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_3.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_4.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_5.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_6.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_7.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_8.png)

Recommendation engines or fraud detection are all use cases where a graph database could be a good fit or you're trying to understand who is friends with whom or who transacts with whom or who collaborates with whom Amazon Neptune is a fully managed database service that makes it easier to build and run graph databases on AWS Neptune is optimized to store billions of relationships and gives you millisecond latency when querying your graph It can also support hundreds of thousands of queries per second。

 So this database is built for both speed and scale。 Neptune provides built in security features。

 continuous backups and option for serverless compute and integrations with other AWS services。

 The easiest way to create an Amazon Neptune database cluster is to use an AWS cloud formation template which will create all of the required resources for you without you having to go in and build everything by hand Under the hood these database clusters are。



![](img/80e14e91e44dc828fb1c09caaaaf01ca_10.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_11.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_12.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_13.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_14.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_15.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_16.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_17.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_18.png)

up of Amazon E C2 instances you can select the best EC C2 instance type for your use case。

 or you can choose to use the serverless instance type for scaling your database cluster。

 they are built in features that you can use The primary storage for Neptune is external to the database instances that make up the cluster。

 which is your compute This means that compute and storage can scale independently of each other。

 Neptune storage scales automatically as your data grows up to 128 once you've created your database cluster。

 you can connect to it and run queries using query languages like Gremlin open cipher and sparkle at times it might be helpful to visualize your query results and Neptune workbench in many cases can create a visual diagram of your query results as well as returning them in a tabular form。

 Neptune also supports global databases so you can run your globally distributed application against one。



![](img/80e14e91e44dc828fb1c09caaaaf01ca_20.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_21.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_22.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_23.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_24.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_25.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_26.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_27.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_28.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_29.png)

Database that spans multiple AWS regions All right， that's it for Amazon Neptune as always。

 check out the AWS documentation or AWS skill builder if you want to learn more and let me know what you think is coming up next in the comments and stay tuned for more AWS ABcs。



![](img/80e14e91e44dc828fb1c09caaaaf01ca_31.png)

![](img/80e14e91e44dc828fb1c09caaaaf01ca_32.png)