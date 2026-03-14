# 【克莱姆森大学】数据库管理系统 ｜ Database Management Systems p08 03_01_03_relational-database-model-overview -BV1y6rzBXE34_p8-

![](img/35211c1b6c6d0fb3755b1a2ed632dac9_0.png)

![](img/35211c1b6c6d0fb3755b1a2ed632dac9_1.png)

We're going to move into module three now， and this is about the relational database model。

So in this lesson you're going to focus on the relational database logical structure and basic components。

 we're going to get into a concept called relational algebra， but very high level， so don't worry。

Talk about some of the other components of a relational database such as the data dictionary and system catalog。

Entities and relationships and how those pertain to the relational data model。

And also data redundancy and indexing。All of the topics in this lesson correspond to chapter 3 in our reading。

So let's go ahead and jump in and talk about the relational database logical structure and components。

So the beauty of the relational data model is it lets you as a database designer focus on data in its relationships and not have to worry about specifics of how the database is stored on disk。

 and you can really focus on the logical versus the physical。

So it helps you with simplicity and we're going to talk about specifics on how that simplicity is represented The key concept in relational databases is the table and it's a twodisional structure of rows and columns so if you've used Excel。

 which I'm sure most of you have， if not all of you it's very similar to the sheets you have in Excel with the each row and then the fields。

 so the difference is that it's based on this concept of a relation and each table is also called a relation。

 but most people will refer to database tables as tables。So it's a persistent representation of data。

 so maybe the data is on the disk and it looks a lot different than what you see in your table。

 but it's a logical view of all that data that's stored on the disk。For every attribute。

 every column there is a domain of allowable values and we're going to talk more about that。

And for every row， you'll have inter a relational database， a primary key。

 which is an attribute in that row， or could be multiple attributes that uniquely identify a row。

 and I guarantee we'll be talking a lot more about that and just in summary。

 this table gives you some of the key characteristics of a relational table that we just talked about two dimensional rows and columns。

 each row， which is also sometimes called a tuple is an occurrence of an entity。

Each column in the table is an attribute and each column has a name and each column and each attribute has a domain。

The key part of this is the primary key， which is 0。

8 on this table that each table must have an attribute or combination of attributes that uniquely identify each row。

The other thing that's important to know is that in the relation there is no necessarily any order of rows and columns。

 the database can be sorted when we get into selecting data from the tables。

 but it's immaterial to the DBMS， it just knows that it has a row with a primary key and a set of columns。

So what is a key， not all keys are primary keys， it's really just。

The concept of a attribute that can determine other attributes， so a primary key like I said。

 ensures that a row is uniquely identifiable， you can have attributes that may have some relationship to other attributes that aren't primary keys。

So a key is based on the concept of determination， so what that means is that you can figure out the value of one attribute based on the value of another and if you have that type of determination。

Then you have dependence across those attributes where one of the attributes is called the determinant or the key。

 which determines the value of the dependent。And these terms are used when you are looking at attributes in a table and trying to identify what are the various keys so just some other key definition。

 sorry about the word key used so much here you have any attribute or any set of attributes that makes up a primary key or a key is called a composite key。

 so it's more than one。And each individual attribute in that composite key is a key attribute。

You'll have a super key that is a key that can identify any row in the table。

And there may be multiple super keys， but a candidate key is the minimal of those that is it has this the least amount of attributes。

Needed to be a primary key。And then lastly， entity integrity。Is a condition。

 very important condition that you can be guaranteed with。

A relational database where each row has its own unique identity。

 and that's guaranteed by the primary key。Sometimes you'll have。

Values that are null in your database in one of the columns。

 but it is not allowed as part of the primary key， and a null can mean different things。

 It could mean it's an unknown value， It's actually missing， or it's a not applicable condition。

And sometimes you'll have database designers who do not allow any nulls for any attributes in their database。

 and there's ways to deal with that if you're in these conditions and we'll talk about that at a later point。

So another concept in relational databases that is extremely important is the concept of a foreign key。

And a foreign key is a primary key of one table that's been。Placed in another table。

 so it is referencing this table references the primary key in another table。

And I'll show you on the next slide， an example。And if you have a foreign key。

Then you will have the condition of referential integrity if there is either a null or matching entry in the primary key of the related table。

 so this is something you're guaranteed by using the foreign key。And last but not least。

 in our definition of keys is the concept of a secondary key and that's key used。

For data retrieval purposes， so suppose that you have a table that has information about a student at a college。

And you have as one of the attributes， their class， so whether they're a freshman， a sophomore。

 junior or senior and you happen to search on that a lot or sort on that。

 you could identify that as a key for data retrieval purposes and that is something we'll talk about when we get into data performance。

So here's an example to show you the concept of a primary key and a foreign key across two tables。

 One is the product table。 So if you look at the product table it has a list of various products that are in the product description their prices how much on hand they have and then what vendor they come from So the claw hammer has a vendor code of 232 which is linked into the vendor table So if I look at 232 the vendor contact is Annaise Crystal you have her phone number And so I have a dependency between these two tables a。

Link that tells me that I cannot have a product that either has。

 Does it has an incorrect vendor or it has。Missing vendors。

 So now it's not clear from this example if nulls are allowed。

But it is possible that you could have a new product that you put into your inventory that does not yet have a vendor identified。

 and in that case， if you had a null， that should be okay as long as you defined your foreign key for the product table as allowing nullles。

So here and if you look at the vendor table， it does not have any foreign keys， but both product。

And vendor have primary keys。 They must have primary keys。

To ensure entity integrity and the product code is the or the primary key for the product table。

 so it's a unique identifier or product and vendor code has the vendor。

 I mean vendor has the vendor code as the primary key。

Entity integrity and referential integrity extremely important to good database design。

And you'll be happy to know when you start using relational databases。

 they enforce the rules automatically。 So in our case， where I had the product and the vendor。

 If I tried to add a product with a vendor code of 227， which did not exist。

 it would give you an error and say invalid vendor。 So it will take care of that。

 Or if I tried to enter a row into the product table with the same product code as claw hammer。

 it'll give you an error and say this product already exists。

 So the database takes care of all of that integrity management by and your job， though。

 is to define the。😊，Foreign keys and the primary keys to ensure that integrity is enforced。

And here's just a summary of entity integrity and referential integrity， as we said。

The entity integrity is requires that all primary key entries are unique and no part of a primary key may be null。

And the referential integrity is enforced using the foreign key， it could have a null entry。

 and that is determined based on when you create that table with its foreign key。

So here's another example of two tables， customer and agent。

Customer table has a primary key of customer code。The values are。10010 through 10019。

 this is clearly just a subset of the table， and then you have an agent table with 501 through 503 agents。

 So the customer code is your primary key for customer and agent code is the primary key for agent。

Then looking at your customer table， you see that you have a foreign key agent code。

 So it tells me that the customers。Alfred Rammus and Kathy Smith。

And James Brown all have the same agent 502 with a last name of Han， and that's their contact。

 and it shows also the agent year to date sales。Now you'll notice that all Alowski does not have an agent code。

Which is perfectly fine， we assume， because of this must allow nu。Now。

 what I've also seen a lot in practice of databases is。There'll be an agent code called 99，9。

Unassigned with and this is what is used if you do not want to allow null。

 So Paul Oloowski could have an agent code of 9，9，9。

 And then you could go clean that up later and change it to the correct agent。And again。

 so this is real world example where you would be adding a new customer and you don't know who their agent is yet。

 let's say they call into your call center and they say they want to buy some insurance。

You immediately get them in your database， you don't want to lose the customer and you'll tell them you'll get back to them or an agent will get back to them and so you would have a blank or null an agent code。

And assign that later， so you need to make sure， you know that referential integrity allows the foreign key allows a allll to support those types of business conditions where a value is not known at a certain time。

Another thing to think about is if you were to put data in a table。

If I put the data for customer in the table before I created the agent table。

I would get a lot of errors because it would say that I have a foreign key of 502 and it'd say there's no agent 502。

So there is requirements on the order you create your data to ensure you don't get a lot of errors because of referential integrity。

 so you would create the agent table first with all the agent data and then put the customers in and assign them their respective agent codes。

And that's really when you initially load your data as you continue to add agents。

 if you added a new agent and you're going to have customers immediately assigned to that agent again。

 you would need to put the agent in the table first and then you could create customers assigned to that agent。

Okay， so that's the part one of our module three， and we will continue on talking about relational algebra in the next part。



![](img/35211c1b6c6d0fb3755b1a2ed632dac9_3.png)